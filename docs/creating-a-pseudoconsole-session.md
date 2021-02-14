---
title: 建立 Pseudoconsole 工作階段
description: Pseudoconsole 工作階段可讓應用程式主控字元模式應用程式的活動
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api, conpty, pseudoconsole, windows pty, 虛擬主控台
ms.localizationpriority: high
ms.openlocfilehash: c1a83b308e4d9a23fdb6b2778561030e619dfdb3
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357928"
---
# <a name="creating-a-pseudoconsole-session"></a>建立 Pseudoconsole 工作階段

Windows Pseudoconsole (有時也稱為虛擬主控台、ConPTY 或 Windows PTY) 是專為建立字元模式子系統活動的外部主機而設計的機制，而這些子系統活動會取代預設主控台主機視窗的使用者互動性部分。

主控 Pseudoconsole 工作階段與傳統主控台工作階段有點不同。 當作業系統辨識出字元模式應用程式即將執行時，傳統的主控台工作階段就會自動啟動。 相反地，Pseudoconsole 工作階段和通訊通道必須先由主控應用程式建立，才能使用要託管的子字元模式應用程式建立程序。 子程序仍會使用 [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) 函式來建立，但有一些其他資訊會引導作業系統建立適當的環境。

您可以在[初始公告部落格文章](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/)中找到有關此系統的其他背景資訊。

在我們的 GitHub 存放庫 [microsoft/terminal](https://github.com/microsoft/terminal) 的 samples 目錄中，可取得使用 Pseudoconsole 的完整範例。

## <a name="preparing-the-communication-channels"></a>準備通訊通道

第一個步驟是建立一對同步通訊通道，這對通道會在建立 Pseudoconsole 工作階段期間提供，以便與託管的應用程式進行雙向通訊。 這些通道會由 Pseudoconsole 系統使用 [**ReadFile**](/windows/desktop/api/fileapi/nf-fileapi-readfile) 和 [**WriteFile**](/windows/desktop/api/fileapi/nf-fileapi-writefile) 搭配 [同步 I/O](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).進行處理。 只要非同步通訊不需要 [**重疊的**](/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped)結構，就可以接受檔案或 I/O 裝置控點 (例如檔案資料流或管道)。

> [!WARNING]
>若要避免競爭條件和鎖死，我們強烈建議在個別的執行緒上為每個通訊通道提供服務，以在您的應用程式內維護自己的用戶端緩衝區狀態和傳訊佇列。 在同一個執行緒上為所有 Pseudoconsole 活動提供服務可能會導致鎖死，其中有一個通訊緩衝區已滿並在您嘗試在另一個通道上分派封鎖要求時等候您的動作。

## <a name="creating-the-pseudoconsole"></a>建立 Pseudoconsole

使用已建立的通訊通道，識別輸入通道的「讀取」端和輸出通道的「寫入」端。 呼叫 [**CreatePseudoConsole**](createpseudoconsole.md) 來建立物件時，會提供這一對控點。

建立時，需要有代表 X 和 Y 維度的大小 (以字元數表示)。 這些維度將會套用至最終 (終端機) 展示視窗的顯示介面。 這些值用於在 Pseudoconsole 系統中建立記憶體內部緩衝區。

緩衝區大小會提供答案給用戶端字元模式應用程式，以便其使用 [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) 之類的 [用戶端主控台函式](console-functions.md)來探查資訊，並在用戶端使用 [**WriteConsoleOutput**](writeconsoleoutput.md) 之類的函式時，規定文字的版面配置和定位。

最後，建立 Pseudoconsole 時會提供 flags 欄位，以執行特殊功能。 根據預設，將此值設定為 0，表示沒有任何特殊功能。

此時，只有一個特殊旗標可用於要求從已經連結至 Pseudoconsole API 呼叫端的主控台工作階段繼承游標位置。 這適合使用於以下更進階的案例：正在準備 Pseudoconsole 工作階段的主控應用程式本身也是另一個主控台環境的用戶端字元模式應用程式。

下面提供的範例程式碼片段利用 [**CreatePipe**](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe) 來建立一對通訊通道和建立 Pseudoconsole。

```C

HRESULT SetUpPseudoConsole(COORD size)
{
    HRESULT hr = S_OK;

    // Create communication channels

    // - Close these after CreateProcess of child application with pseudoconsole object.
    HANDLE inputReadSide, outputWriteSide;

    // - Hold onto these and use them for communication with the child through the pseudoconsole.
    HANDLE outputReadSide, inputWriteSide;

    if (!CreatePipe(&inputReadSide, &inputWriteSide, NULL, 0))
    {
        return HRESULT_FROM_WIN32(GetLastError());
    }

    if (!CreatePipe(&outputReadSide, &outputWriteSide, NULL, 0))
    {
        return HRESULT_FROM_WIN32(GetLastError());
    }

    HPCON hPC;
    hr = CreatePseudoConsole(size, inputReadSide, outputWriteSide, 0, &hPC);
    if (FAILED(hr))
    {
        return hr;
    }

    // ...

}
```

> [!NOTE]
>此程式碼片段不完整，僅用於示範此特定呼叫。 您必須適當地管理 **HANDLE** 的存留期。 如果無法正確管理 **HANDLE** 的存留期，可能會導致鎖死情況，尤其是同步 I/O 呼叫。

完成 [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) 呼叫來建立已連結至 Pseudoconsole 的用戶端字元模式應用程式時，應該從此程序釋放在建立期間指定的控點。 這會減少基礎裝置物件上的參考計數，並可讓 I/O 作業在 Pseudoconsole 工作階段關閉其控點複本時，正確地偵測中斷的通道。

## <a name="preparing-for-creation-of-the-child-process"></a>準備建立子程序

下一個階段是準備 [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) 結構，以便在啟動子程序時傳達 Pseudoconsole 資訊。

此結構能夠提供複雜的啟動資訊，包括可供建立程序和執行緒的屬性。

以雙重呼叫的方式使用 [**InitializeProcThreadAttributeList**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist)，先計算保留清單所需的位元組數目、配置所要求的記憶體，然後再次呼叫以提供不透明的記憶體指標，使其設定為屬性清單。

接下來，呼叫 [**UpdateProcThreadAttribute**](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) 來傳遞已初始化的屬性清單，其中包含 **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE** 旗標、Pseudoconsole 控點，以及 Pseudoconsole 控點的大小。

```C

HRESULT PrepareStartupInformation(HPCON hpc, STARTUPINFOEX* psi)
{
    // Prepare Startup Information structure
    STARTUPINFOEX si;
    ZeroMemory(&si, sizeof(si));
    si.StartupInfo.cb = sizeof(STARTUPINFOEX);

    // Discover the size required for the list
    size_t bytesRequired;
    InitializeProcThreadAttributeList(NULL, 1, 0, &bytesRequired);

    // Allocate memory to represent the list
    si.lpAttributeList = (PPROC_THREAD_ATTRIBUTE_LIST)HeapAlloc(GetProcessHeap(), 0, bytesRequired);
    if (!si.lpAttributeList)
    {
        return E_OUTOFMEMORY;
    }

    // Initialize the list memory location
    if (!InitializeProcThreadAttributeList(si.lpAttributeList, 1, 0, &bytesRequired))
    {
        HeapFree(GetProcessHeap(), 0, si.lpAttributeList);
        return HRESULT_FROM_WIN32(GetLastError());
    }

    // Set the pseudoconsole information into the list
    if (!UpdateProcThreadAttribute(attributeList,
                                   0,
                                   PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE,
                                   hpc,
                                   sizeof(hpc),
                                   NULL,
                                   NULL))
    {
        HeapFree(GetProcessHeap(), 0, si.lpAttributeList);
        return HRESULT_FROM_WIN32(GetLastError());
    }

    *psi = si;

    return S_OK;
}

```

## <a name="creating-the-hosted-process"></a>建立託管的程序

接下來，呼叫 [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) 來傳遞 [**STARTUPINFOEX**](/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) 結構和可執行檔路徑，以及任何其他組態資訊 (如果適用的話)。 呼叫時，請務必設定 **EXTENDED_STARTUPINFO_PRESENT** 旗標，以警示系統：Pseudoconsole 參考包含在擴充資訊中。

```C
HRESULT SetUpPseudoConsole(COORD size)
{
    // ...

    PCWSTR childApplication = L"C:\\windows\\system32\\cmd.exe";

    // Create mutable text string for CreateProcessW command line string.
    const size_t charsRequired = wcslen(childApplication) + 1; // +1 null terminator
    PWSTR cmdLineMutable = (PWSTR)HeapAlloc(GetProcessHeap(), 0, sizeof(wchar_t) * charsRequired);

    if (!cmdLineMutable)
    {
        return E_OUTOFMEMORY;
    }

    wcscpy_s(cmdLineMutable, bytesRequired, childApplication);

    PROCESS_INFORMATION pi;
    ZeroMemory(&pi, sizeof(pi));

    // Call CreateProcess
    if (!CreateProcessW(NULL,
                        cmdLineMutable,
                        NULL,
                        NULL,
                        FALSE,
                        EXTENDED_STARTUPINFO_PRESENT,
                        NULL,
                        NULL,
                        &siEx.StartupInfo,
                        &pi))
    {
        HeapFree(GetProcessHeap(), 0, cmdLineMutable);
        return HRESULT_FROM_WIN32(GetLastError());
    }

    // ...
}
```

> [!NOTE]
> 在託管的程序仍在啟動和連線時關閉 Pseudoconsole 工作階段，可能導致用戶端應用程式所顯示的錯誤對話方塊。 如果託管的程序獲得用於啟動的 Pseudoconsole 控點無效，則會顯示相同的錯誤對話方塊。 在託管的程序初始化程式碼中，兩個情況都相同。 失敗時，託管的用戶端應用程式中的快顯對話方塊會顯示 `0xc0000142`，其中包含詳細說明初始化失敗的當地語系化訊息。

## <a name="communicating-with-the-pseudoconsole-session"></a>與 Pseudoconsole 工作階段通訊

成功建立程序後，主控應用程式即可使用輸入管道的寫入端，將使用者互動資訊傳送至 Pseudoconsole 和輸出管道的讀取端，以從虛擬主控台接收圖形化展示資訊。

其完全由主控應用程式來決定如何處理進一步的活動。 主控應用程式可能會在另一個執行緒中啟動視窗，以收集使用者互動輸入，並將其序列化為 Pseudoconsole 和託管字元模式應用程式的輸入管道寫入端。 另一個執行緒可能會啟動，以清空 Pseudoconsole 的輸出管道讀取端，將文字和[虛擬終端機序列](console-virtual-terminal-sequences.md)資訊解碼，並將其呈現到螢幕上。

執行緒也可用於將來自 Pseudoconsole 通道的資訊轉送到不同的通道或裝置 (包括網路)、將遠端資訊轉送到另一個程序或電腦，以及避免資訊的任何本機轉碼。

## <a name="resizing-the-pseudoconsole"></a>調整 Pseudoconsole 的大小

在執行階段的整個過程中，可能會有由於使用者互動或從其他顯示/互動裝置頻外收到的要求，而需要變更緩衝區大小的情況。

這可以透過 [**ResizePseudoConsole**](resizepseudoconsole.md) 函式，同時指定緩衝區的高度和寬度 (以字元數表示) 來完成。

```C
// Theoretical event handler function with theoretical
// event that has associated display properties
// on Source property.
void OnWindowResize(Event e)
{
    // Retrieve width and height dimensions of display in
    // characters using theoretical height/width functions
    // that can retrieve the properties from the display
    // attached to the event.
    COORD size;
    size.X = GetViewWidth(e.Source);
    size.Y = GetViewHeight(e.Source);

    // Call pseudoconsole API to inform buffer dimension update
    ResizePseudoConsole(m_hpc, size);
}
```

## <a name="ending-the-pseudoconsole-session"></a>結束 Pseudoconsole 工作階段

若要結束工作階段，請使用原始 Pseudoconsole 建立中的控點來呼叫 [**ClosePseudoConsole**](closepseudoconsole.md) 函式。 任何已連結的用戶端字元模式應用程式 (例如來自 [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) 呼叫的應用程式) 都會在工作階段關閉時終止。 如果原始子系是建立其他程序的 Shell 類型應用程式，則樹狀結構中任何已連結的相關程序也會一併終止。

> [!WARNING]
>如果以單一執行緒同步方式使用 Pseudoconsole，則關閉工作階段有數個副作用，可能會導致鎖死狀況。 關閉 Pseudoconsole 工作階段的行動可能會對應該從通訊通道緩衝區清空的 `hOutput` 發出最終框架更新。 此外，如果在建立 Pseudoconsole 時選取了 `PSEUDOCONSOLE_INHERIT_CURSOR`，則嘗試關閉 Pseudoconsole 而不回應游標繼承查詢訊息 (在 `hOutput` 上接收並透過 `hInput`回覆)，可能會導致另一個鎖死狀況。 建議在個別的執行緒上為 Pseudoconsole 的通訊通道提供服務，並且在用戶端應用程式結束或在呼叫 [**ClosePseudoConsole**](closepseudoconsole.md) 函式中完成卸除活動而自發性中斷連線之前，維持已清空和已處理狀態。
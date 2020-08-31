---
title: 建立 Pseudoconsole 會話
description: Pseudoconsole 會話可讓應用程式裝載字元模式應用程式的活動
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api，conpty，pseudoconsole，windows pty，虛擬主控台
ms.openlocfilehash: ec63cf4bfc1502aa37b0b336f1ffdc7bab2be07e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059222"
---
# <a name="creating-a-pseudoconsole-session"></a>建立 Pseudoconsole 會話

Windows Pseudoconsole （有時也稱為虛擬主控台、ConPTY 或 Windows PTY）是一種機制，其設計目的是要為字元模式子系統活動建立外部主機，以取代預設主控台主機視窗的使用者互動部分。

裝載 pseudoconsole 會話與傳統的主控台會話有點不同。 當作業系統辨識出要執行的字元模式應用程式時，傳統的主控台會話就會自動啟動。 相反地，在建立具有要裝載之子字元模式應用程式的處理常式之前，必須先由裝載應用程式建立 pseudoconsole 會話和通道。 子進程仍會使用 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 函式來建立，但會有一些額外的資訊，可指示作業系統建立適當的環境。

您可以在 [初始公告的 blog 文章](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/)中找到有關此系統的其他背景資訊。

您可以在範例目錄中的 GitHub 存放庫 [Microsoft/主控台](https://github.com/Microsoft/console) 取得使用 Pseudoconsole 的完整範例。

## <a name="preparing-the-communication-channels"></a>準備通道

第一個步驟是建立一對將在建立 pseudoconsole 會話期間提供的同步通道，以便與託管的應用程式進行雙向通訊。 Pseudoconsole 系統會使用 [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) 和 [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) 搭配 [同步 i/o](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output)來處理這些通道。 只要非同步通訊不需要重迭 [**的結構，**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) 就可以接受檔案或 i/o 設備控制碼，例如檔案資料流程或管道。

**注意：**

為了避免競爭情況和鎖死，強烈建議在個別的執行緒上提供每個通道的服務，以在您的應用程式中維護自己的用戶端緩衝區狀態和訊息佇列。 針對相同執行緒上的所有 pseudoconsole 活動提供服務，可能會導致當您嘗試在另一個通道上分派封鎖要求時，其中一個通訊緩衝區已填滿，並且正在等候您的動作時，就會產生鎖死。

## <a name="creating-the-pseudoconsole"></a>建立 Pseudoconsole

使用已建立的通道，識別輸入通道的「讀取」結尾和輸出通道的「寫入」結尾。 呼叫 [**CreatePseudoConsole**](createpseudoconsole.md) 時，會提供這組控制碼來建立物件。

建立時，也會提供表示 X 和 Y 維度的大小 (以字元數為單位的) 。 這是將套用至最終 (終端) 展示視窗之顯示介面的維度。 這些值可用來在 pseudoconsole 系統內建立記憶體中的緩衝區。 

緩衝區大小提供用戶端字元模式應用程式的答案，這些應用程式會使用 [用戶端主控台功能](console-functions.md) （例如 [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) ）來探查資訊，並在用戶端使用 [**WriteConsoleOutput**](writeconsoleoutput.md)之類的函式時指定文字的版面配置和位置。

最後，在建立 pseudoconsole 時，會提供旗標欄位來執行特殊功能。 預設會將此值設定為0，而沒有特殊功能。

目前只有一個特殊旗標可要求從已經附加至 pseudoconsole API 呼叫端的主控台會話，要求資料指標位置的繼承。 這是為了在更先進的案例中使用，也就是正在準備 pseudoconsole 會話的裝載應用程式本身也是另一個主控台環境的用戶端字元模式應用程式。 

下面提供的範例程式碼片段會使用 [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) 來建立一對通道，並建立 pseudoconsole。

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


**注意**： 

此程式碼片段不完整，只用于示範此特定呼叫。 您將需要適當地管理 **控制碼**的存留期。 如果無法正確管理 **控制碼**的存留期，可能會導致鎖死的情況，特別是在同步的 i/o 呼叫中。

完成 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 呼叫以建立附加至 pseudoconsole 的用戶端字元模式應用程式時，應該從此進程釋放在建立期間提供的控制碼。 這會減少基礎裝置物件的參考計數，並允許 i/o 作業在 pseudoconsole 會話關閉其控制碼的複本時，適當地偵測到中斷的通道。

## <a name="preparing-for-creation-of-the-child-process"></a>準備建立子進程

下一個階段是準備 [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) 結構，以在啟動子進程時傳達 pseudoconsole 資訊。

此結構包含提供複雜啟動資訊的功能，包括處理常式和執行緒建立的屬性。

以雙呼叫方式使用 [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) ，以先計算保留清單所需的位元組數目、配置所要求的記憶體，然後再次呼叫，提供不透明的記憶體指標讓它設定為屬性清單。

接下來，呼叫 [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) 傳遞已初始化的屬性清單和旗標 **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**、PSEUDOCONSOLE 控制碼，以及 PSEUDOCONSOLE 控制碼的大小。

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

## <a name="creating-the-hosted-process"></a>建立託管進程

接下來，呼叫 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 以傳遞 [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) 結構，以及可執行檔的路徑，以及任何其他設定資訊（如果適用）。 請務必在呼叫時設定 **EXTENDED_STARTUPINFO_PRESENT** 旗標，以警示系統 pseudoconsole 參考包含在擴充資訊中。

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

**注意：**

當裝載的進程仍在啟動並聯機時，關閉 pseudoconsole 會話會導致用戶端應用程式顯示錯誤對話方塊。 如果裝載的進程具有不正確啟動 pseudoconsole 控制碼，就會顯示相同的錯誤對話方塊。 在託管的進程初始化程式碼中，兩種情況都相同。 失敗時，裝載用戶端應用程式中的快顯對話方塊會讀取 `0xc0000142` 詳細說明無法初始化的錯誤。

## <a name="communicating-with-the-pseudoconsole-session"></a>與 Pseudoconsole 會話通訊

成功建立程式之後，裝載應用程式可以使用輸入管道的寫入端，將使用者互動資訊傳送至 pseudoconsole，並將輸出管道的讀取端傳送到輸出管道，以從虛擬主控台接收圖形呈現資訊。 

它完全取決於裝載應用程式，以決定如何處理進一步的活動。 裝載應用程式可以在另一個執行緒中啟動視窗，以收集使用者互動輸入，並將其序列化為 pseudoconsole 和裝載的字元模式應用程式之輸入管道的寫入結尾。 您可以啟動另一個執行緒，以清空 pseudoconsole 輸出管道的讀取端、將文字和 [虛擬終端機序列](console-virtual-terminal-sequences.md) 資訊解碼，然後將其顯示在畫面上。 

執行緒也可以用來將 pseudoconsole 通道中的資訊轉送至不同的通道或裝置，包括網路對其他進程或電腦的遠端資訊，以及避免資訊的任何本地轉碼。

## <a name="resizing-the-pseudoconsole"></a>調整 Pseudoconsole 大小

在執行時間的整個過程中，可能會發生因為使用者互動或從另一個顯示/互動裝置的頻外接收的要求而需要變更緩衝區大小的情況。

您可以使用 [**ResizePseudoConsole**](resizepseudoconsole.md) 函式來指定緩衝區的高度和寬度（以字元數為單位）來完成這項工作。

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

## <a name="ending-the-pseudoconsole-session"></a>結束 Pseudoconsole 會話

若要結束會話，請使用原始 pseudoconsole 建立中的控制碼來呼叫 [**ClosePseudoConsole**](closepseudoconsole.md) 函數。 任何附加的用戶端字元模式應用程式（例如 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 呼叫中的應用程式）都將在會話關閉時終止。 如果原始子系是建立其他進程的 shell 型別應用程式，則樹狀結構中的任何相關附加進程也會一併終止。

**注意：**

關閉會話會有數個副作用，如果 pseudoconsole 是以單一執行緒同步方式來使用，可能會產生鎖死狀況。 關閉 pseudoconsole 會話的動作可能會發出最後的畫面格更新， `hOutput` 而該更新應從通道緩衝區耗盡。 此外，如果在 `PSEUDOCONSOLE_INHERIT_CURSOR` 建立 pseudoconsole 時選取了，則嘗試) 在未回應資料指標繼承查詢 (訊息的情況下，嘗試關閉 pseudoconsole， `hOutput` `hInput` 就會產生另一個鎖死的情況。 建議將 pseudoconsole 的通訊通道提供給個別的執行緒，並保持耗盡和處理，直到用戶端應用程式結束或終止活動在呼叫 [**ClosePseudoConsole**](closepseudoconsole.md) 函式完成時才會中斷。

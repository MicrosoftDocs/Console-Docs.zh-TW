---
title: 建立 Pseudoconsole 工作階段
description: Pseudoconsole 工作階段可讓應用程式主控字元模式應用程式的活動
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api, conpty, pseudoconsole, windows pty, 虛擬主控台
ms.localizationpriority: high
ms.openlocfilehash: 8cd057d3e74659fdeff6c569ddb053c881af1de8
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420227"
---
# <a name="creating-a-pseudoconsole-session"></a><span data-ttu-id="6da4b-104">建立 Pseudoconsole 工作階段</span><span class="sxs-lookup"><span data-stu-id="6da4b-104">Creating a Pseudoconsole session</span></span>

<span data-ttu-id="6da4b-105">Windows Pseudoconsole (有時也稱為虛擬主控台、ConPTY 或 Windows PTY) 是專為建立字元模式子系統活動的外部主機而設計的機制，而這些子系統活動會取代預設主控台主機視窗的使用者互動性部分。</span><span class="sxs-lookup"><span data-stu-id="6da4b-105">The Windows Pseudoconsole, sometimes also referred to as pseudo console, ConPTY, or the Windows PTY, is a mechanism designed for creating an external host for character-mode subsystem activities that replace the user interactivity portion of the default console host window.</span></span>

<span data-ttu-id="6da4b-106">主控 Pseudoconsole 工作階段與傳統主控台工作階段有點不同。</span><span class="sxs-lookup"><span data-stu-id="6da4b-106">Hosting a pseudoconsole session is a bit different than a traditional console session.</span></span> <span data-ttu-id="6da4b-107">當作業系統辨識出字元模式應用程式即將執行時，傳統的主控台工作階段就會自動啟動。</span><span class="sxs-lookup"><span data-stu-id="6da4b-107">Traditional console sessions automatically start when the operating system recognizes that a character-mode application is about to run.</span></span> <span data-ttu-id="6da4b-108">相反地，Pseudoconsole 工作階段和通訊通道必須先由主控應用程式建立，才能使用要託管的子字元模式應用程式建立程序。</span><span class="sxs-lookup"><span data-stu-id="6da4b-108">In contrast, a pseudoconsole session and the communication channels need to be created by the hosting application prior to creating the process with the child character-mode application to be hosted.</span></span> <span data-ttu-id="6da4b-109">子程序仍會使用 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 函式來建立，但有一些其他資訊會引導作業系統建立適當的環境。</span><span class="sxs-lookup"><span data-stu-id="6da4b-109">The child process will still be created using the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function, but with some additional information that will direct the operating system to establish the appropriate environment.</span></span>

<span data-ttu-id="6da4b-110">您可以在[初始公告部落格文章](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/)中找到有關此系統的其他背景資訊。</span><span class="sxs-lookup"><span data-stu-id="6da4b-110">You can find additional background information about this system on the [initial announcement blog post](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span></span>

<span data-ttu-id="6da4b-111">在我們的 GitHub 存放庫 [microsoft/terminal](https://github.com/microsoft/terminal) 的 samples 目錄中，可取得使用 Pseudoconsole 的完整範例。</span><span class="sxs-lookup"><span data-stu-id="6da4b-111">Complete examples of using the Pseudoconsole are available on our GitHub repository [microsoft/terminal](https://github.com/microsoft/terminal) in the samples directory.</span></span>

## <a name="preparing-the-communication-channels"></a><span data-ttu-id="6da4b-112">準備通訊通道</span><span class="sxs-lookup"><span data-stu-id="6da4b-112">Preparing the communication channels</span></span>

<span data-ttu-id="6da4b-113">第一個步驟是建立一對同步通訊通道，這對通道會在建立 Pseudoconsole 工作階段期間提供，以便與託管的應用程式進行雙向通訊。</span><span class="sxs-lookup"><span data-stu-id="6da4b-113">The first step is to create a pair of synchronous communication channels that will be provided during creation of the pseudoconsole session for bidirectional communication with the hosted application.</span></span> <span data-ttu-id="6da4b-114">這些通道會由 Pseudoconsole 系統使用 [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) 和 [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) 搭配[同步 I/O](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).進行處理。</span><span class="sxs-lookup"><span data-stu-id="6da4b-114">These channels are processed by the pseudoconsole system using [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) with [synchronous I/O](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).</span></span> <span data-ttu-id="6da4b-115">只要非同步通訊不需要 [**重疊的**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped)結構，就可以接受檔案或 I/O 裝置控點 (例如檔案資料流或管道)。</span><span class="sxs-lookup"><span data-stu-id="6da4b-115">File or I/O device handles like a file stream or pipe are acceptable as long as an [**OVERLAPPED**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) structure is not required for asynchronous communication.</span></span>

> [!WARNING]
><span data-ttu-id="6da4b-116">若要避免競爭條件和鎖死，我們強烈建議在個別的執行緒上為每個通訊通道提供服務，以在您的應用程式內維護自己的用戶端緩衝區狀態和傳訊佇列。</span><span class="sxs-lookup"><span data-stu-id="6da4b-116">To prevent race conditions and deadlocks, we highly recommend that each of the communication channels is serviced on a separate thread that maintains its own client buffer state and messaging queue inside your application.</span></span> <span data-ttu-id="6da4b-117">在同一個執行緒上為所有 Pseudoconsole 活動提供服務可能會導致鎖死，其中有一個通訊緩衝區已滿並在您嘗試在另一個通道上分派封鎖要求時等候您的動作。</span><span class="sxs-lookup"><span data-stu-id="6da4b-117">Servicing all of the pseudoconsole activities on the same thread may result in a deadlock where one of the communications buffers is filled and waiting for your action while you attempt to dispatch a blocking request on another channel.</span></span>

## <a name="creating-the-pseudoconsole"></a><span data-ttu-id="6da4b-118">建立 Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="6da4b-118">Creating the Pseudoconsole</span></span>

<span data-ttu-id="6da4b-119">使用已建立的通訊通道，識別輸入通道的「讀取」端和輸出通道的「寫入」端。</span><span class="sxs-lookup"><span data-stu-id="6da4b-119">With the communications channels that have been established, identify the "read" end of the input channel and the "write" end of the output channel.</span></span> <span data-ttu-id="6da4b-120">呼叫 [**CreatePseudoConsole**](createpseudoconsole.md) 來建立物件時，會提供這一對控點。</span><span class="sxs-lookup"><span data-stu-id="6da4b-120">This pair of handles is provided on calling [**CreatePseudoConsole**](createpseudoconsole.md) to create the object.</span></span>

<span data-ttu-id="6da4b-121">建立時，需要有代表 X 和 Y 維度的大小 (以字元數表示)。</span><span class="sxs-lookup"><span data-stu-id="6da4b-121">On creation, a size representing the X and Y dimensions (in count of characters) is required.</span></span> <span data-ttu-id="6da4b-122">這些維度將會套用至最終 (終端機) 展示視窗的顯示介面。</span><span class="sxs-lookup"><span data-stu-id="6da4b-122">These are the dimensions that will apply to the display surface for the final (terminal) presentation window.</span></span> <span data-ttu-id="6da4b-123">這些值用於在 Pseudoconsole 系統中建立記憶體內部緩衝區。</span><span class="sxs-lookup"><span data-stu-id="6da4b-123">The values are used to create an in-memory buffer inside the pseudoconsole system.</span></span>

<span data-ttu-id="6da4b-124">緩衝區大小會提供答案給用戶端字元模式應用程式，以便其使用 [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) 之類的 [用戶端主控台函式](console-functions.md)來探查資訊，並在用戶端使用 [**WriteConsoleOutput**](writeconsoleoutput.md) 之類的函式時，規定文字的版面配置和定位。</span><span class="sxs-lookup"><span data-stu-id="6da4b-124">The buffer size provide answers to client character-mode applications that probe for information using the [client-side console functions](console-functions.md) like [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) and dictates the layout and positioning of text when clients use functions like [**WriteConsoleOutput**](writeconsoleoutput.md).</span></span>

<span data-ttu-id="6da4b-125">最後，建立 Pseudoconsole 時會提供 flags 欄位，以執行特殊功能。</span><span class="sxs-lookup"><span data-stu-id="6da4b-125">Finally, a flags field is provided on creation of a pseudoconsole to perform special functionality.</span></span> <span data-ttu-id="6da4b-126">根據預設，將此值設定為 0，表示沒有任何特殊功能。</span><span class="sxs-lookup"><span data-stu-id="6da4b-126">By default, set this to 0 to have no special functionality.</span></span>

<span data-ttu-id="6da4b-127">此時，只有一個特殊旗標可用於要求從已經連結至 Pseudoconsole API 呼叫端的主控台工作階段繼承游標位置。</span><span class="sxs-lookup"><span data-stu-id="6da4b-127">At this time, only one special flag is available to request the inheritence of the cursor position from a console session already attached to the caller of the pseudoconsole API.</span></span> <span data-ttu-id="6da4b-128">這適合使用於以下更進階的案例：正在準備 Pseudoconsole 工作階段的主控應用程式本身也是另一個主控台環境的用戶端字元模式應用程式。</span><span class="sxs-lookup"><span data-stu-id="6da4b-128">This is intended for use in more advanced scenarios where a hosting application that is preparing a pseudoconsole session is itself also a client character-mode application of a another console environment.</span></span>

<span data-ttu-id="6da4b-129">下面提供的範例程式碼片段利用 [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) 來建立一對通訊通道和建立 Pseudoconsole。</span><span class="sxs-lookup"><span data-stu-id="6da4b-129">A sample snippet is provided below utilizing [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) to establish a pair of communication channels and create the pseudoconsole.</span></span>

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
><span data-ttu-id="6da4b-130">此程式碼片段不完整，僅用於示範此特定呼叫。</span><span class="sxs-lookup"><span data-stu-id="6da4b-130">This snippet is incomplete and used for demonstration of this specific call only.</span></span> <span data-ttu-id="6da4b-131">您必須適當地管理 **HANDLE** 的存留期。</span><span class="sxs-lookup"><span data-stu-id="6da4b-131">You will need to manage the lifetime of the **HANDLE** s appropriately.</span></span> <span data-ttu-id="6da4b-132">如果無法正確管理 **HANDLE** 的存留期，可能會導致鎖死情況，尤其是同步 I/O 呼叫。</span><span class="sxs-lookup"><span data-stu-id="6da4b-132">Failure to manage the lifetime of **HANDLE** s correctly can result in deadlock scenarios, especially with synchronous I/O calls.</span></span>

<span data-ttu-id="6da4b-133">完成 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 呼叫來建立已連結至 Pseudoconsole 的用戶端字元模式應用程式時，應該從此程序釋放在建立期間指定的控點。</span><span class="sxs-lookup"><span data-stu-id="6da4b-133">Upon completion of the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) call to create the client character-mode application attached to the pseudoconsole, the handles given during creation should be freed from this process.</span></span> <span data-ttu-id="6da4b-134">這會減少基礎裝置物件上的參考計數，並可讓 I/O 作業在 Pseudoconsole 工作階段關閉其控點複本時，正確地偵測中斷的通道。</span><span class="sxs-lookup"><span data-stu-id="6da4b-134">This will decrease the reference count on the underlying device object and allow I/O operations to properly detect a broken channel when the pseudoconsole session closes its copy of the handles.</span></span>

## <a name="preparing-for-creation-of-the-child-process"></a><span data-ttu-id="6da4b-135">準備建立子程序</span><span class="sxs-lookup"><span data-stu-id="6da4b-135">Preparing for Creation of the Child Process</span></span>

<span data-ttu-id="6da4b-136">下一個階段是準備 [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) 結構，以便在啟動子程序時傳達 Pseudoconsole 資訊。</span><span class="sxs-lookup"><span data-stu-id="6da4b-136">The next phase is to prepare the [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure that will convey the pseudoconsole information while starting the child process.</span></span>

<span data-ttu-id="6da4b-137">此結構能夠提供複雜的啟動資訊，包括可供建立程序和執行緒的屬性。</span><span class="sxs-lookup"><span data-stu-id="6da4b-137">This structure contains the ability to provide complex startup information including attributes for process and thread creation.</span></span>

<span data-ttu-id="6da4b-138">以雙重呼叫的方式使用 [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist)，先計算保留清單所需的位元組數目、配置所要求的記憶體，然後再次呼叫以提供不透明的記憶體指標，使其設定為屬性清單。</span><span class="sxs-lookup"><span data-stu-id="6da4b-138">Use [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) in a double-call fashion to first calculate the number of bytes required to hold the list, allocate the memory requested, then call again providing the opaque memory pointer to have it set up as the attribute list.</span></span>

<span data-ttu-id="6da4b-139">接下來，呼叫 [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) 來傳遞已初始化的屬性清單，其中包含 **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE** 旗標、Pseudoconsole 控點，以及 Pseudoconsole 控點的大小。</span><span class="sxs-lookup"><span data-stu-id="6da4b-139">Next, call [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) passing the initialized attribute list with the flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE**, the pseudoconsole handle, and the size of the pseudoconsole handle.</span></span>

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

## <a name="creating-the-hosted-process"></a><span data-ttu-id="6da4b-140">建立託管的程序</span><span class="sxs-lookup"><span data-stu-id="6da4b-140">Creating the Hosted Process</span></span>

<span data-ttu-id="6da4b-141">接下來，呼叫 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 來傳遞 [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) 結構和可執行檔路徑，以及任何其他組態資訊 (如果適用的話)。</span><span class="sxs-lookup"><span data-stu-id="6da4b-141">Next, call [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) passing the [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure along with the path to the executable and any additional configuration information if applicable.</span></span> <span data-ttu-id="6da4b-142">呼叫時，請務必設定 **EXTENDED_STARTUPINFO_PRESENT** 旗標，以警示系統：Pseudoconsole 參考包含在擴充資訊中。</span><span class="sxs-lookup"><span data-stu-id="6da4b-142">It is important to set the **EXTENDED_STARTUPINFO_PRESENT** flag when calling to alert the system that the pseudoconsole reference is contained in the extended information.</span></span>

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
> <span data-ttu-id="6da4b-143">在託管的程序仍在啟動和連線時關閉 Pseudoconsole 工作階段，可能導致用戶端應用程式所顯示的錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6da4b-143">Closing the pseudoconsole session while the hosted process is still starting up and connecting can result in an error dialog being shown by the client application.</span></span> <span data-ttu-id="6da4b-144">如果託管的程序獲得用於啟動的 Pseudoconsole 控點無效，則會顯示相同的錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6da4b-144">The same error dialog is shown if the hosted process is given an invalid pseudoconsole handle for startup.</span></span> <span data-ttu-id="6da4b-145">在託管的程序初始化程式碼中，兩個情況都相同。</span><span class="sxs-lookup"><span data-stu-id="6da4b-145">To the hosted process initialization code, the two circumstances are identical.</span></span> <span data-ttu-id="6da4b-146">失敗時，託管的用戶端應用程式中的快顯對話方塊會顯示 `0xc0000142`，其中包含詳細說明初始化失敗的當地語系化訊息。</span><span class="sxs-lookup"><span data-stu-id="6da4b-146">The pop-up dialog from the hosted client application on failure will read `0xc0000142` with a localized message detailing failure to initialize.</span></span>

## <a name="communicating-with-the-pseudoconsole-session"></a><span data-ttu-id="6da4b-147">與 Pseudoconsole 工作階段通訊</span><span class="sxs-lookup"><span data-stu-id="6da4b-147">Communicating with the Pseudoconsole Session</span></span>

<span data-ttu-id="6da4b-148">成功建立程序後，主控應用程式即可使用輸入管道的寫入端，將使用者互動資訊傳送至 Pseudoconsole 和輸出管道的讀取端，以從虛擬主控台接收圖形化展示資訊。</span><span class="sxs-lookup"><span data-stu-id="6da4b-148">Once the process is created successfully, the hosting application can use the write end of the input pipe to send user interaction information into the pseudoconsole and the read end of the output pipe to receive graphical presentation information from the pseudo console.</span></span>

<span data-ttu-id="6da4b-149">其完全由主控應用程式來決定如何處理進一步的活動。</span><span class="sxs-lookup"><span data-stu-id="6da4b-149">It is completely up to the hosting application to decide how to handle further activity.</span></span> <span data-ttu-id="6da4b-150">主控應用程式可能會在另一個執行緒中啟動視窗，以收集使用者互動輸入，並將其序列化為 Pseudoconsole 和託管字元模式應用程式的輸入管道寫入端。</span><span class="sxs-lookup"><span data-stu-id="6da4b-150">The hosting application could launch a window in another thread to collect user interaction input and serialize it into the write end of the input pipe for the pseudoconsole and the hosted character-mode application.</span></span> <span data-ttu-id="6da4b-151">另一個執行緒可能會啟動，以清空 Pseudoconsole 的輸出管道讀取端，將文字和[虛擬終端機序列](console-virtual-terminal-sequences.md)資訊解碼，並將其呈現到螢幕上。</span><span class="sxs-lookup"><span data-stu-id="6da4b-151">Another thread could be launched to drain the read end of the output pipe for the pseudoconsole, decode the text and [virtual terminal sequence](console-virtual-terminal-sequences.md) information, and present that to the screen.</span></span>

<span data-ttu-id="6da4b-152">執行緒也可用於將來自 Pseudoconsole 通道的資訊轉送到不同的通道或裝置 (包括網路)、將遠端資訊轉送到另一個程序或電腦，以及避免資訊的任何本機轉碼。</span><span class="sxs-lookup"><span data-stu-id="6da4b-152">Threads could also be used to relay the information from the pseudoconsole channels out to a different channel or device including a network to remote information to another process or machine and avoiding any local transcoding of the information.</span></span>

## <a name="resizing-the-pseudoconsole"></a><span data-ttu-id="6da4b-153">調整 Pseudoconsole 的大小</span><span class="sxs-lookup"><span data-stu-id="6da4b-153">Resizing the Pseudoconsole</span></span>

<span data-ttu-id="6da4b-154">在執行階段的整個過程中，可能會有由於使用者互動或從其他顯示/互動裝置頻外收到的要求，而需要變更緩衝區大小的情況。</span><span class="sxs-lookup"><span data-stu-id="6da4b-154">Throughout the course of runtime, there may be a circumstance by which the size of the buffer needs to be changed due to a user interaction or a request received out of band from another display/interaction device.</span></span>

<span data-ttu-id="6da4b-155">這可以透過 [**ResizePseudoConsole**](resizepseudoconsole.md) 函式，同時指定緩衝區的高度和寬度 (以字元數表示) 來完成。</span><span class="sxs-lookup"><span data-stu-id="6da4b-155">This can be done with the [**ResizePseudoConsole**](resizepseudoconsole.md) function specifying both the height and width of the buffer in a count of characters.</span></span>

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

## <a name="ending-the-pseudoconsole-session"></a><span data-ttu-id="6da4b-156">結束 Pseudoconsole 工作階段</span><span class="sxs-lookup"><span data-stu-id="6da4b-156">Ending the Pseudoconsole Session</span></span>

<span data-ttu-id="6da4b-157">若要結束工作階段，請使用原始 Pseudoconsole 建立中的控點來呼叫 [**ClosePseudoConsole**](closepseudoconsole.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="6da4b-157">To end the session, call the [**ClosePseudoConsole**](closepseudoconsole.md) function with the handle from the original pseudoconsole creation.</span></span> <span data-ttu-id="6da4b-158">任何已連結的用戶端字元模式應用程式 (例如來自 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 呼叫的應用程式) 都會在工作階段關閉時終止。</span><span class="sxs-lookup"><span data-stu-id="6da4b-158">Any attached client character-mode applications, such as the one from the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) call, will be terminated when the session is closed.</span></span> <span data-ttu-id="6da4b-159">如果原始子系是建立其他程序的 Shell 類型應用程式，則樹狀結構中任何已連結的相關程序也會一併終止。</span><span class="sxs-lookup"><span data-stu-id="6da4b-159">If the original child was a shell-type application that creates other processes, any related attached processes in the tree will also be terminated.</span></span>

> [!WARNING]
><span data-ttu-id="6da4b-160">如果以單一執行緒同步方式使用 Pseudoconsole，則關閉工作階段有數個副作用，可能會導致鎖死狀況。</span><span class="sxs-lookup"><span data-stu-id="6da4b-160">Closing the session has several side effects which can result in a deadlock condition if the pseudoconsole is used in a single-threaded synchronous fashion.</span></span> <span data-ttu-id="6da4b-161">關閉 Pseudoconsole 工作階段的行動可能會對應該從通訊通道緩衝區清空的 `hOutput` 發出最終框架更新。</span><span class="sxs-lookup"><span data-stu-id="6da4b-161">The act of closing the pseudoconsole session may emit a final frame update to `hOutput` which should be drained from the communications channel buffer.</span></span> <span data-ttu-id="6da4b-162">此外，如果在建立 Pseudoconsole 時選取了 `PSEUDOCONSOLE_INHERIT_CURSOR`，則嘗試關閉 Pseudoconsole 而不回應游標繼承查詢訊息 (在 `hOutput` 上接收並透過 `hInput`回覆)，可能會導致另一個鎖死狀況。</span><span class="sxs-lookup"><span data-stu-id="6da4b-162">Additionally, if `PSEUDOCONSOLE_INHERIT_CURSOR` was selected while creating the pseudoconsole, attempting to close the pseudoconsole without responding to the cursor inheritence query message (received on `hOutput` and replied to via `hInput`) may result in another deadlock condition.</span></span> <span data-ttu-id="6da4b-163">建議在個別的執行緒上為 Pseudoconsole 的通訊通道提供服務，並且在用戶端應用程式結束或在呼叫 [**ClosePseudoConsole**](closepseudoconsole.md) 函式中完成卸除活動而自發性中斷連線之前，維持已清空和已處理狀態。</span><span class="sxs-lookup"><span data-stu-id="6da4b-163">It is recommended that communications channels for the pseudoconsole are serviced on individual threads and remain drained and processed until broken of their own accord by the client application exiting or by the completion of teardown activities in calling the [**ClosePseudoConsole**](closepseudoconsole.md) function.</span></span>

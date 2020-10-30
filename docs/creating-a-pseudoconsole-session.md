---
title: 建立 Pseudoconsole 會話
description: Pseudoconsole 會話可讓應用程式裝載字元模式應用程式的活動
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api，conpty，pseudoconsole，windows pty，虛擬主控台
ms.openlocfilehash: 17b53bc2f0afb60be1a8311de9ab54b00fbf71d6
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039106"
---
# <a name="creating-a-pseudoconsole-session"></a><span data-ttu-id="9b448-104">建立 Pseudoconsole 會話</span><span class="sxs-lookup"><span data-stu-id="9b448-104">Creating a Pseudoconsole session</span></span>

<span data-ttu-id="9b448-105">Windows Pseudoconsole （有時也稱為虛擬主控台、ConPTY 或 Windows PTY）是一種機制，其設計目的是要為字元模式子系統活動建立外部主機，以取代預設主控台主機視窗的使用者互動部分。</span><span class="sxs-lookup"><span data-stu-id="9b448-105">The Windows Pseudoconsole, sometimes also referred to as pseudo console, ConPTY, or the Windows PTY, is a mechanism designed for creating an external host for character-mode subsystem activities that replace the user interactivity portion of the default console host window.</span></span>

<span data-ttu-id="9b448-106">裝載 pseudoconsole 會話與傳統的主控台會話有點不同。</span><span class="sxs-lookup"><span data-stu-id="9b448-106">Hosting a pseudoconsole session is a bit different than a traditional console session.</span></span> <span data-ttu-id="9b448-107">當作業系統辨識出要執行的字元模式應用程式時，傳統的主控台會話就會自動啟動。</span><span class="sxs-lookup"><span data-stu-id="9b448-107">Traditional console sessions automatically start when the operating system recognizes that a character-mode application is about to run.</span></span> <span data-ttu-id="9b448-108">相反地，在建立具有要裝載之子字元模式應用程式的處理常式之前，必須先由裝載應用程式建立 pseudoconsole 會話和通道。</span><span class="sxs-lookup"><span data-stu-id="9b448-108">In contrast, a pseudoconsole session and the communication channels need to be created by the hosting application prior to creating the process with the child character-mode application to be hosted.</span></span> <span data-ttu-id="9b448-109">子進程仍會使用 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 函式來建立，但會有一些額外的資訊，可指示作業系統建立適當的環境。</span><span class="sxs-lookup"><span data-stu-id="9b448-109">The child process will still be created using the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function, but with some additional information that will direct the operating system to establish the appropriate environment.</span></span>

<span data-ttu-id="9b448-110">您可以在 [初始公告的 blog 文章](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/)中找到有關此系統的其他背景資訊。</span><span class="sxs-lookup"><span data-stu-id="9b448-110">You can find additional background information about this system on the [initial announcement blog post](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span></span>

<span data-ttu-id="9b448-111">範例目錄中的 GitHub 存放庫 [microsoft/terminal](https://github.com/microsoft/terminal) 提供使用 Pseudoconsole 的完整範例。</span><span class="sxs-lookup"><span data-stu-id="9b448-111">Complete examples of using the Pseudoconsole are available on our GitHub repository [microsoft/terminal](https://github.com/microsoft/terminal) in the samples directory.</span></span>

## <a name="preparing-the-communication-channels"></a><span data-ttu-id="9b448-112">準備通道</span><span class="sxs-lookup"><span data-stu-id="9b448-112">Preparing the communication channels</span></span>

<span data-ttu-id="9b448-113">第一個步驟是建立一對將在建立 pseudoconsole 會話期間提供的同步通道，以便與託管的應用程式進行雙向通訊。</span><span class="sxs-lookup"><span data-stu-id="9b448-113">The first step is to create a pair of synchronous communication channels that will be provided during creation of the pseudoconsole session for bidirectional communication with the hosted application.</span></span> <span data-ttu-id="9b448-114">Pseudoconsole 系統會使用 [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) 和 [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) 搭配 [同步 i/o](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output)來處理這些通道。</span><span class="sxs-lookup"><span data-stu-id="9b448-114">These channels are processed by the pseudoconsole system using [**ReadFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-writefile) with [synchronous I/O](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output).</span></span> <span data-ttu-id="9b448-115">只要非同步通訊不需要重迭 [**的結構，**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) 就可以接受檔案或 i/o 設備控制碼，例如檔案資料流程或管道。</span><span class="sxs-lookup"><span data-stu-id="9b448-115">File or I/O device handles like a file stream or pipe are acceptable as long as an [**OVERLAPPED**](https://docs.microsoft.com/windows/desktop/api/minwinbase/ns-minwinbase-_overlapped) structure is not required for asynchronous communication.</span></span>

> [!WARNING]
><span data-ttu-id="9b448-116">為了避免競爭情況和鎖死，強烈建議在個別的執行緒上提供每個通道的服務，以在您的應用程式中維護自己的用戶端緩衝區狀態和訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="9b448-116">To prevent race conditions and deadlocks, we highly recommend that each of the communication channels is serviced on a separate thread that maintains its own client buffer state and messaging queue inside your application.</span></span> <span data-ttu-id="9b448-117">針對相同執行緒上的所有 pseudoconsole 活動提供服務，可能會導致當您嘗試在另一個通道上分派封鎖要求時，其中一個通訊緩衝區已填滿，並且正在等候您的動作時，就會產生鎖死。</span><span class="sxs-lookup"><span data-stu-id="9b448-117">Servicing all of the pseudoconsole activities on the same thread may result in a deadlock where one of the communications buffers is filled and waiting for your action while you attempt to dispatch a blocking request on another channel.</span></span>

## <a name="creating-the-pseudoconsole"></a><span data-ttu-id="9b448-118">建立 Pseudoconsole</span><span class="sxs-lookup"><span data-stu-id="9b448-118">Creating the Pseudoconsole</span></span>

<span data-ttu-id="9b448-119">使用已建立的通道，識別輸入通道的「讀取」結尾和輸出通道的「寫入」結尾。</span><span class="sxs-lookup"><span data-stu-id="9b448-119">With the communications channels that have been established, identify the "read" end of the input channel and the "write" end of the output channel.</span></span> <span data-ttu-id="9b448-120">呼叫 [**CreatePseudoConsole**](createpseudoconsole.md) 時，會提供這組控制碼來建立物件。</span><span class="sxs-lookup"><span data-stu-id="9b448-120">This pair of handles is provided on calling [**CreatePseudoConsole**](createpseudoconsole.md) to create the object.</span></span>

<span data-ttu-id="9b448-121">建立時，需要的字元大小 (的) 字元計數中。</span><span class="sxs-lookup"><span data-stu-id="9b448-121">On creation, a size representing the X and Y dimensions (in count of characters) is required.</span></span> <span data-ttu-id="9b448-122">這些維度會套用至最終 (終端) 展示視窗的顯示介面。</span><span class="sxs-lookup"><span data-stu-id="9b448-122">These are the dimensions that will apply to the display surface for the final (terminal) presentation window.</span></span> <span data-ttu-id="9b448-123">這些值可用來在 pseudoconsole 系統內建立記憶體中的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9b448-123">The values are used to create an in-memory buffer inside the pseudoconsole system.</span></span>

<span data-ttu-id="9b448-124">緩衝區大小提供用戶端字元模式應用程式的答案，這些應用程式會使用 [用戶端主控台功能](console-functions.md) （例如 [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) ）來探查資訊，並在用戶端使用 [**WriteConsoleOutput**](writeconsoleoutput.md)之類的函式時指定文字的版面配置和位置。</span><span class="sxs-lookup"><span data-stu-id="9b448-124">The buffer size provide answers to client character-mode applications that probe for information using the [client-side console functions](console-functions.md) like [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) and dictates the layout and positioning of text when clients use functions like [**WriteConsoleOutput**](writeconsoleoutput.md).</span></span>

<span data-ttu-id="9b448-125">最後，在建立 pseudoconsole 時，會提供旗標欄位來執行特殊功能。</span><span class="sxs-lookup"><span data-stu-id="9b448-125">Finally, a flags field is provided on creation of a pseudoconsole to perform special functionality.</span></span> <span data-ttu-id="9b448-126">預設會將此值設定為0，而沒有特殊功能。</span><span class="sxs-lookup"><span data-stu-id="9b448-126">By default, set this to 0 to have no special functionality.</span></span>

<span data-ttu-id="9b448-127">目前只有一個特殊旗標可要求從已經附加至 pseudoconsole API 呼叫端的主控台會話，要求資料指標位置的繼承。</span><span class="sxs-lookup"><span data-stu-id="9b448-127">At this time, only one special flag is available to request the inheritence of the cursor position from a console session already attached to the caller of the pseudoconsole API.</span></span> <span data-ttu-id="9b448-128">這是為了在更先進的案例中使用，也就是正在準備 pseudoconsole 會話的裝載應用程式本身也是另一個主控台環境的用戶端字元模式應用程式。</span><span class="sxs-lookup"><span data-stu-id="9b448-128">This is intended for use in more advanced scenarios where a hosting application that is preparing a pseudoconsole session is itself also a client character-mode application of a another console environment.</span></span>

<span data-ttu-id="9b448-129">下面提供的範例程式碼片段會使用 [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) 來建立一對通道，並建立 pseudoconsole。</span><span class="sxs-lookup"><span data-stu-id="9b448-129">A sample snippet is provided below utilizing [**CreatePipe**](https://msdn.microsoft.com/library/windows/desktop/aa365152(v=vs.85).aspx) to establish a pair of communication channels and create the pseudoconsole.</span></span>

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
><span data-ttu-id="9b448-130">此程式碼片段不完整，只用于示範此特定呼叫。</span><span class="sxs-lookup"><span data-stu-id="9b448-130">This snippet is incomplete and used for demonstration of this specific call only.</span></span> <span data-ttu-id="9b448-131">您將需要適當地管理 **控制碼** 的存留期。</span><span class="sxs-lookup"><span data-stu-id="9b448-131">You will need to manage the lifetime of the **HANDLE** s appropriately.</span></span> <span data-ttu-id="9b448-132">如果無法正確管理 **控制碼** 的存留期，可能會導致鎖死的情況，特別是在同步的 i/o 呼叫中。</span><span class="sxs-lookup"><span data-stu-id="9b448-132">Failure to manage the lifetime of **HANDLE** s correctly can result in deadlock scenarios, especially with synchronous I/O calls.</span></span>

<span data-ttu-id="9b448-133">完成 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 呼叫以建立附加至 pseudoconsole 的用戶端字元模式應用程式時，應該從此進程釋放在建立期間提供的控制碼。</span><span class="sxs-lookup"><span data-stu-id="9b448-133">Upon completion of the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) call to create the client character-mode application attached to the pseudoconsole, the handles given during creation should be freed from this process.</span></span> <span data-ttu-id="9b448-134">這會減少基礎裝置物件的參考計數，並允許 i/o 作業在 pseudoconsole 會話關閉其控制碼的複本時，適當地偵測到中斷的通道。</span><span class="sxs-lookup"><span data-stu-id="9b448-134">This will decrease the reference count on the underlying device object and allow I/O operations to properly detect a broken channel when the pseudoconsole session closes its copy of the handles.</span></span>

## <a name="preparing-for-creation-of-the-child-process"></a><span data-ttu-id="9b448-135">準備建立子進程</span><span class="sxs-lookup"><span data-stu-id="9b448-135">Preparing for Creation of the Child Process</span></span>

<span data-ttu-id="9b448-136">下一個階段是準備 [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) 結構，以在啟動子進程時傳達 pseudoconsole 資訊。</span><span class="sxs-lookup"><span data-stu-id="9b448-136">The next phase is to prepare the [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure that will convey the pseudoconsole information while starting the child process.</span></span>

<span data-ttu-id="9b448-137">此結構包含提供複雜啟動資訊的功能，包括處理常式和執行緒建立的屬性。</span><span class="sxs-lookup"><span data-stu-id="9b448-137">This structure contains the ability to provide complex startup information including attributes for process and thread creation.</span></span>

<span data-ttu-id="9b448-138">以雙呼叫方式使用 [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) ，以先計算保留清單所需的位元組數目、配置所要求的記憶體，然後再次呼叫，提供不透明的記憶體指標讓它設定為屬性清單。</span><span class="sxs-lookup"><span data-stu-id="9b448-138">Use [**InitializeProcThreadAttributeList**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-initializeprocthreadattributelist) in a double-call fashion to first calculate the number of bytes required to hold the list, allocate the memory requested, then call again providing the opaque memory pointer to have it set up as the attribute list.</span></span>

<span data-ttu-id="9b448-139">接下來，呼叫 [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) 傳遞已初始化的屬性清單和旗標 **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE** 、PSEUDOCONSOLE 控制碼，以及 PSEUDOCONSOLE 控制碼的大小。</span><span class="sxs-lookup"><span data-stu-id="9b448-139">Next, call [**UpdateProcThreadAttribute**](https://docs.microsoft.com/windows/desktop/api/processthreadsapi/nf-processthreadsapi-updateprocthreadattribute) passing the initialized attribute list with the flag **PROC_THREAD_ATTRIBUTE_PSEUDOCONSOLE** , the pseudoconsole handle, and the size of the pseudoconsole handle.</span></span>

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

## <a name="creating-the-hosted-process"></a><span data-ttu-id="9b448-140">建立託管進程</span><span class="sxs-lookup"><span data-stu-id="9b448-140">Creating the Hosted Process</span></span>

<span data-ttu-id="9b448-141">接下來，呼叫 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 以傳遞 [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) 結構，以及可執行檔的路徑，以及任何其他設定資訊（如果適用）。</span><span class="sxs-lookup"><span data-stu-id="9b448-141">Next, call [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) passing the [**STARTUPINFOEX**](https://docs.microsoft.com/windows/desktop/api/winbase/ns-winbase-_startupinfoexw) structure along with the path to the executable and any additional configuration information if applicable.</span></span> <span data-ttu-id="9b448-142">請務必在呼叫時設定 **EXTENDED_STARTUPINFO_PRESENT** 旗標，以警示系統 pseudoconsole 參考包含在擴充資訊中。</span><span class="sxs-lookup"><span data-stu-id="9b448-142">It is important to set the **EXTENDED_STARTUPINFO_PRESENT** flag when calling to alert the system that the pseudoconsole reference is contained in the extended information.</span></span>

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
> <span data-ttu-id="9b448-143">當裝載的進程仍在啟動並聯機時，關閉 pseudoconsole 會話會導致用戶端應用程式顯示錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9b448-143">Closing the pseudoconsole session while the hosted process is still starting up and connecting can result in an error dialog being shown by the client application.</span></span> <span data-ttu-id="9b448-144">如果裝載的進程具有不正確啟動 pseudoconsole 控制碼，就會顯示相同的錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9b448-144">The same error dialog is shown if the hosted process is given an invalid pseudoconsole handle for startup.</span></span> <span data-ttu-id="9b448-145">在託管的進程初始化程式碼中，兩種情況都相同。</span><span class="sxs-lookup"><span data-stu-id="9b448-145">To the hosted process initialization code, the two circumstances are identical.</span></span> <span data-ttu-id="9b448-146">失敗時，裝載用戶端應用程式中的快顯對話方塊會讀取 `0xc0000142` 詳細說明無法初始化的錯誤。</span><span class="sxs-lookup"><span data-stu-id="9b448-146">The pop-up dialog from the hosted client application on failure will read `0xc0000142` with a localized message detailing failure to initialize.</span></span>

## <a name="communicating-with-the-pseudoconsole-session"></a><span data-ttu-id="9b448-147">與 Pseudoconsole 會話通訊</span><span class="sxs-lookup"><span data-stu-id="9b448-147">Communicating with the Pseudoconsole Session</span></span>

<span data-ttu-id="9b448-148">成功建立程式之後，裝載應用程式可以使用輸入管道的寫入端，將使用者互動資訊傳送至 pseudoconsole，並將輸出管道的讀取端傳送到輸出管道，以從虛擬主控台接收圖形呈現資訊。</span><span class="sxs-lookup"><span data-stu-id="9b448-148">Once the process is created successfully, the hosting application can use the write end of the input pipe to send user interaction information into the pseudoconsole and the read end of the output pipe to receive graphical presentation information from the pseudo console.</span></span>

<span data-ttu-id="9b448-149">它完全取決於裝載應用程式，以決定如何處理進一步的活動。</span><span class="sxs-lookup"><span data-stu-id="9b448-149">It is completely up to the hosting application to decide how to handle further activity.</span></span> <span data-ttu-id="9b448-150">裝載應用程式可以在另一個執行緒中啟動視窗，以收集使用者互動輸入，並將其序列化為 pseudoconsole 和裝載的字元模式應用程式之輸入管道的寫入結尾。</span><span class="sxs-lookup"><span data-stu-id="9b448-150">The hosting application could launch a window in another thread to collect user interaction input and serialize it into the write end of the input pipe for the pseudoconsole and the hosted character-mode application.</span></span> <span data-ttu-id="9b448-151">您可以啟動另一個執行緒，以清空 pseudoconsole 輸出管道的讀取端、將文字和 [虛擬終端機序列](console-virtual-terminal-sequences.md) 資訊解碼，然後將其顯示在畫面上。</span><span class="sxs-lookup"><span data-stu-id="9b448-151">Another thread could be launched to drain the read end of the output pipe for the pseudoconsole, decode the text and [virtual terminal sequence](console-virtual-terminal-sequences.md) information, and present that to the screen.</span></span>

<span data-ttu-id="9b448-152">執行緒也可以用來將 pseudoconsole 通道中的資訊轉送至不同的通道或裝置，包括網路對其他進程或電腦的遠端資訊，以及避免資訊的任何本地轉碼。</span><span class="sxs-lookup"><span data-stu-id="9b448-152">Threads could also be used to relay the information from the pseudoconsole channels out to a different channel or device including a network to remote information to another process or machine and avoiding any local transcoding of the information.</span></span>

## <a name="resizing-the-pseudoconsole"></a><span data-ttu-id="9b448-153">調整 Pseudoconsole 大小</span><span class="sxs-lookup"><span data-stu-id="9b448-153">Resizing the Pseudoconsole</span></span>

<span data-ttu-id="9b448-154">在執行時間的整個過程中，可能會發生因為使用者互動或從另一個顯示/互動裝置的頻外接收的要求而需要變更緩衝區大小的情況。</span><span class="sxs-lookup"><span data-stu-id="9b448-154">Throughout the course of runtime, there may be a circumstance by which the size of the buffer needs to be changed due to a user interaction or a request received out of band from another display/interaction device.</span></span>

<span data-ttu-id="9b448-155">您可以使用 [**ResizePseudoConsole**](resizepseudoconsole.md) 函式來指定緩衝區的高度和寬度（以字元數為單位）來完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="9b448-155">This can be done with the [**ResizePseudoConsole**](resizepseudoconsole.md) function specifying both the height and width of the buffer in a count of characters.</span></span>

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

## <a name="ending-the-pseudoconsole-session"></a><span data-ttu-id="9b448-156">結束 Pseudoconsole 會話</span><span class="sxs-lookup"><span data-stu-id="9b448-156">Ending the Pseudoconsole Session</span></span>

<span data-ttu-id="9b448-157">若要結束會話，請使用原始 pseudoconsole 建立中的控制碼來呼叫 [**ClosePseudoConsole**](closepseudoconsole.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="9b448-157">To end the session, call the [**ClosePseudoConsole**](closepseudoconsole.md) function with the handle from the original pseudoconsole creation.</span></span> <span data-ttu-id="9b448-158">任何附加的用戶端字元模式應用程式（例如 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 呼叫中的應用程式）都將在會話關閉時終止。</span><span class="sxs-lookup"><span data-stu-id="9b448-158">Any attached client character-mode applications, such as the one from the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) call, will be terminated when the session is closed.</span></span> <span data-ttu-id="9b448-159">如果原始子系是建立其他進程的 shell 型別應用程式，則樹狀結構中的任何相關附加進程也會一併終止。</span><span class="sxs-lookup"><span data-stu-id="9b448-159">If the original child was a shell-type application that creates other processes, any related attached processes in the tree will also be terminated.</span></span>

> [!WARNING]
><span data-ttu-id="9b448-160">關閉會話會有數個副作用，如果 pseudoconsole 是以單一執行緒同步方式來使用，可能會產生鎖死狀況。</span><span class="sxs-lookup"><span data-stu-id="9b448-160">Closing the session has several side effects which can result in a deadlock condition if the pseudoconsole is used in a single-threaded synchronous fashion.</span></span> <span data-ttu-id="9b448-161">關閉 pseudoconsole 會話的動作可能會發出最後的畫面格更新， `hOutput` 而該更新應從通道緩衝區耗盡。</span><span class="sxs-lookup"><span data-stu-id="9b448-161">The act of closing the pseudoconsole session may emit a final frame update to `hOutput` which should be drained from the communications channel buffer.</span></span> <span data-ttu-id="9b448-162">此外，如果在 `PSEUDOCONSOLE_INHERIT_CURSOR` 建立 pseudoconsole 時選取了，則嘗試) 在未回應資料指標繼承查詢 (訊息的情況下，嘗試關閉 pseudoconsole， `hOutput` `hInput` 就會產生另一個鎖死的情況。</span><span class="sxs-lookup"><span data-stu-id="9b448-162">Additionally, if `PSEUDOCONSOLE_INHERIT_CURSOR` was selected while creating the pseudoconsole, attempting to close the pseudoconsole without responding to the cursor inheritence query message (received on `hOutput` and replied to via `hInput`) may result in another deadlock condition.</span></span> <span data-ttu-id="9b448-163">建議將 pseudoconsole 的通訊通道提供給個別的執行緒，並保持耗盡和處理，直到用戶端應用程式結束或終止活動在呼叫 [**ClosePseudoConsole**](closepseudoconsole.md) 函式完成時才會中斷。</span><span class="sxs-lookup"><span data-stu-id="9b448-163">It is recommended that communications channels for the pseudoconsole are serviced on individual threads and remain drained and processed until broken of their own accord by the client application exiting or by the completion of teardown activities in calling the [**ClosePseudoConsole**](closepseudoconsole.md) function.</span></span>

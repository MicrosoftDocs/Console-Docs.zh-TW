---
title: GetStdHandle 函式
description: " (標準輸入、標準輸出或標準錯誤) ，抓取指定標準裝置的控制碼。"
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- base.getstdhandle
- consoles.getstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348
topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 42857417cedb661014de869536b798d29c9eb884
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420207"
---
# <a name="getstdhandle-function"></a><span data-ttu-id="3c0af-104">GetStdHandle 函式</span><span class="sxs-lookup"><span data-stu-id="3c0af-104">GetStdHandle function</span></span>

<span data-ttu-id="3c0af-105"> (標準輸入、標準輸出或標準錯誤) ，抓取指定標準裝置的控制碼。</span><span class="sxs-lookup"><span data-stu-id="3c0af-105">Retrieves a handle to the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="3c0af-106">語法</span><span class="sxs-lookup"><span data-stu-id="3c0af-106">Syntax</span></span>

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a><span data-ttu-id="3c0af-107">參數</span><span class="sxs-lookup"><span data-stu-id="3c0af-107">Parameters</span></span>

<span data-ttu-id="3c0af-108">*nStdHandle* \[在\]</span><span class="sxs-lookup"><span data-stu-id="3c0af-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="3c0af-109">標準裝置。</span><span class="sxs-lookup"><span data-stu-id="3c0af-109">The standard device.</span></span> <span data-ttu-id="3c0af-110">這個參數可以是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="3c0af-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="3c0af-111">值</span><span class="sxs-lookup"><span data-stu-id="3c0af-111">Value</span></span> | <span data-ttu-id="3c0af-112">意義</span><span class="sxs-lookup"><span data-stu-id="3c0af-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="3c0af-113">**STD_INPUT_HANDLE** (DWORD) -10</span><span class="sxs-lookup"><span data-stu-id="3c0af-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="3c0af-114">標準輸入設備。</span><span class="sxs-lookup"><span data-stu-id="3c0af-114">The standard input device.</span></span> <span data-ttu-id="3c0af-115">一開始，這是主控台輸入緩衝區 `CONIN$` 。</span><span class="sxs-lookup"><span data-stu-id="3c0af-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="3c0af-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span><span class="sxs-lookup"><span data-stu-id="3c0af-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="3c0af-117">標準輸出裝置。</span><span class="sxs-lookup"><span data-stu-id="3c0af-117">The standard output device.</span></span> <span data-ttu-id="3c0af-118">這一開始是使用中的主控台畫面緩衝區 `CONOUT$` 。</span><span class="sxs-lookup"><span data-stu-id="3c0af-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="3c0af-119">**STD_ERROR_HANDLE** (DWORD) -12</span><span class="sxs-lookup"><span data-stu-id="3c0af-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="3c0af-120">標準錯誤裝置。</span><span class="sxs-lookup"><span data-stu-id="3c0af-120">The standard error device.</span></span> <span data-ttu-id="3c0af-121">這一開始是使用中的主控台畫面緩衝區 `CONOUT$` 。</span><span class="sxs-lookup"><span data-stu-id="3c0af-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

## <a name="return-value"></a><span data-ttu-id="3c0af-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="3c0af-122">Return value</span></span>

<span data-ttu-id="3c0af-123">如果函式成功，則傳回值是指定之裝置的控制碼，或先前呼叫 [**SetStdHandle**](setstdhandle.md)所設定的重新導向控制碼。</span><span class="sxs-lookup"><span data-stu-id="3c0af-123">If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md).</span></span> <span data-ttu-id="3c0af-124">控制碼具有 **一般 \_ 讀取** 和 **一般 \_ 寫入** 存取權限，除非應用程式已使用 **SetStdHandle** 來設定較少存取的標準控制碼。</span><span class="sxs-lookup"><span data-stu-id="3c0af-124">The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.</span></span>

<span data-ttu-id="3c0af-125">如果函式失敗，則傳回值是 **不正確 \_ 控制碼 \_ 值**。</span><span class="sxs-lookup"><span data-stu-id="3c0af-125">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="3c0af-126">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="3c0af-126">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="3c0af-127">如果應用程式沒有相關聯的標準控制碼（例如在互動式桌面上執行的服務），而且尚未將它們重新導向，則傳回值為 **Null**。</span><span class="sxs-lookup"><span data-stu-id="3c0af-127">If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c0af-128">備註</span><span class="sxs-lookup"><span data-stu-id="3c0af-128">Remarks</span></span>

<span data-ttu-id="3c0af-129">**GetStdHandle** 所傳回的控制碼可供需要讀取或寫入主控台的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="3c0af-129">Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console.</span></span> <span data-ttu-id="3c0af-130">建立主控台時，標準輸入控制碼是主控台輸入緩衝區的控制碼，而標準輸出和標準錯誤控制碼則是主控台的作用中螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="3c0af-130">When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer.</span></span> <span data-ttu-id="3c0af-131">這些控制碼可供 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 和 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 函式使用，或由任何可存取主控台輸入緩衝區或螢幕緩衝區的主控台函式使用 (例如， [**ReadConsoleInput**](readconsoleinput.md)、 [**WriteConsole**](writeconsole.md)或 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數) 。</span><span class="sxs-lookup"><span data-stu-id="3c0af-131">These handles can be used by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).</span></span>

<span data-ttu-id="3c0af-132">呼叫 [**SetStdHandle**](setstdhandle.md)可能會重新導向進程的標準控制碼，在這種情況下， **GetStdHandle** 會傳回重新導向的控制碼。</span><span class="sxs-lookup"><span data-stu-id="3c0af-132">The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle.</span></span> <span data-ttu-id="3c0af-133">如果已重新導向標準控制碼，您可以在對 CreateFile 函式的 `CONIN$` 呼叫中 [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)指定值，以取得主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="3c0af-133">If the standard handles have been redirected, you can specify the `CONIN$` value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="3c0af-134">同樣地，您可以指定 `CONOUT$` 值以取得主控台的作用中螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="3c0af-134">Similarly, you can specify the `CONOUT$` value to get a handle to a console's active screen buffer.</span></span>

<span data-ttu-id="3c0af-135">當建立應用程式時，將傳遞給連結器的 [**/SUBSYSTEM**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem) 旗標設定，會決定如何在 main 方法的專案上設定標準處理常式。</span><span class="sxs-lookup"><span data-stu-id="3c0af-135">The standard handles of a process on entry of the main method are dictated by the configuration of the [**/SUBSYSTEM**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem) flag passed to the linker when the application was built.</span></span> <span data-ttu-id="3c0af-136">指定 **/SUBSYSTEM：主控台** 要求作業系統在啟動時以主控台會話填滿控制碼，如果父系尚未依繼承填滿標準控制碼表格。</span><span class="sxs-lookup"><span data-stu-id="3c0af-136">Specifying **/SUBSYSTEM:CONSOLE** requests that the operating system fill the handles with a console session on startup, if the parent didn't already fill the standard handle table by inheritance.</span></span> <span data-ttu-id="3c0af-137">相反地， **/SUBSYSTEM： WINDOWS** 表示應用程式不需要主控台，而且可能不會使用標準控點。</span><span class="sxs-lookup"><span data-stu-id="3c0af-137">On the contrary, **/SUBSYSTEM:WINDOWS** implies that the application does not need a console and will likely not be making use of the standard handles.</span></span> <span data-ttu-id="3c0af-138">如需有關控制碼繼承的詳細資訊，請參閱 [**STARTF \_ USESTDHANDLES**](https://docs.microsoft.com/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa)的檔。</span><span class="sxs-lookup"><span data-stu-id="3c0af-138">More information on handle inheritance can be found in the documentation for [**STARTF\_USESTDHANDLES**](https://docs.microsoft.com/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span></span>

<span data-ttu-id="3c0af-139">有些應用程式會在其宣告的子系統界限之外運作;比方說， **/SUBSYSTEM： WINDOWS** 應用程式可能會檢查/使用標準控制碼進行記錄或偵測，但以圖形化使用者介面正常運作。</span><span class="sxs-lookup"><span data-stu-id="3c0af-139">Some applications operate outside the boundaries of their declared subsystem; for instance, a **/SUBSYSTEM:WINDOWS** application might check/use standard handles for logging or debugging purposes but operate normally with a graphical user interface.</span></span> <span data-ttu-id="3c0af-140">這些應用程式必須在啟動時仔細探查標準控制碼的狀態，並使用 [**AttachConsole**](attachconsole.md)、 [**AllocConsole**](allocconsole.md)和 [**FreeConsole**](freeconsole.md) 來新增/移除主控台（如有需要）。</span><span class="sxs-lookup"><span data-stu-id="3c0af-140">These applications will need to carefully probe the state of standard handles on startup and make use of [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md), and [**FreeConsole**](freeconsole.md) to add/remove a console if desired.</span></span>

<span data-ttu-id="3c0af-141">某些應用程式可能也會在繼承控制碼的類型上改變其行為。</span><span class="sxs-lookup"><span data-stu-id="3c0af-141">Some applications may also vary their behavior on the type of inherited handle.</span></span> <span data-ttu-id="3c0af-142">您可以使用 [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype)來執行主控台、管道、檔案和其他專案之間的類型 Disambiguating。</span><span class="sxs-lookup"><span data-stu-id="3c0af-142">Disambiguating the type between console, pipe, file, and others can be performed with [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype).</span></span>

### <a name="attachdetach-behavior"></a><span data-ttu-id="3c0af-143">附加/卸離行為</span><span class="sxs-lookup"><span data-stu-id="3c0af-143">Attach/detach behavior</span></span>

<span data-ttu-id="3c0af-144">附加至新的主控台時，除非在進程建立期間指定了 **STARTF \_ USESTDHANDLES** ，否則一律會使用主控台控制碼來取代標準控制碼。</span><span class="sxs-lookup"><span data-stu-id="3c0af-144">When attaching to a new console, standard handles are always replaced with console handles unless **STARTF\_USESTDHANDLES** was specified during process creation.</span></span>

<span data-ttu-id="3c0af-145">如果標準控制碼的現有值為 **Null**，或標準控制碼的現有值看起來像主控台 pseudohandle，控制碼就會取代為主控台控制碼。</span><span class="sxs-lookup"><span data-stu-id="3c0af-145">If the existing value of the standard handle is **NULL**, or the existing value of the standard handle looks like a console pseudohandle, the handle is replaced with a console handle.</span></span>

<span data-ttu-id="3c0af-146">當父系同時使用 [ **建立 \_ 新的 \_ 主控台** ] 和 [ **STARTF \_ USESTDHANDLES** ] 建立主控台進程時，除非標準控制碼的現有值為 **Null** 或主控台 pseudohandle，否則不會取代標準控制碼。</span><span class="sxs-lookup"><span data-stu-id="3c0af-146">When a parent uses both **CREATE\_NEW\_CONSOLE** and **STARTF\_USESTDHANDLES** to create a console process, standard handles will not be replaced unless the existing value of the standard handle is **NULL** or a console pseudohandle.</span></span>

> [!NOTE]
><span data-ttu-id="3c0af-147">主控台處理常式 *必須* 以填滿的標準控點作為開頭，否則系統將會自動使用適當的控制碼來填滿新的主控台。</span><span class="sxs-lookup"><span data-stu-id="3c0af-147">Console processes *must* start with the standard handles filled or they will be filled automatically with appropriate handles to a new console.</span></span> <span data-ttu-id="3c0af-148">圖形化使用者介面 (GUI) 應用程式可以在沒有標準控制碼的情況下啟動，且不會自動填入。</span><span class="sxs-lookup"><span data-stu-id="3c0af-148">Graphical user interface (GUI) applications can be started without the standard handles and they will not be automatically filled.</span></span>

## <a name="examples"></a><span data-ttu-id="3c0af-149">範例</span><span class="sxs-lookup"><span data-stu-id="3c0af-149">Examples</span></span>

<span data-ttu-id="3c0af-150">如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。</span><span class="sxs-lookup"><span data-stu-id="3c0af-150">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="3c0af-151">規格需求</span><span class="sxs-lookup"><span data-stu-id="3c0af-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="3c0af-152">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="3c0af-152">Minimum supported client</span></span> | <span data-ttu-id="3c0af-153">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="3c0af-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="3c0af-154">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="3c0af-154">Minimum supported server</span></span> | <span data-ttu-id="3c0af-155">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="3c0af-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="3c0af-156">標頭</span><span class="sxs-lookup"><span data-stu-id="3c0af-156">Header</span></span> | <span data-ttu-id="3c0af-157">ProcessEnv .h (via Winbase，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="3c0af-157">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="3c0af-158">程式庫</span><span class="sxs-lookup"><span data-stu-id="3c0af-158">Library</span></span> | <span data-ttu-id="3c0af-159">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="3c0af-159">Kernel32.lib</span></span> |
| <span data-ttu-id="3c0af-160">DLL</span><span class="sxs-lookup"><span data-stu-id="3c0af-160">DLL</span></span> | <span data-ttu-id="3c0af-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3c0af-161">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="3c0af-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c0af-162">See also</span></span>

[<span data-ttu-id="3c0af-163">主控台功能</span><span class="sxs-lookup"><span data-stu-id="3c0af-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3c0af-164">主控台控制代碼</span><span class="sxs-lookup"><span data-stu-id="3c0af-164">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="3c0af-165">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="3c0af-165">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="3c0af-166">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="3c0af-166">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="3c0af-167">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="3c0af-167">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="3c0af-168">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="3c0af-168">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="3c0af-169">**SetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="3c0af-169">**SetStdHandle**</span></span>](setstdhandle.md)

[<span data-ttu-id="3c0af-170">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="3c0af-170">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="3c0af-171">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="3c0af-171">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

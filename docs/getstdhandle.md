---
title: GetStdHandle 函式
description: 擷取指定標準裝置的控制代碼 (標準輸入、標準輸出或標準錯誤)。
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
ms.openlocfilehash: 0804e12ff7510cd41bec66e1a45f8a31add7c17a
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358748"
---
# <a name="getstdhandle-function"></a><span data-ttu-id="25f23-104">GetStdHandle 函式</span><span class="sxs-lookup"><span data-stu-id="25f23-104">GetStdHandle function</span></span>

<span data-ttu-id="25f23-105">擷取指定標準裝置的控制代碼 (標準輸入、標準輸出或標準錯誤)。</span><span class="sxs-lookup"><span data-stu-id="25f23-105">Retrieves a handle to the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="25f23-106">語法</span><span class="sxs-lookup"><span data-stu-id="25f23-106">Syntax</span></span>

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a><span data-ttu-id="25f23-107">參數</span><span class="sxs-lookup"><span data-stu-id="25f23-107">Parameters</span></span>

<span data-ttu-id="25f23-108">*nStdHandle* \[輸入\]</span><span class="sxs-lookup"><span data-stu-id="25f23-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="25f23-109">標準裝置。</span><span class="sxs-lookup"><span data-stu-id="25f23-109">The standard device.</span></span> <span data-ttu-id="25f23-110">此參數可以是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="25f23-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="25f23-111">值</span><span class="sxs-lookup"><span data-stu-id="25f23-111">Value</span></span> | <span data-ttu-id="25f23-112">意義</span><span class="sxs-lookup"><span data-stu-id="25f23-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="25f23-113">**STD_INPUT_HANDLE** (DWORD) -10</span><span class="sxs-lookup"><span data-stu-id="25f23-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="25f23-114">標準輸入裝置。</span><span class="sxs-lookup"><span data-stu-id="25f23-114">The standard input device.</span></span> <span data-ttu-id="25f23-115">一開始，這是主控台輸入緩衝區 `CONIN$`。</span><span class="sxs-lookup"><span data-stu-id="25f23-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="25f23-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span><span class="sxs-lookup"><span data-stu-id="25f23-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="25f23-117">標準輸出裝置。</span><span class="sxs-lookup"><span data-stu-id="25f23-117">The standard output device.</span></span> <span data-ttu-id="25f23-118">一開始，這是作用中的主控台畫面緩衝區 `CONOUT$`。</span><span class="sxs-lookup"><span data-stu-id="25f23-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="25f23-119">**STD_ERROR_HANDLE** (DWORD) -12</span><span class="sxs-lookup"><span data-stu-id="25f23-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="25f23-120">標準錯誤裝置。</span><span class="sxs-lookup"><span data-stu-id="25f23-120">The standard error device.</span></span> <span data-ttu-id="25f23-121">一開始，這是作用中的主控台畫面緩衝區 `CONOUT$`。</span><span class="sxs-lookup"><span data-stu-id="25f23-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

## <a name="return-value"></a><span data-ttu-id="25f23-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="25f23-122">Return value</span></span>

<span data-ttu-id="25f23-123">如果函式成功，則傳回值是指定裝置的控制代碼，或是先前呼叫 [**SetStdHandle**](setstdhandle.md) 時所設定的重新導向控制代碼。</span><span class="sxs-lookup"><span data-stu-id="25f23-123">If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md).</span></span> <span data-ttu-id="25f23-124">除非應用程式已使用 **SetStdHandle** 將標準控制代碼設定為具有較低存取權，否則控制代碼會具有 **GENERIC\_READ** 和 **GENERIC\_WRITE** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="25f23-124">The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.</span></span>

<span data-ttu-id="25f23-125">如果函式失敗，則傳回值是 **INVALID\_HANDLE\_VALUE**。</span><span class="sxs-lookup"><span data-stu-id="25f23-125">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="25f23-126">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="25f23-126">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

<span data-ttu-id="25f23-127">如果應用程式沒有相關聯的標準控制代碼 (例如在互動式桌面上執行的服務)，而且尚未將其重新導向，則傳回值會是 **Null**。</span><span class="sxs-lookup"><span data-stu-id="25f23-127">If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.</span></span>

## <a name="remarks"></a><span data-ttu-id="25f23-128">備註</span><span class="sxs-lookup"><span data-stu-id="25f23-128">Remarks</span></span>

<span data-ttu-id="25f23-129">**GetStdHandle** 傳回的控制代碼可供需要讀取或寫入主控台的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="25f23-129">Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console.</span></span> <span data-ttu-id="25f23-130">建立主控台時，標準輸入控制代碼是主控台輸入緩衝區的控制代碼，而標準輸出和標準錯誤控制代碼則是主控台作用中畫面緩衝區的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="25f23-130">When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer.</span></span> <span data-ttu-id="25f23-131">這些控制代碼可由 [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) 和 [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) 函式使用，或由任何存取主控台輸入緩衝區或畫面緩衝區的主控台函式使用 (例如 [**ReadConsoleInput**](readconsoleinput.md)、[**WriteConsole**](writeconsole.md)或 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函式)。</span><span class="sxs-lookup"><span data-stu-id="25f23-131">These handles can be used by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).</span></span>

<span data-ttu-id="25f23-132">對 [**SetStdHandle**](setstdhandle.md) 發出的呼叫可能會將程序的標準控制代碼重新導向，在此情況下，**GetStdHandle** 會傳回重新導向的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="25f23-132">The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle.</span></span> <span data-ttu-id="25f23-133">如果標準控制代碼已重新導向，您可以在呼叫 [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) 函式時指定 `CONIN$` 值，以取得主控台輸入緩衝區的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="25f23-133">If the standard handles have been redirected, you can specify the `CONIN$` value in a call to the [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="25f23-134">同樣地，您可以指定 `CONOUT$` 值，以取得主控台作用中畫面緩衝區的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="25f23-134">Similarly, you can specify the `CONOUT$` value to get a handle to a console's active screen buffer.</span></span>

<span data-ttu-id="25f23-135">建立應用程式時，傳遞至連結器的 [ **/SUBSYSTEM**](/cpp/build/reference/subsystem-specify-subsystem) 旗標設定會決定在 main 方法進入點上的程序標準控制代碼。</span><span class="sxs-lookup"><span data-stu-id="25f23-135">The standard handles of a process on entry of the main method are dictated by the configuration of the [**/SUBSYSTEM**](/cpp/build/reference/subsystem-specify-subsystem) flag passed to the linker when the application was built.</span></span> <span data-ttu-id="25f23-136">指定 **/SUBSYSTEM:CONSOLE** 會要求作業系統在啟動時以主控台工作階段填滿控制代碼 (如果父系尚未透過繼承來填滿標準控制代碼資料表)。</span><span class="sxs-lookup"><span data-stu-id="25f23-136">Specifying **/SUBSYSTEM:CONSOLE** requests that the operating system fill the handles with a console session on startup, if the parent didn't already fill the standard handle table by inheritance.</span></span> <span data-ttu-id="25f23-137">相反地， **/SUBSYSTEM:WINDOWS** 則是表示應用程式不需要主控台，而且很可能不會使用標準控制代碼。</span><span class="sxs-lookup"><span data-stu-id="25f23-137">On the contrary, **/SUBSYSTEM:WINDOWS** implies that the application does not need a console and will likely not be making use of the standard handles.</span></span> <span data-ttu-id="25f23-138">如需有關控制代碼繼承的詳細資訊，請參閱 [**STARTF\_USESTDHANDLES**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa) 的文件。</span><span class="sxs-lookup"><span data-stu-id="25f23-138">More information on handle inheritance can be found in the documentation for [**STARTF\_USESTDHANDLES**](/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa).</span></span>

<span data-ttu-id="25f23-139">有些應用程式會在其宣告的子系統界限外運作；例如， **/SUBSYSTEM:WINDOWS** 應用程式可能會檢查/使用標準控制代碼進行記錄或偵錯，但通常會搭配圖形使用者介面運作。</span><span class="sxs-lookup"><span data-stu-id="25f23-139">Some applications operate outside the boundaries of their declared subsystem; for instance, a **/SUBSYSTEM:WINDOWS** application might check/use standard handles for logging or debugging purposes but operate normally with a graphical user interface.</span></span> <span data-ttu-id="25f23-140">這些應用程式必須在啟動時仔細探查標準控制代碼的狀態，並使用 [**AttachConsole**](attachconsole.md)、[**AllocConsole**](allocconsole.md) 和 [**FreeConsole**](freeconsole.md) 來新增/移除主控台 (如有需要)。</span><span class="sxs-lookup"><span data-stu-id="25f23-140">These applications will need to carefully probe the state of standard handles on startup and make use of [**AttachConsole**](attachconsole.md), [**AllocConsole**](allocconsole.md), and [**FreeConsole**](freeconsole.md) to add/remove a console if desired.</span></span>

<span data-ttu-id="25f23-141">某些應用程式也可能會改變其在所繼承控制代碼類型上的行為。</span><span class="sxs-lookup"><span data-stu-id="25f23-141">Some applications may also vary their behavior on the type of inherited handle.</span></span> <span data-ttu-id="25f23-142">若要釐清主控台、管道、檔案和其他類型，可以使用 [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype) 來執行。</span><span class="sxs-lookup"><span data-stu-id="25f23-142">Disambiguating the type between console, pipe, file, and others can be performed with [**GetFileType**](/windows/win32/api/fileapi/nf-fileapi-getfiletype).</span></span>

### <a name="attachdetach-behavior"></a><span data-ttu-id="25f23-143">連結/卸離行為</span><span class="sxs-lookup"><span data-stu-id="25f23-143">Attach/detach behavior</span></span>

<span data-ttu-id="25f23-144">連結至新的主控台時，除非已在程序建立期間指定了 **STARTF\_USESTDHANDLES**，否則一律會使用主控台控制代碼取代標準控制代碼。</span><span class="sxs-lookup"><span data-stu-id="25f23-144">When attaching to a new console, standard handles are always replaced with console handles unless **STARTF\_USESTDHANDLES** was specified during process creation.</span></span>

<span data-ttu-id="25f23-145">如果標準控制代碼的現有值為 **Null**，或標準控制代碼的現有值看起來像主控台 pseudohandle，則控制代碼會取代為主控台控制代碼。</span><span class="sxs-lookup"><span data-stu-id="25f23-145">If the existing value of the standard handle is **NULL**, or the existing value of the standard handle looks like a console pseudohandle, the handle is replaced with a console handle.</span></span>

<span data-ttu-id="25f23-146">當父系同時使用 **CREATE\_NEW\_CONSOLE** 和 **STARTF\_USESTDHANDLES** 來建立主控台程序時，除非標準控制代碼的現有值為 **Null** 或主控台 pseudohandle，否則不會取代標準控制代碼。</span><span class="sxs-lookup"><span data-stu-id="25f23-146">When a parent uses both **CREATE\_NEW\_CONSOLE** and **STARTF\_USESTDHANDLES** to create a console process, standard handles will not be replaced unless the existing value of the standard handle is **NULL** or a console pseudohandle.</span></span>

> [!NOTE]
><span data-ttu-id="25f23-147">主控台程序「必須」從填滿標準控制代碼開始，否則新的主控台會自動以適當的控制代碼填入。</span><span class="sxs-lookup"><span data-stu-id="25f23-147">Console processes *must* start with the standard handles filled or they will be filled automatically with appropriate handles to a new console.</span></span> <span data-ttu-id="25f23-148">圖形使用者介面 (GUI) 應用程式可以在沒有標準控制代碼的情況下啟動，而且不會自動填入。</span><span class="sxs-lookup"><span data-stu-id="25f23-148">Graphical user interface (GUI) applications can be started without the standard handles and they will not be automatically filled.</span></span>

## <a name="examples"></a><span data-ttu-id="25f23-149">範例</span><span class="sxs-lookup"><span data-stu-id="25f23-149">Examples</span></span>

<span data-ttu-id="25f23-150">如需範例，請參閱[讀取輸入緩衝區事件](reading-input-buffer-events.md)。</span><span class="sxs-lookup"><span data-stu-id="25f23-150">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="25f23-151">規格需求</span><span class="sxs-lookup"><span data-stu-id="25f23-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="25f23-152">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="25f23-152">Minimum supported client</span></span> | <span data-ttu-id="25f23-153">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="25f23-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="25f23-154">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="25f23-154">Minimum supported server</span></span> | <span data-ttu-id="25f23-155">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="25f23-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="25f23-156">標頭</span><span class="sxs-lookup"><span data-stu-id="25f23-156">Header</span></span> | <span data-ttu-id="25f23-157">ProcessEnv.h (透過 Winbase.h，包括 Windows.h)</span><span class="sxs-lookup"><span data-stu-id="25f23-157">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="25f23-158">程式庫</span><span class="sxs-lookup"><span data-stu-id="25f23-158">Library</span></span> | <span data-ttu-id="25f23-159">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="25f23-159">Kernel32.lib</span></span> |
| <span data-ttu-id="25f23-160">DLL</span><span class="sxs-lookup"><span data-stu-id="25f23-160">DLL</span></span> | <span data-ttu-id="25f23-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="25f23-161">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="25f23-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25f23-162">See also</span></span>

[<span data-ttu-id="25f23-163">主控台函式</span><span class="sxs-lookup"><span data-stu-id="25f23-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="25f23-164">主控台控制代碼</span><span class="sxs-lookup"><span data-stu-id="25f23-164">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="25f23-165">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="25f23-165">**CreateFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[<span data-ttu-id="25f23-166">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="25f23-166">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="25f23-167">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="25f23-167">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="25f23-168">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="25f23-168">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="25f23-169">**SetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="25f23-169">**SetStdHandle**</span></span>](setstdhandle.md)

[<span data-ttu-id="25f23-170">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="25f23-170">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="25f23-171">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="25f23-171">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)
---
title: GetStdHandle 函式
description: " (標準輸入、標準輸出或標準錯誤) ，抓取指定標準裝置的控制碼。"
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
ms.openlocfilehash: 613aacf4052e8e3b38c0a3e254ac4dd2b55ced5d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059082"
---
# <a name="getstdhandle-function"></a><span data-ttu-id="e1342-104">GetStdHandle 函式</span><span class="sxs-lookup"><span data-stu-id="e1342-104">GetStdHandle function</span></span>


<span data-ttu-id="e1342-105"> (標準輸入、標準輸出或標準錯誤) ，抓取指定標準裝置的控制碼。</span><span class="sxs-lookup"><span data-stu-id="e1342-105">Retrieves a handle to the specified standard device (standard input, standard output, or standard error).</span></span>

<a name="syntax"></a><span data-ttu-id="e1342-106">語法</span><span class="sxs-lookup"><span data-stu-id="e1342-106">Syntax</span></span>
------

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

<a name="parameters"></a><span data-ttu-id="e1342-107">參數</span><span class="sxs-lookup"><span data-stu-id="e1342-107">Parameters</span></span>
----------

<span data-ttu-id="e1342-108">*nStdHandle* \[在\]</span><span class="sxs-lookup"><span data-stu-id="e1342-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="e1342-109">標準裝置。</span><span class="sxs-lookup"><span data-stu-id="e1342-109">The standard device.</span></span> <span data-ttu-id="e1342-110">這個參數可以是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="e1342-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="e1342-111">值</span><span class="sxs-lookup"><span data-stu-id="e1342-111">Value</span></span></th>
<th><span data-ttu-id="e1342-112">意義</span><span class="sxs-lookup"><span data-stu-id="e1342-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="e1342-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD) -10</span><span class="sxs-lookup"><span data-stu-id="e1342-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD) -10</span></span></td>
<td><p><span data-ttu-id="e1342-114">標準輸入設備。</span><span class="sxs-lookup"><span data-stu-id="e1342-114">The standard input device.</span></span> <span data-ttu-id="e1342-115">一開始，這是主控台輸入緩衝區 CONIN $。</span><span class="sxs-lookup"><span data-stu-id="e1342-115">Initially, this is the console input buffer, CONIN$.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e1342-116"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD) -11</span><span class="sxs-lookup"><span data-stu-id="e1342-116"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD) -11</span></span></td>
<td><p><span data-ttu-id="e1342-117">標準輸出裝置。</span><span class="sxs-lookup"><span data-stu-id="e1342-117">The standard output device.</span></span> <span data-ttu-id="e1342-118">一開始，這是使用中的主控台畫面緩衝區 CONOUT $。</span><span class="sxs-lookup"><span data-stu-id="e1342-118">Initially, this is the active console screen buffer, CONOUT$.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e1342-119"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD) -12</span><span class="sxs-lookup"><span data-stu-id="e1342-119"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD) -12</span></span></td>
<td><p><span data-ttu-id="e1342-120">標準錯誤裝置。</span><span class="sxs-lookup"><span data-stu-id="e1342-120">The standard error device.</span></span> <span data-ttu-id="e1342-121">一開始，這是使用中的主控台畫面緩衝區 CONOUT $。</span><span class="sxs-lookup"><span data-stu-id="e1342-121">Initially, this is the active console screen buffer, CONOUT$.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="e1342-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="e1342-122">Return value</span></span>
------------

<span data-ttu-id="e1342-123">如果函式成功，則傳回值是指定之裝置的控制碼，或先前呼叫 [**SetStdHandle**](setstdhandle.md)所設定的重新導向控制碼。</span><span class="sxs-lookup"><span data-stu-id="e1342-123">If the function succeeds, the return value is a handle to the specified device, or a redirected handle set by a previous call to [**SetStdHandle**](setstdhandle.md).</span></span> <span data-ttu-id="e1342-124">控制碼具有 **一般 \_ 讀取** 和 **一般 \_ 寫入** 存取權限，除非應用程式已使用 **SetStdHandle** 來設定較少存取的標準控制碼。</span><span class="sxs-lookup"><span data-stu-id="e1342-124">The handle has **GENERIC\_READ** and **GENERIC\_WRITE** access rights, unless the application has used **SetStdHandle** to set a standard handle with lesser access.</span></span>

<span data-ttu-id="e1342-125">如果函式失敗，則傳回值是 **不正確 \_ 控制碼 \_ 值**。</span><span class="sxs-lookup"><span data-stu-id="e1342-125">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="e1342-126">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="e1342-126">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="e1342-127">如果應用程式沒有相關聯的標準控制碼（例如在互動式桌面上執行的服務），而且尚未將它們重新導向，則傳回值為 **Null**。</span><span class="sxs-lookup"><span data-stu-id="e1342-127">If an application does not have associated standard handles, such as a service running on an interactive desktop, and has not redirected them, the return value is **NULL**.</span></span>

<a name="remarks"></a><span data-ttu-id="e1342-128">備註</span><span class="sxs-lookup"><span data-stu-id="e1342-128">Remarks</span></span>
-------

<span data-ttu-id="e1342-129">**GetStdHandle**所傳回的控制碼可供需要讀取或寫入主控台的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="e1342-129">Handles returned by **GetStdHandle** can be used by applications that need to read from or write to the console.</span></span> <span data-ttu-id="e1342-130">建立主控台時，標準輸入控制碼是主控台輸入緩衝區的控制碼，而標準輸出和標準錯誤控制碼則是主控台的作用中螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="e1342-130">When a console is created, the standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles of the console's active screen buffer.</span></span> <span data-ttu-id="e1342-131">這些控制碼可供 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 和 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 函式使用，或由任何可存取主控台輸入緩衝區或螢幕緩衝區的主控台函式使用 (例如， [**ReadConsoleInput**](readconsoleinput.md)、 [**WriteConsole**](writeconsole.md)或 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數) 。</span><span class="sxs-lookup"><span data-stu-id="e1342-131">These handles can be used by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) functions, or by any of the console functions that access the console input buffer or a screen buffer (for example, the [**ReadConsoleInput**](readconsoleinput.md), [**WriteConsole**](writeconsole.md), or [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) functions).</span></span>

<span data-ttu-id="e1342-132">呼叫 [**SetStdHandle**](setstdhandle.md)可能會重新導向進程的標準控制碼，在這種情況下， **GetStdHandle** 會傳回重新導向的控制碼。</span><span class="sxs-lookup"><span data-stu-id="e1342-132">The standard handles of a process may be redirected by a call to [**SetStdHandle**](setstdhandle.md), in which case **GetStdHandle** returns the redirected handle.</span></span> <span data-ttu-id="e1342-133">如果已重新導向標準控制碼，您可以在 [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) 函式的呼叫中指定 CONIN $ 值，以取得主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="e1342-133">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="e1342-134">同樣地，您可以指定 CONOUT $ 值，以取得主控台的作用中螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="e1342-134">Similarly, you can specify the CONOUT$ value to get a handle to a console's active screen buffer.</span></span>

### <a name="span-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanattachdetach-behavior"></a><span data-ttu-id="e1342-135"><span id="Attach_detach_behavior"></span><span id="attach_detach_behavior"></span><span id="ATTACH_DETACH_BEHAVIOR"></span>附加/卸離行為</span><span class="sxs-lookup"><span data-stu-id="e1342-135"><span id="Attach_detach_behavior"></span><span id="attach_detach_behavior"></span><span id="ATTACH_DETACH_BEHAVIOR"></span>Attach/detach behavior</span></span>

<span data-ttu-id="e1342-136">附加至新的主控台時，除非在進程建立期間指定了 **STARTF \_ USESTDHANDLES** ，否則一律會使用主控台控制碼來取代標準控制碼。</span><span class="sxs-lookup"><span data-stu-id="e1342-136">When attaching to a new console, standard handles are always replaced with console handles unless **STARTF\_USESTDHANDLES** was specified during process creation.</span></span>

<span data-ttu-id="e1342-137">如果標準控制碼的現有值為 **Null**，或標準控制碼的現有值看起來像主控台 pseudohandle，控制碼就會取代為主控台控制碼。</span><span class="sxs-lookup"><span data-stu-id="e1342-137">If the existing value of the standard handle is **NULL**, or the existing value of the standard handle looks like a console pseudohandle, the handle is replaced with a console handle.</span></span>

<span data-ttu-id="e1342-138">當父系同時使用 [ **建立 \_ 新的 \_ 主控台** ] 和 [ **STARTF \_ USESTDHANDLES** ] 建立主控台進程時，除非標準控制碼的現有值為 Null 或主控台 pseudohandle，否則不會取代標準控制碼。</span><span class="sxs-lookup"><span data-stu-id="e1342-138">When a parent uses both **CREATE\_NEW\_CONSOLE** and **STARTF\_USESTDHANDLES** to create a console process, standard handles will not be replaced unless the existing value of the standard handle is NULL or a console pseudohandle.</span></span>

<a name="examples"></a><span data-ttu-id="e1342-139">範例</span><span class="sxs-lookup"><span data-stu-id="e1342-139">Examples</span></span>
--------

<span data-ttu-id="e1342-140">如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。</span><span class="sxs-lookup"><span data-stu-id="e1342-140">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="e1342-141">規格需求</span><span class="sxs-lookup"><span data-stu-id="e1342-141">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e1342-142">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="e1342-142">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e1342-143">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="e1342-143">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e1342-144">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="e1342-144">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e1342-145">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="e1342-145">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e1342-146">標頭</span><span class="sxs-lookup"><span data-stu-id="e1342-146">Header</span></span></p></td>
<td><span data-ttu-id="e1342-147">ProcessEnv .h (via Winbase，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="e1342-147">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e1342-148">程式庫</span><span class="sxs-lookup"><span data-stu-id="e1342-148">Library</span></span></p></td>
<td><span data-ttu-id="e1342-149">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="e1342-149">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e1342-150">DLL</span><span class="sxs-lookup"><span data-stu-id="e1342-150">DLL</span></span></p></td>
<td><span data-ttu-id="e1342-151">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e1342-151">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e1342-152"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1342-152"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e1342-153">主控台功能</span><span class="sxs-lookup"><span data-stu-id="e1342-153">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e1342-154">主控台控制碼</span><span class="sxs-lookup"><span data-stu-id="e1342-154">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="e1342-155">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="e1342-155">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="e1342-156">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="e1342-156">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="e1342-157">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="e1342-157">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="e1342-158">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="e1342-158">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="e1342-159">**SetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="e1342-159">**SetStdHandle**</span></span>](setstdhandle.md)

[<span data-ttu-id="e1342-160">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="e1342-160">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="e1342-161">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="e1342-161">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 





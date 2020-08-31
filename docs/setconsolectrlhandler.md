---
title: SetConsoleCtrlHandler 函式
description: 從呼叫進程的處理常式函式清單中，加入或移除應用程式定義的 HandlerRoutine 函數。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi/SetConsoleCtrlHandler
- wincon/SetConsoleCtrlHandler
- SetConsoleCtrlHandler
MS-HAID:
- '\_win32\_setconsolectrlhandler'
- base.setconsolectrlhandler
- consoles.setconsolectrlhandler
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6fc64265-1403-45ea-925c-c5eb31d56734
topic_type:
- apiref
api_name:
- SetConsoleCtrlHandler
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: cd7b491c1a395483d4aef052d4147d3edf2514e5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059415"
---
# <a name="setconsolectrlhandler-function"></a><span data-ttu-id="fe361-104">SetConsoleCtrlHandler 函式</span><span class="sxs-lookup"><span data-stu-id="fe361-104">SetConsoleCtrlHandler function</span></span>


<span data-ttu-id="fe361-105">從呼叫進程的處理常式函式清單中，加入或移除應用程式定義的 [**HandlerRoutine**](handlerroutine.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="fe361-105">Adds or removes an application-defined [**HandlerRoutine**](handlerroutine.md) function from the list of handler functions for the calling process.</span></span>

<span data-ttu-id="fe361-106">如果未指定任何處理程式函式，此函式會設定可繼承的屬性，以判斷呼叫進程是否會忽略 CTRL + C 信號。</span><span class="sxs-lookup"><span data-stu-id="fe361-106">If no handler function is specified, the function sets an inheritable attribute that determines whether the calling process ignores CTRL+C signals.</span></span>

<a name="syntax"></a><span data-ttu-id="fe361-107">語法</span><span class="sxs-lookup"><span data-stu-id="fe361-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

<a name="parameters"></a><span data-ttu-id="fe361-108">參數</span><span class="sxs-lookup"><span data-stu-id="fe361-108">Parameters</span></span>
----------

<span data-ttu-id="fe361-109">*HandlerRoutine* \[在中，選擇性\]</span><span class="sxs-lookup"><span data-stu-id="fe361-109">*HandlerRoutine* \[in, optional\]</span></span>  
<span data-ttu-id="fe361-110">要加入或移除的應用程式定義 [**HandlerRoutine**](handlerroutine.md) 函數的指標。</span><span class="sxs-lookup"><span data-stu-id="fe361-110">A pointer to the application-defined [**HandlerRoutine**](handlerroutine.md) function to be added or removed.</span></span> <span data-ttu-id="fe361-111">這個參數可以是 **Null**。</span><span class="sxs-lookup"><span data-stu-id="fe361-111">This parameter can be **NULL**.</span></span>

<span data-ttu-id="fe361-112">*新增* \[在\]</span><span class="sxs-lookup"><span data-stu-id="fe361-112">*Add* \[in\]</span></span>  
<span data-ttu-id="fe361-113">如果此參數為 **TRUE**，則會加入處理常式;如果為 **FALSE**，則會移除處理常式。</span><span class="sxs-lookup"><span data-stu-id="fe361-113">If this parameter is **TRUE**, the handler is added; if it is **FALSE**, the handler is removed.</span></span>

<span data-ttu-id="fe361-114">如果 *HandlerRoutine* 參數為 **Null**， **則 TRUE** 值會導致呼叫進程忽略 ctrl + c 輸入， **FALSE** 值則會還原 ctrl + c 輸入的正常處理。</span><span class="sxs-lookup"><span data-stu-id="fe361-114">If the *HandlerRoutine* parameter is **NULL**, a **TRUE** value causes the calling process to ignore CTRL+C input, and a **FALSE** value restores normal processing of CTRL+C input.</span></span> <span data-ttu-id="fe361-115">忽略或處理 CTRL + C 的這個屬性會由子進程繼承。</span><span class="sxs-lookup"><span data-stu-id="fe361-115">This attribute of ignoring or processing CTRL+C is inherited by child processes.</span></span>

<a name="return-value"></a><span data-ttu-id="fe361-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="fe361-116">Return value</span></span>
------------

<span data-ttu-id="fe361-117">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="fe361-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="fe361-118">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="fe361-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="fe361-119">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="fe361-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="fe361-120">備註</span><span class="sxs-lookup"><span data-stu-id="fe361-120">Remarks</span></span>
-------

<span data-ttu-id="fe361-121">此函式會提供類似于 [**WM \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) 為圖形化應用程式提供訊息提取的主控台應用程式和服務的通知。</span><span class="sxs-lookup"><span data-stu-id="fe361-121">This function provides a similar notification for console application and services that [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) provides for graphical applications with a message pump.</span></span> <span data-ttu-id="fe361-122">您也可以從圖形化應用程式使用這個函式，但不保證會在來自 **WM \_ QUERYENDSESSION**的通知之前送達。</span><span class="sxs-lookup"><span data-stu-id="fe361-122">You could also use this function from a graphical application, but there is no guarantee it would arrive before the notification from **WM\_QUERYENDSESSION**.</span></span>

<span data-ttu-id="fe361-123">每個主控台進程都有自己的應用程式定義 [**HandlerRoutine**](handlerroutine.md) 函式清單，可處理 Ctrl + C 和 CTRL + 中斷信號。</span><span class="sxs-lookup"><span data-stu-id="fe361-123">Each console process has its own list of application-defined [**HandlerRoutine**](handlerroutine.md) functions that handle CTRL+C and CTRL+BREAK signals.</span></span> <span data-ttu-id="fe361-124">當使用者關閉主控台、登出或關閉系統時，處理常式函式也會處理系統所產生的信號。</span><span class="sxs-lookup"><span data-stu-id="fe361-124">The handler functions also handle signals generated by the system when the user closes the console, logs off, or shuts down the system.</span></span> <span data-ttu-id="fe361-125">一開始，每個進程的處理常式清單只包含呼叫 [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) 函數的預設處理函式。</span><span class="sxs-lookup"><span data-stu-id="fe361-125">Initially, the handler list for each process contains only a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function.</span></span> <span data-ttu-id="fe361-126">主控台處理常式會藉由呼叫 **SetConsoleCtrlHandler** 函式來新增或移除其他處理函式，而不會影響其他進程的處理常式函式清單。</span><span class="sxs-lookup"><span data-stu-id="fe361-126">A console process adds or removes additional handler functions by calling the **SetConsoleCtrlHandler** function, which does not affect the list of handler functions for other processes.</span></span> <span data-ttu-id="fe361-127">當主控台進程接收到任何控制信號時，會在最後一次註冊的第一個呼叫的基礎上呼叫其處理函式，直到其中一個處理常式傳回 TRUE 為止。</span><span class="sxs-lookup"><span data-stu-id="fe361-127">When a console process receives any of the control signals, its handler functions are called on a last-registered, first-called basis until one of the handlers returns TRUE.</span></span> <span data-ttu-id="fe361-128">如果沒有任何處理程式傳回 TRUE，則會呼叫預設處理常式。</span><span class="sxs-lookup"><span data-stu-id="fe361-128">If none of the handlers returns TRUE, the default handler is called.</span></span>

<span data-ttu-id="fe361-129">針對主控台進程，CTRL + C 和 CTRL + BREAK 按鍵組合通常會被視為信號 (**ctrl \_ C \_ 事件** 和 **ctrl \_ BREAK \_ 事件**) 。</span><span class="sxs-lookup"><span data-stu-id="fe361-129">For console processes, the CTRL+C and CTRL+BREAK key combinations are typically treated as signals (**CTRL\_C\_EVENT** and **CTRL\_BREAK\_EVENT**).</span></span> <span data-ttu-id="fe361-130">當具有鍵盤焦點的主控台視窗收到 CTRL + C 或 CTRL + BREAK 時，信號通常會傳遞至共用該主控台的所有進程。</span><span class="sxs-lookup"><span data-stu-id="fe361-130">When a console window with the keyboard focus receives CTRL+C or CTRL+BREAK, the signal is typically passed to all processes sharing that console.</span></span>

<span data-ttu-id="fe361-131">CTRL + BREAK 一律視為信號，但一般 CTRL + C 行為可透過三種方式來變更，以防止處理函式被呼叫：</span><span class="sxs-lookup"><span data-stu-id="fe361-131">CTRL+BREAK is always treated as a signal, but typical CTRL+C behavior can be changed in three ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="fe361-132">[**SetConsoleMode**](setconsolemode.md)函式可以停用主控台輸入緩衝區的 [**啟用已處理的 \_ \_ 輸入**] 模式，因此 CTRL + C 會回報為鍵盤輸入而非信號。</span><span class="sxs-lookup"><span data-stu-id="fe361-132">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="fe361-133">使用**Null**和**TRUE**引數呼叫**SetConsoleCtrlHandler** ，會導致呼叫進程忽略 CTRL + C 信號。</span><span class="sxs-lookup"><span data-stu-id="fe361-133">Calling **SetConsoleCtrlHandler** with the **NULL** and **TRUE** arguments causes the calling process to ignore CTRL+C signals.</span></span> <span data-ttu-id="fe361-134">這個屬性是由子進程繼承的，但可以由任何程式啟用或停用，而不會影響現有的進程。</span><span class="sxs-lookup"><span data-stu-id="fe361-134">This attribute is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>
- <span data-ttu-id="fe361-135">如果正在調試主控台進程，且未停用 CTRL + C 信號，系統會產生一個 **DBG \_ 控制項 \_ C** 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fe361-135">If a console process is being debugged and CTRL+C signals have not been disabled, the system generates a **DBG\_CONTROL\_C** exception.</span></span> <span data-ttu-id="fe361-136">只有偵錯工具的優點會引發這個例外狀況，而且應用程式不應該使用例外狀況處理常式來處理它。</span><span class="sxs-lookup"><span data-stu-id="fe361-136">This exception is raised only for the benefit of the debugger, and an application should never use an exception handler to deal with it.</span></span> <span data-ttu-id="fe361-137">如果偵錯工具處理例外狀況，應用程式將不會注意到 CTRL + C，但有一個例外狀況：可提供警示等候將會終止。</span><span class="sxs-lookup"><span data-stu-id="fe361-137">If the debugger handles the exception, an application will not notice the CTRL+C, with one exception: alertable waits will terminate.</span></span> <span data-ttu-id="fe361-138">如果偵錯工具在未處理的情況下傳遞例外狀況，則會將 CTRL + C 傳遞給主控台進程並視為信號，如先前所述。</span><span class="sxs-lookup"><span data-stu-id="fe361-138">If the debugger passes the exception on unhandled, CTRL+C is passed to the console process and treated as a signal, as previously discussed.</span></span>

<span data-ttu-id="fe361-139">主控台處理常式可以使用 [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) 函式，將 Ctrl + C 或 CTRL + BREAK 信號傳送到主控台進程群組。</span><span class="sxs-lookup"><span data-stu-id="fe361-139">A console process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a CTRL+C or CTRL+BREAK signal to a console process group.</span></span>

<span data-ttu-id="fe361-140">系統會在使用者關閉主控台、登出或關閉系統時，產生 **ctrl \_ CLOSE \_ 事件**、 **ctrl \_ 登出 \_ 事件**和 **ctrl \_ SHUTDOWN \_ 事件** 信號，讓進程有機會在終止前進行清除。</span><span class="sxs-lookup"><span data-stu-id="fe361-140">The system generates **CTRL\_CLOSE\_EVENT**, **CTRL\_LOGOFF\_EVENT**, and **CTRL\_SHUTDOWN\_EVENT** signals when the user closes the console, logs off, or shuts down the system so that the process has an opportunity to clean up before termination.</span></span> <span data-ttu-id="fe361-141">主控台函式或任何呼叫主控台函式的 C 執行時間函式，在處理先前提及的三個信號中的任一個時，可能無法可靠地運作。</span><span class="sxs-lookup"><span data-stu-id="fe361-141">Console functions, or any C run-time functions that call console functions, may not work reliably during processing of any of the three signals mentioned previously.</span></span> <span data-ttu-id="fe361-142">原因是，您可能會在執行處理信號處理常式之前呼叫部分或所有的內部主控台清除常式。</span><span class="sxs-lookup"><span data-stu-id="fe361-142">The reason is that some or all of the internal console cleanup routines may have been called before executing the process signal handler.</span></span>

<span data-ttu-id="fe361-143">**Windows 7、Windows 8、Windows 8.1 和 Windows 10：**</span><span class="sxs-lookup"><span data-stu-id="fe361-143">**Windows 7, Windows 8, Windows 8.1 and Windows 10:**</span></span>

<span data-ttu-id="fe361-144">如果主控台應用程式載入 gdi32.dll 或 user32.dll 程式庫，則在呼叫**SetConsoleCtrlHandler**時指定的[**HandlerRoutine**](handlerroutine.md)函式不會被呼叫**ctrl \_ 登出 \_ 事件**和**ctrl \_ SHUTDOWN \_ 事件**事件。</span><span class="sxs-lookup"><span data-stu-id="fe361-144">If a console application loads the gdi32.dll or user32.dll library, the [**HandlerRoutine**](handlerroutine.md) function that you specify when you call **SetConsoleCtrlHandler** does not get called for the **CTRL\_LOGOFF\_EVENT** and **CTRL\_SHUTDOWN\_EVENT** events.</span></span> <span data-ttu-id="fe361-145">作業系統會辨識載入 gdi32.dll 或 user32.dll 為 Windows 應用程式的處理常式，而不是主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="fe361-145">The operating system recognizes processes that load gdi32.dll or user32.dll as Windows applications rather than console applications.</span></span> <span data-ttu-id="fe361-146">這種行為也會發生在主控台應用程式中，這些應用程式不會直接呼叫 gdi32.dll 或 user32.dll 中的函式，而是呼叫函式（例如 [Shell](https://msdn.microsoft.com/library/windows/desktop/bb776426) 函式），進而在 gdi32.dll 或 user32.dll 中呼叫函數。</span><span class="sxs-lookup"><span data-stu-id="fe361-146">This behavior also occurs for console applications that do not call functions in gdi32.dll or user32.dll directly, but do call functions such as [Shell functions](https://msdn.microsoft.com/library/windows/desktop/bb776426) that do in turn call functions in gdi32.dll or user32.dll.</span></span>

<span data-ttu-id="fe361-147">若要在使用者登出或裝置在這些情況下關閉時接收事件，請在主控台應用程式中建立隱藏的視窗，然後處理隱藏視窗所接收的 [**wm \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) 和 [**wm \_ ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) 視窗訊息。</span><span class="sxs-lookup"><span data-stu-id="fe361-147">To receive events when a user signs out or the device shuts down in these circumstances, create a hidden window in your console application, and then handle the [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) and [**WM\_ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) window messages that the hidden window receives.</span></span> <span data-ttu-id="fe361-148">您可以呼叫 [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) 方法，並將 *dwExStyle* 參數設定為0，以建立隱藏視窗。</span><span class="sxs-lookup"><span data-stu-id="fe361-148">You can create a hidden window by calling the [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) method with the *dwExStyle* parameter set to 0.</span></span>

<a name="examples"></a><span data-ttu-id="fe361-149">範例</span><span class="sxs-lookup"><span data-stu-id="fe361-149">Examples</span></span>
--------

<span data-ttu-id="fe361-150">如需範例，請參閱 [註冊控制項處理常式函數](registering-a-control-handler-function.md)。</span><span class="sxs-lookup"><span data-stu-id="fe361-150">For an example, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>

<a name="requirements"></a><span data-ttu-id="fe361-151">規格需求</span><span class="sxs-lookup"><span data-stu-id="fe361-151">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="fe361-152">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="fe361-152">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="fe361-153">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="fe361-153">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="fe361-154">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="fe361-154">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="fe361-155">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="fe361-155">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="fe361-156">標頭</span><span class="sxs-lookup"><span data-stu-id="fe361-156">Header</span></span></p></td>
<td><span data-ttu-id="fe361-157">ConsoleApi .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="fe361-157">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="fe361-158">程式庫</span><span class="sxs-lookup"><span data-stu-id="fe361-158">Library</span></span></p></td>
<td><span data-ttu-id="fe361-159">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="fe361-159">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="fe361-160">DLL</span><span class="sxs-lookup"><span data-stu-id="fe361-160">DLL</span></span></p></td>
<td><span data-ttu-id="fe361-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="fe361-161">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="fe361-162"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe361-162"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="fe361-163">主控台控制處理常式</span><span class="sxs-lookup"><span data-stu-id="fe361-163">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="fe361-164">主控台功能</span><span class="sxs-lookup"><span data-stu-id="fe361-164">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="fe361-165">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="fe361-165">**ExitProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[<span data-ttu-id="fe361-166">**GenerateConsoleCtrlEvent**</span><span class="sxs-lookup"><span data-stu-id="fe361-166">**GenerateConsoleCtrlEvent**</span></span>](generateconsolectrlevent.md)

[<span data-ttu-id="fe361-167">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="fe361-167">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="fe361-168">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="fe361-168">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="fe361-169">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="fe361-169">**SetConsoleMode**</span></span>](setconsolemode.md)

 

 





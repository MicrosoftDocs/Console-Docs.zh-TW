---
title: SetConsoleCtrlHandler 函式
description: 從呼叫程序的處理常式函式清單中新增或移除應用程式定義的 HandlerRoutine 函式。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
ms.localizationpriority: high
ms.openlocfilehash: 03e7166f84be2f760a4ffea385225390bdb3ffa1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357708"
---
# <a name="setconsolectrlhandler-function"></a><span data-ttu-id="8ae6a-104">SetConsoleCtrlHandler 函式</span><span class="sxs-lookup"><span data-stu-id="8ae6a-104">SetConsoleCtrlHandler function</span></span>

<span data-ttu-id="8ae6a-105">從呼叫程序的處理常式函式清單中新增或移除應用程式定義的 [**HandlerRoutine**](handlerroutine.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-105">Adds or removes an application-defined [**HandlerRoutine**](handlerroutine.md) function from the list of handler functions for the calling process.</span></span>

<span data-ttu-id="8ae6a-106">如果未指定處理常式函式，該函式就會設定可繼承的屬性，以決定呼叫程序是否會忽略 <kbd>CTRL</kbd>+<kbd>C</kbd> 訊號。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-106">If no handler function is specified, the function sets an inheritable attribute that determines whether the calling process ignores <kbd>CTRL</kbd>+<kbd>C</kbd> signals.</span></span>

## <a name="syntax"></a><span data-ttu-id="8ae6a-107">語法</span><span class="sxs-lookup"><span data-stu-id="8ae6a-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

## <a name="parameters"></a><span data-ttu-id="8ae6a-108">參數</span><span class="sxs-lookup"><span data-stu-id="8ae6a-108">Parameters</span></span>

<span data-ttu-id="8ae6a-109">*HandlerRoutine* \[輸入、選擇性\]</span><span class="sxs-lookup"><span data-stu-id="8ae6a-109">*HandlerRoutine* \[in, optional\]</span></span>  
<span data-ttu-id="8ae6a-110">指標，指示要加入或移除應用程式定義的 [**HandlerRoutine**](handlerroutine.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-110">A pointer to the application-defined [**HandlerRoutine**](handlerroutine.md) function to be added or removed.</span></span> <span data-ttu-id="8ae6a-111">此參數可以是 **Null**。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-111">This parameter can be **NULL**.</span></span>

<span data-ttu-id="8ae6a-112">*Add* \[輸入\]</span><span class="sxs-lookup"><span data-stu-id="8ae6a-112">*Add* \[in\]</span></span>  
<span data-ttu-id="8ae6a-113">如果此參數是 **TRUE**，則會加入處理常式；如果是 **FALSE**，則會移除處理常式。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-113">If this parameter is **TRUE**, the handler is added; if it is **FALSE**, the handler is removed.</span></span>

<span data-ttu-id="8ae6a-114">如果 *HandlerRoutine* 參數是 **Null**，**TRUE** 值就會使呼叫程序忽略 <kbd>CTRL</kbd>+<kbd>C</kbd> 的輸入，而 **FALSE** 值則會還原 <kbd>CTRL</kbd>+<kbd>C</kbd> 輸入的正常處理程序。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-114">If the *HandlerRoutine* parameter is **NULL**, a **TRUE** value causes the calling process to ignore <kbd>CTRL</kbd>+<kbd>C</kbd> input, and a **FALSE** value restores normal processing of <kbd>CTRL</kbd>+<kbd>C</kbd> input.</span></span> <span data-ttu-id="8ae6a-115">忽略或處理 <kbd>CTRL</kbd>+<kbd>C</kbd> 的此屬性會由子程序繼承。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-115">This attribute of ignoring or processing <kbd>CTRL</kbd>+<kbd>C</kbd> is inherited by child processes.</span></span>

## <a name="return-value"></a><span data-ttu-id="8ae6a-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="8ae6a-116">Return value</span></span>

<span data-ttu-id="8ae6a-117">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="8ae6a-118">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="8ae6a-119">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-119">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="8ae6a-120">備註</span><span class="sxs-lookup"><span data-stu-id="8ae6a-120">Remarks</span></span>

<span data-ttu-id="8ae6a-121">針對 [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) 使用訊息幫浦為圖形應用程式提供的通知，此函式會為主控台應用程式和服務提供類似的通知。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-121">This function provides a similar notification for console application and services that [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) provides for graphical applications with a message pump.</span></span> <span data-ttu-id="8ae6a-122">您也可以從圖形應用程式中使用此函式，但不保證其會在 **WM\_QUERYENDSESSION** 的通知之前抵達。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-122">You could also use this function from a graphical application, but there is no guarantee it would arrive before the notification from **WM\_QUERYENDSESSION**.</span></span>

<span data-ttu-id="8ae6a-123">每個主控台程序都會自備應用程式定義的 [**HandlerRoutine**](handlerroutine.md)清單，可處理 <kbd>CTRL</kbd>+<kbd>C</kbd> 和 <kbd>CTRL</kbd>+<kbd>BREAK</kbd> 函式。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-123">Each console process has its own list of application-defined [**HandlerRoutine**](handlerroutine.md) functions that handle <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> signals.</span></span> <span data-ttu-id="8ae6a-124">當使用者關閉主控台、登出或關閉系統時，處理常式函式也會處理系統所產生的訊號。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-124">The handler functions also handle signals generated by the system when the user closes the console, logs off, or shuts down the system.</span></span> <span data-ttu-id="8ae6a-125">一開始，每個程序的處理常式清單只會包含預設的處理常式函式，該函式會呼叫 [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) 函式。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-125">Initially, the handler list for each process contains only a default handler function that calls the [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) function.</span></span> <span data-ttu-id="8ae6a-126">主控台程序會藉由呼叫 **SetConsoleCtrlHandler** 函式來新增或移除其他處理常式函式，而這不會影響其他程序的處理常式函式清單。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-126">A console process adds or removes additional handler functions by calling the **SetConsoleCtrlHandler** function, which does not affect the list of handler functions for other processes.</span></span> <span data-ttu-id="8ae6a-127">主控台程序會在收到任何控制訊號時，依據「最後註冊的先呼叫」原則來呼叫其處理常式函式，直到其中一個處理常式傳回 `TRUE` 為止。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-127">When a console process receives any of the control signals, its handler functions are called on a last-registered, first-called basis until one of the handlers returns `TRUE`.</span></span> <span data-ttu-id="8ae6a-128">如果沒有任何處理常式傳回 `TRUE`，則會呼叫預設的處理常式。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-128">If none of the handlers returns `TRUE`, the default handler is called.</span></span>

<span data-ttu-id="8ae6a-129">對於主控台程序，<kbd>CTRL</kbd>+<kbd>C</kbd> 和 <kbd>CTRL</kbd>+<kbd>BREAK</kbd> 按鍵組合通常會被視為訊號 (**CTRL\_C\_EVENT** 和 **CTRL\_BREAK\_EVENT**)。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-129">For console processes, the <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations are typically treated as signals (**CTRL\_C\_EVENT** and **CTRL\_BREAK\_EVENT**).</span></span> <span data-ttu-id="8ae6a-130">當具有鍵盤焦點的主控台視窗收到 <kbd>CTRL</kbd>+<kbd>C</kbd> 或 <kbd>CTRL</kbd>+<kbd>BREAK</kbd> 時，訊號通常會傳遞至所有共用該主控台的程序。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-130">When a console window with the keyboard focus receives <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd>, the signal is typically passed to all processes sharing that console.</span></span>

<span data-ttu-id="8ae6a-131"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> 一律會被視為訊號，但是典型的 <kbd>CTRL</kbd>+<kbd>C</kbd> 行為可透過三種方式來變更，以防止呼叫處理常式函式：</span><span class="sxs-lookup"><span data-stu-id="8ae6a-131"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but typical <kbd>CTRL</kbd>+<kbd>C</kbd> behavior can be changed in three ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="8ae6a-132">[**SetConsoleMode**](setconsolemode.md) 函式可以停用主控台輸入緩衝區的 **ENABLE\_PROCESSED\_INPUT** 模式，因此會將 <kbd>CTRL</kbd>+<kbd>C</kbd> 回報為鍵盤輸入，而非訊號。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-132">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** mode for a console's input buffer, so <kbd>CTRL</kbd>+<kbd>C</kbd> is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="8ae6a-133">使用 **Null** 和 **TRUE** 引數呼叫 **SetConsoleCtrlHandler** 會使呼叫程序忽略 <kbd>CTRL</kbd>+<kbd>C</kbd> 訊號。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-133">Calling **SetConsoleCtrlHandler** with the **NULL** and **TRUE** arguments causes the calling process to ignore <kbd>CTRL</kbd>+<kbd>C</kbd> signals.</span></span> <span data-ttu-id="8ae6a-134">此屬性會由子程序繼承，但是可由任何程序啟用或停用，而不會影響現有的程序。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-134">This attribute is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>
- <span data-ttu-id="8ae6a-135">如果正在對主控台程序進行偵錯，而且尚未停用 <kbd>CTRL</kbd>+<kbd>C</kbd> 訊號，則系統會產生 **DBG\_CONTROL\_C** 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-135">If a console process is being debugged and <kbd>CTRL</kbd>+<kbd>C</kbd> signals have not been disabled, the system generates a **DBG\_CONTROL\_C** exception.</span></span> <span data-ttu-id="8ae6a-136">此例外狀況的引發只會有益於偵錯工具，應用程式不應使用例外狀況處理常式來處理此狀況。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-136">This exception is raised only for the benefit of the debugger, and an application should never use an exception handler to deal with it.</span></span> <span data-ttu-id="8ae6a-137">如果偵錯工具處理了此例外狀況，應用程式將不會注意到 <kbd>CTRL</kbd>+<kbd>C</kbd>，但會有一個例外：可警告的等待會終止。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-137">If the debugger handles the exception, an application will not notice the <kbd>CTRL</kbd>+<kbd>C</kbd>, with one exception: alertable waits will terminate.</span></span> <span data-ttu-id="8ae6a-138">如果偵錯工具傳遞未處理的例外狀況，則 <kbd>CTRL</kbd>+<kbd>C</kbd> 會傳遞至主控台程序並視為訊號，如先前所述。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-138">If the debugger passes the exception on unhandled, <kbd>CTRL</kbd>+<kbd>C</kbd> is passed to the console process and treated as a signal, as previously discussed.</span></span>

<span data-ttu-id="8ae6a-139">主控台程序可以使用 [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) 函式來將 <kbd>CTRL</kbd>+<kbd>C</kbd> 或 <kbd>CTRL</kbd>+<kbd>BREAK</kbd> 訊號傳送到主控台程序群組。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-139">A console process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> signal to a console process group.</span></span>

<span data-ttu-id="8ae6a-140">當使用者關閉主控台、登出或關閉系統時，系統會產生 **CTRL\_CLOSE\_EVENT**、**CTRL\_LOGOFF\_EVENT** 及 **CTRL\_SHUTDOWN\_EVENT** ，讓程序有機會在終止前進行清除。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-140">The system generates **CTRL\_CLOSE\_EVENT**, **CTRL\_LOGOFF\_EVENT**, and **CTRL\_SHUTDOWN\_EVENT** signals when the user closes the console, logs off, or shuts down the system so that the process has an opportunity to clean up before termination.</span></span> <span data-ttu-id="8ae6a-141">在處理上述三個訊號中的任何一個時，主控台函式或任何呼叫主控台函式的任何 C 執行階段函式可能無法可靠地運作。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-141">Console functions, or any C run-time functions that call console functions, may not work reliably during processing of any of the three signals mentioned previously.</span></span> <span data-ttu-id="8ae6a-142">這可能是因為執行程序訊號處理常式之前，已經呼叫部分或所有內部主控台清理常式。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-142">The reason is that some or all of the internal console cleanup routines may have been called before executing the process signal handler.</span></span>

<span data-ttu-id="8ae6a-143">**Windows 7、Windows 8、Windows 8.1 和 Windows 10：**</span><span class="sxs-lookup"><span data-stu-id="8ae6a-143">**Windows 7, Windows 8, Windows 8.1 and Windows 10:**</span></span>

<span data-ttu-id="8ae6a-144">如果主控台應用程式載入 gdi32.dll 或 user32.dll 程式庫，則發生 **CTRL\_LOGOFF\_EVENT** 和 **CTRL\_SHUTDOWN\_EVENT** 事件時，就不會呼叫您在呼叫 **SetConsoleCtrlHandler** 時指定的 [**HandlerRoutine**](handlerroutine.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-144">If a console application loads the gdi32.dll or user32.dll library, the [**HandlerRoutine**](handlerroutine.md) function that you specify when you call **SetConsoleCtrlHandler** does not get called for the **CTRL\_LOGOFF\_EVENT** and **CTRL\_SHUTDOWN\_EVENT** events.</span></span> <span data-ttu-id="8ae6a-145">作業系統會將載入 gdi32.dll 或 user32.dll 的程序辨識為 Windows 應用程式，而非主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-145">The operating system recognizes processes that load gdi32.dll or user32.dll as Windows applications rather than console applications.</span></span> <span data-ttu-id="8ae6a-146">如果主控台應用程式不會直接呼叫 gdi32.dll 或 user32.dll 中的函式，也會發生這種行為，但呼叫 [Shell 函式](/previous-versions/windows/desktop/legacy/bb776426(v=vs.85))之類的函式反而會呼叫 gdi32.dll 或 user32.dll 中的函式。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-146">This behavior also occurs for console applications that do not call functions in gdi32.dll or user32.dll directly, but do call functions such as [Shell functions](/previous-versions/windows/desktop/legacy/bb776426(v=vs.85)) that do in turn call functions in gdi32.dll or user32.dll.</span></span>

<span data-ttu-id="8ae6a-147">若要在因為這些情況造成使用者登出或關閉裝置時接收事件，請在您的主控台應用程式中建立隱藏視窗，然後處理已隱藏視窗接收的 [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) 和 [**WM\_ENDSESSION**](/windows/win32/shutdown/wm-endsession) 視窗訊息。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-147">To receive events when a user signs out or the device shuts down in these circumstances, create a hidden window in your console application, and then handle the [**WM\_QUERYENDSESSION**](/windows/win32/shutdown/wm-queryendsession) and [**WM\_ENDSESSION**](/windows/win32/shutdown/wm-endsession) window messages that the hidden window receives.</span></span> <span data-ttu-id="8ae6a-148">您可以藉由呼叫 [**CreateWindowEx**](/windows/win32/api/winuser/nf-winuser-createwindowexa) 方法，並將 *dwExStyle* 參數設定為 0，來建立隱藏視窗。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-148">You can create a hidden window by calling the [**CreateWindowEx**](/windows/win32/api/winuser/nf-winuser-createwindowexa) method with the *dwExStyle* parameter set to 0.</span></span>

## <a name="examples"></a><span data-ttu-id="8ae6a-149">範例</span><span class="sxs-lookup"><span data-stu-id="8ae6a-149">Examples</span></span>

<span data-ttu-id="8ae6a-150">如需範例，請參閱[註冊控制處理常式函式](registering-a-control-handler-function.md)。</span><span class="sxs-lookup"><span data-stu-id="8ae6a-150">For an example, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="8ae6a-151">規格需求</span><span class="sxs-lookup"><span data-stu-id="8ae6a-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="8ae6a-152">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="8ae6a-152">Minimum supported client</span></span> | <span data-ttu-id="8ae6a-153">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="8ae6a-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="8ae6a-154">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="8ae6a-154">Minimum supported server</span></span> | <span data-ttu-id="8ae6a-155">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="8ae6a-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="8ae6a-156">標頭</span><span class="sxs-lookup"><span data-stu-id="8ae6a-156">Header</span></span> | <span data-ttu-id="8ae6a-157">ConsoleApi.h (透過 WinCon.h，包括 Windows.h)</span><span class="sxs-lookup"><span data-stu-id="8ae6a-157">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="8ae6a-158">程式庫</span><span class="sxs-lookup"><span data-stu-id="8ae6a-158">Library</span></span> | <span data-ttu-id="8ae6a-159">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="8ae6a-159">Kernel32.lib</span></span> |
| <span data-ttu-id="8ae6a-160">DLL</span><span class="sxs-lookup"><span data-stu-id="8ae6a-160">DLL</span></span> | <span data-ttu-id="8ae6a-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="8ae6a-161">Kernel32.dll</span></span> |
| <span data-ttu-id="8ae6a-162">Unicode 與 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="8ae6a-162">Unicode and ANSI names</span></span> | |

## <a name="see-also"></a><span data-ttu-id="8ae6a-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ae6a-163">See also</span></span>

[<span data-ttu-id="8ae6a-164">主控台控制處理常式</span><span class="sxs-lookup"><span data-stu-id="8ae6a-164">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="8ae6a-165">主控台函式</span><span class="sxs-lookup"><span data-stu-id="8ae6a-165">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="8ae6a-166">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="8ae6a-166">**ExitProcess**</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)

[<span data-ttu-id="8ae6a-167">**GenerateConsoleCtrlEvent**</span><span class="sxs-lookup"><span data-stu-id="8ae6a-167">**GenerateConsoleCtrlEvent**</span></span>](generateconsolectrlevent.md)

[<span data-ttu-id="8ae6a-168">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="8ae6a-168">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="8ae6a-169">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="8ae6a-169">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="8ae6a-170">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="8ae6a-170">**SetConsoleMode**</span></span>](setconsolemode.md)
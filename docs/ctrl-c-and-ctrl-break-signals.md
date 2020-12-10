---
title: CTRL+C 和 CTRL+BREAK 訊號
description: CTRL+C 和 CTRL+BREAK 按鍵組合會經由主控台程序接收特殊處理。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- base.ctrl\_c\_and\_ctrl\_break\_signals
- consoles.ctrl\_c\_and\_ctrl\_break\_signals
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
ms.localizationpriority: high
ms.openlocfilehash: 38cc3486a9e945635147c2e17a4d2f0d197d1d3c
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420187"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a><span data-ttu-id="48078-104">CTRL+C 和 CTRL+BREAK 訊號</span><span class="sxs-lookup"><span data-stu-id="48078-104">CTRL+C and CTRL+BREAK Signals</span></span>

<span data-ttu-id="48078-105"><kbd>CTRL</kbd>+<kbd>C</kbd> 和 <kbd>CTRL</kbd>+<kbd>BREAK</kbd> 按鍵組合會經由主控台程序接收特殊處理。</span><span class="sxs-lookup"><span data-stu-id="48078-105">The <kbd>CTRL</kbd>+<kbd>C</kbd> and <kbd>CTRL</kbd>+<kbd>BREAK</kbd> key combinations receive special handling by console processes.</span></span> <span data-ttu-id="48078-106">根據預設，當主控台視窗具有鍵盤焦點時，<kbd>CTRL</kbd>+<kbd>C</kbd> 或 <kbd>CTRL</kbd>+<kbd>BREAK</kbd> 會被視為訊號 (SIGINT 或 SIGBREAK)，而不是鍵盤輸入。</span><span class="sxs-lookup"><span data-stu-id="48078-106">By default, when a console window has the keyboard focus, <kbd>CTRL</kbd>+<kbd>C</kbd> or <kbd>CTRL</kbd>+<kbd>BREAK</kbd> is treated as a signal (SIGINT or SIGBREAK) and not as keyboard input.</span></span> <span data-ttu-id="48078-107">根據預設，這些訊號會傳遞到已連結至主控台的所有主控台程序。</span><span class="sxs-lookup"><span data-stu-id="48078-107">By default, these signals are passed to all console processes that are attached to the console.</span></span> <span data-ttu-id="48078-108">(已中斷連結的程序不受影響。</span><span class="sxs-lookup"><span data-stu-id="48078-108">(Detached processes are not affected.</span></span> <span data-ttu-id="48078-109">請參閱 [**建立主控台**](creation-of-a-console.md)。)系統會在每個用戶端程序中建立新執行緒來處理事件。</span><span class="sxs-lookup"><span data-stu-id="48078-109">See [**Creation of a Console**](creation-of-a-console.md).) The system creates a new thread in each client process to handle the event.</span></span> <span data-ttu-id="48078-110">如果程序正在進行偵錯，執行緒就會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="48078-110">The thread raises an exception if the process is being debugged.</span></span> <span data-ttu-id="48078-111">偵錯工具可以處理例外狀況，或繼續未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="48078-111">The debugger can handle the exception or continue with the exception unhandled.</span></span>

<span data-ttu-id="48078-112"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> 一律會被視為訊號，但是應用程式可以使用兩種方式來變更預設的 <kbd>CTRL</kbd>+<kbd>C</kbd> 行為，以防止呼叫處理常式函式：</span><span class="sxs-lookup"><span data-stu-id="48078-112"><kbd>CTRL</kbd>+<kbd>BREAK</kbd> is always treated as a signal, but an application can change the default <kbd>CTRL</kbd>+<kbd>C</kbd> behavior in two ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="48078-113">[**SetConsoleMode**](setconsolemode.md) 函式可以停用主控台輸入緩衝區的 **ENABLE\_PROCESSED\_INPUT** 輸入模式，因此會將 CTRL+C 回報為鍵盤輸入，而非訊號。</span><span class="sxs-lookup"><span data-stu-id="48078-113">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** input mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="48078-114">當 [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) 與其參數的 **NULL** and **TRUE** 值一起呼叫時，呼叫程序會忽略 CTRL+C 訊號。</span><span class="sxs-lookup"><span data-stu-id="48078-114">When [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) is called with **NULL** and **TRUE** values for its parameters, the calling process ignores CTRL+C signals.</span></span> <span data-ttu-id="48078-115">正常的 CTRL+C 處理會使用 **NULL** 和 **FALSE** 值呼叫 **SetConsoleCtrlHandler**，藉此進行還原。</span><span class="sxs-lookup"><span data-stu-id="48078-115">Normal CTRL+C processing is restored by calling **SetConsoleCtrlHandler** with **NULL** and **FALSE** values.</span></span> <span data-ttu-id="48078-116">這個忽略或不忽略 CTRL+C 訊號的屬性會由子程序繼承，但是可由任何程序啟用或停用，而不會影響現有的程序。</span><span class="sxs-lookup"><span data-stu-id="48078-116">This attribute of ignoring or not ignoring CTRL+C signals is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>

<span data-ttu-id="48078-117">如需有關如何處理這些訊號 (包括逾時) 的詳細資訊，請參閱 [**處理常式**](handlerroutine.md)回呼文件。</span><span class="sxs-lookup"><span data-stu-id="48078-117">For more information on how these signals are processed, including timeouts, please see the [**Handler Routine**](handlerroutine.md) callback documentation.</span></span>

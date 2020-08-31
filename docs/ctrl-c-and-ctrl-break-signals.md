---
title: CTRL + C 和 CTRL + BREAK 信號
description: CTRL + C 和 CTRL + BREAK 按鍵組合會接收主控台進程的特殊處理。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- base.ctrl\_c\_and\_ctrl\_break\_signals
- consoles.ctrl\_c\_and\_ctrl\_break\_signals
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
ms.openlocfilehash: 95e28c9d390e9edb0be7dcac5aa4600224ab118c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059215"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a><span data-ttu-id="ce7c2-104">CTRL + C 和 CTRL + BREAK 信號</span><span class="sxs-lookup"><span data-stu-id="ce7c2-104">CTRL+C and CTRL+BREAK Signals</span></span>


<span data-ttu-id="ce7c2-105">CTRL + C 和 CTRL + BREAK 按鍵組合會接收主控台進程的特殊處理。</span><span class="sxs-lookup"><span data-stu-id="ce7c2-105">The CTRL+C and CTRL+BREAK key combinations receive special handling by console processes.</span></span> <span data-ttu-id="ce7c2-106">根據預設，當主控台視窗具有鍵盤焦點時，會將 CTRL + C 或 CTRL + BREAK 視為信號 (SIGINT 或 SIGBREAK) ，而不是鍵盤輸入。</span><span class="sxs-lookup"><span data-stu-id="ce7c2-106">By default, when a console window has the keyboard focus, CTRL+C or CTRL+BREAK is treated as a signal (SIGINT or SIGBREAK) and not as keyboard input.</span></span> <span data-ttu-id="ce7c2-107">根據預設，這些信號會傳遞至所有連接到主控台的主控台處理常式。</span><span class="sxs-lookup"><span data-stu-id="ce7c2-107">By default, these signals are passed to all console processes that are attached to the console.</span></span> <span data-ttu-id="ce7c2-108"> (卸離的進程不會受到影響。 ) 系統會在每個用戶端進程中建立新的執行緒，以處理事件。</span><span class="sxs-lookup"><span data-stu-id="ce7c2-108">(Detached processes are not affected.) The system creates a new thread in each client process to handle the event.</span></span> <span data-ttu-id="ce7c2-109">如果正在調試進程，執行緒就會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ce7c2-109">The thread raises an exception if the process is being debugged.</span></span> <span data-ttu-id="ce7c2-110">偵錯工具可以處理例外狀況，或繼續進行未處理的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ce7c2-110">The debugger can handle the exception or continue with the exception unhandled.</span></span>

<span data-ttu-id="ce7c2-111">CTRL + BREAK 一律會被視為信號，但是應用程式可以透過兩種防止處理函式被呼叫的方式，來變更預設的 CTRL + C 行為：</span><span class="sxs-lookup"><span data-stu-id="ce7c2-111">CTRL+BREAK is always treated as a signal, but an application can change the default CTRL+C behavior in two ways that prevent the handler functions from being called:</span></span>

- <span data-ttu-id="ce7c2-112">[**SetConsoleMode**](setconsolemode.md)函式可以停用主控台輸入緩衝區的已\*\* \_ 處理 \_ 輸入\*\*輸入模式，因此 CTRL + C 會回報為鍵盤輸入而非信號。</span><span class="sxs-lookup"><span data-stu-id="ce7c2-112">The [**SetConsoleMode**](setconsolemode.md) function can disable the **ENABLE\_PROCESSED\_INPUT** input mode for a console's input buffer, so CTRL+C is reported as keyboard input rather than as a signal.</span></span>
- <span data-ttu-id="ce7c2-113">當針對其參數使用**Null**和**TRUE**值呼叫[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)時，呼叫進程會忽略 CTRL + C 信號。</span><span class="sxs-lookup"><span data-stu-id="ce7c2-113">When [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) is called with **NULL** and **TRUE** values for its parameters, the calling process ignores CTRL+C signals.</span></span> <span data-ttu-id="ce7c2-114">使用**Null**和**FALSE**值來呼叫**SETCONSOLECTRLHANDLER** ，即可還原一般 CTRL + C 處理。</span><span class="sxs-lookup"><span data-stu-id="ce7c2-114">Normal CTRL+C processing is restored by calling **SetConsoleCtrlHandler** with **NULL** and **FALSE** values.</span></span> <span data-ttu-id="ce7c2-115">忽略或忽略 CTRL + C 信號的這個屬性會由子進程繼承，但是任何程式都可以啟用或停用它，而不會影響現有的進程。</span><span class="sxs-lookup"><span data-stu-id="ce7c2-115">This attribute of ignoring or not ignoring CTRL+C signals is inherited by child processes, but it can be enabled or disabled by any process without affecting existing processes.</span></span>

 

 





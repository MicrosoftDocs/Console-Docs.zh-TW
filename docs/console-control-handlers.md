---
title: 主控台控制處理常式
description: 每個主控台程式都有自己的控制項處理常式函式清單，當進程收到 CTRL + C、CTRL + BREAK 或 CTRL + CLOSE 信號時，系統會呼叫這些函式。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_console\_control\_handlers'
- base.console\_control\_handlers
- consoles.console\_control\_handlers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6480e8ee-d228-4c07-99df-de1e0c3ca250
ms.openlocfilehash: 41a1326b5b27531bf74ac571d6881a0f67c2b073
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038426"
---
# <a name="console-control-handlers"></a><span data-ttu-id="6bddf-104">主控台控制處理常式</span><span class="sxs-lookup"><span data-stu-id="6bddf-104">Console Control Handlers</span></span>

<span data-ttu-id="6bddf-105">每個主控台程式都有自己的控制項處理常式函式清單，當進程收到 [ctrl + C](ctrl-c-and-ctrl-break-signals.md)、 [ctrl + BREAK](ctrl-c-and-ctrl-break-signals.md)或 [ctrl + CLOSE](ctrl-close-signal.md) 信號時，系統會呼叫這些函式。</span><span class="sxs-lookup"><span data-stu-id="6bddf-105">Each console process has its own list of control handler functions that are called by the system when the process receives a [CTRL+C](ctrl-c-and-ctrl-break-signals.md), [CTRL+BREAK](ctrl-c-and-ctrl-break-signals.md), or [CTRL+CLOSE](ctrl-close-signal.md) signal.</span></span> <span data-ttu-id="6bddf-106">一開始，每個進程的控制項處理常式清單只包含呼叫 [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) 函數的預設處理函式。</span><span class="sxs-lookup"><span data-stu-id="6bddf-106">Initially, the list of control handlers for each process contains only a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function.</span></span> <span data-ttu-id="6bddf-107">主控台進程可以藉由呼叫 [**SetConsoleCtrlHandler**](setconsolectrlhandler.md)函數來新增或移除其他 [**HandlerRoutine**](handlerroutine.md)函式。</span><span class="sxs-lookup"><span data-stu-id="6bddf-107">A console process can add or remove additional [**HandlerRoutine**](handlerroutine.md) functions by calling the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function.</span></span> <span data-ttu-id="6bddf-108">此函數不會影響其他進程的控制項處理常式清單。</span><span class="sxs-lookup"><span data-stu-id="6bddf-108">This function does not affect the lists of control handlers for other processes.</span></span> <span data-ttu-id="6bddf-109">當主控台進程收到任何控制信號時，它會在最後註冊的第一個呼叫端上呼叫處理函式，直到其中一個處理常式傳回 **TRUE** 為止。</span><span class="sxs-lookup"><span data-stu-id="6bddf-109">When a console process receives any of the control signals, it calls the handler functions on a last-registered, first-called basis until one of the handlers returns **TRUE** .</span></span> <span data-ttu-id="6bddf-110">如果沒有任何處理程式傳回 **TRUE** ，則會呼叫預設處理常式。</span><span class="sxs-lookup"><span data-stu-id="6bddf-110">If none of the handlers returns **TRUE** , the default handler is called.</span></span>

<span data-ttu-id="6bddf-111">函式的 *dwCtrlType* 參數會識別收到的控制項信號，而傳回值會指出是否已處理信號。</span><span class="sxs-lookup"><span data-stu-id="6bddf-111">The function's *dwCtrlType* parameter identifies which control signal was received, and the return value indicates whether the signal was handled.</span></span>

<span data-ttu-id="6bddf-112">新的執行緒會在命令列用戶端進程內啟動，以執行處理常式常式。</span><span class="sxs-lookup"><span data-stu-id="6bddf-112">A new thread is started inside the command-line client process to run the handler routines.</span></span> <span data-ttu-id="6bddf-113">您可以在 [**HandlerRoutine**](handlerroutine.md#remarks) 函式檔中找到有關此執行緒之超時值和動作的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="6bddf-113">More information on the timeout values and action of this thread can be found in the [**HandlerRoutine**](handlerroutine.md#remarks) function documentation.</span></span>

<span data-ttu-id="6bddf-114">如需控制項處理常式函式的範例，請參閱 [註冊控制項處理常式](registering-a-control-handler-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="6bddf-114">For an example of a control handler function, see [Registering a Control Handler Function](registering-a-control-handler-function.md).</span></span>

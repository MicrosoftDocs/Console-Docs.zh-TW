---
title: 主控台模式
description: 與每個主控台輸入緩衝區相關聯的是一組會影響輸入作業的輸入模式。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_console\_modes'
- base.console\_modes
- consoles.console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f0dcc123-3b12-44c4-8f94-920203f5198e
ms.openlocfilehash: b00f53a282833b560a29c6bed4c7ef0b9e056ba5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059318"
---
# <a name="console-modes"></a><span data-ttu-id="7eba7-104">主控台模式</span><span class="sxs-lookup"><span data-stu-id="7eba7-104">Console Modes</span></span>


<span data-ttu-id="7eba7-105">與每個主控台輸入緩衝區相關聯的是一組會影響輸入作業的輸入模式。</span><span class="sxs-lookup"><span data-stu-id="7eba7-105">Associated with each console input buffer is a set of input modes that affects input operations.</span></span> <span data-ttu-id="7eba7-106">同樣地，每個主控台畫面緩衝區都有一組會影響輸出作業的輸出模式。</span><span class="sxs-lookup"><span data-stu-id="7eba7-106">Similarly, each console screen buffer has a set of output modes that affects output operations.</span></span> <span data-ttu-id="7eba7-107">輸入模式可以分為兩個群組：影響高階輸入函式的群組，以及影響低層級輸入函數的群組。</span><span class="sxs-lookup"><span data-stu-id="7eba7-107">The input modes can be divided into two groups: those that affect the high-level input functions and those that affect the low-level input functions.</span></span> <span data-ttu-id="7eba7-108">輸出模式只會影響使用高階輸出功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7eba7-108">The output modes only affect applications that use the high-level output functions.</span></span>

<span data-ttu-id="7eba7-109">[**GetConsoleMode**](getconsolemode.md)函式會報告目前的主控台輸入緩衝區輸入模式，或螢幕緩衝區目前的輸出模式。</span><span class="sxs-lookup"><span data-stu-id="7eba7-109">The [**GetConsoleMode**](getconsolemode.md) function reports the current input mode of a console's input buffer or the current output mode of a screen buffer.</span></span> <span data-ttu-id="7eba7-110">[**SetConsoleMode**](setconsolemode.md)函式會設定主控台輸入緩衝區或螢幕緩衝區的目前模式。</span><span class="sxs-lookup"><span data-stu-id="7eba7-110">The [**SetConsoleMode**](setconsolemode.md) function sets the current mode of either a console input buffer or a screen buffer.</span></span> <span data-ttu-id="7eba7-111">如果主控台有多個螢幕緩衝區，則每個畫面的輸出模式都可能不同。</span><span class="sxs-lookup"><span data-stu-id="7eba7-111">If a console has multiple screen buffers, the output modes of each can be different.</span></span> <span data-ttu-id="7eba7-112">應用程式可以隨時變更 i/o 模式。</span><span class="sxs-lookup"><span data-stu-id="7eba7-112">An application can change I/O modes at any time.</span></span> <span data-ttu-id="7eba7-113">如需影響高階和低層級 i/o 作業的主控台模式詳細資訊，請參閱 [高階主控台模式](high-level-console-modes.md) 和 [低層級的主控台模式](low-level-console-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="7eba7-113">For more information about the console modes that affect high-level and low-level I/O operations, see [High-Level Console Modes](high-level-console-modes.md) and [Low-Level Console Modes](low-level-console-modes.md).</span></span>

<span data-ttu-id="7eba7-114">[**GetConsoleDisplayMode**](getconsoledisplaymode.md)函式會報告目前的主控台是否處於全螢幕模式，以及它是否與硬體直接通訊。</span><span class="sxs-lookup"><span data-stu-id="7eba7-114">The [**GetConsoleDisplayMode**](getconsoledisplaymode.md) function reports whether the current console is in full-screen mode and whether it communicates directly with the hardware.</span></span>

 

 





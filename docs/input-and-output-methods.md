---
title: 輸入和輸出方法
description: 主控台 i/o 有兩種不同的方法，其選擇取決於應用程式所需的彈性和控制程度。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_input\_and\_output\_methods'
- base.input\_and\_output\_methods
- consoles.input\_and\_output\_methods
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55a86d5d-d0b1-4d0c-b42f-7342809289ad
ms.openlocfilehash: 8ad03cc2be8cce2c174ac4a72f700cbb31b7fd94
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039556"
---
# <a name="input-and-output-methods"></a><span data-ttu-id="81b0f-104">輸入和輸出方法</span><span class="sxs-lookup"><span data-stu-id="81b0f-104">Input and Output Methods</span></span>

<span data-ttu-id="81b0f-105">主控台 i/o 有兩種不同的方法，其選擇取決於應用程式所需的彈性和控制程度。</span><span class="sxs-lookup"><span data-stu-id="81b0f-105">There are two different approaches to console I/O, the choice of which depends on how much flexibility and control an application needs.</span></span> <span data-ttu-id="81b0f-106">高階方法可啟用簡單的字串流 i/o，但它會限制對主控台的輸入和螢幕緩衝區的存取。</span><span class="sxs-lookup"><span data-stu-id="81b0f-106">The high-level approach enables simple character stream I/O, but it limits access to a console's input and screen buffers.</span></span> <span data-ttu-id="81b0f-107">低層級的方法需要開發人員撰寫更多程式碼，並在更廣泛的函式中進行選擇，但它也能讓應用程式更有彈性。</span><span class="sxs-lookup"><span data-stu-id="81b0f-107">The low-level approach requires that developers write more code and choose among a greater range of functions, but it also gives an application more flexibility.</span></span>

> [!NOTE]
> <span data-ttu-id="81b0f-108">低層級的方法不建議用於新的和進行中的開發。</span><span class="sxs-lookup"><span data-stu-id="81b0f-108">The low-level approach is not recommended for new and ongoing development.</span></span> <span data-ttu-id="81b0f-109">我們鼓勵需要來自低層級主控台 i/o 功能的應用程式使用 **[虛擬終端機序列](console-virtual-terminal-sequences.md)** ，並探索我們的檔，以瞭解 **[傳統功能與虛擬終端](classic-vs-vt.md)** 機和 **[生態系統藍圖](ecosystem-roadmap.md)** 。</span><span class="sxs-lookup"><span data-stu-id="81b0f-109">Applications needing functionality from the low-level console I/O functions are encouraged to use **[virtual terminal sequences](console-virtual-terminal-sequences.md)** and explore our documentation on both **[classic functions versus virtual terminal](classic-vs-vt.md)** and **[the ecosystem roadmap](ecosystem-roadmap.md)** .</span></span>

<span data-ttu-id="81b0f-110">應用程式可以使用檔案 i/o 函式、 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 和 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)，以及主控台函式（ [**ReadConsole**](readconsole.md) 和 [**WriteConsole**](writeconsole.md)），以取得可間接存取主控台的輸入和螢幕緩衝區的高階 i/o 功能。</span><span class="sxs-lookup"><span data-stu-id="81b0f-110">An application can use the file I/O functions, [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747), and the console functions, [**ReadConsole**](readconsole.md) and [**WriteConsole**](writeconsole.md), for high-level I/O that provides indirect access to a console's input and screen buffers.</span></span> <span data-ttu-id="81b0f-111">高階輸入函式會篩選和處理主控台輸入緩衝區中的資料，將輸入以字元資料流的形式傳回，並捨棄滑鼠和緩衝區大小的輸入。</span><span class="sxs-lookup"><span data-stu-id="81b0f-111">The high-level input functions filter and process the data in a console's input buffer to return input as a stream of characters, discarding mouse and buffer-resizing input.</span></span> <span data-ttu-id="81b0f-112">同樣地，高階輸出函式會寫入螢幕緩衝區中目前游標位置所顯示的字元資料流。</span><span class="sxs-lookup"><span data-stu-id="81b0f-112">Similarly, the high-level output functions write a stream of characters that are displayed at the current cursor location in a screen buffer.</span></span> <span data-ttu-id="81b0f-113">應用程式會藉由設定主控台的 i/o 模式來控制這些函式的運作方式。</span><span class="sxs-lookup"><span data-stu-id="81b0f-113">An application controls the way these functions work by setting a console's I/O modes.</span></span>

<span data-ttu-id="81b0f-114">低層級 i/o 函數可讓您直接存取主控台的輸入和螢幕緩衝區，讓應用程式能夠存取滑鼠和緩衝區大小的輸入事件，以及鍵盤事件的延伸資訊。</span><span class="sxs-lookup"><span data-stu-id="81b0f-114">The low-level I/O functions provide direct access to a console's input and screen buffers, enabling an application to access mouse and buffer-resizing input events and extended information for keyboard events.</span></span> <span data-ttu-id="81b0f-115">低層級的輸出函式可讓應用程式讀取或寫入螢幕緩衝區中指定數目的連續字元資料格，或讀取或寫入螢幕緩衝區中指定位置的字元資料格的矩形區塊。</span><span class="sxs-lookup"><span data-stu-id="81b0f-115">Low-level output functions enable an application to read from or write to a specified number of consecutive character cells in a screen buffer, or to read or write to rectangular blocks of character cells at a specified location in a screen buffer.</span></span> <span data-ttu-id="81b0f-116">主控台的輸入模式會影響低層級的輸入，方法是讓應用程式判斷滑鼠和緩衝區調整大小事件是否放置於輸入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="81b0f-116">A console's input modes affect low-level input by enabling the application to determine whether mouse and buffer-resizing events are placed in the input buffer.</span></span> <span data-ttu-id="81b0f-117">主控台的輸出模式不會影響低層級的輸出。</span><span class="sxs-lookup"><span data-stu-id="81b0f-117">A console's output modes have no effect on low-level output.</span></span>

<span data-ttu-id="81b0f-118">高階層級和低層級 i/o 方法不是互斥的，應用程式可以使用這些函式的任何組合。</span><span class="sxs-lookup"><span data-stu-id="81b0f-118">The high-level and low-level I/O methods are not mutually exclusive, and an application can use any combination of these functions.</span></span> <span data-ttu-id="81b0f-119">不過，一般而言，應用程式會使用其中一種方法，而我們建議您將焦點放在一個特定的典範以獲得最佳結果。</span><span class="sxs-lookup"><span data-stu-id="81b0f-119">Typically, however, an application uses one approach or the other exclusively and we recommend focusing on one particular paradigm for optimal results.</span></span>

> [!TIP]
> <span data-ttu-id="81b0f-120">理想的向前尋找應用程式將著重于高階方法，並在必要時，透過高階 i/o 方法來增加 **[虛擬終端機序列](console-virtual-terminal-sequences.md)** 的額外需求，以避免使用低層級的 i/o 功能。</span><span class="sxs-lookup"><span data-stu-id="81b0f-120">The ideal forward looking application will focus on the high-level methods and augment further needs with **[virtual terminal sequences](console-virtual-terminal-sequences.md)** through the high-level I/O methods when necessary avoiding the use of low-level I/O functions entirely.</span></span>

<span data-ttu-id="81b0f-121">下列主題描述主控台模式以及高階和低層級的 i/o 函式。</span><span class="sxs-lookup"><span data-stu-id="81b0f-121">The following topics describe the console modes and the high-level and low-level I/O functions.</span></span>

- [<span data-ttu-id="81b0f-122">主控台模式</span><span class="sxs-lookup"><span data-stu-id="81b0f-122">Console Modes</span></span>](console-modes.md)
- [<span data-ttu-id="81b0f-123">高層級主控台 i/o</span><span class="sxs-lookup"><span data-stu-id="81b0f-123">High-Level Console I/O</span></span>](high-level-console-i-o.md)
- [<span data-ttu-id="81b0f-124">高層級主控台模式</span><span class="sxs-lookup"><span data-stu-id="81b0f-124">High-Level Console Modes</span></span>](high-level-console-modes.md)
- [<span data-ttu-id="81b0f-125">高層級主控台輸入和輸出功能</span><span class="sxs-lookup"><span data-stu-id="81b0f-125">High-Level Console Input and Output Functions</span></span>](high-level-console-input-and-output-functions.md)
- [<span data-ttu-id="81b0f-126">主控台虛擬終端機序列</span><span class="sxs-lookup"><span data-stu-id="81b0f-126">Console Virtual Terminal Sequences</span></span>](console-virtual-terminal-sequences.md)
- [<span data-ttu-id="81b0f-127">傳統函式與虛擬終端機序列</span><span class="sxs-lookup"><span data-stu-id="81b0f-127">Classic Functions versus Virtual Terminal Sequences</span></span>](classic-vs-vt.md)
- [<span data-ttu-id="81b0f-128">生態系統藍圖</span><span class="sxs-lookup"><span data-stu-id="81b0f-128">Ecosystem Roadmap</span></span>](ecosystem-roadmap.md)
- [<span data-ttu-id="81b0f-129">低層級主控台 i/o</span><span class="sxs-lookup"><span data-stu-id="81b0f-129">Low-Level Console I/O</span></span>](low-level-console-i-o.md)
- [<span data-ttu-id="81b0f-130">低層級主控台模式</span><span class="sxs-lookup"><span data-stu-id="81b0f-130">Low-Level Console Modes</span></span>](low-level-console-modes.md)
- [<span data-ttu-id="81b0f-131">低層級主控台輸入函式</span><span class="sxs-lookup"><span data-stu-id="81b0f-131">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)
- [<span data-ttu-id="81b0f-132">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="81b0f-132">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

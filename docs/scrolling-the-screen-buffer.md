---
title: 滾動螢幕緩衝區
description: 描述主控台視窗如何顯示作用中螢幕緩衝區的一部分。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_scrolling\_the\_screen\_buffer'
- base.scrolling\_the\_screen\_buffer
- consoles.scrolling\_the\_screen\_buffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c8404e78-9807-4bed-bc12-25377fa96151
ms.openlocfilehash: 4c55a40f43827deeacfd1302d507732ec9bcc248
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358658"
---
# <a name="scrolling-the-screen-buffer"></a><span data-ttu-id="f542f-104">滾動螢幕緩衝區</span><span class="sxs-lookup"><span data-stu-id="f542f-104">Scrolling the Screen Buffer</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="f542f-105">主控台視窗會顯示作用中螢幕緩衝區的一部分。</span><span class="sxs-lookup"><span data-stu-id="f542f-105">The console window displays a portion of the active screen buffer.</span></span> <span data-ttu-id="f542f-106">每個螢幕緩衝區都會維護它自己的目前視窗矩形，以指定要在主控台視窗中顯示的左上角和右下角字元資料格的座標。</span><span class="sxs-lookup"><span data-stu-id="f542f-106">Each screen buffer maintains its own current window rectangle that specifies the coordinates of the upper left and lower right character cells to be displayed in the console window.</span></span> <span data-ttu-id="f542f-107">若要判斷螢幕緩衝區的目前視窗矩形，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)。</span><span class="sxs-lookup"><span data-stu-id="f542f-107">To determine the current window rectangle of a screen buffer, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span> <span data-ttu-id="f542f-108">建立螢幕緩衝區時，其視窗的左上角位於主控台螢幕緩衝區的左上角，位於 (0，0) 。</span><span class="sxs-lookup"><span data-stu-id="f542f-108">When a screen buffer is created, the upper left corner of its window is at the upper left corner of the console screen buffer at (0,0).</span></span>

<span data-ttu-id="f542f-109">視窗矩形可以變更，以顯示主控台螢幕緩衝區的不同部分。</span><span class="sxs-lookup"><span data-stu-id="f542f-109">The window rectangle can change to display different parts of the console screen buffer.</span></span> <span data-ttu-id="f542f-110">螢幕緩衝區的視窗矩形可能會在下列情況下變更：</span><span class="sxs-lookup"><span data-stu-id="f542f-110">The window rectangle of a screen buffer can change in the following situations:</span></span>

- <span data-ttu-id="f542f-111">當呼叫 [**SetConsoleWindowInfo**](setconsolewindowinfo.md) 來指定新的視窗矩形時，會變更視窗矩形的位置，而不變更視窗的大小，藉此滾動主控台畫面緩衝區的視圖。</span><span class="sxs-lookup"><span data-stu-id="f542f-111">When [**SetConsoleWindowInfo**](setconsolewindowinfo.md) is called to specify a new window rectangle, it scrolls the view of the console screen buffer by changing the position of the window rectangle without changing the size of the window.</span></span> <span data-ttu-id="f542f-112">如需滾動視窗內容的範例，請參閱 [滾動螢幕緩衝區的視窗](scrolling-a-screen-buffer-s-window.md)。</span><span class="sxs-lookup"><span data-stu-id="f542f-112">For examples of scrolling the window's contents, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

  ![螢幕緩衝區視窗移動大型緩衝區內容](images/cscon-01.png)

- <span data-ttu-id="f542f-114">當使用 [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) 函式來寫入換行的螢幕緩衝區時，如果已啟用行尾 (EOL) 輸出模式，則視窗矩形會自動移動，因此一律會顯示游標。</span><span class="sxs-lookup"><span data-stu-id="f542f-114">When using the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) function to write to a screen buffer with wrap at end-of-line (EOL) output mode enabled, the window rectangle shifts automatically, so the cursor is always displayed.</span></span>
- <span data-ttu-id="f542f-115">當 [**SetConsoleCursorPosition**](setconsolecursorposition.md) 函式指定的新資料指標位置超出目前視窗矩形的界限時，視窗矩形會自動移動以顯示游標。</span><span class="sxs-lookup"><span data-stu-id="f542f-115">When the [**SetConsoleCursorPosition**](setconsolecursorposition.md) function specifies a new cursor position that is outside the boundaries of the current window rectangle, the window rectangle shifts automatically to display the cursor.</span></span>
- <span data-ttu-id="f542f-116">當使用者變更控制台視窗的大小，或使用視窗的捲軸時，可以變更現用螢幕緩衝區的視窗矩形。</span><span class="sxs-lookup"><span data-stu-id="f542f-116">When the user changes the size of the console window or uses the window's scroll bars, the window rectangle of the active screen buffer can change.</span></span> <span data-ttu-id="f542f-117">這項變更不會回報為輸入緩衝區中的視窗大小事件。</span><span class="sxs-lookup"><span data-stu-id="f542f-117">This change is not reported as a window resizing event in the input buffer.</span></span>

<span data-ttu-id="f542f-118">在上述每一種情況下，視窗矩形會切換為顯示主控台螢幕緩衝區的不同部分，但是主控台畫面緩衝區的內容會保留在相同的位置。</span><span class="sxs-lookup"><span data-stu-id="f542f-118">In each of these situations, the window rectangle shifts to display a different part of the console screen buffer, but the contents of the console screen buffer remain in the same position.</span></span> <span data-ttu-id="f542f-119">下列情況可能會導致主控台畫面緩衝區的內容轉移：</span><span class="sxs-lookup"><span data-stu-id="f542f-119">The following situations can cause the console screen buffer's contents to shift:</span></span>

- <span data-ttu-id="f542f-120">呼叫 [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 函式時，會從螢幕緩衝區的某個部分將矩形區塊複製到另一個部分。</span><span class="sxs-lookup"><span data-stu-id="f542f-120">When the [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) function is called, a rectangular block is copied from one part of a screen buffer to another.</span></span>
- <span data-ttu-id="f542f-121">當您使用 [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) 寫入到已啟用 wrap 輸出模式的螢幕緩衝區時，主控台畫面緩衝區的內容會在遇到主控台畫面緩衝區的結尾時自動滾動。</span><span class="sxs-lookup"><span data-stu-id="f542f-121">When using [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) to write to a screen buffer with wrap at EOL output mode enabled, the console screen buffer's contents scroll automatically when the end of the console screen buffer is encountered.</span></span> <span data-ttu-id="f542f-122">這項滾動會捨棄主控台畫面緩衝區的頂端列。</span><span class="sxs-lookup"><span data-stu-id="f542f-122">This scrolling discards the top row of the console screen buffer.</span></span>

<span data-ttu-id="f542f-123">[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 指定移動的主控台螢幕緩衝區矩形，以及要複製矩形的新左上座標。</span><span class="sxs-lookup"><span data-stu-id="f542f-123">[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) specifies the console screen buffer rectangle that is moved and the new upper left coordinates to which the rectangle is copied.</span></span> <span data-ttu-id="f542f-124">此函式可將主控台螢幕緩衝區的一部分或整個內容滾動。</span><span class="sxs-lookup"><span data-stu-id="f542f-124">This function can scroll a portion or the entire contents of the console screen buffer.</span></span>

<span data-ttu-id="f542f-125">下圖顯示的 [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 作業，會將主控台畫面緩衝區的整個內容，由數個數據列滾動。</span><span class="sxs-lookup"><span data-stu-id="f542f-125">The illustration shows a [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) operation that scrolls the entire contents of the console screen buffer up by several rows.</span></span> <span data-ttu-id="f542f-126">將會捨棄頂端資料列的內容，並以指定的字元和色彩填滿底部的資料列。</span><span class="sxs-lookup"><span data-stu-id="f542f-126">The contents of the top rows are discarded, and the bottom rows are filled with a specified character and color.</span></span>

![螢幕緩衝區視窗將內容從上方滾動至捨棄](images/cscon-02.png)

<span data-ttu-id="f542f-128">您可以藉由指定選擇性裁剪矩形來限制 [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 的效果，如此一來，裁剪矩形外的主控台螢幕緩衝區內容就不會變更。</span><span class="sxs-lookup"><span data-stu-id="f542f-128">The effects of [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) can be limited by specifying an optional clipping rectangle so that the contents of the console screen buffer outside the clipping rectangle are unchanged.</span></span> <span data-ttu-id="f542f-129">裁剪的效果是建立子視窗 (剪切矩形) 其內容會在不影響主控台螢幕緩衝區其餘部分的情況下滾動。</span><span class="sxs-lookup"><span data-stu-id="f542f-129">The effect of clipping is to create a subwindow (the clipping rectangle) whose contents are scrolled without affecting the rest of the console screen buffer.</span></span> <span data-ttu-id="f542f-130">如需使用 **ScrollConsoleScreenBuffer** 的範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="f542f-130">For an example that uses **ScrollConsoleScreenBuffer**, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>
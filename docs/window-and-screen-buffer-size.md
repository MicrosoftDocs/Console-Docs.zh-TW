---
title: 視窗和螢幕緩衝區大小
description: 螢幕緩衝區的大小是根據字元儲存格以座標方格表示。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_window\_and\_screen\_buffer\_size'
- base.window\_and\_screen\_buffer\_size
- consoles.window\_and\_screen\_buffer\_size
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55246039-31eb-41ca-ad8e-d314cb508644
ms.openlocfilehash: 86a8967eeff35a7a5416273e639ba8bbe5a31ef1
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059534"
---
# <a name="window-and-screen-buffer-size"></a><span data-ttu-id="64f2f-104">視窗和螢幕緩衝區大小</span><span class="sxs-lookup"><span data-stu-id="64f2f-104">Window and Screen Buffer Size</span></span>


<span data-ttu-id="64f2f-105">螢幕緩衝區的大小是根據字元儲存格以座標方格表示。</span><span class="sxs-lookup"><span data-stu-id="64f2f-105">The size of a screen buffer is expressed in terms of a coordinate grid based on character cells.</span></span> <span data-ttu-id="64f2f-106">寬度是每個資料列中的字元資料格數目，而高度是資料列的數目。</span><span class="sxs-lookup"><span data-stu-id="64f2f-106">The width is the number of character cells in each row, and the height is the number of rows.</span></span> <span data-ttu-id="64f2f-107">與每個螢幕緩衝區相關聯的視窗，會決定主控台視窗中顯示的主控台螢幕緩衝區矩形部分的大小和位置。</span><span class="sxs-lookup"><span data-stu-id="64f2f-107">Associated with each screen buffer is a window that determines the size and location of the rectangular portion of the console screen buffer displayed in the console window.</span></span> <span data-ttu-id="64f2f-108">螢幕緩衝區的視窗是藉由指定視窗矩形左上角和右下角儲存格的字元儲存格座標來定義。</span><span class="sxs-lookup"><span data-stu-id="64f2f-108">A screen buffer's window is defined by specifying the character-cell coordinates of the upper left and lower right cells of the window's rectangle.</span></span>

<span data-ttu-id="64f2f-109">螢幕緩衝區可以是任何大小，只受限於可用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="64f2f-109">A screen buffer can be any size, limited only by available memory.</span></span> <span data-ttu-id="64f2f-110">螢幕緩衝區視窗的大小不能超過主控台螢幕緩衝區的對應維度或可在螢幕上容納的最大視窗大小（根據目前的字型大小 (由使用者) 獨佔控制）。</span><span class="sxs-lookup"><span data-stu-id="64f2f-110">The dimensions of a screen buffer's window cannot exceed the corresponding dimensions of either the console screen buffer or the maximum window that can fit on the screen based on the current font size (controlled exclusively by the user).</span></span>

<span data-ttu-id="64f2f-111">[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)函式會傳回關於螢幕緩衝區和其視窗的下列資訊：</span><span class="sxs-lookup"><span data-stu-id="64f2f-111">The [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function returns the following information about a screen buffer and its window:</span></span>

- <span data-ttu-id="64f2f-112">目前的主控台螢幕緩衝區大小</span><span class="sxs-lookup"><span data-stu-id="64f2f-112">The current size of the console screen buffer</span></span>
- <span data-ttu-id="64f2f-113">視窗的目前位置</span><span class="sxs-lookup"><span data-stu-id="64f2f-113">The current location of the window</span></span>
- <span data-ttu-id="64f2f-114">指定目前螢幕緩衝區大小、目前的字型大小和螢幕大小的視窗大小上限</span><span class="sxs-lookup"><span data-stu-id="64f2f-114">The maximum size of the window given the current screen buffer size, the current font size, and the screen size</span></span>

<span data-ttu-id="64f2f-115">[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)函式會根據目前的字型和螢幕大小，傳回主控台視窗的大小上限。</span><span class="sxs-lookup"><span data-stu-id="64f2f-115">The [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) function returns the maximum size of a console's window based on the current font and screen sizes.</span></span> <span data-ttu-id="64f2f-116">這個大小與 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 所傳回的最大視窗大小不同，因為會忽略主控台螢幕緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="64f2f-116">This size differs from the maximum window size returned by [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) in that the console screen buffer size is ignored.</span></span>

<span data-ttu-id="64f2f-117">若要變更螢幕緩衝區大小，請使用 [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="64f2f-117">To change a screen buffer's size, use the [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) function.</span></span> <span data-ttu-id="64f2f-118">如果指定大小的任一維度小於主控台視窗的對應維度，則此函式會失敗。</span><span class="sxs-lookup"><span data-stu-id="64f2f-118">This function fails if either dimension of the specified size is less than the corresponding dimension of the console's window.</span></span>

<span data-ttu-id="64f2f-119">若要變更螢幕緩衝區視窗的大小或位置，請使用 [**SetConsoleWindowInfo**](setconsolewindowinfo.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="64f2f-119">To change the size or location of a screen buffer's window, use the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function.</span></span> <span data-ttu-id="64f2f-120">如果指定的視窗邊角座標超過主控台螢幕緩衝區或畫面的限制，則此函式會失敗。</span><span class="sxs-lookup"><span data-stu-id="64f2f-120">This function fails if the specified window-corner coordinates exceed the limits of the console screen buffer or the screen.</span></span> <span data-ttu-id="64f2f-121">變更作用中螢幕緩衝區的視窗大小，會變更顯示在畫面上的主控台視窗大小。</span><span class="sxs-lookup"><span data-stu-id="64f2f-121">Changing the window size of the active screen buffer changes the size of the console window displayed on the screen.</span></span>

<span data-ttu-id="64f2f-122">進程可以變更其主控台的輸入模式，以啟用視窗輸入，讓程式能夠在使用者變更控制台螢幕緩衝區大小時接收輸入。</span><span class="sxs-lookup"><span data-stu-id="64f2f-122">A process can change its console's input mode to enable window input so that the process is able to receive input when the user changes the console screen buffer size.</span></span> <span data-ttu-id="64f2f-123">如果應用程式啟用視窗輸入，就可以在啟動時使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 來取得視窗和螢幕緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="64f2f-123">If an application enables window input, it can use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) to retrieve window and screen buffer size at startup.</span></span> <span data-ttu-id="64f2f-124">然後，您可以使用此資訊來決定資料在視窗中的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="64f2f-124">This information can then be used to determine the way data is displayed in the window.</span></span> <span data-ttu-id="64f2f-125">如果使用者變更控制台螢幕緩衝區大小，則應用程式可以藉由變更資料顯示方式來回應。</span><span class="sxs-lookup"><span data-stu-id="64f2f-125">If the user changes the console screen buffer size, the application can respond by changing the way data is displayed.</span></span> <span data-ttu-id="64f2f-126">例如，如果每個資料列的字元數變更，應用程式可以調整文字在行尾換行的方式。</span><span class="sxs-lookup"><span data-stu-id="64f2f-126">For example, an application can adjust the way text wraps at the end of the line if the number of characters per row changes.</span></span> <span data-ttu-id="64f2f-127">如果應用程式未啟用視窗輸入，則必須使用繼承的視窗和螢幕緩衝區大小，或在啟動期間將它們設定為所需的大小，並在結束時還原繼承的大小。</span><span class="sxs-lookup"><span data-stu-id="64f2f-127">If an application does not enable window input, it must either use the inherited window and screen buffer sizes, or set them to the desired size during startup and restore the inherited sizes at exit.</span></span> <span data-ttu-id="64f2f-128">如需有關視窗輸入模式的詳細資訊，請參閱 [低層級主控台模式](low-level-console-modes.md)。</span><span class="sxs-lookup"><span data-stu-id="64f2f-128">For additional information about window input mode, see [Low-Level Console Modes](low-level-console-modes.md).</span></span>

 

 





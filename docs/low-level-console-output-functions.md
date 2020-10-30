---
title: Low-Level 主控台輸出函式
description: 低層級的主控台輸出函式可讓您直接存取螢幕緩衝區的字元儲存格。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_low\_level\_console\_output\_functions'
- base.low\_level\_console\_output\_functions
- consoles.low\_level\_console\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 94185428-e8c7-4926-93ec-867b8c97b4ca
ms.openlocfilehash: 70782c7bdc6d009be97315d3405cd44e4e7aa866
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038556"
---
# <a name="low-level-console-output-functions"></a><span data-ttu-id="e3835-104">Low-Level 主控台輸出函式</span><span class="sxs-lookup"><span data-stu-id="e3835-104">Low-Level Console Output Functions</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e3835-105">低層級的主控台輸出函式可讓您直接存取螢幕緩衝區的字元儲存格。</span><span class="sxs-lookup"><span data-stu-id="e3835-105">The low-level console output functions provide direct access to the character cells of a screen buffer.</span></span> <span data-ttu-id="e3835-106">一組函式會從主控台螢幕緩衝區中的任何位置開始，讀取或寫入連續的儲存格。</span><span class="sxs-lookup"><span data-stu-id="e3835-106">One set of functions reads from or writes to consecutive cells beginning at any location in the console screen buffer.</span></span> <span data-ttu-id="e3835-107">另一組函數會讀取或寫入儲存格的矩形區塊。</span><span class="sxs-lookup"><span data-stu-id="e3835-107">Another set of functions reads from or writes to rectangular blocks of cells.</span></span>

<span data-ttu-id="e3835-108">下列函式會從指定的資料格開始，讀取或寫入螢幕緩衝區中指定數目的連續字元儲存格。</span><span class="sxs-lookup"><span data-stu-id="e3835-108">The following functions read from or write to a specified number of consecutive character cells in a screen buffer, beginning with a specified cell.</span></span>

| <span data-ttu-id="e3835-109">函式</span><span class="sxs-lookup"><span data-stu-id="e3835-109">Function</span></span> | <span data-ttu-id="e3835-110">描述</span><span class="sxs-lookup"><span data-stu-id="e3835-110">Description</span></span> |
|-|-|
| [<span data-ttu-id="e3835-111">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="e3835-111">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md) | <span data-ttu-id="e3835-112">從螢幕緩衝區複製 Unicode 或 ANSI 字元字串。</span><span class="sxs-lookup"><span data-stu-id="e3835-112">Copies a string of Unicode or ANSI characters from a screen buffer.</span></span> |
| [<span data-ttu-id="e3835-113">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="e3835-113">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md) | <span data-ttu-id="e3835-114">將 Unicode 或 ANSI 字元字串寫入螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e3835-114">Writes a string of Unicode or ANSI characters to a screen buffer.</span></span> |
| [<span data-ttu-id="e3835-115">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="e3835-115">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md) | <span data-ttu-id="e3835-116">從螢幕緩衝區複製文字和背景色彩屬性的字串。</span><span class="sxs-lookup"><span data-stu-id="e3835-116">Copies a string of text and background color attributes from a screen buffer.</span></span> |
| [<span data-ttu-id="e3835-117">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="e3835-117">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md) | <span data-ttu-id="e3835-118">將文字和背景色彩屬性的字串寫入螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e3835-118">Writes a string of text and background color attributes to a screen buffer.</span></span> |
| [<span data-ttu-id="e3835-119">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="e3835-119">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md) | <span data-ttu-id="e3835-120">將單一 Unicode 或 ANSI 字元寫入螢幕緩衝區中指定數目的連續儲存格。</span><span class="sxs-lookup"><span data-stu-id="e3835-120">Writes a single Unicode or ANSI character to a specified number of consecutive cells in a screen buffer.</span></span> |
| [<span data-ttu-id="e3835-121">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="e3835-121">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md) | <span data-ttu-id="e3835-122">將文字和背景色彩屬性組合寫入螢幕緩衝區中指定數目的連續儲存格。</span><span class="sxs-lookup"><span data-stu-id="e3835-122">Writes a text and background color attribute combination to a specified number of consecutive cells in a screen buffer.</span></span> |

<span data-ttu-id="e3835-123">針對所有這些函式，當遇到資料列的最後一個資料格時，讀取或寫入至下一個資料列的第一個資料格。</span><span class="sxs-lookup"><span data-stu-id="e3835-123">For all of these functions, when the last cell of a row is encountered, reading or writing wraps around to the first cell of the next row.</span></span> <span data-ttu-id="e3835-124">當遇到主控台畫面緩衝區最後一個資料列的結尾時，寫入函式會捨棄所有不成文的字元或屬性，而 read 函數會報告實際寫入的字元數或屬性數目。</span><span class="sxs-lookup"><span data-stu-id="e3835-124">When the end of the last row of the console screen buffer is encountered, the write functions discard all unwritten characters or attributes, and the read functions report the number of characters or attributes actually written.</span></span>

<span data-ttu-id="e3835-125">下列函式會讀取或寫入螢幕緩衝區中指定位置之字元資料格的矩形區塊。</span><span class="sxs-lookup"><span data-stu-id="e3835-125">The following functions read from or write to rectangular blocks of character cells at a specified location in a screen buffer.</span></span>

| <span data-ttu-id="e3835-126">函式</span><span class="sxs-lookup"><span data-stu-id="e3835-126">Function</span></span> | <span data-ttu-id="e3835-127">描述</span><span class="sxs-lookup"><span data-stu-id="e3835-127">Description</span></span> |
|-|-|
| [<span data-ttu-id="e3835-128">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="e3835-128">**ReadConsoleOutput**</span></span>](readconsoleoutput.md) | <span data-ttu-id="e3835-129">將字元和色彩資料從指定的螢幕緩衝區資料格區塊複製到目的緩衝區中的指定區塊。</span><span class="sxs-lookup"><span data-stu-id="e3835-129">Copies character and color data from a specified block of screen buffer cells into a given block in a destination buffer.</span></span> |
| [<span data-ttu-id="e3835-130">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="e3835-130">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md) | <span data-ttu-id="e3835-131">從來源緩衝區中的指定區塊，將字元和色彩資料寫入指定的螢幕緩衝區資料格區塊。</span><span class="sxs-lookup"><span data-stu-id="e3835-131">Writes character and color data to a specified block of screen buffer cells from a given block in a source buffer.</span></span> |

<span data-ttu-id="e3835-132">這些函數會將螢幕緩衝區和來源或目的地緩衝區視為 [**CHAR \_ 資訊**](char-info-str.md) 結構的二維陣列， (包含每個資料格) 的字元和色彩屬性資料。</span><span class="sxs-lookup"><span data-stu-id="e3835-132">These functions treat screen buffers and source or destination buffers as two-dimensional arrays of [**CHAR\_INFO**](char-info-str.md) structures (containing character and color attribute data for each cell).</span></span> <span data-ttu-id="e3835-133">這些函數會指定來源或目的地緩衝區的寬度和高度（以字元資料格為限），而緩衝區的指標會被視為原始資料格的指標， (0，0) 的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="e3835-133">The functions specify the width and height, in character cells, of the source or destination buffer, and the pointer to the buffer is treated as a pointer to the origin cell (0,0) of the two-dimensional array.</span></span> <span data-ttu-id="e3835-134">這些函式會使用 [**小型 \_ RECT**](small-rect-str.md) 結構來指定要在主控台螢幕緩衝區中存取的矩形，以及來源或目的地緩衝區中左上方儲存格的座標，決定該緩衝區中對應矩形的位置。</span><span class="sxs-lookup"><span data-stu-id="e3835-134">The functions use a [**SMALL\_RECT**](small-rect-str.md) structure to specify which rectangle to access in the console screen buffer, and the coordinates of the upper left cell in the source or destination buffer determine the location of the corresponding rectangle in that buffer.</span></span>

<span data-ttu-id="e3835-135">這些函式會自動裁剪指定的螢幕緩衝區矩形，使其符合主控台螢幕緩衝區的界限內。</span><span class="sxs-lookup"><span data-stu-id="e3835-135">These functions automatically clip the specified screen buffer rectangle to fit within the boundaries of the console screen buffer.</span></span> <span data-ttu-id="e3835-136">例如，如果矩形指定的右下座標是 (資料行100、資料列 50) ，而且主控台螢幕緩衝區只是80資料行，則會裁剪座標，使其 (資料行79、資料列 50) 。</span><span class="sxs-lookup"><span data-stu-id="e3835-136">For example, if the rectangle specifies lower right coordinates that are (column 100, row 50) and the console screen buffer is only 80 columns wide, the coordinates are clipped so that they are (column 79, row 50).</span></span> <span data-ttu-id="e3835-137">同樣地，這個調整的矩形會再次裁剪，以符合來源或目的緩衝區的界限。</span><span class="sxs-lookup"><span data-stu-id="e3835-137">Similarly, this adjusted rectangle is again clipped to fit within the boundaries of the source or destination buffer.</span></span> <span data-ttu-id="e3835-138">指定讀取或寫入之實際矩形的螢幕緩衝區座標。</span><span class="sxs-lookup"><span data-stu-id="e3835-138">The screen buffer coordinates of the actual rectangle that was read from or written to are specified.</span></span> <span data-ttu-id="e3835-139">如需使用這些函數的範例，請參閱 [讀取和寫入字元和屬性的區塊](reading-and-writing-blocks-of-characters-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="e3835-139">For an example that uses these functions, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

<span data-ttu-id="e3835-140">下圖顯示在從主控台螢幕緩衝區讀取區塊時，以及當區塊複製到目的緩衝區時，發生裁剪的 [**ReadConsoleOutput**](readconsoleoutput.md) 作業。</span><span class="sxs-lookup"><span data-stu-id="e3835-140">The illustration shows a [**ReadConsoleOutput**](readconsoleoutput.md) operation where clipping occurs when the block is read from the console screen buffer, and again when the block is copied into the destination buffer.</span></span> <span data-ttu-id="e3835-141">函數會報告其複製來源的實際螢幕緩衝區矩形。</span><span class="sxs-lookup"><span data-stu-id="e3835-141">The function reports the actual screen buffer rectangle that it copied from.</span></span>

![具有目的地緩衝區的螢幕緩衝區視窗](images/cscon-03.png)

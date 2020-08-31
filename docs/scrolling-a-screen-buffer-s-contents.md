---
title: 滾動螢幕緩衝區的內容
description: ScrollConsoleScreenBuffer 函式會將字元儲存格的區塊從螢幕緩衝區的某個部分移至相同螢幕緩衝區的另一個部分。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_scrolling\_a\_screen\_buffer\_s\_contents'
- base.scrolling\_a\_screen\_buffer\_s\_contents
- consoles.scrolling\_a\_screen\_buffer\_s\_contents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 288c6a0f-fbaa-4eee-895e-a25884b7b70a
ms.openlocfilehash: a25e9ad7a27977e6dbfcf58de2cf7a250ffd6c4d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059446"
---
# <a name="scrolling-a-screen-buffers-contents"></a><span data-ttu-id="2a03c-104">滾動螢幕緩衝區的內容</span><span class="sxs-lookup"><span data-stu-id="2a03c-104">Scrolling a Screen Buffer's Contents</span></span>


<span data-ttu-id="2a03c-105">[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)函式會將字元儲存格的區塊從螢幕緩衝區的某個部分移至相同螢幕緩衝區的另一個部分。</span><span class="sxs-lookup"><span data-stu-id="2a03c-105">The [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) function moves a block of character cells from one part of a screen buffer to another part of the same screen buffer.</span></span> <span data-ttu-id="2a03c-106">函式會指定要移動之來源矩形的左上角和右下角儲存格，以及左上角儲存格之新位置的目的地座標。</span><span class="sxs-lookup"><span data-stu-id="2a03c-106">The function specifies the upper left and lower right cells of the source rectangle to be moved and the destination coordinates of the new location for the upper left cell.</span></span> <span data-ttu-id="2a03c-107">來源資料格中的字元和色彩資料會移至新的位置，並以指定的字元和色彩填入移動空白的任何資料格。</span><span class="sxs-lookup"><span data-stu-id="2a03c-107">The character and color data in the source cells is moved to the new location, and any cells left empty by the move are filled in with a specified character and color.</span></span> <span data-ttu-id="2a03c-108">如果指定裁剪矩形，則會將它以外的儲存格保持不變。</span><span class="sxs-lookup"><span data-stu-id="2a03c-108">If a clipping rectangle is specified, the cells outside of it are left unchanged.</span></span>

<span data-ttu-id="2a03c-109">[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 可以用來刪除線條，方法是指定線條中第一個資料格的座標做為目的地座標，並指定包含該行下方所有資料列的滾動矩形。</span><span class="sxs-lookup"><span data-stu-id="2a03c-109">[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) can be used to delete a line by specifying coordinates of the first cell in the line as the destination coordinates and specifying a scrolling rectangle that includes all the rows below the line.</span></span>

<span data-ttu-id="2a03c-110">下列範例示範如何使用裁剪矩形，只滾動主控台螢幕緩衝區的下15個數據列。</span><span class="sxs-lookup"><span data-stu-id="2a03c-110">The following example shows the use of a clipping rectangle to scroll only the bottom 15 rows of the console screen buffer.</span></span> <span data-ttu-id="2a03c-111">指定之矩形中的資料列會一次向上滾動一行，而且會捨棄區塊的頂端資料列。</span><span class="sxs-lookup"><span data-stu-id="2a03c-111">The rows in the specified rectangle are scrolled up one line at a time, and the top row of the block is discarded.</span></span> <span data-ttu-id="2a03c-112">裁剪矩形外的主控台螢幕緩衝區內容會保持不變。</span><span class="sxs-lookup"><span data-stu-id="2a03c-112">The contents of the console screen buffer outside the clipping rectangle are left unchanged.</span></span>

```C
#include <windows.h>
#include <stdio.h>

int main( void )
{
    HANDLE hStdout; 
    CONSOLE_SCREEN_BUFFER_INFO csbiInfo; 
    SMALL_RECT srctScrollRect, srctClipRect; 
    CHAR_INFO chiFill; 
    COORD coordDest; 
    int i;

    printf("\nPrinting 20 lines for reference. ");
    printf("Notice that line 6 is discarded during scrolling.\n");
    for(i=0; i<=20; i++)
        printf("%d\n", i);
 
    hStdout = GetStdHandle(STD_OUTPUT_HANDLE); 

    if (hStdout == INVALID_HANDLE_VALUE) 
    {
        printf("GetStdHandle failed with %d\n", GetLastError()); 
        return 1;
    }
 
    // Get the screen buffer size. 
 
    if (!GetConsoleScreenBufferInfo(hStdout, &csbiInfo)) 
    {
        printf("GetConsoleScreenBufferInfo failed %d\n", GetLastError()); 
        return 1;
    }
 
    // The scrolling rectangle is the bottom 15 rows of the 
    // screen buffer. 
 
    srctScrollRect.Top = csbiInfo.dwSize.Y - 16; 
    srctScrollRect.Bottom = csbiInfo.dwSize.Y - 1; 
    srctScrollRect.Left = 0; 
    srctScrollRect.Right = csbiInfo.dwSize.X - 1; 
 
    // The destination for the scroll rectangle is one row up. 
 
    coordDest.X = 0; 
    coordDest.Y = csbiInfo.dwSize.Y - 17; 
 
    // The clipping rectangle is the same as the scrolling rectangle. 
    // The destination row is left unchanged. 
 
    srctClipRect = srctScrollRect; 
 
    // Fill the bottom row with green blanks. 
 
    chiFill.Attributes = BACKGROUND_GREEN | FOREGROUND_RED; 
    chiFill.Char.AsciiChar = (char)' '; 
 
    // Scroll up one line. 
 
    if(!ScrollConsoleScreenBuffer(  
        hStdout,         // screen buffer handle 
        &srctScrollRect, // scrolling rectangle 
        &srctClipRect,   // clipping rectangle 
        coordDest,       // top left destination cell 
        &chiFill))       // fill character and color
    {
        printf("ScrollConsoleScreenBuffer failed %d\n", GetLastError()); 
        return 1;
    }
return 0;
}
```

## <a name="span-idrelated_topicsspanrelated-topics"></a><span data-ttu-id="2a03c-113"><span id="related_topics"></span>相關主題</span><span class="sxs-lookup"><span data-stu-id="2a03c-113"><span id="related_topics"></span>Related topics</span></span>


[<span data-ttu-id="2a03c-114">滾動螢幕緩衝區視窗</span><span class="sxs-lookup"><span data-stu-id="2a03c-114">Scrolling a Screen Buffer's Window</span></span>](scrolling-a-screen-buffer-s-window.md)

[<span data-ttu-id="2a03c-115">滾動螢幕緩衝區</span><span class="sxs-lookup"><span data-stu-id="2a03c-115">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

 

 





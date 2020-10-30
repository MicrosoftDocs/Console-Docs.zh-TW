---
title: 捲動畫面緩衝區的內容
description: ScrollConsoleScreenBuffer 函式會將字元儲存格的區塊從螢幕緩衝區的某個部分移至相同螢幕緩衝區的另一個部分。
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_scrolling\_a\_screen\_buffer\_s\_contents'
- base.scrolling\_a\_screen\_buffer\_s\_contents
- consoles.scrolling\_a\_screen\_buffer\_s\_contents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 288c6a0f-fbaa-4eee-895e-a25884b7b70a
ms.openlocfilehash: 835176680cc0408dc6c4e0331f4668da2e7f07e1
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037576"
---
# <a name="scrolling-a-screen-buffers-contents"></a>捲動畫面緩衝區的內容

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)函式會將字元儲存格的區塊從螢幕緩衝區的某個部分移至相同螢幕緩衝區的另一個部分。 函式會指定要移動之來源矩形的左上角和右下角儲存格，以及左上角儲存格之新位置的目的地座標。 來源資料格中的字元和色彩資料會移至新的位置，並以指定的字元和色彩填入移動空白的任何資料格。 如果指定裁剪矩形，則會將它以外的儲存格保持不變。

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 可以用來刪除線條，方法是指定線條中第一個資料格的座標做為目的地座標，並指定包含該行下方所有資料列的滾動矩形。

下列範例示範如何使用裁剪矩形，只滾動主控台螢幕緩衝區的下15個數據列。 指定之矩形中的資料列會一次向上滾動一行，而且會捨棄區塊的頂端資料列。 裁剪矩形外的主控台螢幕緩衝區內容會保持不變。

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

## <a name="related-topics"></a>相關主題

[捲動畫面緩衝區的視窗](scrolling-a-screen-buffer-s-window.md)

[滾動螢幕緩衝區](scrolling-the-screen-buffer.md)

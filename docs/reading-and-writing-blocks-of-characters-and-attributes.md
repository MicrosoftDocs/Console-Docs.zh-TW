---
title: 讀取和寫入字元和屬性的區塊
description: ReadConsoleOutput 函式會從主控台畫面緩衝區將字元和色彩屬性資料的矩形區塊複製到目的緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_reading\_and\_writing\_blocks\_of\_characters\_and\_attributes'
- base.reading\_and\_writing\_blocks\_of\_characters\_and\_attributes
- consoles.reading\_and\_writing\_blocks\_of\_characters\_and\_attributes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: eaa57723-f003-4e90-8156-be8c3b42b912
ms.openlocfilehash: 17c50e3cc0d519e087cdb8bb40e04db43cfea36f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039466"
---
# <a name="reading-and-writing-blocks-of-characters-and-attributes"></a><span data-ttu-id="98055-104">讀取和寫入字元和屬性的區塊</span><span class="sxs-lookup"><span data-stu-id="98055-104">Reading and Writing Blocks of Characters and Attributes</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="98055-105">[**ReadConsoleOutput**](readconsoleoutput.md)函式會從主控台畫面緩衝區將字元和色彩屬性資料的矩形區塊複製到目的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="98055-105">The [**ReadConsoleOutput**](readconsoleoutput.md) function copies a rectangular block of character and color attribute data from a console screen buffer into a destination buffer.</span></span> <span data-ttu-id="98055-106">函數會將目的緩衝區視為 [**CHAR \_ 資訊**](char-info-str.md) 結構的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="98055-106">The function treats the destination buffer as a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures.</span></span> <span data-ttu-id="98055-107">同樣地， [**WriteConsoleOutput**](writeconsoleoutput.md) 函式會從來源緩衝區將字元和色彩屬性資料的矩形區塊複製到主控台螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="98055-107">Similarly, the [**WriteConsoleOutput**](writeconsoleoutput.md) function copies a rectangular block of character and color attribute data from a source buffer to a console screen buffer.</span></span> <span data-ttu-id="98055-108">如需讀取或寫入螢幕緩衝區儲存格之矩形區塊的詳細資訊，請參閱 [輸入和輸出方法](input-and-output-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="98055-108">For more information about reading from or writing to rectangular blocks of screen buffer cells, see [Input and Output Methods](input-and-output-methods.md).</span></span>

<span data-ttu-id="98055-109">下列範例會使用 [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) 函數來建立新的螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="98055-109">The following example uses the [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) function to create a new screen buffer.</span></span> <span data-ttu-id="98055-110">在 [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) 函式使其成為作用中螢幕緩衝區之後，會將字元和色彩屬性區塊從 STDOUT 螢幕緩衝區的前兩個數據列複製到暫存緩衝區。</span><span class="sxs-lookup"><span data-stu-id="98055-110">After the [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) function makes this the active screen buffer, a block of characters and color attributes is copied from the top two rows of the STDOUT screen buffer into a temporary buffer.</span></span> <span data-ttu-id="98055-111">然後，資料會從暫存緩衝區複製到新的使用中螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="98055-111">The data is then copied from the temporary buffer into the new active screen buffer.</span></span> <span data-ttu-id="98055-112">當應用程式使用新的螢幕緩衝區完成時，它會呼叫 **SetConsoleActiveScreenBuffer** 來還原原始 STDOUT 螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="98055-112">When the application is finished using the new screen buffer, it calls **SetConsoleActiveScreenBuffer** to restore the original STDOUT screen buffer.</span></span>

```C
#include <windows.h>
#include <stdio.h>

int main(void)
{
    HANDLE hStdout, hNewScreenBuffer;
    SMALL_RECT srctReadRect;
    SMALL_RECT srctWriteRect;
    CHAR_INFO chiBuffer[160]; // [2][80];
    COORD coordBufSize;
    COORD coordBufCoord;
    BOOL fSuccess;

    // Get a handle to the STDOUT screen buffer to copy from and
    // create a new screen buffer to copy to.

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);
    hNewScreenBuffer = CreateConsoleScreenBuffer(
       GENERIC_READ |           // read/write access
       GENERIC_WRITE,
       FILE_SHARE_READ |
       FILE_SHARE_WRITE,        // shared
       NULL,                    // default security attributes
       CONSOLE_TEXTMODE_BUFFER, // must be TEXTMODE
       NULL);                   // reserved; must be NULL
    if (hStdout == INVALID_HANDLE_VALUE ||
            hNewScreenBuffer == INVALID_HANDLE_VALUE)
    {
        printf("CreateConsoleScreenBuffer failed - (%d)\n", GetLastError());
        return 1;
    }

    // Make the new screen buffer the active screen buffer.

    if (! SetConsoleActiveScreenBuffer(hNewScreenBuffer) )
    {
        printf("SetConsoleActiveScreenBuffer failed - (%d)\n", GetLastError());
        return 1;
    }

    // Set the source rectangle.

    srctReadRect.Top = 0;    // top left: row 0, col 0
    srctReadRect.Left = 0;
    srctReadRect.Bottom = 1; // bot. right: row 1, col 79
    srctReadRect.Right = 79;

    // The temporary buffer size is 2 rows x 80 columns.

    coordBufSize.Y = 2;
    coordBufSize.X = 80;

    // The top left destination cell of the temporary buffer is
    // row 0, col 0.

    coordBufCoord.X = 0;
    coordBufCoord.Y = 0;

    // Copy the block from the screen buffer to the temp. buffer.

    fSuccess = ReadConsoleOutput(
       hStdout,        // screen buffer to read from
       chiBuffer,      // buffer to copy into
       coordBufSize,   // col-row size of chiBuffer
       coordBufCoord,  // top left dest. cell in chiBuffer
       &srctReadRect); // screen buffer source rectangle
    if (! fSuccess)
    {
        printf("ReadConsoleOutput failed - (%d)\n", GetLastError());
        return 1;
    }

    // Set the destination rectangle.

    srctWriteRect.Top = 10;    // top lt: row 10, col 0
    srctWriteRect.Left = 0;
    srctWriteRect.Bottom = 11; // bot. rt: row 11, col 79
    srctWriteRect.Right = 79;

    // Copy from the temporary buffer to the new screen buffer.

    fSuccess = WriteConsoleOutput(
        hNewScreenBuffer, // screen buffer to write to
        chiBuffer,        // buffer to copy from
        coordBufSize,     // col-row size of chiBuffer
        coordBufCoord,    // top left src cell in chiBuffer
        &srctWriteRect);  // dest. screen buffer rectangle
    if (! fSuccess)
    {
        printf("WriteConsoleOutput failed - (%d)\n", GetLastError());
        return 1;
    }
    Sleep(5000);

    // Restore the original active screen buffer.

    if (! SetConsoleActiveScreenBuffer(hStdout))
    {
        printf("SetConsoleActiveScreenBuffer failed - (%d)\n", GetLastError());
        return 1;
    }

    return 0;
}
```

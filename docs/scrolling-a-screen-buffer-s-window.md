---
title: 捲動畫面緩衝區的視窗
description: SetConsoleWindowInfo 函式可在主控台視窗中用來將螢幕緩衝區的內容滾動。
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_scrolling\_a\_screen\_buffer\_s\_window'
- base.scrolling\_a\_screen\_buffer\_s\_window
- consoles.scrolling\_a\_screen\_buffer\_s\_window
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bc300349-9bfa-4417-92ad-57a05a658ce5
ms.openlocfilehash: 332edf04a2f6f4ebaa9b482d2dc3f15381190855
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039426"
---
# <a name="scrolling-a-screen-buffers-window"></a><span data-ttu-id="7eeed-104">捲動畫面緩衝區的視窗</span><span class="sxs-lookup"><span data-stu-id="7eeed-104">Scrolling a Screen Buffer's Window</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="7eeed-105">[**SetConsoleWindowInfo**](setconsolewindowinfo.md)函式可在主控台視窗中用來將螢幕緩衝區的內容滾動。</span><span class="sxs-lookup"><span data-stu-id="7eeed-105">The [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function can be used to scroll the contents of a screen buffer in the console window.</span></span> <span data-ttu-id="7eeed-106">此函數也可以變更視窗大小。</span><span class="sxs-lookup"><span data-stu-id="7eeed-106">This function can also change the window size.</span></span> <span data-ttu-id="7eeed-107">函式可以將主控台螢幕緩衝區視窗的新左上角和右下角指定為絕對螢幕緩衝區座標，或指定目前視窗座標的變更。</span><span class="sxs-lookup"><span data-stu-id="7eeed-107">The function can either specify the new upper left and lower right corners of the console screen buffer's window as absolute screen buffer coordinates or specify the changes from the current window coordinates.</span></span> <span data-ttu-id="7eeed-108">如果指定的視窗座標超出主控台螢幕緩衝區的界限，則函式會失敗。</span><span class="sxs-lookup"><span data-stu-id="7eeed-108">The function fails if the specified window coordinates are outside the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="7eeed-109">下列範例會藉由修改 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函式所傳回的視窗座標，來將主控台螢幕緩衝區的視圖向上滾動。</span><span class="sxs-lookup"><span data-stu-id="7eeed-109">The following example scrolls the view of the console screen buffer up by modifying the window coordinates returned by the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span> <span data-ttu-id="7eeed-110">`ScrollByAbsoluteCoord`函數會示範如何指定絕對座標，而函式會 `ScrollByRelativeCoord` 示範如何指定相對座標。</span><span class="sxs-lookup"><span data-stu-id="7eeed-110">The `ScrollByAbsoluteCoord` function demonstrates how to specify absolute coordinates, while the `ScrollByRelativeCoord` function demonstrates how to specify relative coordinates.</span></span>

```C
#include <windows.h>
#include <stdio.h>
#include <conio.h>

HANDLE hStdout;

int ScrollByAbsoluteCoord(int iRows)
{
    CONSOLE_SCREEN_BUFFER_INFO csbiInfo;
    SMALL_RECT srctWindow;

    // Get the current screen buffer size and window position.

    if (! GetConsoleScreenBufferInfo(hStdout, &csbiInfo))
    {
        printf("GetConsoleScreenBufferInfo (%d)\n", GetLastError());
        return 0;
    }

    // Set srctWindow to the current window size and location.

    srctWindow = csbiInfo.srWindow;

    // Check whether the window is too close to the screen buffer top

    if ( srctWindow.Top >= iRows )
    {
        srctWindow.Top -= (SHORT)iRows;     // move top up
        srctWindow.Bottom -= (SHORT)iRows;  // move bottom up

        if (! SetConsoleWindowInfo(
                   hStdout,          // screen buffer handle
                   TRUE,             // absolute coordinates
                   &srctWindow))     // specifies new location
        {
            printf("SetConsoleWindowInfo (%d)\n", GetLastError());
            return 0;
        }
        return iRows;
    }
    else
    {
        printf("\nCannot scroll; the window is too close to the top.\n");
        return 0;
    }
}

int ScrollByRelativeCoord(int iRows)
{
    CONSOLE_SCREEN_BUFFER_INFO csbiInfo;
    SMALL_RECT srctWindow;

    // Get the current screen buffer window position.

    if (! GetConsoleScreenBufferInfo(hStdout, &csbiInfo))
    {
        printf("GetConsoleScreenBufferInfo (%d)\n", GetLastError());
        return 0;
    }

    // Check whether the window is too close to the screen buffer top

    if (csbiInfo.srWindow.Top >= iRows)
    {
        srctWindow.Top =- (SHORT)iRows;     // move top up
        srctWindow.Bottom =- (SHORT)iRows;  // move bottom up
        srctWindow.Left = 0;         // no change
        srctWindow.Right = 0;        // no change

        if (! SetConsoleWindowInfo(
                   hStdout,          // screen buffer handle
                   FALSE,            // relative coordinates
                   &srctWindow))     // specifies new location
        {
            printf("SetConsoleWindowInfo (%d)\n", GetLastError());
            return 0;
        }
        return iRows;
    }
    else
    {
        printf("\nCannot scroll; the window is too close to the top.\n");
        return 0;
    }
}

int main( void )
{
    int i;

    printf("\nPrinting twenty lines, then scrolling up five lines.\n");
    printf("Press any key to scroll up ten lines; ");
    printf("then press another key to stop the demo.\n");
    for(i=0; i<=20; i++)
        printf("%d\n", i);

    hStdout = GetStdHandle(STD_OUTPUT_HANDLE);

    if(ScrollByAbsoluteCoord(5))
        _getch();
    else return 0;

    if(ScrollByRelativeCoord(10))
        _getch();
    else return 0;
}
```

## <a name="related-topics"></a><span data-ttu-id="7eeed-111">相關主題</span><span class="sxs-lookup"><span data-stu-id="7eeed-111">Related topics</span></span>

[<span data-ttu-id="7eeed-112">捲動畫面緩衝區的內容</span><span class="sxs-lookup"><span data-stu-id="7eeed-112">Scrolling a Screen Buffer's Contents</span></span>](scrolling-a-screen-buffer-s-contents.md)

[<span data-ttu-id="7eeed-113">滾動螢幕緩衝區</span><span class="sxs-lookup"><span data-stu-id="7eeed-113">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

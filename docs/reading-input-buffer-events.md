---
title: 讀取輸入緩衝區事件
description: ReadConsoleInput 函數可以用來直接存取主控台的輸入緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_reading\_input\_buffer\_events'
- base.reading\_input\_buffer\_events
- consoles.reading\_input\_buffer\_events
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 57570f3b-4a37-4789-bf6c-474fae60171d
ms.openlocfilehash: 2604add28fa89fa5650d2802069e3e0559272e11
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059447"
---
# <a name="reading-input-buffer-events"></a><span data-ttu-id="67880-104">讀取輸入緩衝區事件</span><span class="sxs-lookup"><span data-stu-id="67880-104">Reading Input Buffer Events</span></span>


<span data-ttu-id="67880-105">[**ReadConsoleInput**](readconsoleinput.md)函數可以用來直接存取主控台的輸入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="67880-105">The [**ReadConsoleInput**](readconsoleinput.md) function can be used to directly access a console's input buffer.</span></span> <span data-ttu-id="67880-106">建立主控台時，會啟用滑鼠輸入並停用視窗輸入。</span><span class="sxs-lookup"><span data-stu-id="67880-106">When a console is created, mouse input is enabled and window input is disabled.</span></span> <span data-ttu-id="67880-107">為了確保進程會接收所有類型的事件，此範例會使用 [**SetConsoleMode**](setconsolemode.md) 函式來啟用視窗和滑鼠輸入。</span><span class="sxs-lookup"><span data-stu-id="67880-107">To ensure that the process receives all types of events, this example uses the [**SetConsoleMode**](setconsolemode.md) function to enable window and mouse input.</span></span> <span data-ttu-id="67880-108">然後，它會進入一個可讀取和處理100主控台輸入事件的迴圈。</span><span class="sxs-lookup"><span data-stu-id="67880-108">Then it goes into a loop that reads and handles 100 console input events.</span></span> <span data-ttu-id="67880-109">例如，當使用者按下按鍵時，即會顯示「鍵盤事件」訊息，並在使用者與滑鼠互動時顯示「滑鼠事件」訊息。</span><span class="sxs-lookup"><span data-stu-id="67880-109">For example, the message "Keyboard event" is displayed when the user presses a key and the message "Mouse event" is displayed when the user interacts with the mouse.</span></span>

```C
#include <windows.h>
#include <stdio.h>

HANDLE hStdin; 
DWORD fdwSaveOldMode;

VOID ErrorExit(LPSTR);
VOID KeyEventProc(KEY_EVENT_RECORD); 
VOID MouseEventProc(MOUSE_EVENT_RECORD); 
VOID ResizeEventProc(WINDOW_BUFFER_SIZE_RECORD); 
 
int main(VOID) 
{ 
    DWORD cNumRead, fdwMode, i; 
    INPUT_RECORD irInBuf[128]; 
    int counter=0;
 
    // Get the standard input handle. 
 
    hStdin = GetStdHandle(STD_INPUT_HANDLE); 
    if (hStdin == INVALID_HANDLE_VALUE) 
        ErrorExit("GetStdHandle"); 
 
    // Save the current input mode, to be restored on exit. 
 
    if (! GetConsoleMode(hStdin, &fdwSaveOldMode) ) 
        ErrorExit("GetConsoleMode"); 

    // Enable the window and mouse input events. 
 
    fdwMode = ENABLE_WINDOW_INPUT | ENABLE_MOUSE_INPUT; 
    if (! SetConsoleMode(hStdin, fdwMode) ) 
        ErrorExit("SetConsoleMode"); 
 
    // Loop to read and handle the next 100 input events. 
 
    while (counter++ <= 100) 
    { 
        // Wait for the events. 
 
        if (! ReadConsoleInput( 
                hStdin,      // input buffer handle 
                irInBuf,     // buffer to read into 
                128,         // size of read buffer 
                &cNumRead) ) // number of records read 
            ErrorExit("ReadConsoleInput"); 
 
        // Dispatch the events to the appropriate handler. 
 
        for (i = 0; i < cNumRead; i++) 
        {
            switch(irInBuf[i].EventType) 
            { 
                case KEY_EVENT: // keyboard input 
                    KeyEventProc(irInBuf[i].Event.KeyEvent); 
                    break; 
 
                case MOUSE_EVENT: // mouse input 
                    MouseEventProc(irInBuf[i].Event.MouseEvent); 
                    break; 
 
                case WINDOW_BUFFER_SIZE_EVENT: // scrn buf. resizing 
                    ResizeEventProc( irInBuf[i].Event.WindowBufferSizeEvent ); 
                    break; 
 
                case FOCUS_EVENT:  // disregard focus events 
 
                case MENU_EVENT:   // disregard menu events 
                    break; 
 
                default: 
                    ErrorExit("Unknown event type"); 
                    break; 
            } 
        }
    } 

    // Restore input mode on exit.

    SetConsoleMode(hStdin, fdwSaveOldMode);
 
    return 0; 
}

VOID ErrorExit (LPSTR lpszMessage) 
{ 
    fprintf(stderr, "%s\n", lpszMessage); 

    // Restore input mode on exit.

    SetConsoleMode(hStdin, fdwSaveOldMode);

    ExitProcess(0); 
}

VOID KeyEventProc(KEY_EVENT_RECORD ker)
{
    printf("Key event: ");

    if(ker.bKeyDown)
        printf("key pressed\n");
    else printf("key released\n");
}

VOID MouseEventProc(MOUSE_EVENT_RECORD mer)
{
#ifndef MOUSE_HWHEELED
#define MOUSE_HWHEELED 0x0008
#endif
    printf("Mouse event: ");
    
    switch(mer.dwEventFlags)
    {
        case 0:

            if(mer.dwButtonState == FROM_LEFT_1ST_BUTTON_PRESSED)
            {
                printf("left button press \n");
            }
            else if(mer.dwButtonState == RIGHTMOST_BUTTON_PRESSED)
            {
                printf("right button press \n");
            }
            else
            {
                printf("button press\n");
            }
            break;
        case DOUBLE_CLICK:
            printf("double click\n");
            break;
        case MOUSE_HWHEELED:
            printf("horizontal mouse wheel\n");
            break;
        case MOUSE_MOVED:
            printf("mouse moved\n");
            break;
        case MOUSE_WHEELED:
            printf("vertical mouse wheel\n");
            break;
        default:
            printf("unknown\n");
            break;
    }
}

VOID ResizeEventProc(WINDOW_BUFFER_SIZE_RECORD wbsr)
{
    printf("Resize event\n");
    printf("Console screen buffer is %d columns by %d rows.\n", wbsr.dwSize.X, wbsr.dwSize.Y);
}
```

 

 





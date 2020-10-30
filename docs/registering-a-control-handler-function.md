---
title: 註冊控制處理常式函式
description: 這是用來安裝控制項處理常式的 SetConsoleCtrlHandler 函數範例。
author: miniksa
ms.author: miniksa
ms.topic: sample
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_registering\_a\_control\_handler\_function'
- base.registering\_a\_control\_handler\_function
- consoles.registering\_a\_control\_handler\_function
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f1c72277-f06c-4147-a74c-6aaf6feb730e
ms.openlocfilehash: 4142f4f0871bd11a56085324195702ab47301227
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039446"
---
# <a name="registering-a-control-handler-function"></a><span data-ttu-id="47a06-104">註冊控制處理常式函式</span><span class="sxs-lookup"><span data-stu-id="47a06-104">Registering a Control Handler Function</span></span>

<span data-ttu-id="47a06-105">這是用來安裝控制項處理常式的 [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) 函數範例。</span><span class="sxs-lookup"><span data-stu-id="47a06-105">This is an example of the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function that is used to install a control handler.</span></span>

<span data-ttu-id="47a06-106">收到 CTRL + C 信號時，控制處理常式會傳回 **TRUE** ，表示它已處理信號。</span><span class="sxs-lookup"><span data-stu-id="47a06-106">When a CTRL+C signal is received, the control handler returns **TRUE** , indicating that it has handled the signal.</span></span> <span data-ttu-id="47a06-107">這樣做可防止呼叫其他控制處理常式。</span><span class="sxs-lookup"><span data-stu-id="47a06-107">Doing this prevents other control handlers from being called.</span></span>

<span data-ttu-id="47a06-108">當收到 **CTRL \_ CLOSE \_ 事件** 信號時，控制處理常式會傳回 **TRUE** ，而且進程會終止。</span><span class="sxs-lookup"><span data-stu-id="47a06-108">When a **CTRL\_CLOSE\_EVENT** signal is received, the control handler returns **TRUE** and the process terminates.</span></span>

<span data-ttu-id="47a06-109">當您 **收到 ctrl \_ BREAK \_ 事件** 、 **ctrl \_ 登出 \_ 事件** 或 **ctrl \_ SHUTDOWN \_ 事件** 信號時，控制處理常式會傳回 **FALSE** 。</span><span class="sxs-lookup"><span data-stu-id="47a06-109">When a **CTRL\_BREAK\_EVENT** , **CTRL\_LOGOFF\_EVENT** , or **CTRL\_SHUTDOWN\_EVENT** signal is received, the control handler returns **FALSE** .</span></span> <span data-ttu-id="47a06-110">這樣做會導致信號傳遞給下一個控制處理函式。</span><span class="sxs-lookup"><span data-stu-id="47a06-110">Doing this causes the signal to be passed to the next control handler function.</span></span> <span data-ttu-id="47a06-111">如果未註冊其他控制項處理常式，或沒有任何已註冊的處理常式傳回 **TRUE** ，則會使用預設處理常式，而導致進程終止。</span><span class="sxs-lookup"><span data-stu-id="47a06-111">If no other control handlers have been registered or none of the registered handlers returns **TRUE** , the default handler will be used, resulting in the process being terminated.</span></span>

```C
// CtrlHandler.cpp : This file contains the 'main' function. Program execution begins and ends there.
//

#include "pch.h"

#include <windows.h>
#include <stdio.h>

BOOL WINAPI CtrlHandler(DWORD fdwCtrlType)
{
    switch (fdwCtrlType)
    {
        // Handle the CTRL-C signal.
    case CTRL_C_EVENT:
        printf("Ctrl-C event\n\n");
        Beep(750, 300);
        return TRUE;

        // CTRL-CLOSE: confirm that the user wants to exit.
    case CTRL_CLOSE_EVENT:
        Beep(600, 200);
        printf("Ctrl-Close event\n\n");
        return TRUE;

        // Pass other signals to the next handler.
    case CTRL_BREAK_EVENT:
        Beep(900, 200);
        printf("Ctrl-Break event\n\n");
        return FALSE;

    case CTRL_LOGOFF_EVENT:
        Beep(1000, 200);
        printf("Ctrl-Logoff event\n\n");
        return FALSE;

    case CTRL_SHUTDOWN_EVENT:
        Beep(750, 500);
        printf("Ctrl-Shutdown event\n\n");
        return FALSE;

    default:
        return FALSE;
    }
}

int main(void)
{
    if (SetConsoleCtrlHandler(CtrlHandler, TRUE))
    {
        printf("\nThe Control Handler is installed.\n");
        printf("\n -- Now try pressing Ctrl+C or Ctrl+Break, or");
        printf("\n    try logging off or closing the console...\n");
        printf("\n(...waiting in a loop for events...)\n\n");

        while (1) {}
    }
    else
    {
        printf("\nERROR: Could not set control handler");
        return 1;
    }
    return 0;
}
```

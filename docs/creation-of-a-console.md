---
title: 建立主控台
description: 系統會在啟動主控台進程時建立新的主控台，其進入點是主要函式的字元模式進程。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_creation\_of\_a\_console'
- base.creation\_of\_a\_console
- consoles.creation\_of\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ec2559-cade-447e-8594-5b824d3d3e81
ms.openlocfilehash: b3b4143596035fed6896243043853932ae68233f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059218"
---
# <a name="creation-of-a-console"></a><span data-ttu-id="7e07d-104">建立主控台</span><span class="sxs-lookup"><span data-stu-id="7e07d-104">Creation of a Console</span></span>


<span data-ttu-id="7e07d-105">系統會在啟動 *主控台進程*時建立新的主控台，其進入點是 **主要** 函式的字元模式進程。</span><span class="sxs-lookup"><span data-stu-id="7e07d-105">The system creates a new console when it starts a *console process*, a character-mode process whose entry point is the **main** function.</span></span> <span data-ttu-id="7e07d-106">例如，當系統啟動命令處理器時，系統會建立新的主控台。</span><span class="sxs-lookup"><span data-stu-id="7e07d-106">For example, the system creates a new console when it starts the command processor.</span></span> <span data-ttu-id="7e07d-107">當命令處理器啟動新的主控台進程時，使用者可以指定系統是否為新的進程建立新的主控台，或是否要繼承命令處理器的主控台。</span><span class="sxs-lookup"><span data-stu-id="7e07d-107">When the command processor starts a new console process, the user can specify whether the system creates a new console for the new process or whether it inherits the command processor's console.</span></span>

<span data-ttu-id="7e07d-108">處理常式可以使用下列其中一種方法來建立主控台：</span><span class="sxs-lookup"><span data-stu-id="7e07d-108">A process can create a console by using one of the following methods:</span></span>

- <span data-ttu-id="7e07d-109">GUI 或主控台進程可以搭配使用 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 函式與 **建立 \_ 新的 \_ 主控台** ，以使用新的主控台建立主控台進程。</span><span class="sxs-lookup"><span data-stu-id="7e07d-109">A GUI or console process can use the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function with **CREATE\_NEW\_CONSOLE** to create a console process with a new console.</span></span> <span data-ttu-id="7e07d-110"> (根據預設，主控台進程會繼承其父代的主控台，而且不保證會由其預定的進程接收輸入。 ) </span><span class="sxs-lookup"><span data-stu-id="7e07d-110">(By default, a console process inherits its parent's console, and there is no guarantee that input is received by the process for which it was intended.)</span></span>
- <span data-ttu-id="7e07d-111">目前未連接到主控台的圖形化使用者介面 (GUI) 或主控台進程，可以使用 [**AllocConsole**](allocconsole.md) 函式來建立新的主控台。</span><span class="sxs-lookup"><span data-stu-id="7e07d-111">A graphical user interface (GUI) or console process that is not currently attached to a console can use the [**AllocConsole**](allocconsole.md) function to create a new console.</span></span> <span data-ttu-id="7e07d-112"> (GUI 進程在建立時不會附加至主控台。</span><span class="sxs-lookup"><span data-stu-id="7e07d-112">(GUI processes are not attached to a console when they are created.</span></span> <span data-ttu-id="7e07d-113">主控台進程如果是使用具有卸**離 \_ 進程**的[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)來建立，則不會連接到主控台。 ) </span><span class="sxs-lookup"><span data-stu-id="7e07d-113">Console processes are not attached to a console if they are created using [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) with **DETACHED\_PROCESS**.)</span></span>

<span data-ttu-id="7e07d-114">一般來說，當發生需要與使用者互動的錯誤時，進程會使用 [**AllocConsole**](allocconsole.md) 來建立主控台。</span><span class="sxs-lookup"><span data-stu-id="7e07d-114">Typically, a process uses [**AllocConsole**](allocconsole.md) to create a console when an error occurs requiring interaction with the user.</span></span> <span data-ttu-id="7e07d-115">例如，GUI 進程可以在發生錯誤時建立主控台，使其無法使用其一般圖形介面，或者通常不與使用者互動的主控台進程可以建立主控台來顯示錯誤。</span><span class="sxs-lookup"><span data-stu-id="7e07d-115">For example, a GUI process can create a console when an error occurs that prevents it from using its normal graphical interface, or a console process that does not normally interact with the user can create a console to display an error.</span></span>

<span data-ttu-id="7e07d-116">進程也可以在對[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)的呼叫中指定 [**建立 \_ 新的 \_ 主控台**] 旗標，藉以建立主控台。</span><span class="sxs-lookup"><span data-stu-id="7e07d-116">A process can also create a console by specifying the **CREATE\_NEW\_CONSOLE** flag in a call to [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425).</span></span> <span data-ttu-id="7e07d-117">這個方法會建立可供子進程存取的新主控台，而不是父進程。</span><span class="sxs-lookup"><span data-stu-id="7e07d-117">This method creates a new console that is accessible to the child process but not to the parent process.</span></span> <span data-ttu-id="7e07d-118">個別的主控台可讓父系和子進程與使用者互動，而不會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="7e07d-118">Separate consoles enable both parent and child processes to interact with the user without conflict.</span></span> <span data-ttu-id="7e07d-119">如果建立主控台進程時未指定此旗標，則這兩個處理常式會附加到相同的主控台，而且不保證正確的程式會收到所需的輸入。</span><span class="sxs-lookup"><span data-stu-id="7e07d-119">If this flag is not specified when a console process is created, both processes are attached to the same console, and there is no guarantee that the correct process will receive the input intended for it.</span></span> <span data-ttu-id="7e07d-120">應用程式可以藉由建立不繼承輸入緩衝區控制碼的子進程，或一次只啟用一個子進程來繼承輸入緩衝區控制碼，並防止父進程讀取主控台輸入，直到子系完成為止，藉此防止混淆。</span><span class="sxs-lookup"><span data-stu-id="7e07d-120">Applications can prevent confusion by creating child processes that do not inherit handles of the input buffer, or by enabling only one child process at a time to inherit an input buffer handle while preventing the parent process from reading console input until the child has finished.</span></span>

<span data-ttu-id="7e07d-121">建立新的主控台會產生新的主控台視窗，以及個別的 i/o 螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7e07d-121">Creating a new console results in a new console window, as well as separate I/O screen buffers.</span></span> <span data-ttu-id="7e07d-122">與新主控台相關聯的進程會使用 [**GetStdHandle**](getstdhandle.md) 函式來取得新主控台之輸入和螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="7e07d-122">The process associated with the new console uses the [**GetStdHandle**](getstdhandle.md) function to get the handles of the new console's input and screen buffers.</span></span> <span data-ttu-id="7e07d-123">這些控點可讓進程存取主控台。</span><span class="sxs-lookup"><span data-stu-id="7e07d-123">These handles enable the process to access the console.</span></span>

<span data-ttu-id="7e07d-124">當處理常式使用 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)時，它可以指定 [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) 結構，其成員可控制第一個新主控台的特性 (如果為子進程建立的任何) 。</span><span class="sxs-lookup"><span data-stu-id="7e07d-124">When a process uses [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425), it can specify a [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) structure, whose members control the characteristics of the first new console (if any) created for the child process.</span></span> <span data-ttu-id="7e07d-125">如果指定了**建立 \_ 新的 \_ 主控台**旗標，則在對**CreateProcess**的呼叫中指定的**STARTUPINFO**結構會影響主控台所建立的。</span><span class="sxs-lookup"><span data-stu-id="7e07d-125">The **STARTUPINFO** structure specified in the call to **CreateProcess** affects a console created if the **CREATE\_NEW\_CONSOLE** flag is specified.</span></span> <span data-ttu-id="7e07d-126">如果子進程後續使用 [**AllocConsole**](allocconsole.md)，它也會影響建立的主控台。</span><span class="sxs-lookup"><span data-stu-id="7e07d-126">It also affects a console created if the child process subsequently uses [**AllocConsole**](allocconsole.md).</span></span> <span data-ttu-id="7e07d-127">您可以指定下列主控台特性：</span><span class="sxs-lookup"><span data-stu-id="7e07d-127">The following console characteristics can be specified:</span></span>

- <span data-ttu-id="7e07d-128">新主控台視窗的大小（以字元儲存格為限）</span><span class="sxs-lookup"><span data-stu-id="7e07d-128">Size of the new console window, in character cells</span></span>
- <span data-ttu-id="7e07d-129">新主控台視窗的位置，以螢幕圖元座標表示</span><span class="sxs-lookup"><span data-stu-id="7e07d-129">Location of the new console window, in screen pixel coordinates</span></span>
- <span data-ttu-id="7e07d-130">新主控台的螢幕緩衝區大小，以字元儲存格為限</span><span class="sxs-lookup"><span data-stu-id="7e07d-130">Size of the new console's screen buffer, in character cells</span></span>
- <span data-ttu-id="7e07d-131">新主控台螢幕緩衝區的文字和背景色彩屬性</span><span class="sxs-lookup"><span data-stu-id="7e07d-131">Text and background color attributes of the new console's screen buffer</span></span>
- <span data-ttu-id="7e07d-132">新主控台視窗之標題列的顯示名稱</span><span class="sxs-lookup"><span data-stu-id="7e07d-132">Display name for the title bar of the new console's window</span></span>

<span data-ttu-id="7e07d-133">如果未指定 [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) 值，系統會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="7e07d-133">The system uses default values if the [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) values are not specified.</span></span> <span data-ttu-id="7e07d-134">子進程可以使用 [**GetStartupInfo**](https://msdn.microsoft.com/library/windows/desktop/ms683230) 函數來判斷其 **STARTUPINFO** 結構中的值。</span><span class="sxs-lookup"><span data-stu-id="7e07d-134">A child process can use the [**GetStartupInfo**](https://msdn.microsoft.com/library/windows/desktop/ms683230) function to determine the values in its **STARTUPINFO** structure.</span></span>

<span data-ttu-id="7e07d-135">進程無法變更其主控台視窗在螢幕上的位置，但是下列主控台函式可用來設定或抓取 [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) 結構中指定的其他屬性。</span><span class="sxs-lookup"><span data-stu-id="7e07d-135">A process cannot change the location of its console window on the screen, but the following console functions are available to set or retrieve the other properties specified in the [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) structure.</span></span>


| <span data-ttu-id="7e07d-136">函式</span><span class="sxs-lookup"><span data-stu-id="7e07d-136">Function</span></span>                                                         | <span data-ttu-id="7e07d-137">描述</span><span class="sxs-lookup"><span data-stu-id="7e07d-137">Description</span></span>                                                          |
|------------------------------------------------------------------|----------------------------------------------------------------------|
| [<span data-ttu-id="7e07d-138">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="7e07d-138">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md) | <span data-ttu-id="7e07d-139">抓取視窗大小、螢幕緩衝區大小和色彩屬性。</span><span class="sxs-lookup"><span data-stu-id="7e07d-139">Retrieves the window size, screen buffer size, and color attributes.</span></span> |
| [<span data-ttu-id="7e07d-140">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="7e07d-140">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)             | <span data-ttu-id="7e07d-141">變更控制台視窗的大小。</span><span class="sxs-lookup"><span data-stu-id="7e07d-141">Changes the size of the console window.</span></span>                              |
| [<span data-ttu-id="7e07d-142">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="7e07d-142">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md) | <span data-ttu-id="7e07d-143">變更控制台螢幕緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="7e07d-143">Changes the size of the console screen buffer.</span></span>                       |
| [<span data-ttu-id="7e07d-144">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="7e07d-144">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)       | <span data-ttu-id="7e07d-145">設定色彩屬性。</span><span class="sxs-lookup"><span data-stu-id="7e07d-145">Sets the color attributes.</span></span>                                           |
| [<span data-ttu-id="7e07d-146">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="7e07d-146">**SetConsoleTitle**</span></span>](setconsoletitle.md)                       | <span data-ttu-id="7e07d-147">設定主控台視窗標題。</span><span class="sxs-lookup"><span data-stu-id="7e07d-147">Sets the console window title.</span></span>                                       |
| [<span data-ttu-id="7e07d-148">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="7e07d-148">**GetConsoleTitle**</span></span>](getconsoletitle.md)                       | <span data-ttu-id="7e07d-149">抓取主控台視窗標題。</span><span class="sxs-lookup"><span data-stu-id="7e07d-149">Retrieves the console window title.</span></span>                                  |




<span data-ttu-id="7e07d-150">進程可以使用 [**FreeConsole**](freeconsole.md) 函式，從繼承的主控台或 [**AllocConsole**](allocconsole.md)所建立的主控台卸離本身。</span><span class="sxs-lookup"><span data-stu-id="7e07d-150">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from an inherited console or from a console created by [**AllocConsole**](allocconsole.md).</span></span>









---
title: 主控台-Windows 桌面
description: 主控台是一種應用程式，可提供命令列應用程式的 i/o。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: 7b447e3c1d6d72c58890797177f6668f5d835d35
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059242"
---
# <a name="consoles"></a><span data-ttu-id="bc70e-104">機</span><span class="sxs-lookup"><span data-stu-id="bc70e-104">Consoles</span></span>

<span data-ttu-id="bc70e-105">*主控台* (或*終端*機) 是提供 i/o 給字元模式應用程式的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bc70e-105">A *console* (or *terminal*) is an application that provides I/O to character-mode applications.</span></span> <span data-ttu-id="bc70e-106">這種與處理器無關的機制可讓您輕鬆地移植現有的字元模式應用程式，或建立新的字元模式工具和應用程式。</span><span class="sxs-lookup"><span data-stu-id="bc70e-106">This processor-independent mechanism makes it easy to port existing character-mode applications or to create new character-mode tools and applications.</span></span>

<span data-ttu-id="bc70e-107">主控台包含輸入緩衝區和一或多個螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="bc70e-107">A console consists of an input buffer and one or more screen buffers.</span></span> <span data-ttu-id="bc70e-108">*輸入緩衝區*包含輸入記錄的佇列，其中每一個都包含輸入事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bc70e-108">The *input buffer* contains a queue of input records, each of which contains information about an input event.</span></span> <span data-ttu-id="bc70e-109">輸入佇列一律會包含按鍵和金鑰釋放事件。</span><span class="sxs-lookup"><span data-stu-id="bc70e-109">The input queue always includes key-press and key-release events.</span></span> <span data-ttu-id="bc70e-110">它也可能包含滑鼠事件 (指標移動和按鈕按下和釋放) 和事件，在這段期間，使用者動作會影響作用中螢幕緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="bc70e-110">It may also include mouse events (pointer movements and button presses and releases) and events during which user actions affect the size of the active screen buffer.</span></span> <span data-ttu-id="bc70e-111">*螢幕緩衝區*是在主控台視窗中輸出之字元和色彩資料的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="bc70e-111">A *screen buffer* is a two-dimensional array of character and color data for output in a console window.</span></span> <span data-ttu-id="bc70e-112">任何數目的進程都可以共用主控台。</span><span class="sxs-lookup"><span data-stu-id="bc70e-112">Any number of processes can share a console.</span></span>

- [<span data-ttu-id="bc70e-113">建立主控台</span><span class="sxs-lookup"><span data-stu-id="bc70e-113">Creation of a Console</span></span>](creation-of-a-console.md)
- [<span data-ttu-id="bc70e-114">附加至主控台</span><span class="sxs-lookup"><span data-stu-id="bc70e-114">Attaching to a Console</span></span>](attaching-to-a-console.md)
- [<span data-ttu-id="bc70e-115">關閉主控台</span><span class="sxs-lookup"><span data-stu-id="bc70e-115">Closing a Console</span></span>](closing-a-console.md)
- [<span data-ttu-id="bc70e-116">主控台控制碼</span><span class="sxs-lookup"><span data-stu-id="bc70e-116">Console Handles</span></span>](console-handles.md)
- [<span data-ttu-id="bc70e-117">主控台輸入緩衝區</span><span class="sxs-lookup"><span data-stu-id="bc70e-117">Console Input Buffer</span></span>](console-input-buffer.md)
- [<span data-ttu-id="bc70e-118">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="bc70e-118">Console Screen Buffers</span></span>](console-screen-buffers.md)
- [<span data-ttu-id="bc70e-119">視窗和螢幕緩衝區大小</span><span class="sxs-lookup"><span data-stu-id="bc70e-119">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)
- [<span data-ttu-id="bc70e-120">主控台選取專案</span><span class="sxs-lookup"><span data-stu-id="bc70e-120">Console Selection</span></span>](console-selection.md)
- [<span data-ttu-id="bc70e-121">滾動螢幕緩衝區</span><span class="sxs-lookup"><span data-stu-id="bc70e-121">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

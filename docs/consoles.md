---
title: 主控台-Windows 桌面
description: 主控台是一種應用程式，可提供命令列應用程式的 i/o。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: b50ccd3d38b70ce67498451c8272b832c59fcef9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039116"
---
# <a name="consoles"></a><span data-ttu-id="ecebc-104">機</span><span class="sxs-lookup"><span data-stu-id="ecebc-104">Consoles</span></span>

<span data-ttu-id="ecebc-105">*主控台* 是一種應用程式，可將 i/o 服務提供給字元模式應用程式。</span><span class="sxs-lookup"><span data-stu-id="ecebc-105">A *console* is an application that provides I/O services to character-mode applications.</span></span>

<span data-ttu-id="ecebc-106">主控台包含輸入緩衝區和一或多個螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ecebc-106">A console consists of an input buffer and one or more screen buffers.</span></span> <span data-ttu-id="ecebc-107">*輸入緩衝區* 包含輸入記錄的佇列，其中每一個都包含輸入事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ecebc-107">The *input buffer* contains a queue of input records, each of which contains information about an input event.</span></span> <span data-ttu-id="ecebc-108">輸入佇列一律會包含按鍵和金鑰釋放事件。</span><span class="sxs-lookup"><span data-stu-id="ecebc-108">The input queue always includes key-press and key-release events.</span></span> <span data-ttu-id="ecebc-109">它也可能包含滑鼠事件 (指標移動和按鈕按下和釋放) 和事件，在這段期間，使用者動作會影響作用中螢幕緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="ecebc-109">It may also include mouse events (pointer movements and button presses and releases) and events during which user actions affect the size of the active screen buffer.</span></span> <span data-ttu-id="ecebc-110">*螢幕緩衝區* 是在主控台視窗中輸出之字元和色彩資料的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="ecebc-110">A *screen buffer* is a two-dimensional array of character and color data for output in a console window.</span></span> <span data-ttu-id="ecebc-111">任何數目的進程都可以共用主控台。</span><span class="sxs-lookup"><span data-stu-id="ecebc-111">Any number of processes can share a console.</span></span>

> [!TIP]
><span data-ttu-id="ecebc-112">您可以在 **[生態系統藍圖](ecosystem-roadmap.md)** 中找到更廣泛的主控台，以及它們與終端機和命令列用戶端應用程式之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="ecebc-112">A broader idea of consoles and how they relate to terminals and command-line client applications can be found in the **[ecosystem roadmap](ecosystem-roadmap.md)** .</span></span>

- [<span data-ttu-id="ecebc-113">建立主控台</span><span class="sxs-lookup"><span data-stu-id="ecebc-113">Creation of a Console</span></span>](creation-of-a-console.md)
- [<span data-ttu-id="ecebc-114">正在連結到主控台</span><span class="sxs-lookup"><span data-stu-id="ecebc-114">Attaching to a Console</span></span>](attaching-to-a-console.md)
- [<span data-ttu-id="ecebc-115">關閉主控台</span><span class="sxs-lookup"><span data-stu-id="ecebc-115">Closing a Console</span></span>](closing-a-console.md)
- [<span data-ttu-id="ecebc-116">主控台控制代碼</span><span class="sxs-lookup"><span data-stu-id="ecebc-116">Console Handles</span></span>](console-handles.md)
- [<span data-ttu-id="ecebc-117">主控台輸入緩衝區</span><span class="sxs-lookup"><span data-stu-id="ecebc-117">Console Input Buffer</span></span>](console-input-buffer.md)
- [<span data-ttu-id="ecebc-118">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="ecebc-118">Console Screen Buffers</span></span>](console-screen-buffers.md)
- [<span data-ttu-id="ecebc-119">視窗和螢幕緩衝區大小</span><span class="sxs-lookup"><span data-stu-id="ecebc-119">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)
- [<span data-ttu-id="ecebc-120">主控台選取</span><span class="sxs-lookup"><span data-stu-id="ecebc-120">Console Selection</span></span>](console-selection.md)
- [<span data-ttu-id="ecebc-121">滾動螢幕緩衝區</span><span class="sxs-lookup"><span data-stu-id="ecebc-121">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

---
title: 機
description: 主控台會管理字元模式應用程式的輸入和輸出 (i/o)  (不會提供自己的圖形化使用者介面) 的應用程式。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_character\_mode\_applications'
- base.character\_mode\_applications
- consoles.character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ea3ea214-892c-4953-bc22-7905efbc173f
ms.openlocfilehash: 99f351efbf6b68733b5c3e7b94cee03708d6cbef
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059371"
---
# <a name="consoles"></a><span data-ttu-id="7691d-104">機</span><span class="sxs-lookup"><span data-stu-id="7691d-104">Consoles</span></span>


<span data-ttu-id="7691d-105">主控台會管理字元模式應用程式的輸入和輸出 (i/o)  (不會提供自己的圖形化使用者介面) 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7691d-105">Consoles manage input and output (I/O) for character-mode applications (applications that do not provide their own graphical user interface).</span></span>

<span data-ttu-id="7691d-106">主控台功能可啟用不同層級的主控台存取。</span><span class="sxs-lookup"><span data-stu-id="7691d-106">The console functions enable different levels of access to a console.</span></span> <span data-ttu-id="7691d-107">高階主控台 i/o 函數可讓應用程式從標準輸入讀取，以抓取儲存在主控台輸入緩衝區中的鍵盤輸入。</span><span class="sxs-lookup"><span data-stu-id="7691d-107">The high-level console I/O functions enable an application to read from standard input to retrieve keyboard input stored in a console's input buffer.</span></span> <span data-ttu-id="7691d-108">這些函式也可讓應用程式寫入標準輸出或標準錯誤，以在主控台的螢幕緩衝區中顯示文字。</span><span class="sxs-lookup"><span data-stu-id="7691d-108">The functions also enable an application to write to standard output or standard error to display text in the console's screen buffer.</span></span> <span data-ttu-id="7691d-109">高階函式也支援重新導向標準控制碼，以及控制不同 i/o 功能的主控台模式。</span><span class="sxs-lookup"><span data-stu-id="7691d-109">The high-level functions also support redirection of standard handles and control of console modes for different I/O functionality.</span></span> <span data-ttu-id="7691d-110">低層級主控台 i/o 函式可讓應用程式接收鍵盤和滑鼠事件的詳細輸入，以及涉及使用者與主控台視窗互動的事件。</span><span class="sxs-lookup"><span data-stu-id="7691d-110">The low-level console I/O functions enable applications to receive detailed input about keyboard and mouse events, as well as events involving user interactions with the console window.</span></span> <span data-ttu-id="7691d-111">低層級功能也可讓您更有效地控制畫面的輸出。</span><span class="sxs-lookup"><span data-stu-id="7691d-111">The low-level functions also enable greater control of output to the screen.</span></span>

<span data-ttu-id="7691d-112">本總覽說明對字元模式應用程式的支援。</span><span class="sxs-lookup"><span data-stu-id="7691d-112">This overview describes support for character-mode applications.</span></span>

- [<span data-ttu-id="7691d-113">關於主控台</span><span class="sxs-lookup"><span data-stu-id="7691d-113">About Consoles</span></span>](about-character-mode-applications.md)
- [<span data-ttu-id="7691d-114">使用主控台</span><span class="sxs-lookup"><span data-stu-id="7691d-114">Using the Console</span></span>](using-the-console.md)
- [<span data-ttu-id="7691d-115">主控台參考</span><span class="sxs-lookup"><span data-stu-id="7691d-115">Console Reference</span></span>](console-reference.md)

 

 





---
title: 附加至主控台
description: 進程可以使用 AttachConsole 函式來附加至主控台。 進程可以附加至一個主控台。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_attaching\_to\_a\_console'
- base.attaching\_to\_a\_console
- consoles.attaching\_to\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 348e572f-2448-4384-9822-fab01d4ba255
ms.openlocfilehash: e6ab7da4022d45cd2b1d42957f15f4ffa7e068f3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059378"
---
# <a name="attaching-to-a-console"></a><span data-ttu-id="1d17e-105">附加至主控台</span><span class="sxs-lookup"><span data-stu-id="1d17e-105">Attaching to a Console</span></span>


<span data-ttu-id="1d17e-106">進程可以使用 [**AttachConsole**](attachconsole.md) 函式來附加至主控台。</span><span class="sxs-lookup"><span data-stu-id="1d17e-106">A process can use the [**AttachConsole**](attachconsole.md) function to attach to a console.</span></span> <span data-ttu-id="1d17e-107">進程可以附加至一個主控台。</span><span class="sxs-lookup"><span data-stu-id="1d17e-107">A process can be attached to one console.</span></span>

<span data-ttu-id="1d17e-108">主控台可以有許多附加的進程。</span><span class="sxs-lookup"><span data-stu-id="1d17e-108">A console can have many processes attached to it.</span></span> <span data-ttu-id="1d17e-109">若要取出附加至主控台的進程清單，請呼叫 [**GetConsoleProcessList**](getconsoleprocesslist.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="1d17e-109">To retrieve a list of the processes attached to a console, call the [**GetConsoleProcessList**](getconsoleprocesslist.md) function.</span></span>

 

 





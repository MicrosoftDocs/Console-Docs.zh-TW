---
title: 正在連結到主控台
description: 進程可以使用 AttachConsole 函式來附加至主控台。 進程可以附加至一個主控台。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_attaching\_to\_a\_console'
- base.attaching\_to\_a\_console
- consoles.attaching\_to\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 348e572f-2448-4384-9822-fab01d4ba255
ms.openlocfilehash: 793cc83c0af1f8b0ae4be026f966a79dd034250e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037456"
---
# <a name="attaching-to-a-console"></a><span data-ttu-id="14254-105">正在連結到主控台</span><span class="sxs-lookup"><span data-stu-id="14254-105">Attaching to a Console</span></span>

<span data-ttu-id="14254-106">進程可以使用 [**AttachConsole**](attachconsole.md) 函式，以用戶端的形式附加至主控台。</span><span class="sxs-lookup"><span data-stu-id="14254-106">A process can use the [**AttachConsole**](attachconsole.md) function to attach to a console as a client.</span></span> <span data-ttu-id="14254-107">進程可以附加至一個主控台。</span><span class="sxs-lookup"><span data-stu-id="14254-107">A process can be attached to one console.</span></span>

<span data-ttu-id="14254-108">主控台可以有許多附加的進程。</span><span class="sxs-lookup"><span data-stu-id="14254-108">A console can have many processes attached to it.</span></span> <span data-ttu-id="14254-109">若要取出附加至主控台的進程清單，請呼叫 [**GetConsoleProcessList**](getconsoleprocesslist.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="14254-109">To retrieve a list of the processes attached to a console, call the [**GetConsoleProcessList**](getconsoleprocesslist.md) function.</span></span>

<span data-ttu-id="14254-110">若要附加為伺服器，請參閱 [**Pseudoconsoles**](pseudoconsoles.md)的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="14254-110">To attach as a server, see information about [**Pseudoconsoles**](pseudoconsoles.md).</span></span>

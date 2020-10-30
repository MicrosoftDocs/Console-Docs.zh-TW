---
title: 關閉主控台
description: 進程可以使用 FreeConsole 函式，從其主控台卸離本身。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_closing\_a\_console'
- base.closing\_a\_console
- consoles.closing\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 254b7cfc-4dee-452f-a409-4fc90d20d4c1
ms.openlocfilehash: db424e6d9fc91a7a3b6cff3b5fc5028833d208f9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037316"
---
# <a name="closing-a-console"></a><span data-ttu-id="8dc25-104">關閉主控台</span><span class="sxs-lookup"><span data-stu-id="8dc25-104">Closing a Console</span></span>

<span data-ttu-id="8dc25-105">進程可以使用 [**FreeConsole**](freeconsole.md) 函式，從其主控台卸離本身。</span><span class="sxs-lookup"><span data-stu-id="8dc25-105">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console.</span></span> <span data-ttu-id="8dc25-106">如果有其他進程共用主控台，主控台就不會終結，但呼叫 **FreeConsole** 的進程無法參考它。</span><span class="sxs-lookup"><span data-stu-id="8dc25-106">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="8dc25-107">呼叫 **FreeConsole** 之後，程式可以使用 [**AllocConsole**](allocconsole.md) 來建立新的主控台或 [**AttachConsole**](attachconsole.md) ，以附加至另一個主控台。</span><span class="sxs-lookup"><span data-stu-id="8dc25-107">After calling **FreeConsole** , the process can use [**AllocConsole**](allocconsole.md) to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="8dc25-108">當最後一個附加至它的進程終止或呼叫 [**FreeConsole**](freeconsole.md)時，主控台就會關閉。</span><span class="sxs-lookup"><span data-stu-id="8dc25-108">A console is closed when the last process attached to it terminates or calls [**FreeConsole**](freeconsole.md).</span></span>

---
title: 關閉主控台
description: 進程可以使用 FreeConsole 函式，從其主控台卸離本身。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_closing\_a\_console'
- base.closing\_a\_console
- consoles.closing\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 254b7cfc-4dee-452f-a409-4fc90d20d4c1
ms.openlocfilehash: bdd6b98f96f4ecb64aa6750396c30ef2dd6d0f74
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059358"
---
# <a name="closing-a-console"></a>關閉主控台


進程可以使用 [**FreeConsole**](freeconsole.md) 函式，從其主控台卸離本身。 如果有其他進程共用主控台，主控台就不會終結，但呼叫 **FreeConsole** 的進程無法參考它。 呼叫 **FreeConsole**之後，程式可以使用 [**AllocConsole**](allocconsole.md) 來建立新的主控台或 [**AttachConsole**](attachconsole.md) ，以附加至另一個主控台。

當最後一個附加至它的進程終止或呼叫 [**FreeConsole**](freeconsole.md)時，主控台就會關閉。

 

 





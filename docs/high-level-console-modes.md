---
title: High-Level 主控台模式
description: 高層級主控台功能的行為會受到主控台輸入和輸出模式的影響。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- base.high\_level\_console\_modes
- consoles.high\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
ms.openlocfilehash: 418983a788957578e97fee70624fd80c1b09bc04
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038638"
---
# <a name="high-level-console-modes"></a>High-Level 主控台模式

高層級主控台功能的行為會受到主控台輸入和輸出模式的影響。 主控台建立時，主控台的輸入緩衝區會啟用下列所有的主控台輸入模式：

- 行輸入模式
- 已處理的輸入模式
- Echo 輸入模式

主控台螢幕緩衝區在建立時，會啟用下列兩個主控台輸出模式：

- 處理的輸出模式
- 以 EOL 輸出模式換行

所有三種輸入模式以及已處理的輸出模式都是設計來一起使用。 最好是以群組方式啟用或停用這些模式。 當所有都啟用時，應用程式就會被視為「處理後」模式，這表示大部分的處理都是針對應用程式進行處理。 當全部停用時，應用程式會處於「未經處理」模式，這表示未篩選輸入，而且會對應用程式留下任何處理。

應用程式可以使用 [**GetConsoleMode**](getconsolemode.md) 函式來判斷主控台之輸入緩衝區或螢幕緩衝區的目前模式。 您可以使用 [**SetConsoleMode**](setconsolemode.md) 函式中的下列值，來啟用或停用這些模式中的任何一種。 請注意，設定一個螢幕緩衝區的輸出模式不會影響其他螢幕緩衝區的輸出模式。

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

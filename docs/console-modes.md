---
title: 主控台模式
description: 與每個主控台輸入緩衝區相關聯的是一組會影響輸入作業的輸入模式。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_console\_modes'
- base.console\_modes
- consoles.console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f0dcc123-3b12-44c4-8f94-920203f5198e
ms.openlocfilehash: 0bd048101546d20735745656677702f9f07115fd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039196"
---
# <a name="console-modes"></a>主控台模式

與每個主控台輸入緩衝區相關聯的是一組會影響輸入作業的輸入模式。 同樣地，每個主控台畫面緩衝區都有一組會影響輸出作業的輸出模式。 輸入模式可以分為兩個群組：影響高階輸入函式的群組，以及影響低層級輸入函數的群組。 輸出模式只會影響使用高階輸出功能的應用程式。

[**GetConsoleMode**](getconsolemode.md)函式會報告目前的主控台輸入緩衝區輸入模式，或螢幕緩衝區目前的輸出模式。 [**SetConsoleMode**](setconsolemode.md)函式會設定主控台輸入緩衝區或螢幕緩衝區的目前模式。 如果主控台有多個螢幕緩衝區，則每個畫面的輸出模式都可能不同。 應用程式可以隨時變更 i/o 模式。 如需影響高階和低層級 i/o 作業的主控台模式詳細資訊，請參閱 [高階主控台模式](high-level-console-modes.md) 和 [低層級的主控台模式](low-level-console-modes.md)。

命令列應用程式應該會預期其他命令列應用程式可能會隨時變更控制台模式，而且在傳回控制權之前，可能不會將它還原成原始格式。 此外，我們建議所有的命令列應用程式在啟動時都應該捕獲初始主控台模式，並在結束時嘗試將它還原，以確保對附加至相同主控台的其他命令列應用程式造成最大的影響。

[**GetConsoleDisplayMode**](getconsoledisplaymode.md)函數會報告目前的主控台是否處於全螢幕模式。

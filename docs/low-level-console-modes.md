---
title: Low-Level 主控台模式
description: 主控台輸入緩衝區中報告的輸入事件種類，取決於主控台的滑鼠和視窗輸入模式。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_low\_level\_console\_modes'
- base.low\_level\_console\_modes
- consoles.low\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 41bfdc51-27cb-4d5e-898c-507ffc8789b9
ms.openlocfilehash: acd68e9679f209349f3e0db6989ca905815525a9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039536"
---
# <a name="low-level-console-modes"></a>Low-Level 主控台模式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

主控台輸入緩衝區中報告的輸入事件種類，取決於主控台的滑鼠和視窗輸入模式。 主控台的已處理輸入模式會決定系統如何處理 CTRL + C 按鍵組合。 若要設定或抓取主控台的輸入模式狀態，應用程式可以在 [**SetConsoleMode**](setconsolemode.md) 或 [**GetConsoleMode**](getconsolemode.md) 函式的呼叫中指定主控台輸入緩衝區控制碼。 主控台輸入控制碼會使用下列模式。

| [模式] | 描述 |
|-|-|
| **啟用 \_ 滑鼠 \_ 輸入**     | 控制是否要在輸入緩衝區中報告滑鼠事件。 依預設，會啟用滑鼠輸入並停用視窗輸入。 變更其中一個模式只會影響在設定模式之後所發生的輸入;輸入緩衝區中的暫止滑鼠或視窗事件不會排清。 無論滑鼠模式為何，都會顯示滑鼠指標。                                                |
| **啟用 \_ 視窗 \_ 輸入**    | 控制是否在輸入緩衝區中報告緩衝區調整大小的事件。 依預設，會啟用滑鼠輸入並停用視窗輸入。 變更其中一個模式只會影響在設定模式之後所發生的輸入;輸入緩衝區中的暫止滑鼠或視窗事件不會排清。 無論滑鼠模式為何，都會顯示滑鼠指標。                                      |
| **啟用已 \_ 處理的 \_ 輸入** | 使用高階主控台 i/o 函數控制應用程式的輸入處理。 但是，如果已啟用已處理的輸入模式，則主控台的輸入緩衝區中不會報告 CTRL + C 按鍵組合。 相反地，它會傳遞給適當的控制項處理常式函式。 如需控制處理常式的詳細資訊，請參閱 [主控台控制項處理常式](console-control-handlers.md)。 |

螢幕緩衝區的輸出模式不會影響低層級輸出函數的行為。

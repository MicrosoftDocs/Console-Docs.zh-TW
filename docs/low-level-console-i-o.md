---
title: Low-Level 主控台 i/o
description: 低層級主控台 i/o 函數可讓您直接存取主控台的輸入和螢幕緩衝區，藉以擴充應用程式對主控台 i/o 的控制。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_low\_level\_console\_i\_o'
- base.low\_level\_console\_i\_o
- consoles.low\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c874aff4-6129-4dbc-8949-24d46382d81c
ms.openlocfilehash: b4ec834e44f7ff291466cfe1714442bc17ca7aca
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039546"
---
# <a name="low-level-console-io"></a>Low-Level 主控台 i/o

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

低層級主控台 i/o 函數可讓您直接存取主控台的輸入和螢幕緩衝區，藉以擴充應用程式對主控台 i/o 的控制。 這些函數可讓應用程式執行下列工作：

- 接收關於滑鼠和緩衝區調整大小事件的輸入
- 接收鍵盤輸入事件的擴充資訊
- 將輸入記錄寫入輸入緩衝區
- 讀取輸入記錄而不從輸入緩衝區移除
- 判斷輸入緩衝區中的暫止事件數目
- 清除輸入緩衝區
- 在螢幕緩衝區中的指定位置，讀取及寫入 Unicode 或 ANSI 字元的字串
- 在指定的螢幕緩衝區位置讀取和寫入文字和背景色彩屬性的字串
- 在指定的螢幕緩衝區位置讀取和寫入字元和色彩資料的矩形區塊
- 從指定的螢幕緩衝區位置開始，將單一 Unicode 或 ANSI 字元（或文字和背景色彩屬性組合）寫入指定數目的連續儲存格

如需詳細資訊，請參閱下列主題：

- [主控台模式](console-modes.md)
- [低層級主控台模式](low-level-console-modes.md)
- [低層級主控台輸入函式](low-level-console-input-functions.md)
- [低層級主控台輸出功能](low-level-console-output-functions.md)

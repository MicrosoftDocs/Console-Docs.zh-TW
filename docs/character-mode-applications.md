---
title: 字元模式應用程式
description: 主控台會管理字元模式應用程式的輸入和輸出 (i/o)  (不會提供自己的圖形化使用者介面) 的應用程式。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_character\_mode\_applications'
- base.character\_mode\_applications
- consoles.character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ea3ea214-892c-4953-bc22-7905efbc173f
ms.openlocfilehash: 5e1b0b2b5162360122580f3ea7a100750b96272e
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037346"
---
# <a name="character-mode-applications"></a>字元模式應用程式

主控台會管理字元模式應用程式的輸入和輸出 (i/o)  (不會提供自己的圖形化使用者介面) 的應用程式。

主控台功能可啟用不同層級的主控台存取。 高階主控台 i/o 函數可讓應用程式從標準輸入讀取，以抓取儲存在主控台輸入緩衝區中的鍵盤輸入。 這些函式也可讓應用程式寫入標準輸出或標準錯誤，以在主控台的螢幕緩衝區中顯示文字。 高階函式也支援重新導向標準控制碼，以及控制不同 i/o 功能的主控台模式。 低層級主控台 i/o 函式可讓應用程式接收鍵盤和滑鼠事件的詳細輸入，以及涉及使用者與主控台視窗互動的事件。 低層級功能也可讓您更有效地控制畫面的輸出。

本總覽說明對字元模式應用程式的支援。

- [關於主控台](about-character-mode-applications.md)
- [使用主控台](using-the-console.md)
- [主控台參考](console-reference.md)

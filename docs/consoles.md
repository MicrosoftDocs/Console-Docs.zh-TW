---
title: 主控台-Windows 桌面
description: 主控台是一種應用程式，可提供命令列應用程式的 i/o。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: b50ccd3d38b70ce67498451c8272b832c59fcef9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039116"
---
# <a name="consoles"></a>機

*主控台* 是一種應用程式，可將 i/o 服務提供給字元模式應用程式。

主控台包含輸入緩衝區和一或多個螢幕緩衝區。 *輸入緩衝區* 包含輸入記錄的佇列，其中每一個都包含輸入事件的相關資訊。 輸入佇列一律會包含按鍵和金鑰釋放事件。 它也可能包含滑鼠事件 (指標移動和按鈕按下和釋放) 和事件，在這段期間，使用者動作會影響作用中螢幕緩衝區的大小。 *螢幕緩衝區* 是在主控台視窗中輸出之字元和色彩資料的二維陣列。 任何數目的進程都可以共用主控台。

> [!TIP]
>您可以在 **[生態系統藍圖](ecosystem-roadmap.md)** 中找到更廣泛的主控台，以及它們與終端機和命令列用戶端應用程式之間的關聯性。

- [建立主控台](creation-of-a-console.md)
- [正在連結到主控台](attaching-to-a-console.md)
- [關閉主控台](closing-a-console.md)
- [主控台控制代碼](console-handles.md)
- [主控台輸入緩衝區](console-input-buffer.md)
- [主控台畫面緩衝區](console-screen-buffers.md)
- [視窗和螢幕緩衝區大小](window-and-screen-buffer-size.md)
- [主控台選取](console-selection.md)
- [滾動螢幕緩衝區](scrolling-the-screen-buffer.md)

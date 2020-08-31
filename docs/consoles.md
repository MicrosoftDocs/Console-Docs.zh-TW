---
title: 主控台-Windows 桌面
description: 主控台是一種應用程式，可提供命令列應用程式的 i/o。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_consoles'
- base.consoles
- consoles.consoles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 16148ce6-d3be-40dd-b82e-50ea1df67c4e
ms.openlocfilehash: 7b447e3c1d6d72c58890797177f6668f5d835d35
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059242"
---
# <a name="consoles"></a>機

*主控台* (或*終端*機) 是提供 i/o 給字元模式應用程式的應用程式。 這種與處理器無關的機制可讓您輕鬆地移植現有的字元模式應用程式，或建立新的字元模式工具和應用程式。

主控台包含輸入緩衝區和一或多個螢幕緩衝區。 *輸入緩衝區*包含輸入記錄的佇列，其中每一個都包含輸入事件的相關資訊。 輸入佇列一律會包含按鍵和金鑰釋放事件。 它也可能包含滑鼠事件 (指標移動和按鈕按下和釋放) 和事件，在這段期間，使用者動作會影響作用中螢幕緩衝區的大小。 *螢幕緩衝區*是在主控台視窗中輸出之字元和色彩資料的二維陣列。 任何數目的進程都可以共用主控台。

- [建立主控台](creation-of-a-console.md)
- [附加至主控台](attaching-to-a-console.md)
- [關閉主控台](closing-a-console.md)
- [主控台控制碼](console-handles.md)
- [主控台輸入緩衝區](console-input-buffer.md)
- [主控台畫面緩衝區](console-screen-buffers.md)
- [視窗和螢幕緩衝區大小](window-and-screen-buffer-size.md)
- [主控台選取專案](console-selection.md)
- [滾動螢幕緩衝區](scrolling-the-screen-buffer.md)

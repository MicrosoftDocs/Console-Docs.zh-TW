---
title: 主控台 WinEvents
description: 下列事件常數用於 WinEventProc 回呼函數的事件參數。 如需詳細資訊，請參閱 WinEvents。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- winuser/EVENT_CONSOLE_CARET
- winuser/EVENT_CONSOLE_END_APPLICATION
- winuser/EVENT_CONSOLE_LAYOUT
- winuser/EVENT_CONSOLE_START_APPLICATION
- winuser/EVENT_CONSOLE_UPDATE_REGION
- winuser/EVENT_CONSOLE_UPDATE_SCROLL
- winuser/EVENT_CONSOLE_UPDATE_SIMPLE
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
MS-HAID:
- '\_win32\_console\_winevents'
- base.console\_winevents
- consoles.console\_winevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b7078b2d-5508-4e42-bac2-34b70f1856e2
topic_type:
- apiref
api_name:
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
api_location:
- Winuser.h
api_type:
- HeaderDef
ms.openlocfilehash: 2c5d641140316089b38b836bf3fba7534ccd5600
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038326"
---
# <a name="console-winevents"></a>主控台 WinEvents

> [!IMPORTANT]
> WinEvents 是舊版 **[Microsoft Active Accessibility](https://docs.microsoft.com/windows/win32/winauto/microsoft-active-accessibility)** framework 的一部分。 強烈建議您不要使用這些事件進行開發， **[消費者介面自動化](https://docs.microsoft.com/windows/win32/winauto/entry-uiauto-win32)** 以提供更健全且完整的介面套件，讓協助工具和自動化應用程式與主控台互動。 

> [!WARNING]
> 註冊這些事件是一項全域活動，會大幅影響系統上執行之所有命令列應用程式的效能，包括服務和背景公用程式。 **Microsoft 消費者介面自動化** framework 是特定的主控台會話，克服這項限制。

下列事件常數用於 [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx)回呼函數的 *事件* 參數。 如需詳細資訊，請參閱 [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889)。

| 常數/值 | 描述 |
|-|-|
| **EVENT_CONSOLE_CARET** 0x4001 | 主控台插入號已移動。 *IdObject* 參數是下列其中一個或多個值： **CONSOLE_CARET_SELECTION** 或 **CONSOLE_CARET_VISIBLE** 。 *IdChild* 參數是一種 **[COORD](coord-str.md)** 結構，可指定資料指標的目前位置。 |
| **EVENT_CONSOLE_END_APPLICATION** 0x4007 | 主控台進程已結束。 *IdObject* 參數包含終止進程的處理序識別碼。 |
| **EVENT_CONSOLE_LAYOUT** 0x4005 | 主控台版面配置已變更。 |
| **EVENT_CONSOLE_START_APPLICATION** 0x4006 | 新的主控台進程已啟動。 *IdObject* 參數包含新建立之進程的處理序識別碼。 如果應用程式是16位的應用程式，則會 **CONSOLE_APPLICATION_16BIT** *idChild* 參數，而 *idObject* 是與主控台相關聯之 NTVDM 會話的處理序識別碼。 |
|**EVENT_CONSOLE_UPDATE_REGION** 0x4002 | 有一個以上的字元已經變更。 *IdObject* 參數是指定變更區域開頭的 **[COORD](coord-str.md)** 結構。 *IdChild* 參數是指定已變更區域結尾的 **COORD** 結構。 |
|**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004 | 主控台已滾動。 *IdObject* 參數是主控台滾動的水準距離。 *IdChild* 參數是主控台滾動的垂直距離。 |
|**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003 | 單一字元已經變更。 *IdObject* 參數是指定已變更之字元的 **[COORD](coord-str.md)** 結構。 *IdChild* 參數會指定低字組中的字元和高位字中的 **[字元屬性](console-screen-buffers.md#character-attributes)** 。 |

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | Winuser。h |

---
title: INPUT_RECORD 結構
description: 請參閱在主控台輸入緩衝區中描述輸入事件的 INPUT_RECORD 結構相關參考資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- wincontypes/INPUT_RECORD
- wincon/INPUT_RECORD
- INPUT_RECORD
- wincontypes/PINPUT_RECORD
- wincon/PINPUT_RECORD
- PINPUT_RECORD
MS-HAID:
- '\_win32\_input\_record\_str'
- base.input\_record\_str
- consoles.input\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a46ba7fd-097a-455d-96ac-13aa01e11dc1
topic_type:
- apiref
api_name:
- INPUT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4ad86de170c1fef74f133a5d5c51d8de2dea497f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038536"
---
# <a name="input_record-structure"></a>輸入 \_ 記錄結構

描述主控台輸入緩衝區中的輸入事件。 您可以使用 [**ReadConsoleInput**](readconsoleinput.md) 或 [**PeekConsoleInput**](peekconsoleinput.md) 函數從輸入緩衝區讀取這些記錄，或使用 [**WriteConsoleInput**](writeconsoleinput.md) 函式將它們寫入至輸入緩衝區。

## <a name="syntax"></a>語法

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

## <a name="members"></a>成員

**EventType**  
輸入事件種類的控制碼和儲存在 **事件** 成員中的事件記錄。

這個成員可以是下列其中一個值。

| 值 | 意義 |
|-|-|
| **FOCUS_EVENT** 0x0010 | **事件** 成員包含 **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** 結構。 這些事件會在內部使用，應該予以忽略。 |
| **KEY_EVENT** 0x0001 | **事件** 成員包含具有鍵盤事件相關資訊的 **[KEY_EVENT_RECORD](key-event-record-str.md)** 結構。 |
| **MENU_EVENT** 0x0008 | **事件** 成員包含 **[MENU_EVENT_RECORD](menu-event-record-str.md)** 結構。 這些事件會在內部使用，應該予以忽略。 |
| **MOUSE_EVENT** 0x0002 | **事件** 成員包含 **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** 結構，其中包含滑鼠移動或按鈕按下事件的相關資訊。 |
| **WINDOW_BUFFER_SIZE_EVENT** 0x0004 | **事件** 成員包含 **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** 結構，以及主控台螢幕緩衝區新大小的相關資訊。 |

**事件**  
事件資訊。 此成員的格式取決 **于事件種類成員所** 指定的事件種類。

## <a name="examples"></a>範例

如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | WinConTypes .h (via WinCon，包括 Windows .h)  |

## <a name="see-also"></a>請參閱

[**焦點 \_ 事件 \_ 記錄**](focus-event-record-str.md)

[**關鍵 \_ 事件 \_ 記錄**](key-event-record-str.md)

[**功能表 \_ 事件 \_ 記錄**](menu-event-record-str.md)

[**滑鼠 \_ 事件 \_ 記錄**](mouse-event-record-str.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

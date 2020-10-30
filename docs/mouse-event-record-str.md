---
title: MOUSE_EVENT_RECORD 結構
description: 請參閱 MOUSE_EVENT_RECORD 結構的參考資訊，其描述主控台 INPUT_RECORD 結構中的滑鼠輸入事件。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- wincontypes/MOUSE_EVENT_RECORD
- wincon/MOUSE_EVENT_RECORD
- MOUSE_EVENT_RECORD
- wincontypes/PMOUSE_EVENT_RECORD
- wincon/PMOUSE_EVENT_RECORD
- PMOUSE_EVENT_RECORD
MS-HAID:
- '\_win32\_mouse\_event\_record\_str'
- base.mouse\_event\_record\_str
- consoles.mouse\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ea54c6-8872-4111-8d72-1377409b9247
topic_type:
- apiref
api_name:
- MOUSE_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: c10047d1386f3bce1546ee21bacdc81b8fb7bb55
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038516"
---
# <a name="mouse_event_record-structure"></a>滑鼠 \_ 事件 \_ 記錄結構

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

描述主控台 [**輸入 \_ 記錄**](input-record-str.md) 結構中的滑鼠輸入事件。

## <a name="syntax"></a>語法

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

## <a name="members"></a>成員

**dwMousePosition**  
[**COORD**](coord-str.md)結構，其中包含游標的位置，以主控台螢幕緩衝區的字元儲存格座標為單位。

**dwButtonState**  
滑鼠按鍵的狀態。 最不重要的位會對應到最左邊的滑鼠按鍵。 下一個最小的位會對應至最右邊的滑鼠按鍵。 下個位表示從下到左的滑鼠按鍵。 然後，位會從左至右對應至滑鼠按鍵。 如果已按下按鈕，則位為1。

以下是前五個滑鼠按鍵的定義常數。

| 值 | 意義 |
|-|-|
| **FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001 | 最左邊的滑鼠按鍵。 |
| **FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004 | 第二個按鈕從左邊。 |
| **FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008 | 左邊的第三個按鈕。 |
| **FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010 | 左邊的第四個按鈕。 |
| **RIGHTMOST_BUTTON_PRESSED** 0x0002 | 最右邊的滑鼠按鍵。 |

**dwControlKeyState**  
控制項索引鍵的狀態。 這個成員可以是下列一或多個值。

| 值 | 意義 |
|-|-|
| **CAPSLOCK_ON** 0x0080 | CAPS LOCK 燈開啟。 |
| **ENHANCED_KEY** 0x0100 | 金鑰已增強。 請參閱 [備註](key-event-record-str.md#remarks)。 |
| **LEFT_ALT_PRESSED** 0x0002 | 左 ALT 鍵已按下。 |
| **LEFT_CTRL_PRESSED** 0x0008 | 按下 CTRL 鍵。 |
| **NUMLOCK_ON** 0x0020 | NUM LOCK 燈開啟。 |
| **RIGHT_ALT_PRESSED** 0x0001 | 按下右邊的 ALT 鍵。 |
| **RIGHT_CTRL_PRESSED** 0x0004 | 按下 CTRL 鍵。 |
| **SCROLLLOCK_ON** 0x0040 | 捲軸鎖定燈開啟。 |
| **SHIFT_PRESSED** 0x0010 | 按下 SHIFT 鍵。 |

**dwEventFlags**  
滑鼠事件的類型。 如果這個值為零，表示已按下或放開滑鼠按鍵。 否則，此成員會是下列其中一個值。

| 值 | 意義 |
|-|-|
| **DOUBLE_CLICK** 0x0002 | 第二次按一下 (按鈕時，請按下滑鼠按鍵) 。 第一次按一下會以一般按鈕按下事件的方式傳回。 |
| **MOUSE_HWHEELED** 0x0008 | 移動了水準滑鼠滾輪。<br /><br />如果 **dwButtonState** 成員的最大文字包含正值，滾輪就會向右旋轉。 否則，滾輪會旋轉至左方。 |
| **MOUSE_MOVED** 0x0001 | 發生滑鼠位置變更。 |
| **MOUSE_WHEELED** 0x0004 | 移動了垂直滑鼠滾輪。<br /><br />如果 **dwButtonState** 成員的高單字包含正值，則滾輪會向前旋轉，而不是使用者。 否則，滾輪會向使用者旋轉。 |

## <a name="remarks"></a>備註

當主控台處於滑鼠模式時，滑鼠事件會放置在輸入緩衝區中 ( **啟用 \_ 滑鼠 \_ 輸入** ) 。

每當使用者移動滑鼠或按下或放開其中一個滑鼠按鍵時，就會產生滑鼠事件。 只有當主控台群組具有鍵盤焦點，且游標位於主控台視窗的框線內時，滑鼠事件才會放在主控台的輸入緩衝區中。

## <a name="examples"></a>範例

如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | WinConTypes .h (via WinCon，包括 Windows .h)  |

## <a name="see-also"></a>請參閱

[**COORD**](coord-str.md)

[**輸入 \_ 記錄**](input-record-str.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

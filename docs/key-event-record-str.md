---
title: KEY_EVENT_RECORD 結構
description: 描述主控台輸入記錄結構中的鍵盤輸入事件 \_ 。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- wincontypes/KEY_EVENT_RECORD
- wincon/KEY_EVENT_RECORD
- KEY_EVENT_RECORD
- wincontypes/PKEY_EVENT_RECORD
- wincon/PKEY_EVENT_RECORD
- PKEY_EVENT_RECORD
MS-HAID:
- '\_win32\_key\_event\_record\_str'
- base.key\_event\_record\_str
- consoles.key\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b3fed86b-84ef-48e4-97e1-cb3d65f714a7
topic_type:
- apiref
api_name:
- KEY_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: bcc58b90e71b848e3b6e4b0bf5ba162323830529
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357798"
---
# <a name="key_event_record-structure"></a>關鍵 \_ 事件 \_ 記錄結構

描述主控台 [**輸入 \_ 記錄**](input-record-str.md) 結構中的鍵盤輸入事件。

## <a name="syntax"></a>語法

```C
typedef struct _KEY_EVENT_RECORD {
  BOOL  bKeyDown;
  WORD  wRepeatCount;
  WORD  wVirtualKeyCode;
  WORD  wVirtualScanCode;
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } uChar;
  DWORD dwControlKeyState;
} KEY_EVENT_RECORD;
```

## <a name="members"></a>成員

**bKeyDown**  
如果按下索引鍵，此成員為 **TRUE**。 否則，此成員為 **FALSE** () 釋放金鑰。

**wRepeatCount**  
重複計數，表示正在關閉金鑰。 例如，當索引鍵被保留時，您可能會得到五個事件，這個成員等於1、一個這個成員等於5的事件，或是這個成員大於或等於1的多個事件。

**wVirtualKeyCode**  
以裝置無關的方式識別指定索引鍵的 [虛擬機器碼程式碼](/windows/win32/inputdev/virtual-key-codes) 。

**wVirtualScanCode**  
指定按鍵的虛擬掃描碼，代表鍵盤硬體所產生的裝置相依值。

**uChar**  
下列成員的聯集。

**UnicodeChar**  
已翻譯的 Unicode 字元。

**AsciiChar**  
轉譯的 ASCII 字元。

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

## <a name="remarks"></a>備註

適用于 IBM® 101-和102鍵鍵盤的增強金鑰包括： INS、DEL、HOME、END、PAGE UP、PAGE DOWN 和方向鍵（在叢集中的叢集中）;然後將 (/) ，然後在鍵盤上輸入按鍵。

當按下或放開任何按鍵時，就會產生鍵盤輸入事件，包括控制按鍵。 不過，在未結合另一個字元的情況下，按下並放開 ALT 鍵時，對系統具有特殊意義，且不會傳遞至應用程式。 此外，如果輸入控制碼處於處理模式，則不會傳遞 CTRL + C 按鍵組合 (**啟用已 \_ 處理的 \_ 輸入**) 。

## <a name="examples"></a>範例

如需範例，請參閱[讀取輸入緩衝區事件](reading-input-buffer-events.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | WinConTypes .h (via WinCon，包括 Windows .h)  |

## <a name="see-also"></a>另請參閱

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**WriteConsoleInput**](writeconsoleinput.md)

[**輸入 \_ 記錄**](input-record-str.md)
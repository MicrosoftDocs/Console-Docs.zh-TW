---
title: CONSOLE_READCONSOLE_CONTROL 結構
description: 請參閱 CONSOLE_READCONSOLE_CONTROL 結構的參考資訊，其中包含主控台讀取操作的資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/CONSOLE_READCONSOLE_CONTROL
- wincon/CONSOLE_READCONSOLE_CONTROL
- CONSOLE_READCONSOLE_CONTROL
- consoleapi/PCONSOLE_READCONSOLE_CONTROL
- wincon/PCONSOLE_READCONSOLE_CONTROL
- PCONSOLE_READCONSOLE_CONTROL
MS-HAID:
- base.console\_readconsole\_control
- consoles.console\_readconsole\_control
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a8451a6-d692-43af-88c4-972c4dc5e07c
topic_type:
- apiref
api_name:
- CONSOLE_READCONSOLE_CONTROL
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8a703a1eaa370e16095e1b10eb146a0718f332e9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039186"
---
# <a name="console_readconsole_control-structure"></a>主控台 \_ READCONSOLE \_ 控制結構

包含主控台讀取操作的資訊。

## <a name="syntax"></a>語法

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

## <a name="members"></a>成員

**nLength**  
結構的大小。 將這個成員設定為 `sizeof(CONSOLE_READCONSOLE_CONTROL)` 。

**nInitialChars**  
要略過的字元數 (，因此在傳遞至 [**ReadConsole**](readconsole.md) 函式的緩衝區中寫入新的讀取輸入之前，會保留) 。 這個值必須小於 **ReadConsole** 函數的 *nNumberOfCharsToRead* 參數。

**dwCtrlWakeupMask**  
遮罩，指定應該使用和之間的控制字元 `0x00` `0x1F` 來表示讀取已完成。 每個位都對應到一個字元，且該字元的最小位對應于或 `0x00` `NUL` 以及與或相對應的最高有效位 `0x1F` `US` 。 您可以指定多個位 (控制字元) 。

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

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | \[僅限 Windows Vista 桌面應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2008 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi .h (via WinCon，包括 Windows .h)  |

## <a name="see-also"></a>請參閱

[**ReadConsole**](readconsole.md)

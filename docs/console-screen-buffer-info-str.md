---
title: CONSOLE_SCREEN_BUFFER_INFO 結構
description: 請參閱有關 CONSOLE_SCREEN_BUFFER_INFO 結構的參考資訊，其中包含主控台螢幕緩衝區的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFO
- wincon/CONSOLE_SCREEN_BUFFER_INFO
- CONSOLE_SCREEN_BUFFER_INFO
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFO
- wincon/PCONSOLE_SCREEN_BUFFER_INFO
- PCONSOLE_SCREEN_BUFFER_INFO
MS-HAID:
- '\_win32\_console\_screen\_buffer\_info\_str'
- base.console\_screen\_buffer\_info\_str
- consoles.console\_screen\_buffer\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 586b3e0f-2f6b-4a03-b8e4-602a892be56d
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8b3a739a9f66e25687b60a3450c9381822c16e53
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039176"
---
# <a name="console_screen_buffer_info-structure"></a>主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊結構

包含主控台螢幕緩衝區的相關資訊。

## <a name="syntax"></a>語法

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFO {
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
} CONSOLE_SCREEN_BUFFER_INFO;
```

## <a name="members"></a>成員

**dwSize**  
[**COORD**](coord-str.md)結構，其中包含主控台螢幕緩衝區的大小（以字元資料行和資料列為限）。

**dwCursorPosition**  
[**COORD**](coord-str.md)結構，其中包含主控台螢幕緩衝區中資料指標的資料行和資料列座標。

**wAttributes**  
[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)和 [**WriteConsole**](writeconsole.md)函式寫入螢幕緩衝區的字元屬性，或 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)和 [**ReadConsole**](readconsole.md)函式的螢幕緩衝區。 如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#character-attributes)。

**srWindow**  
[**小型 \_ 矩形**](small-rect-str.md)結構，其中包含顯示視窗左上角和右下角的主控台螢幕緩衝區座標。

**dwMaximumWindowSize**  
[**COORD**](coord-str.md)結構，其中包含主控台視窗的大小上限（以字元資料行和資料列為限），指定目前的螢幕緩衝區大小和字型和螢幕大小。

## <a name="examples"></a>範例

如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |

## <a name="see-also"></a>請參閱

[**COORD**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**小型 \_ 矩形**](small-rect-str.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

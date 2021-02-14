---
title: CONSOLE_SCREEN_BUFFER_INFOEX 結構
description: 請參閱有關 CONSOLE_SCREEN_BUFFER_INFOEX 結構的參考資訊，其中包含主控台螢幕緩衝區的延伸資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFOEX
- wincon/CONSOLE_SCREEN_BUFFER_INFOEX
- CONSOLE_SCREEN_BUFFER_INFOEX
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFOEX
- wincon/PCONSOLE_SCREEN_BUFFER_INFOEX
- PCONSOLE_SCREEN_BUFFER_INFOEX
MS-HAID:
- base.console\_screen\_buffer\_infoex
- consoles.console\_screen\_buffer\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6ed40df3-063d-41c9-8637-510c95104603
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFOEX
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 1e4e30601655190bc6f597bbd33dd99f14f8d488
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358079"
---
# <a name="console_screen_buffer_infoex-structure"></a>主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX 結構

包含有關主控台螢幕緩衝區的延伸資訊。

## <a name="syntax"></a>語法

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

## <a name="members"></a>成員

**cbSize**  
此結構的大小（以位元組為單位）。

**dwSize**  
[**COORD**](coord-str.md)結構，其中包含主控台螢幕緩衝區的大小（以字元資料行和資料列為限）。

**dwCursorPosition**  
[**COORD**](coord-str.md)結構，其中包含主控台螢幕緩衝區中資料指標的資料行和資料列座標。

**wAttributes**  
[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)和 [**WriteConsole**](writeconsole.md)函式寫入螢幕緩衝區的字元屬性，或 [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)和 [**ReadConsole**](readconsole.md)函式的螢幕緩衝區。 如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#character-attributes)。

**srWindow**  
[**小型 \_ 矩形**](small-rect-str.md)結構，其中包含顯示視窗左上角和右下角的主控台螢幕緩衝區座標。

**dwMaximumWindowSize**  
[**COORD**](coord-str.md)結構，其中包含主控台視窗的大小上限（以字元資料行和資料列為限），指定目前的螢幕緩衝區大小和字型和螢幕大小。

**wPopupAttributes**  
主控台快顯視窗的填滿屬性。

**bFullscreenSupported**  
如果這個成員是 `TRUE` ，則支援全螢幕模式; 否則就不支援。 這一律 `FALSE` 適用于 Windows Vista 含 [WDDM 驅動程式模型](/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) 的系統，因為它已不再提供對監視的直接 VGA 存取。

**ColorTable**  
描述主控台色彩設定的 [**COLORREF**](/windows/win32/gdi/colorref) 值陣列。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | \[僅限 Windows Vista 桌面應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2008 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |

## <a name="see-also"></a>另請參閱

[**COORD**](coord-str.md)

[**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md)

[**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md)

[**小型 \_ 矩形**](small-rect-str.md)
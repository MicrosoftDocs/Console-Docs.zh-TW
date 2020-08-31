---
title: CONSOLE_SCREEN_BUFFER_INFOEX 結構
description: 請參閱有關 CONSOLE_SCREEN_BUFFER_INFOEX 結構的參考資訊，其中包含主控台螢幕緩衝區的延伸資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 010120f2d925727e37bd72905bab4536db073371
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059294"
---
# <a name="console_screen_buffer_infoex-structure"></a>主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX 結構


包含有關主控台螢幕緩衝區的延伸資訊。

<a name="syntax"></a>Syntax
------

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

<a name="members"></a>成員
-------

**cbSize**  
此結構的大小（以位元組為單位）。

**dwSize**  
[**COORD**](coord-str.md)結構，其中包含主控台螢幕緩衝區的大小（以字元資料行和資料列為限）。

**dwCursorPosition**  
[**COORD**](coord-str.md)結構，其中包含主控台螢幕緩衝區中資料指標的資料行和資料列座標。

**wAttributes**  
[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)和[**WriteConsole**](writeconsole.md)函式寫入螢幕緩衝區的字元屬性，或[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)和[**ReadConsole**](readconsole.md)函式的螢幕緩衝區。 如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#_win32_font_attributes)。

**srWindow**  
[**小型 \_ 矩形**](small-rect-str.md)結構，其中包含顯示視窗左上角和右下角的主控台螢幕緩衝區座標。

**dwMaximumWindowSize**  
[**COORD**](coord-str.md)結構，其中包含主控台視窗的大小上限（以字元資料行和資料列為限），指定目前的螢幕緩衝區大小和字型和螢幕大小。

**wPopupAttributes**  
主控台快顯視窗的填滿屬性。

**bFullscreenSupported**  
如果這個成員是 TRUE，則支援全螢幕模式;否則，它不會。

**ColorTable**  
描述主控台色彩設定的 [**COLORREF**](https://msdn.microsoft.com/library/windows/desktop/dd183449) 值陣列。

<a name="requirements"></a>規格需求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>最低支援的用戶端</p></td>
<td><p>Windows Vista [僅限桌面應用程式]</p></td>
</tr>
<tr class="even">
<td><p>最低支援的伺服器</p></td>
<td><p>Windows Server 2008 [僅限桌面應用程式]</p></td>
</tr>
<tr class="odd">
<td><p>標頭</p></td>
<td>ConsoleApi2 .h (via Wincon，包括 Windows .h) </td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另請參閱


[**COORD**](coord-str.md)

[**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md)

[**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md)

[**小型 \_ 矩形**](small-rect-str.md)

 

 





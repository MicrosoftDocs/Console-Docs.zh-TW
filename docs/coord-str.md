---
title: COORD 結構
description: 在主控台螢幕緩衝區中定義字元資料格的座標。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- wincontypes/COORD
- wincon/COORD
- COORD
- wincontypes/PCOORD
- wincon/PCOORD
- PCOORD
MS-HAID:
- '\_win32\_coord\_str'
- base.coord\_str
- consoles.coord\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d730c46e-ea17-475e-b956-8ee5f4f5c04e
topic_type:
- apiref
api_name:
- COORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: c29594cbddd69ae8ca6d3f958acd0eeb3cb60e9b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059239"
---
# <a name="coord-structure"></a>COORD 結構


在主控台螢幕緩衝區中定義字元資料格的座標。 座標系統的原點 (0，0) 位於緩衝區的左上角儲存格。

<a name="syntax"></a>Syntax
------

```C
typedef struct _COORD {
  SHORT X;
  SHORT Y;
} COORD, *PCOORD;
```

<a name="members"></a>成員
-------

**X**  
水準座標或資料行值。 單位取決於函式呼叫。

**Y**  
垂直座標或資料行值。 單位取決於函式呼叫。

<a name="examples"></a>範例
--------

如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。

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
<td><p>Windows 2000 Professional [僅限桌面應用程式]</p></td>
</tr>
<tr class="even">
<td><p>最低支援的伺服器</p></td>
<td><p>Windows 2000 伺服器 [僅限桌面應用程式]</p></td>
</tr>
<tr class="odd">
<td><p>標頭</p></td>
<td>WinConTypes .h (via Wincon，包括 Windows .h) </td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另請參閱


[**主控台 \_ 字型 \_ 資訊**](console-font-info-str.md)

[**主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊**](console-screen-buffer-info-str.md)

[**主控台 \_ 選取 \_ 資訊**](console-selection-info-str.md)

[**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)

[**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)

[**GetConsoleFontSize**](getconsolefontsize.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**滑鼠 \_ 事件 \_ 記錄**](mouse-event-record-str.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleDisplayMode**](setconsoledisplaymode.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)

[**視窗 \_ 緩衝區 \_ 大小 \_ 記錄**](window-buffer-size-record-str.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)

 

 





---
title: COORD 結構
description: 在主控台螢幕緩衝區中定義字元資料格的座標。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: c8e6f87c3a2730a8af21b9bc064c71900fb82f5b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038306"
---
# <a name="coord-structure"></a>COORD 結構

在主控台螢幕緩衝區中定義字元資料格的座標。 座標系統的原點 (0，0) 位於緩衝區的左上角儲存格。

## <a name="syntax"></a>語法

```C
typedef struct _COORD {
  SHORT X;
  SHORT Y;
} COORD, *PCOORD;
```

## <a name="members"></a>成員

**X**  
水準座標或資料行值。 單位取決於函式呼叫。

**Y**  
垂直座標或資料行值。 單位取決於函式呼叫。

## <a name="examples"></a>範例

如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | WinConTypes .h (via WinCon，包括 Windows .h)  |

## <a name="see-also"></a>請參閱

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

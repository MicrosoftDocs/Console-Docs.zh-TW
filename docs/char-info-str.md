---
title: CHAR_INFO 結構
description: 指定 Unicode 或 ANSI 字元及其屬性。 主控台函式會使用此結構讀取和寫入主控台螢幕緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- wincontypes/CHAR_INFO
- wincon/CHAR_INFO
- CHAR_INFO
- wincontypes/PCHAR_INFO
- wincon/PCHAR_INFO
- PCHAR_INFO
MS-HAID:
- '\_win32\_char\_info\_str'
- base.char\_info\_str
- consoles.char\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5574a862-b262-41af-8862-e9837c5c7b5f
topic_type:
- apiref
api_name:
- CHAR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: a16fb23d148f75480437211204a0fd7c1f161bfe
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357848"
---
# `CHAR\_INFO structure`

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

指定 Unicode 或 ANSI 字元及其屬性。 主控台函式會使用此結構讀取和寫入主控台螢幕緩衝區。

## <a name="syntax"></a>語法

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## <a name="members"></a>成員

**Char**  
下列成員的聯集。

**UnicodeChar**  
螢幕緩衝區字元資料格的 Unicode 字元。

**AsciiChar**  
螢幕緩衝區字元資料格的 ANSI 字元。

**屬性**  
字元屬性。 這個成員可以是零或下列值的任何組合。

| 值 | 意義 |
|-|-|
| **FOREGROUND_BLUE**`0x0001` | 文字色彩包含藍色。 |
| **FOREGROUND_GREEN**`0x0002` | 文字色彩包含綠色。 |
| **FOREGROUND_RED**`0x0004` | 文字色彩包含紅色。 |
| **FOREGROUND_INTENSITY**`0x0008` | 加深文字色彩。 |
| **BACKGROUND_BLUE**`0x0010` | 背景色彩包含藍色。 |
| **BACKGROUND_GREEN**`0x0020` | 背景色彩包含綠色。 |
| **BACKGROUND_RED**`0x0040` | 背景色彩包含紅色。 |
| **BACKGROUND_INTENSITY**`0x0080` | 加深背景色彩。 |
| **COMMON_LVB_LEADING_BYTE**`0x0100` | 前置位元組。 |
| **COMMON_LVB_TRAILING_BYTE**`0x0200` | 尾端位元組。 |
| **COMMON_LVB_GRID_HORIZONTAL**`0x0400` | 水平置頂。 |
| **COMMON_LVB_GRID_LVERTICAL**`0x0800` | 垂直靠左。 |
| **COMMON_LVB_GRID_RVERTICAL**`0x1000` | 垂直靠右。 |
| **COMMON_LVB_REVERSE_VIDEO**`0x4000` | 反向前景和背景屬性。 |
| **COMMON_LVB_UNDERSCORE**`0x8000` | 底線。 |

## <a name="examples"></a>範例

如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | WinCon (包含) 的 Windows。h |

## <a name="see-also"></a>另請參閱

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

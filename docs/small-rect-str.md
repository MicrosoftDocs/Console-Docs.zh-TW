---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- wincontypes/SMALL_RECT
- wincon/SMALL_RECT
- SMALL_RECT
title: SMALL_RECT 結構
description: 定義矩形左上角和右下角的座標。
MS-HAID:
- '\_win32\_small\_rect\_str'
- base.small\_rect\_str
- consoles.small\_rect\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 62639815-c7e9-4ae2-b152-61290f78422b
topic_type:
- apiref
api_name:
- SMALL_RECT
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 93121864c8754b281b92051a5e4a174b2d5956a3
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037096"
---
# <a name="small_rect-structure"></a>SMALL \_ RECT 結構

定義矩形左上角和右下角的座標。

## <a name="syntax"></a>語法

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

## <a name="members"></a>成員

**離開**  
矩形左上角的 x 座標。

**前幾個**  
矩形左上角的 y 座標。

**對**  
矩形右下角的 x 座標。

**底端**  
矩形右下角的 y 座標。

## <a name="remarks"></a>備註

主控台函式會使用此結構來指定主控台螢幕緩衝區的矩形區域，其中的座標會指定螢幕緩衝區字元資料格的資料列和資料行。

## <a name="examples"></a>範例

如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | WinConTypes .h (via WinCon，包括 Windows .h)  |

## <a name="see-also"></a>請參閱

[**矩形**](https://msdn.microsoft.com/library/windows/desktop/dd162897)

[**RECTL**](https://msdn.microsoft.com/library/windows/desktop/dd162907)

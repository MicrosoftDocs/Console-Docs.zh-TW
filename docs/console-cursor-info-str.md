---
title: CONSOLE_CURSOR_INFO 結構
description: 包含有關主控台資料指標的大小和可見度資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- wincontypes/CONSOLE_CURSOR_INFO
- wincon/CONSOLE_CURSOR_INFO
- CONSOLE_CURSOR_INFO
- wincontypes/PCONSOLE_CURSOR_INFO
- wincon/PCONSOLE_CURSOR_INFO
- PCONSOLE_CURSOR_INFO
MS-HAID:
- '\_win32\_console\_cursor\_info\_str'
- base.console\_cursor\_info\_str
- consoles.console\_cursor\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0e71ce8c-e008-4bd7-922e-c44484b425ef
topic_type:
- apiref
api_name:
- CONSOLE_CURSOR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: cdfcc00035738aa468d9795e4f6d32a54b96e1d0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037008"
---
# <a name="console_cursor_info-structure"></a>主控台資料 \_ 指標 \_ 資訊結構

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

包含主控台資料指標的相關資訊。

## <a name="syntax"></a>語法

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

## <a name="members"></a>成員

**dwSize**  
資料指標所填滿的字元資料格百分比。 此值介於1到100之間。 游標外觀會有所不同，範圍從完全填滿儲存格到顯示為數據格底部的水平線條。

> [!NOTE]
>雖然 **dwSize** 值通常介於1到100之間，但在某些情況下，可能會傳回超出該範圍的值。 例如，如果登錄中的 **CursorSize** 設定為0，則傳回的 **dwSize** 值會是0。

 **bVisible**  
資料指標的可見度。 如果資料指標是可見的，則這個成員是 **TRUE** 。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | WinCon (包含) 的 Windows。h |

## <a name="see-also"></a>請參閱

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**SetConsoleCursorInfo**](setconsolecursorinfo.md)

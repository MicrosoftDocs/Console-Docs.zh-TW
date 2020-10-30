---
title: CONSOLE_FONT_INFO 結構
description: 請參閱 CONSOLE_FONT_INFO 結構的參考資訊，其中包含主控台字型的索引和大小。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- wincontypes/CONSOLE_FONT_INFO
- wincon/CONSOLE_FONT_INFO
- CONSOLE_FONT_INFO
- wincontypes/PCONSOLE_FONT_INFO
- wincon/PCONSOLE_FONT_INFO
- PCONSOLE_FONT_INFO
MS-HAID:
- '\_win32\_console\_font\_info\_str'
- base.console\_font\_info\_str
- consoles.console\_font\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 380b8183-1964-46f2-a511-01f39f21f5c5
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6c437e626ed6d207da4672a3a5ea60c2ea0ee008
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037136"
---
# <a name="console_font_info-structure"></a>主控台 \_ 字型 \_ 資訊結構

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

包含主控台字型的資訊。

## <a name="syntax"></a>語法

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

## <a name="members"></a>成員

**nFont**  
系統的主控台字型表中的字型索引。

**dwFontSize**  
[**COORD**](coord-str.md)結構，其中包含字型中每個字元的寬度和高度（以邏輯單位表示）。 **X** 成員包含寬度，而 **Y** 成員包含高度。

## <a name="remarks"></a>備註

若要取得字型的大小，請將字型索引傳遞給 [**GetConsoleFontSize**](getconsolefontsize.md) 函數。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | \[僅限 WINDOWS XP desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2003 \[ desktop 應用程式\] |
| 標頭 | WinCon (包含) 的 Windows。h |

## <a name="see-also"></a>請參閱

[**COORD**](coord-str.md)

[**GetCurrentConsoleFont**](getcurrentconsolefont.md)

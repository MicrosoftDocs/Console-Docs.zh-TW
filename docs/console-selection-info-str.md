---
title: CONSOLE_SELECTION_INFO 結構
description: 請參閱 CONSOLE_SELECTION_INFO 結構的參考資訊，其中包含主控台選取專案的資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/CONSOLE_SELECTION_INFO
- wincon/CONSOLE_SELECTION_INFO
- CONSOLE_SELECTION_INFO
- consoleapi3/PCONSOLE_SELECTION_INFO
- wincon/PCONSOLE_SELECTION_INFO
- PCONSOLE_SELECTION_INFO
MS-HAID:
- '\_win32\_console\_selection\_info\_str'
- base.console\_selection\_info\_str
- consoles.console\_selection\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9530b249-8db4-4516-9cc8-2b452c6751f9
topic_type:
- apiref
api_name:
- CONSOLE_SELECTION_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: aaf1cfaea2a8822c142aab87f6dcf1b022b7160c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038366"
---
# <a name="console_selection_info-structure"></a>主控台 \_ 選取 \_ 資訊結構

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

包含主控台選項的資訊。

## <a name="syntax"></a>語法

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

## <a name="members"></a>成員

**dwFlags**  
選取指標。 這個成員可以是下列一或多個值。

| 值 | 意義 |
|-|-|
| **CONSOLE_MOUSE_DOWN** 0x0008 | 滑鼠已關閉。 使用者正在使用滑鼠主動調整選取矩形。 |
| **CONSOLE_MOUSE_SELECTION** 0x0004 | 使用滑鼠選取。 如果是 off，則使用者會 `conhost.exe` 以鍵盤選取操作標示模式。 |
| **CONSOLE_NO_SELECTION** 0x0000 | 沒有選取專案。 |
| **CONSOLE_SELECTION_IN_PROGRESS** 0x0001 | 選取範圍已開始。 如果選取滑鼠，通常不會發生此 `CONSOLE_SELECTION_NOT_EMPTY` 旗標。 如果選擇鍵盤，則在輸入標記模式，但使用者仍在流覽至初始位置時，就會發生這種情況。 |
| **CONSOLE_SELECTION_NOT_EMPTY** 0x0002 | 選取範圍矩形不是空的。 *DwSelectionAnchor* 和 *srSelection* 的承載有效。  |

**dwSelectionAnchor**  
指定選取範圍錨點的 [**COORD**](coord-str.md) 結構（以字元為單位）。

**srSelection**  
指定選取矩形的 [**小型 \_ 矩形**](small-rect-str.md) 結構。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | \[僅限 WINDOWS XP desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2003 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi3 .h (via WinCon，包括 Windows .h)  |

## <a name="see-also"></a>請參閱

[**COORD**](coord-str.md)

[**GetConsoleSelectionInfo**](getconsoleselectioninfo.md)

[**小型 \_ 矩形**](small-rect-str.md)

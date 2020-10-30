---
title: WINDOW_BUFFER_SIZE_RECORD 結構
description: 請參閱 WINDOW_BUFFER_SIZE_RECORD 結構的參考資訊，其中描述主控台螢幕緩衝區大小的變更。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- wincontypes/WINDOW_BUFFER_SIZE_RECORD
- wincon/WINDOW_BUFFER_SIZE_RECORD
- WINDOW_BUFFER_SIZE_RECORD
- wincontypes/PWINDOW_BUFFER_SIZE_RECORD
- wincon/PWINDOW_BUFFER_SIZE_RECORD
- PWINDOW_BUFFER_SIZE_RECORD
MS-HAID:
- '\_win32\_window\_buffer\_size\_record\_str'
- base.window\_buffer\_size\_record\_str
- consoles.window\_buffer\_size\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f2875e8-aa09-455b-a923-7cc388525b98
topic_type:
- apiref
api_name:
- WINDOW_BUFFER_SIZE_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 355482dfd162e2c29944d53e5b17b0315ea15950
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039266"
---
# <a name="window_buffer_size_record-structure"></a>視窗 \_ 緩衝區 \_ 大小 \_ 記錄結構

描述主控台螢幕緩衝區大小的變更。

## <a name="syntax"></a>語法

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

## <a name="members"></a>成員

**dwSize**  
[**COORD**](coord-str.md)結構，其中包含主控台螢幕緩衝區的大小、字元資料格資料行和資料列。

## <a name="remarks"></a>備註

當主控台處於視窗感知模式時，緩衝區大小事件就會放在輸入緩衝區中 ( **啟用 \_ 視窗 \_ 輸入** ) 。

## <a name="examples"></a>範例

如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | WinConTypes .h (via WinCon，包括 Windows .h)  |

## <a name="see-also"></a>請參閱

[**COORD**](coord-str.md)

[**輸入 \_ 記錄**](input-record-str.md)

[**ReadConsoleInput**](readconsoleinput.md)

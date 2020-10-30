---
title: CONSOLE_HISTORY_INFO 結構
description: 請參閱有關 CONSOLE_HISTORY_INFO 結構的參考資訊，其中包含主控台歷程記錄的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/CONSOLE_HISTORY_INFO
- wincon/CONSOLE_HISTORY_INFO
- CONSOLE_HISTORY_INFO
- consoleapi3/PCONSOLE_HISTORY_INFO
- wincon/PCONSOLE_HISTORY_INFO
- PCONSOLE_HISTORY_INFO
MS-HAID:
- base.console\_history\_info
- consoles.console\_history\_info
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: df7d2f12-5299-47ed-b1f6-2db903dba81b
topic_type:
- apiref
api_name:
- CONSOLE_HISTORY_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 24d41dca61146cc3e835f405889400ae0d168e7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039216"
---
# <a name="console_history_info-structure"></a>主控台歷程 \_ 記錄 \_ 資訊結構

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

包含主控台歷程記錄的相關資訊。

## <a name="syntax"></a>語法

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

## <a name="members"></a>成員

**cbSize**  
結構的大小（以位元組為單位）。 將這個成員設定為 `sizeof(CONSOLE_HISTORY_INFO)` 。

**HistoryBufferSize**  
每個記錄緩衝區中保留的命令數目。

**NumberOfHistoryBuffers**  
為此主控台進程保留的記錄緩衝區數目。

**dwFlags**  
此參數可以是零或以下值。

| 值 | 意義 |
|-|-|
| **HISTORY_NO_DUP_FLAG** 0x1 | 重複的專案將不會儲存在歷程記錄緩衝區中。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | \[僅限 Windows Vista 桌面應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2008 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi3 .h (via WinCon，包括 Windows .h)  |

## <a name="see-also"></a>請參閱

[**GetConsoleHistoryInfo**](getconsolehistoryinfo.md)

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)

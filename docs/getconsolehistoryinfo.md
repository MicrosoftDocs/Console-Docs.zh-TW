---
title: GetConsoleHistoryInfo 函式
description: 請參閱 GetConsoleHistoryInfo 函式的參考資訊，此函式會抓取呼叫進程主控台的歷程記錄設定。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetConsoleHistoryInfo
- wincon/GetConsoleHistoryInfo
- GetConsoleHistoryInfo
MS-HAID:
- base.getconsolehistoryinfo
- consoles.getconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 145008b3-8a4a-4e6a-9144-ee787ce90ef4
topic_type:
- apiref
api_name:
- GetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 8335b7e23ffec0e894221f97f2c01be5b081d31f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038026"
---
# <a name="getconsolehistoryinfo-function"></a>GetConsoleHistoryInfo 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

抓取呼叫進程主控台的歷程記錄設定。

## <a name="syntax"></a>語法

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a>參數

*lpConsoleHistoryInfo* \[擴展\]  
[**主控台歷程 \_ 記錄 \_ 資訊**](console-history-info.md)結構的指標，此結構會接收呼叫進程主控台的歷程記錄設定。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

如果呼叫進程不是主控台進程，此函式會失敗，並將最後一個錯誤設定為 **\_ \_ 拒絕存取錯誤** 。

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | \[僅限 Windows Vista 桌面應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2008 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi3 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>請參閱

[主控台功能](console-functions.md)

[**主控台歷程 \_ 記錄 \_ 資訊**](console-history-info.md)

[**SetConsoleHistoryInfo**](setconsolehistoryinfo.md)

---
title: SetConsoleHistoryInfo 函式
description: 為呼叫進程的 Windows 主控台設定歷程記錄設定。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/SetConsoleHistoryInfo
- wincon/SetConsoleHistoryInfo
- SetConsoleHistoryInfo
MS-HAID:
- base.setconsolehistoryinfo
- consoles.setconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: db180f53-aa3c-4a91-bc3e-9f3f0bb7ab01
topic_type:
- apiref
api_name:
- SetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 3c2dcce41994929292253793fe94512ab7bc5a01
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357648"
---
# <a name="setconsolehistoryinfo-function"></a>SetConsoleHistoryInfo 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

設定呼叫進程主控台的歷程記錄設定。

## <a name="syntax"></a>語法

```C
BOOL WINAPI SetConsoleHistoryInfo(
  _In_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a>參數

*lpConsoleHistoryInfo* \[在\]  
[**主控台歷程 \_ 記錄 \_ 資訊**](console-history-info.md)結構的指標，其中包含進程主控台的歷程記錄設定。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

如果呼叫進程不是主控台進程，此函式會失敗，並將最後一個錯誤碼設定 **為 \_ \_ 拒絕存取錯誤**。

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | \[僅限 Windows Vista 桌面應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2008 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi3 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

[**主控台歷程 \_ 記錄 \_ 資訊**](console-history-info.md)

[**GetConsoleHistoryInfo**](getconsolehistoryinfo.md)
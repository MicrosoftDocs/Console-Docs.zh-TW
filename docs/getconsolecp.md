---
title: GetConsoleCP 函式
description: 抓取與呼叫進程相關聯的主控台所使用的輸入字碼頁。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/GetConsoleCP
- wincon/GetConsoleCP
- GetConsoleCP
MS-HAID:
- '\_win32\_getconsolecp'
- base.getconsolecp
- consoles.getconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9e0af6d9-0f5c-45b3-a686-22449d26de47
topic_type:
- apiref
api_name:
- GetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: fd581c1f11f457054257e1e36e55b726f48b34fb
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358458"
---
# <a name="getconsolecp-function"></a>GetConsoleCP 函式

抓取與呼叫進程相關聯的主控台所使用的輸入字碼頁。 主控台會使用其輸入字碼頁面，將鍵盤輸入轉譯成對應的字元值。

## <a name="syntax"></a>語法

```C
UINT WINAPI GetConsoleCP(void);
```

## <a name="parameters"></a>參數

此函式沒有參數。

## <a name="return-value"></a>傳回值

傳回值是可識別字碼頁的程式碼。 如需識別碼的清單，請參閱 [字碼頁識別碼](/windows/win32/intl/code-page-identifiers)。

如果傳回值為零，則函數會失敗。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

字碼頁會將256字元碼對應至個別字元。 不同的字碼頁包含不同的特殊字元，一般而言是針對語言或語言群組進行自訂。 若要取得字碼頁的詳細資訊（包括其名稱），請參閱 [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) 函數。

若要設定主控台的輸入字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 函數。 若要設定及查詢主控台的輸出字碼頁，請使用 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 和 [**GetConsoleOutputCP**](getconsoleoutputcp.md) 函數。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | ConsoleApi.h (透過 WinCon.h，包括 Windows.h) |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>另請參閱

[主控台字碼頁](console-code-pages.md)

[主控台函式](console-functions.md)

[**GetConsoleOutputCP**](getconsoleoutputcp.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)
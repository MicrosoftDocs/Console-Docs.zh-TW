---
title: GetConsoleOutputCP 函式
description: 抓取與呼叫進程相關聯的主控台所使用的輸出字碼頁。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/GetConsoleOutputCP
- wincon/GetConsoleOutputCP
- GetConsoleOutputCP
MS-HAID:
- '\_win32\_getconsoleoutputcp'
- base.getconsoleoutputcp
- consoles.getconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c23706c7-ce17-4825-a494-20ca44534d45
topic_type:
- apiref
api_name:
- GetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 30276765b35e9179767fa4e82fc40643ee3b2558
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038816"
---
# <a name="getconsoleoutputcp-function"></a>GetConsoleOutputCP 函式

抓取與呼叫進程相關聯的主控台所使用的輸出字碼頁。 主控台會使用其輸出字碼頁，將各種輸出函式所寫入的字元值轉譯為主控台視窗中顯示的影像。

## <a name="syntax"></a>語法

```C
UINT WINAPI GetConsoleOutputCP(void);
```

## <a name="parameters"></a>參數

此函式沒有參數。

## <a name="return-value"></a>傳回值

傳回值是可識別字碼頁的程式碼。 如需識別碼的清單，請參閱 [字碼頁識別碼](https://msdn.microsoft.com/library/windows/desktop/dd317756)。

如果傳回值為零，則函數會失敗。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

字碼頁會將256字元碼對應至個別字元。 不同的字碼頁包含不同的特殊字元，一般而言是針對語言或語言群組進行自訂。 若要取得字碼頁的詳細資訊（包括其名稱），請參閱 [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) 函數。

若要設定主控台的輸出字碼頁，請使用 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函數。 若要設定及查詢主控台的輸入字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 和 [**GetConsoleCP**](getconsolecp.md) 函數。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>請參閱

[主控台字碼頁](console-code-pages.md)

[主控台功能](console-functions.md)

[**GetConsoleCP**](getconsolecp.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

---
title: SetConsoleOutputCP 函式
description: 設定與呼叫進程相關聯的主控台所使用的輸出字碼頁。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleOutputCP
- wincon/SetConsoleOutputCP
- SetConsoleOutputCP
MS-HAID:
- '\_win32\_setconsoleoutputcp'
- base.setconsoleoutputcp
- consoles.setconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0b41e66b-ca19-4d69-9f39-92da158344ef
topic_type:
- apiref
api_name:
- SetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: abe04e2be5256097e19742bfbc8566c3ab613c4d
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357518"
---
# <a name="setconsoleoutputcp-function"></a>SetConsoleOutputCP 函式

設定與呼叫進程相關聯的主控台所使用的輸出字碼頁。 主控台會使用其輸出字碼頁，將各種輸出函式所寫入的字元值轉譯為主控台視窗中顯示的影像。

## <a name="syntax"></a>語法

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a>參數

*wCodePageID* \[在\]  
要設定的字碼頁識別碼。 如需詳細資訊，請參閱＜備註＞。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

字碼頁會將256字元碼對應至個別字元。 不同的字碼頁包含不同的特殊字元，一般而言是針對語言或語言群組進行自訂。

如果目前的字型是固定音調的 Unicode 字型， **SetConsoleOutputCP** 會將字元值的對應變更為字型的字元組，而不是每次呼叫時載入個別的字型。 這會影響在主控台視窗中顯示擴充字元 (ASCII 值大於 127) 的方式。 但是，如果目前的字型是點陣字型， **SetConsoleOutputCP** 就不會影響擴充字元的顯示方式。

若要尋找作業系統所安裝或支援的字碼頁，請使用 [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) 函數。 本機電腦上可用的字碼頁識別碼也會儲存在登錄的下列機碼底下：

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

不過，最好使用 [EnumSystemCodePages](/windows/win32/api/winnls/nf-winnls-enumsystemcodepagesa) 來列舉字碼頁，因為不同版本的 Windows 中的登錄可能不同。
若要判斷特定字碼頁是否有效，請使用 [IsValidCodePage](/windows/win32/api/winnls/nf-winnls-isvalidcodepage) 函數。 若要取得字碼頁的詳細資訊（包括其名稱），請使用 [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) 函數。 如需可用字碼頁識別碼的清單，請參閱 [字碼頁識別碼](/windows/win32/intl/code-page-identifiers)。

若要判斷主控台的目前輸出字碼頁，請使用 [**GetConsoleOutputCP**](getconsoleoutputcp.md) 函數。 若要設定和抓取主控台的輸入字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 和 [**GetConsoleCP**](getconsolecp.md) 函數。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>另請參閱

[主控台字碼頁](console-code-pages.md)

[主控台函式](console-functions.md)

[**GetConsoleCP**](getconsolecp.md)

[**GetConsoleOutputCP**](getconsoleoutputcp.md)

[**SetConsoleCP**](setconsolecp.md)
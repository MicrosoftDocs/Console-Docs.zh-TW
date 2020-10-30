---
title: SetConsoleCP 函式
description: 設定與呼叫進程相關聯的主控台所使用的輸入字碼頁。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleCP
- wincon/SetConsoleCP
- SetConsoleCP
MS-HAID:
- '\_win32\_setconsolecp'
- base.setconsolecp
- consoles.setconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a1a9ba5-c792-491d-ae51-979f462dcb53
topic_type:
- apiref
api_name:
- SetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 644f4d925b31da94f42a465d4bce21bb2dc2ecf9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039406"
---
# <a name="setconsolecp-function"></a>SetConsoleCP 函式

設定與呼叫進程相關聯的主控台所使用的輸入字碼頁。 主控台會使用其輸入字碼頁面，將鍵盤輸入轉譯成對應的字元值。

## <a name="syntax"></a>語法

```C
BOOL WINAPI SetConsoleCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a>參數

*wCodePageID* \[在\]  
要設定的字碼頁識別碼。 如需詳細資訊，請參閱＜備註＞。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

字碼頁會將256字元碼對應至個別字元。 不同的字碼頁包含不同的特殊字元，一般而言是針對語言或語言群組進行自訂。

若要尋找作業系統所安裝或支援的字碼頁，請使用 [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) 函數。 本機電腦上可用的字碼頁識別碼也會儲存在登錄的下列機碼底下：

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

不過，最好使用 [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) 來列舉字碼頁，因為不同版本的 Windows 中的登錄可能不同。

若要判斷特定字碼頁是否有效，請使用 [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) 函數。 若要取得字碼頁的詳細資訊（包括其名稱），請使用 [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) 函數。 如需可用字碼頁識別碼的清單，請參閱 [字碼頁識別碼](https://msdn.microsoft.com/library/windows/desktop/dd317756)。

若要判斷主控台的目前輸入字碼頁，請使用 [**GetConsoleCP**](getconsolecp.md) 函數。 若要設定和取出主控台的輸出字碼頁，請使用 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 和 [**GetConsoleOutputCP**](getconsoleoutputcp.md) 函式。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>請參閱

[主控台字碼頁](console-code-pages.md)

[主控台功能](console-functions.md)

[**GetConsoleCP**](getconsolecp.md)

[**GetConsoleOutputCP**](getconsoleoutputcp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

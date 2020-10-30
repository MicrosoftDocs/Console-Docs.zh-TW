---
title: GetConsoleAliasExes 函式
description: 使用定義的主控台別名，抓取所有可執行檔的名稱。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetConsoleAliasExes
- wincon/GetConsoleAliasExes
- GetConsoleAliasExes
- consoleapi3/GetConsoleAliasExesA
- wincon/GetConsoleAliasExesA
- GetConsoleAliasExesA
- consoleapi3/GetConsoleAliasExesW
- wincon/GetConsoleAliasExesW
- GetConsoleAliasExesW
MS-HAID:
- base.getconsolealiasexes
- consoles.getconsolealiasexes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c229de09-cfa6-4829-9c9a-8ff63500eaf4
topic_type:
- apiref
api_name:
- GetConsoleAliasExes
- GetConsoleAliasExesA
- GetConsoleAliasExesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0e818c8ecee8ac777f7cc3cf2394d8846bebd034
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038076"
---
# <a name="getconsolealiasexes-function"></a>GetConsoleAliasExes 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

使用定義的主控台別名，抓取所有可執行檔的名稱。

## <a name="syntax"></a>語法

```C
DWORD WINAPI GetConsoleAliasExes(
  _Out_ LPTSTR lpExeNameBuffer,
  _In_  DWORD  ExeNameBufferLength
);
```

## <a name="parameters"></a>參數

*lpExeNameBuffer* \[擴展\]  
接收可執行檔名稱之緩衝區的指標。

*ExeNameBufferLength* \[在\]  
*LpExeNameBuffer* 所指向的緩衝區大小（以位元組為單位）。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

若要判斷 *lpExeNameBuffer* 緩衝區所需的大小，請使用 [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) 函數。

若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0501 或更新版本。 如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi3 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |
| Unicode 和 ANSI 名稱 | **GetConsoleAliasExesW** (Unicode) 和 **GetConsoleAliasExesA** (ANSI)  |

## <a name="see-also"></a>請參閱

[**AddConsoleAlias**](addconsolealias.md)

[主控台別名](console-aliases.md)

[主控台功能](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliasExesLength**](getconsolealiasexeslength.md)

[**GetConsoleAliases**](getconsolealiases.md)

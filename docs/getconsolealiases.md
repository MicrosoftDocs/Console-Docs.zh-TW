---
title: GetConsoleAliases 函式
description: 針對指定的可執行檔，抓取所有已定義的主控台別名。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetConsoleAliases
- wincon/GetConsoleAliases
- GetConsoleAliases
- consoleapi3/GetConsoleAliasesA
- wincon/GetConsoleAliasesA
- GetConsoleAliasesA
- consoleapi3/GetConsoleAliasesW
- wincon/GetConsoleAliasesW
- GetConsoleAliasesW
MS-HAID:
- base.getconsolealiases
- consoles.getconsolealiases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 92eefa4e-ffde-4886-afde-5aecf450b425
topic_type:
- apiref
api_name:
- GetConsoleAliases
- GetConsoleAliasesA
- GetConsoleAliasesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: a84579ce7bf27787e986ded2e1f21520f8d442b9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038116"
---
# <a name="getconsolealiases-function"></a>GetConsoleAliases 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

針對指定的可執行檔，抓取所有已定義的主控台別名。

## <a name="syntax"></a>語法

```C
DWORD WINAPI GetConsoleAliases(
  _Out_ LPTSTR lpAliasBuffer,
  _In_  DWORD  AliasBufferLength,
  _In_  LPTSTR lpExeName
);
```

## <a name="parameters"></a>參數

*lpAliasBuffer* \[擴展\]  
接收別名的緩衝區指標。

資料的格式如下： *source1.rc* = *Target1* \\ 0 *>source2* = *Target2* \\ 0 .。。 *SourceN* =*TargetN* \\0，其中 *N* 是已定義的主控台別名數目。

*AliasBufferLength* \[在\]  
*LpAliasBuffer* 所指向的緩衝區大小（以位元組為單位）。

*lpExeName* \[在\]  
要取出其別名的可執行檔。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

若要判斷 *lpExeName* 緩衝區所需的大小，請使用 [**GetConsoleAliasesLength**](getconsolealiaseslength.md) 函數。

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
| Unicode 和 ANSI 名稱 | **GetConsoleAliasesW** (Unicode) 和 **GetConsoleAliasesA** (ANSI)  |

## <a name="see-also"></a>請參閱

[**AddConsoleAlias**](addconsolealias.md)

[主控台別名](console-aliases.md)

[主控台功能](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliasesLength**](getconsolealiaseslength.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)

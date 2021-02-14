---
title: AddConsoleAlias 函式
description: 請參閱 AddConsoleAlias 函式的參考資訊，此函式會定義指定之可執行檔的主控台別名。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/AddConsoleAlias
- consoleapi3/AddConsoleAliasA
- consoleapi3/AddConsoleAliasW
- wincon/AddConsoleAlias
- wincon/AddConsoleAliasA
- wincon/AddConsoleAliasW
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
MS-HAID:
- base.addconsolealias
- consoles.addconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e4072c3c-cf32-4992-847e-efdb846e5784
topic_type:
- apiref
api_name:
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 9ff901615fa2a17ee9902bd028a2f63ee6b7a4b4
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357868"
---
# <a name="addconsolealias-function"></a>AddConsoleAlias 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

定義指定之可執行檔的主控台別名。

## <a name="syntax"></a>語法

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

## <a name="parameters"></a>參數

*來源* \[在\]  
要對應至 *目標* 所指定之文字的主控台別名。

*目標* \[在\]  
要取代為 *來源* 的文字。 如果此參數為 **Null**，則會移除主控台別名。

*ExeName* \[在\]  
要定義的主控台別名之可執行檔的名稱。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為 **TRUE**。

如果函式失敗，則傳回值為 **FALSE**。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0501 或更新版本。 如需詳細資訊，請參閱 [使用 Windows 標頭](/windows/win32/winprog/using-the-windows-headers)。

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="examples"></a>範例

如需範例，請參閱 [主控台別名](console-aliases.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | ConsoleApi3 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode 與 ANSI 名稱 | **AddConsoleAliasW** (Unicode) 和 **AddConsoleAliasA** (ANSI)  |

## <a name="see-also"></a>另請參閱

[主控台別名](console-aliases.md)

[主控台函式](console-functions.md)

[**GetConsoleAlias**](getconsolealias.md)

[**GetConsoleAliases**](getconsolealiases.md)

[**GetConsoleAliasExes**](getconsolealiasexes.md)
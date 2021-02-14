---
title: AllocConsole 函式
description: 請參閱 AllocConsole 函式的參考資訊，此函式會為呼叫程序配置新的主控台。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/AllocConsole
- wincon/AllocConsole
- AllocConsole
MS-HAID:
- '\_win32\_allocconsole'
- base.allocconsole
- consoles.allocconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bdf3bf2f-8eb8-4ba6-bf3a-a67b29dffda2
topic_type:
- apiref
api_name:
- AllocConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 3b48570424a4c60a56094f5c41934f9946f67203
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357858"
---
# <a name="allocconsole-function"></a>AllocConsole 函式

為呼叫程序配置新的主控台。

## <a name="syntax"></a>語法

```C
BOOL WINAPI AllocConsole(void);
```

## <a name="parameters"></a>參數

此函式沒有參數。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

一個程序只能與一個主控台相關聯，因此，如果呼叫程序已經有主控台，**AllocConsole** 函式就會失敗。 程序可以使用 [**FreeConsole**](freeconsole.md) 函式將其本身從目前的主控台卸離，然後呼叫 **AllocConsole** 來建立新的主控台，或呼叫 [**AttachConsole**](attachconsole.md) 來連結至另一個主控台。

如果呼叫程序建立了子程序，則子程序會繼承新的主控台。

**AllocConsole** 會初始化新主控台的標準輸入、標準輸出和標準錯誤控制代碼。 標準輸入控制代碼是主控台輸入緩衝區的控制代碼，而標準輸出和標準錯誤控制代碼則是主控台畫面緩衝區的控制代碼。 若要取得這些控制代碼，請使用 [**GetStdHandle**](getstdhandle.md) 函式。

此函式的主要用途是讓圖形使用者介面 (GUI) 應用程式用來建立主控台視窗。 GUI 應用程式會在沒有主控台的情況下進行初始化。 除非是建立為卸離的程序 (呼叫 [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) 函式搭配 **DETACHED\_PROCESS** 旗標)，否則主控台應用程式會使用主控台進行初始化。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | ConsoleApi.h (透過 WinCon.h，包括 Windows.h) |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

[主控台](consoles.md)

[**AttachConsole**](attachconsole.md)

[**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)

[**FreeConsole**](freeconsole.md)

[**GetStdHandle**](getstdhandle.md)
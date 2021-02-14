---
title: AttachConsole 函式
description: 請參閱 AttachConsole 函式的參考資訊，此函式會將呼叫進程附加至指定進程的主控台。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: a1be050dccc0c77b6ad448cc45e87906a115d82c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357838"
---
# <a name="attachconsole-function"></a>AttachConsole 函式

將呼叫進程附加至指定進程的主控台做為用戶端應用程式。

## <a name="syntax"></a>語法

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

## <a name="parameters"></a>參數

*dwProcessId* \[在\]  
要使用其主控台的進程識別碼。 此參數可以是下列其中一個值。

| 值 | 意義 |
|-|-|
| *pid* | 使用指定進程的主控台。 |
| **附加 \_父 \_ 進程**`(DWORD)-1` | 使用目前進程父系的主控台。 |

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

一個進程最多可以附加至一個主控台。 如果呼叫的進程已附加至主控台，則傳回的錯誤碼會是 **\_ \_ 拒絕存取** () 錯誤 `5` 。 如果指定的進程沒有主控台，則傳回的錯誤碼會是 **錯誤不正確 \_ \_ 控制碼** (`6`) 。 如果指定的處理常式不存在，則傳回的錯誤碼會是 **錯誤 \_ 不正確 \_ 參數** (`87`) 。

進程可以使用 [**FreeConsole**](freeconsole.md) 函式，從其主控台卸離本身。 如果有其他進程共用主控台，主控台就不會終結，但呼叫 **FreeConsole** 的進程無法參考它。 當最後一個附加至它的進程終止或呼叫 **FreeConsole** 時，主控台就會關閉。 在進程呼叫 **FreeConsole** 之後，它就可以呼叫 [**AllocConsole**](allocconsole.md) 函式來建立新的主控台或 **AttachConsole** ，以附加至另一個主控台。

這項功能主要適用于與 [**/SUBSYSTEM： WINDOWS**](/cpp/build/reference/subsystem-specify-subsystem)連結的應用程式，這表示在輸入程式的 main 方法之前，不需要主控台。 在該實例中，使用 [**GetStdHandle**](getstdhandle.md) 抓取的標準處理常式在啟動時可能會無效，直到呼叫 **AttachConsole** 為止。 例外狀況是，如果應用程式是由其父進程的控制碼繼承啟動的。

若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為 `0x0501` 或更新版本。 如需詳細資訊，請參閱 [使用 Windows 標頭](/windows/win32/winprog/using-the-windows-headers)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | \[僅限 WINDOWS XP desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2003 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi.h (透過 WinCon.h，包括 Windows.h) |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

[主控台](consoles.md)

[**AllocConsole**](allocconsole.md)

[**FreeConsole**](freeconsole.md)

[**GetConsoleProcessList**](getconsoleprocesslist.md)
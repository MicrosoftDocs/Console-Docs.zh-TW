---
title: FreeConsole 函式
description: 請參閱 FreeConsole 函式的參考資訊，此函式會從其主控台卸離呼叫進程。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/FreeConsole
- wincon/FreeConsole
- FreeConsole
MS-HAID:
- '\_win32\_freeconsole'
- base.freeconsole
- consoles.freeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6c525325-696e-4d8b-8337-cbf9e31c900c
topic_type:
- apiref
api_name:
- FreeConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: af4382026b8e6455319e16ee21255fbc9352e3cd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039016"
---
# <a name="freeconsole-function"></a>FreeConsole 函式

從其主控台卸離呼叫進程。

## <a name="syntax"></a>語法

```C
BOOL WINAPI FreeConsole(void);
```

## <a name="parameters"></a>參數

此函式沒有參數。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

一個進程最多可以附加至一個主控台。 如果呼叫進程尚未附加到主控台，則傳回的錯誤碼會是 **錯誤 \_ 不正確 \_ 參數** (87) 。

進程可以使用 **FreeConsole** 函式，從其主控台卸離本身。 如果有其他進程共用主控台，主控台就不會終結，但呼叫 **FreeConsole** 的進程無法參考它。 當最後一個附加至它的進程終止或呼叫 **FreeConsole** 時，主控台就會關閉。 在進程呼叫 **FreeConsole** 之後，它就可以呼叫 [**AllocConsole**](allocconsole.md) 函式來建立新的主控台或 [**AttachConsole**](attachconsole.md) ，以附加至另一個主控台。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>請參閱

[**AllocConsole**](allocconsole.md)

[**AttachConsole**](attachconsole.md)

[主控台功能](console-functions.md)

[機](consoles.md)

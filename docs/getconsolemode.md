---
title: GetConsoleMode 函式
description: 抓取主控台之輸入緩衝區的目前輸入模式，或主控台螢幕緩衝區目前的輸出模式。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/GetConsoleMode
- wincon/GetConsoleMode
- GetConsoleMode
MS-HAID:
- '\_win32\_getconsolemode'
- base.getconsolemode
- consoles.getconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 49adf618-196d-4490-93ca-cd177807f58e
topic_type:
- apiref
api_name:
- GetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 54667d92509687111cb562f517d488c8adbc2181
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038868"
---
# <a name="getconsolemode-function"></a>GetConsoleMode 函式

抓取主控台之輸入緩衝區的目前輸入模式，或主控台螢幕緩衝區目前的輸出模式。

## <a name="syntax"></a>語法

```C
BOOL WINAPI GetConsoleMode(
  _In_  HANDLE  hConsoleHandle,
  _Out_ LPDWORD lpMode
);
```

## <a name="parameters"></a>參數

*hConsoleHandle* \[在\]  
主控台輸入緩衝區或主控台螢幕緩衝區的控制碼。 控制碼必須具有 **一般 \_ 讀取** 許可權。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpMode* \[擴展\]  
變數的指標，此變數會接收指定緩衝區的目前模式。

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

若要變更控制台的 i/o 模式，請呼叫 [**SetConsoleMode**](setconsolemode.md) 函式。

## <a name="examples"></a>範例

如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>請參閱

[主控台功能](console-functions.md)

[主控台模式](console-modes.md)

[**ReadConsole**](readconsole.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleMode**](setconsolemode.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

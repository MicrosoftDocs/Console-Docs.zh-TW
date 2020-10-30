---
title: GenerateConsoleCtrlEvent 函式
description: 將指定的信號傳送至主控台進程群組，該群組會共用與呼叫進程相關聯的主控台。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/GenerateConsoleCtrlEvent
- wincon/GenerateConsoleCtrlEvent
- GenerateConsoleCtrlEvent
MS-HAID:
- '\_win32\_generateconsolectrlevent'
- base.generateconsolectrlevent
- consoles.generateconsolectrlevent
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ed392d97-6fd0-4256-a783-bc7d27d01a10
topic_type:
- apiref
api_name:
- GenerateConsoleCtrlEvent
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: f074ad87676673221d34461e8bae484895781f56
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038136"
---
# <a name="generateconsolectrlevent-function"></a>GenerateConsoleCtrlEvent 函式

將指定的信號傳送至主控台進程群組，該群組會共用與呼叫進程相關聯的主控台。

## <a name="syntax"></a>語法

```C
BOOL WINAPI GenerateConsoleCtrlEvent(
  _In_ DWORD dwCtrlEvent,
  _In_ DWORD dwProcessGroupId
);
```

## <a name="parameters"></a>參數

*dwCtrlEvent* \[在\]  
要產生的信號類型。 這個參數可以是下列其中一個值。

| 值 | 意義 |
|-|-|
| **CTRL_C_EVENT** 0 | 產生 CTRL + C 信號。 無法產生進程群組的這個信號。 如果 *dwProcessGroupId* 為非零值，則此函式會成功，但是在指定的進程群組內，進程將不會收到 CTRL + C 信號。 |
| **CTRL_BREAK_EVENT** 1 | 產生 CTRL + BREAK 信號。 |

*dwProcessGroupId* \[在\]  
要接收信號之進程群組的識別碼。 在對 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)函式的呼叫中指定了 **建立 \_ 新的 \_ 進程 \_ 群組** 旗標時，就會建立進程群組。 新進程的處理序識別碼也是新進程群組的進程群組識別碼。 進程群組包含根進程下階的所有進程。 只有群組中與呼叫進程共用相同主控台的進程會收到信號。 換句話說，如果群組中的進程會建立新的主控台，該進程就不會收到信號，也不會有其子系。

如果此參數為零，則會在共用呼叫進程主控台的所有進程中產生信號。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

**GenerateConsoleCtrlEvent** 會在目標群組中呼叫進程的控制項處理常式函式。 所有主控台進程都有一個呼叫 [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) 函式的預設處理函式。 主控台處理常式可以使用 [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) 函數來安裝或移除其他處理常式函式。

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) 也可以啟用可繼承的屬性，使呼叫進程忽略 CTRL + C 信號。 如果 **GenerateConsoleCtrlEvent** 將 CTRL + C 信號傳送給已啟用這個屬性的進程，就不會呼叫該處理常式的處理常式函式。 CTRL + BREAK 信號一律會導致呼叫處理函式。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>請參閱

[主控台控制處理常式](console-control-handlers.md)

[主控台功能](console-functions.md)

[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)

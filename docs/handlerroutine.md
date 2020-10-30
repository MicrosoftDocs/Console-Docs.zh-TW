---
title: HandlerRoutine 回呼函式
description: 搭配 SetConsoleCtrlHandler 函數使用的應用程式定義函數。 主控台進程會使用此函式來處理處理常式所接收的控制信號。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/HandlerRoutine
- wincon/HandlerRoutine
- HandlerRoutine
MS-HAID:
- '\_win32\_handlerroutine'
- base.handlerroutine
- consoles.handlerroutine
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2e8732fa-7dfd-415b-b2fc-c27a400496f2
topic_type:
- apiref
api_name:
- HandlerRoutine
api_location:
- WinCon.h
api_type:
- UserDefined
ms.openlocfilehash: d078000b7c0acee73593543058f2195befc6f5e2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037746"
---
# <a name="handlerroutine-callback-function"></a>HandlerRoutine 回呼函式

搭配 [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) 函數使用的應用程式定義函數。 主控台進程會使用此函式來處理處理常式所接收的控制信號。 收到信號時，系統會在進程中建立新的執行緒，以執行函式。

**PHANDLER \_ 常式** 類型會定義此回呼函數的指標。 **HandlerRoutine** 是應用程式定義函數名稱的預留位置。

## <a name="syntax"></a>語法

```C
BOOL WINAPI HandlerRoutine(
  _In_ DWORD dwCtrlType
);
```

## <a name="parameters"></a>參數

*dwCtrlType* \[在\]  
處理常式接收的控制項信號類型。 這個參數可以是下列其中一個值。

| 值 | 意義 |
|-|-|
| **CTRL_C_EVENT** 0 | <kbd>CTRL</kbd> + 從鍵盤輸入或 **[GenerateConsoleCtrlEvent](generateconsolectrlevent.md)** 函式所產生的信號收到了 CTRL <kbd>C</kbd>信號。 |
| **CTRL_BREAK_EVENT** 1 | <kbd>CTRL</kbd> + 從鍵盤輸入或 **[GenerateConsoleCtrlEvent](generateconsolectrlevent.md)** 所產生的信號收到了 CTRL <kbd>中斷</kbd>信號。 |
| **CTRL_CLOSE_EVENT** 2 | 當使用者關閉主控台 (在主控台視窗的 [視窗] 功能表上按一下 [ **關閉** ]，或按一下工作管理員) 中的 [ **結束** 工作] 按鈕命令時，系統傳送給連接至主控台之所有進程的信號。 |
| **CTRL_LOGOFF_EVENT** 5 | 當使用者登出時，系統傳送給所有主控台進程的信號。 此信號不會指出正在登出的使用者，因此不會進行任何假設。<br /><br />請注意，只有服務會收到此信號。 互動式應用程式會在登出時終止，因此當系統傳送此信號時，不會出現這些應用程式。 |
| **CTRL_SHUTDOWN_EVENT** 6 | 系統正在關閉時，系統所傳送的信號。 當系統傳送此信號時，不會出現互動式應用程式，因此在這種情況下，只能使用服務來接收。 服務也有自己的關機事件通知機制。 如需詳細資訊，請參閱 **[處理常式](https://msdn.microsoft.com/library/windows/desktop/ms683240)** 。<br /><br />此信號也可以由使用 **[GenerateConsoleCtrlEvent](generateconsolectrlevent.md)** 的應用程式產生。 |

## <a name="return-value"></a>傳回值

如果函式處理控制項信號，則應該傳回 **TRUE** 。 如果傳回 **FALSE** ，則會使用此處理程式的處理常式清單中的下一個處理常式函數。

## <a name="remarks"></a>備註

由於系統會在執行處理常式函式的進程中建立新執行緒，因此進程中的另一個執行緒可能會終止處理常式函數。 請務必將進程中的執行緒與處理函式的執行緒同步處理。

每個主控台進程都有自己的 **HandlerRoutine** 函式清單。 一開始，此清單只包含呼叫 [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)的預設處理函式。 主控台處理常式會藉由呼叫 [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) 函式來新增或移除其他處理函式，而不會影響其他進程的處理常式函式清單。 當主控台進程接收到任何控制信號時，會在最後一次註冊的第一個呼叫的基礎上呼叫其處理函式，直到其中一個處理常式傳回 **TRUE** 為止。 如果沒有任何處理程式傳回 **TRUE** ，則會呼叫預設處理常式。

**Ctrl \_ CLOSE \_ 事件** 、 **ctrl \_ 登出 \_ 事件** 和 **ctrl \_ SHUTDOWN \_ 事件** 信號讓處理常式有機會在終止前進行清除。 **HandlerRoutine** 可以執行任何必要的清除，然後採取下列其中一項動作：

- 呼叫 [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) 函式以終止進程。
- 傳回 **FALSE** 。 如果沒有任何已註冊的處理常式函式傳回 **TRUE** ，則預設處理常式會終止進程。
- 傳回 **TRUE** 。 在此情況下，不會呼叫任何其他處理常式函式，而且系統會終止進程。

處理常式可以使用 [**SetProcessShutdownParameters**](https://msdn.microsoft.com/library/windows/desktop/ms686227) 函式，防止系統在登出或關閉期間，向使用者顯示對話方塊。 在這種情況下，系統會在 **HandlerRoutine** 傳回 **TRUE** 或超時期間結束時終止進程。

當主控台應用程式以服務的形式執行時，它會收到修改過的預設主控台控制處理常式。 這個修改過的處理常式不會在處理 **ctrl \_ 登出 \_ 事件** 和 **ctrl \_ 關機 \_ 事件** 信號時呼叫 [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) 。 這可讓服務在使用者登出之後繼續執行。 如果服務安裝本身的主控台控制處理常式，則會在預設處理常式之前呼叫此處理程式。 如果已安裝的處理常式在處理 **CTRL \_ 登出 \_ 事件** 信號時呼叫 **ExitProcess** ，則服務會在使用者登出時結束。

請注意，協力廠商程式庫或 DLL 可以為您的應用程式安裝主控台控制處理常式。 如果有的話，這個處理常式會覆寫預設的處理常式，而且可能會在使用者登出時讓應用程式結束。

## <a name="timeouts"></a>逾時

| 事件                  | 情況                   | 逾時                                                     |
|------------------------|---------------------------------|-------------------------------------------------------------|
| `CTRL_CLOSE_EVENT`     | _任何_                           | 系統參數 `SPI_GETHUNGAPPTIMEOUT` ，5000毫秒            |
| `CTRL_LOGOFF_EVENT`    | _快速_ [1] | 登錄機碼 `CriticalAppShutdownTimeout` 或500毫秒          |
| `CTRL_LOGOFF_EVENT`    | _以上皆非_             | 系統參數 `SPI_GETWAITTOKILLTIMEOUT` ，5000毫秒         |
| `CTRL_SHUTDOWN_EVENT`  | **服務進程**             | 系統參數 `SPI_GETWAITTOKILLSERVICETIMEOUT` ，20000ms |
| `CTRL_SHUTDOWN_EVENT`  | _快速_ [1] | 登錄機碼 `CriticalAppShutdownTimeout` 或500毫秒          |
| `CTRL_SHUTDOWN_EVENT`  | _以上皆非_             | 系統參數 `SPI_GETWAITTOKILLTIMEOUT` ，5000毫秒         |
| `CTRL_C`, `CTRL_BREAK` | _任何_                           | **無 timeout**                                              |

_[1]：永不使用「快速」事件，但仍有程式碼可支援它們。_

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi .h (via WinCon，包括 Windows .h)  |

## <a name="see-also"></a>請參閱

[主控台控制處理常式](console-control-handlers.md)

[主控台功能](console-functions.md)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetProcessShutdownParameters**](https://msdn.microsoft.com/library/windows/desktop/ms683221)

[**SetConsoleCtrlHandler**](setconsolectrlhandler.md)

[**SetProcessShutdownParameters**](https://msdn.microsoft.com/library/windows/desktop/ms686227)

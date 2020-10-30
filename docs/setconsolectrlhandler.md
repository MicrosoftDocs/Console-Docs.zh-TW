---
title: SetConsoleCtrlHandler 函式
description: 從呼叫進程的處理常式函式清單中，加入或移除應用程式定義的 HandlerRoutine 函數。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/SetConsoleCtrlHandler
- wincon/SetConsoleCtrlHandler
- SetConsoleCtrlHandler
MS-HAID:
- '\_win32\_setconsolectrlhandler'
- base.setconsolectrlhandler
- consoles.setconsolectrlhandler
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6fc64265-1403-45ea-925c-c5eb31d56734
topic_type:
- apiref
api_name:
- SetConsoleCtrlHandler
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 1c5c67bc5900a36bb50c0da90516fab0cec2e366
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039416"
---
# <a name="setconsolectrlhandler-function"></a>SetConsoleCtrlHandler 函式

從呼叫進程的處理常式函式清單中，加入或移除應用程式定義的 [**HandlerRoutine**](handlerroutine.md) 函數。

如果未指定任何處理程式函式，此函式會設定可繼承的屬性，以判斷呼叫進程是否會忽略<kbd>CTRL</kbd># + <kbd>C</kbd>信號。

## <a name="syntax"></a>語法

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

## <a name="parameters"></a>參數

*HandlerRoutine* \[在中，選擇性\]  
要加入或移除的應用程式定義 [**HandlerRoutine**](handlerroutine.md) 函數的指標。 這個參數可以是 **Null** 。

*新增* \[在\]  
如果此參數為 **TRUE** ，則會加入處理常式;如果為 **FALSE** ，則會移除處理常式。

如果 *HandlerRoutine* 參數為 **Null** ， **則 TRUE** 值會導致呼叫進程忽略 <kbd>ctrl</kbd> + <kbd>c</kbd>輸入，而 **FALSE** 值會還原 <kbd>ctrl</kbd> + <kbd>c</kbd>輸入的正常處理。 忽略或處理<kbd>CTRL</kbd> + <kbd>C</kbd>的這個屬性會由子進程繼承。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

此函式會提供類似于 [**WM \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) 為圖形化應用程式提供訊息提取的主控台應用程式和服務的通知。 您也可以從圖形化應用程式使用這個函式，但不保證會在來自 **WM \_ QUERYENDSESSION** 的通知之前送達。

每個主控台進程都有自己的應用程式定義 [**HandlerRoutine**](handlerroutine.md)函式清單，可處理 <kbd>ctrl +</kbd> + <kbd>C</kbd>和 <kbd>ctrl</kbd> + <kbd>中斷</kbd>信號。 當使用者關閉主控台、登出或關閉系統時，處理常式函式也會處理系統所產生的信號。 一開始，每個進程的處理常式清單只包含呼叫 [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) 函數的預設處理函式。 主控台處理常式會藉由呼叫 **SetConsoleCtrlHandler** 函式來新增或移除其他處理函式，而不會影響其他進程的處理常式函式清單。 當主控台進程收到任何控制信號時，會在最後一次註冊的第一個呼叫的基礎上呼叫其處理函式，直到其中一個處理常式傳回為止 `TRUE` 。 如果沒有任何處理程式傳回 `TRUE` ，則會呼叫預設處理常式。

針對主控台進程， <kbd>ctrl +</kbd> + <kbd>C</kbd>和 <kbd>ctrl</kbd> + <kbd>break</kbd>按鍵組合通常會視為信號 ( **ctrl \_ c \_ 事件** 和 **ctrl \_ break \_ 事件** ) 。 當具有鍵盤焦點的主控台視窗收到<kbd>ctrl</kbd> + <kbd>C</kbd>或<kbd>ctrl</kbd> + <kbd>中斷</kbd>時，信號通常會傳遞至共用該主控台的所有進程。

<kbd>CTRL</kbd> +<kbd>BREAK</kbd>一律會被視為信號，但一般的<kbd>CTRL</kbd> + <kbd>C</kbd>行為可透過下列三種方式來變更，以防止呼叫處理函式：

- [**SetConsoleMode**](setconsolemode.md)函式可以停用主控台輸入緩衝區的 [ **啟用已處理的 \_ \_ 輸入** ] 模式，因此會將 <kbd>CTRL</kbd> + <kbd>C</kbd>回報為鍵盤輸入而非信號。
- 使用 **Null** 和 **TRUE** 引數呼叫 **SetConsoleCtrlHandler** ，會導致呼叫進程略過 <kbd>CTRL</kbd> + <kbd>C</kbd>信號。 這個屬性是由子進程繼承的，但可以由任何程式啟用或停用，而不會影響現有的進程。
- 如果正在調試主控台進程，且 <kbd>CTRL</kbd> + 未停用 CTRL <kbd>C</kbd>信號，系統會產生一個 **DBG \_ 控制項 \_ C** 例外狀況。 只有偵錯工具的優點會引發這個例外狀況，而且應用程式不應該使用例外狀況處理常式來處理它。 如果偵錯工具處理例外狀況，應用程式將不會注意到<kbd>CTRL</kbd> + <kbd>C</kbd>，但有一個例外狀況：可提供警示等候將會終止。 如果偵錯工具在未處理的情況下傳遞例外狀況，則會將<kbd>CTRL</kbd> + <kbd>C</kbd>傳遞給主控台進程並視為信號，如先前所述。

主控台處理常式可以使用 [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)函式，將 <kbd>ctrl</kbd> + <kbd>C</kbd>或 <kbd>ctrl</kbd> + <kbd>中斷</kbd>信號傳送到主控台進程群組。

系統會在使用者關閉主控台、登出或關閉系統時，產生 **ctrl \_ CLOSE \_ 事件** 、 **ctrl \_ 登出 \_ 事件** 和 **ctrl \_ SHUTDOWN \_ 事件** 信號，讓進程有機會在終止前進行清除。 主控台函式或任何呼叫主控台函式的 C 執行時間函式，在處理先前提及的三個信號中的任一個時，可能無法可靠地運作。 原因是，您可能會在執行處理信號處理常式之前呼叫部分或所有的內部主控台清除常式。

**Windows 7、Windows 8、Windows 8.1 和 Windows 10：**

如果主控台應用程式載入 gdi32.dll 或 user32.dll 程式庫，則在呼叫 **SetConsoleCtrlHandler** 時指定的 [**HandlerRoutine**](handlerroutine.md)函式不會被呼叫 **ctrl \_ 登出 \_ 事件** 和 **ctrl \_ SHUTDOWN \_ 事件** 事件。 作業系統會辨識載入 gdi32.dll 或 user32.dll 為 Windows 應用程式的處理常式，而不是主控台應用程式。 這種行為也會發生在主控台應用程式中，這些應用程式不會直接呼叫 gdi32.dll 或 user32.dll 中的函式，而是呼叫函式（例如 [Shell](https://msdn.microsoft.com/library/windows/desktop/bb776426) 函式），進而在 gdi32.dll 或 user32.dll 中呼叫函數。

若要在使用者登出或裝置在這些情況下關閉時接收事件，請在主控台應用程式中建立隱藏的視窗，然後處理隱藏視窗所接收的 [**wm \_ QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) 和 [**wm \_ ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) 視窗訊息。 您可以呼叫 [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) 方法，並將 *dwExStyle* 參數設定為0，以建立隱藏視窗。

## <a name="examples"></a>範例

如需範例，請參閱 [註冊控制項處理常式函數](registering-a-control-handler-function.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |
| Unicode 和 ANSI 名稱 | |

## <a name="see-also"></a>請參閱

[主控台控制處理常式](console-control-handlers.md)

[主控台功能](console-functions.md)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetConsoleMode**](getconsolemode.md)

[**HandlerRoutine**](handlerroutine.md)

[**SetConsoleMode**](setconsolemode.md)

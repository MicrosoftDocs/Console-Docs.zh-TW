---
title: SetConsoleCtrlHandler 函式
description: 從呼叫程序的處理常式函式清單中新增或移除應用程式定義的 HandlerRoutine 函式。
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
ms.localizationpriority: high
ms.openlocfilehash: 208eebc92b718fed9856a48dfaf5cbebdaddc1e1
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420267"
---
# <a name="setconsolectrlhandler-function"></a>SetConsoleCtrlHandler 函式

從呼叫程序的處理常式函式清單中新增或移除應用程式定義的 [**HandlerRoutine**](handlerroutine.md) 函式。

如果未指定處理常式函式，該函式就會設定可繼承的屬性，以決定呼叫程序是否會忽略 <kbd>CTRL</kbd>+<kbd>C</kbd> 訊號。

## <a name="syntax"></a>語法

```C
BOOL WINAPI SetConsoleCtrlHandler(
  _In_opt_ PHANDLER_ROUTINE HandlerRoutine,
  _In_     BOOL             Add
);
```

## <a name="parameters"></a>參數

*HandlerRoutine* \[輸入、選擇性\]  
指標，指示要加入或移除應用程式定義的 [**HandlerRoutine**](handlerroutine.md) 函式。 此參數可以是 **Null**。

*Add* \[輸入\]  
如果此參數是 **TRUE**，則會加入處理常式；如果是 **FALSE**，則會移除處理常式。

如果 *HandlerRoutine* 參數是 **Null**，**TRUE** 值就會使呼叫程序忽略 <kbd>CTRL</kbd>+<kbd>C</kbd> 的輸入，而 **FALSE** 值則會還原 <kbd>CTRL</kbd>+<kbd>C</kbd> 輸入的正常處理程序。 忽略或處理 <kbd>CTRL</kbd>+<kbd>C</kbd> 的此屬性會由子程序繼承。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

針對 [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) 使用訊息幫浦為圖形應用程式提供的通知，此函式會為主控台應用程式和服務提供類似的通知。 您也可以從圖形應用程式中使用此函式，但不保證其會在 **WM\_QUERYENDSESSION** 的通知之前抵達。

每個主控台程序都會自備應用程式定義的 [**HandlerRoutine**](handlerroutine.md)清單，可處理 <kbd>CTRL</kbd>+<kbd>C</kbd> 和 <kbd>CTRL</kbd>+<kbd>BREAK</kbd> 函式。 當使用者關閉主控台、登出或關閉系統時，處理常式函式也會處理系統所產生的訊號。 一開始，每個程序的處理常式清單只會包含預設的處理常式函式，該函式會呼叫 [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) 函式。 主控台程序會藉由呼叫 **SetConsoleCtrlHandler** 函式來新增或移除其他處理常式函式，而這不會影響其他程序的處理常式函式清單。 主控台程序會在收到任何控制訊號時，依據「最後註冊的先呼叫」原則來呼叫其處理常式函式，直到其中一個處理常式傳回 `TRUE` 為止。 如果沒有任何處理常式傳回 `TRUE`，則會呼叫預設的處理常式。

對於主控台程序，<kbd>CTRL</kbd>+<kbd>C</kbd> 和 <kbd>CTRL</kbd>+<kbd>BREAK</kbd> 按鍵組合通常會被視為訊號 (**CTRL\_C\_EVENT** 和 **CTRL\_BREAK\_EVENT**)。 當具有鍵盤焦點的主控台視窗收到 <kbd>CTRL</kbd>+<kbd>C</kbd> 或 <kbd>CTRL</kbd>+<kbd>BREAK</kbd> 時，訊號通常會傳遞至所有共用該主控台的程序。

<kbd>CTRL</kbd>+<kbd>BREAK</kbd> 一律會被視為訊號，但是典型的 <kbd>CTRL</kbd>+<kbd>C</kbd> 行為可透過三種方式來變更，以防止呼叫處理常式函式：

- [**SetConsoleMode**](setconsolemode.md) 函式可以停用主控台輸入緩衝區的 **ENABLE\_PROCESSED\_INPUT** 模式，因此會將 <kbd>CTRL</kbd>+<kbd>C</kbd> 回報為鍵盤輸入，而非訊號。
- 使用 **Null** 和 **TRUE** 引數呼叫 **SetConsoleCtrlHandler** 會使呼叫程序忽略 <kbd>CTRL</kbd>+<kbd>C</kbd> 訊號。 此屬性會由子程序繼承，但是可由任何程序啟用或停用，而不會影響現有的程序。
- 如果正在對主控台程序進行偵錯，而且尚未停用 <kbd>CTRL</kbd>+<kbd>C</kbd> 訊號，則系統會產生 **DBG\_CONTROL\_C** 例外狀況。 此例外狀況的引發只會有益於偵錯工具，應用程式不應使用例外狀況處理常式來處理此狀況。 如果偵錯工具處理了此例外狀況，應用程式將不會注意到 <kbd>CTRL</kbd>+<kbd>C</kbd>，但會有一個例外：可警告的等待會終止。 如果偵錯工具傳遞未處理的例外狀況，則 <kbd>CTRL</kbd>+<kbd>C</kbd> 會傳遞至主控台程序並視為訊號，如先前所述。

主控台程序可以使用 [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) 函式來將 <kbd>CTRL</kbd>+<kbd>C</kbd> 或 <kbd>CTRL</kbd>+<kbd>BREAK</kbd> 訊號傳送到主控台程序群組。

當使用者關閉主控台、登出或關閉系統時，系統會產生 **CTRL\_CLOSE\_EVENT**、**CTRL\_LOGOFF\_EVENT** 及 **CTRL\_SHUTDOWN\_EVENT** ，讓程序有機會在終止前進行清除。 在處理上述三個訊號中的任何一個時，主控台函式或任何呼叫主控台函式的任何 C 執行階段函式可能無法可靠地運作。 這可能是因為執行程序訊號處理常式之前，已經呼叫部分或所有內部主控台清理常式。

**Windows 7、Windows 8、Windows 8.1 和 Windows 10：**

如果主控台應用程式載入 gdi32.dll 或 user32.dll 程式庫，則發生 **CTRL\_LOGOFF\_EVENT** 和 **CTRL\_SHUTDOWN\_EVENT** 事件時，就不會呼叫您在呼叫 **SetConsoleCtrlHandler** 時指定的 [**HandlerRoutine**](handlerroutine.md) 函式。 作業系統會將載入 gdi32.dll 或 user32.dll 的程序辨識為 Windows 應用程式，而非主控台應用程式。 如果主控台應用程式不會直接呼叫 gdi32.dll 或 user32.dll 中的函式，也會發生這種行為，但呼叫 [Shell 函式](https://msdn.microsoft.com/library/windows/desktop/bb776426)之類的函式反而會呼叫 gdi32.dll 或 user32.dll 中的函式。

若要在因為這些情況造成使用者登出或關閉裝置時接收事件，請在您的主控台應用程式中建立隱藏視窗，然後處理已隱藏視窗接收的 [**WM\_QUERYENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376890) 和 [**WM\_ENDSESSION**](https://msdn.microsoft.com/library/windows/desktop/aa376889) 視窗訊息。 您可以藉由呼叫 [**CreateWindowEx**](https://msdn.microsoft.com/library/windows/desktop/ms632680) 方法，並將 *dwExStyle* 參數設定為 0，來建立隱藏視窗。

## <a name="examples"></a>範例

如需範例，請參閱[註冊控制處理常式函式](registering-a-control-handler-function.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | ConsoleApi.h (透過 WinCon.h，包括 Windows.h) |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode 與 ANSI 名稱 | |

## <a name="see-also"></a>另請參閱

[主控台控制處理常式](console-control-handlers.md)

[主控台函式](console-functions.md)

[**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)

[**GetConsoleMode**](getconsolemode.md)

[**HandlerRoutine**](handlerroutine.md)

[**SetConsoleMode**](setconsolemode.md)

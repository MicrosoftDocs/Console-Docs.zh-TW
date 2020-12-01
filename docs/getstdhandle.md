---
title: GetStdHandle 函式
description: " (標準輸入、標準輸出或標準錯誤) ，抓取指定標準裝置的控制碼。"
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- processenv/GetStdHandle
- winbase/GetStdHandle
- GetStdHandle
MS-HAID:
- '\_win32\_getstdhandle'
- base.getstdhandle
- consoles.getstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 23cd76e9-671a-48d0-9b82-2beda8917348
topic_type:
- apiref
api_name:
- GetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 42857417cedb661014de869536b798d29c9eb884
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420207"
---
# <a name="getstdhandle-function"></a>GetStdHandle 函式

 (標準輸入、標準輸出或標準錯誤) ，抓取指定標準裝置的控制碼。

## <a name="syntax"></a>語法

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a>參數

*nStdHandle* \[在\]  
標準裝置。 這個參數可以是下列其中一個值。

| 值 | 意義 |
|-|-|
| **STD_INPUT_HANDLE** (DWORD) -10 | 標準輸入設備。 一開始，這是主控台輸入緩衝區 `CONIN$` 。 |
| **STD_OUTPUT_HANDLE** (DWORD) -11 | 標準輸出裝置。 這一開始是使用中的主控台畫面緩衝區 `CONOUT$` 。 |
| **STD_ERROR_HANDLE** (DWORD) -12 | 標準錯誤裝置。 這一開始是使用中的主控台畫面緩衝區 `CONOUT$` 。 |

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值是指定之裝置的控制碼，或先前呼叫 [**SetStdHandle**](setstdhandle.md)所設定的重新導向控制碼。 控制碼具有 **一般 \_ 讀取** 和 **一般 \_ 寫入** 存取權限，除非應用程式已使用 **SetStdHandle** 來設定較少存取的標準控制碼。

如果函式失敗，則傳回值是 **不正確 \_ 控制碼 \_ 值**。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

如果應用程式沒有相關聯的標準控制碼（例如在互動式桌面上執行的服務），而且尚未將它們重新導向，則傳回值為 **Null**。

## <a name="remarks"></a>備註

**GetStdHandle** 所傳回的控制碼可供需要讀取或寫入主控台的應用程式使用。 建立主控台時，標準輸入控制碼是主控台輸入緩衝區的控制碼，而標準輸出和標準錯誤控制碼則是主控台的作用中螢幕緩衝區的控制碼。 這些控制碼可供 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 和 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 函式使用，或由任何可存取主控台輸入緩衝區或螢幕緩衝區的主控台函式使用 (例如， [**ReadConsoleInput**](readconsoleinput.md)、 [**WriteConsole**](writeconsole.md)或 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數) 。

呼叫 [**SetStdHandle**](setstdhandle.md)可能會重新導向進程的標準控制碼，在這種情況下， **GetStdHandle** 會傳回重新導向的控制碼。 如果已重新導向標準控制碼，您可以在對 CreateFile 函式的 `CONIN$` 呼叫中 [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)指定值，以取得主控台輸入緩衝區的控制碼。 同樣地，您可以指定 `CONOUT$` 值以取得主控台的作用中螢幕緩衝區的控制碼。

當建立應用程式時，將傳遞給連結器的 [**/SUBSYSTEM**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem) 旗標設定，會決定如何在 main 方法的專案上設定標準處理常式。 指定 **/SUBSYSTEM：主控台** 要求作業系統在啟動時以主控台會話填滿控制碼，如果父系尚未依繼承填滿標準控制碼表格。 相反地， **/SUBSYSTEM： WINDOWS** 表示應用程式不需要主控台，而且可能不會使用標準控點。 如需有關控制碼繼承的詳細資訊，請參閱 [**STARTF \_ USESTDHANDLES**](https://docs.microsoft.com/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa)的檔。

有些應用程式會在其宣告的子系統界限之外運作;比方說， **/SUBSYSTEM： WINDOWS** 應用程式可能會檢查/使用標準控制碼進行記錄或偵測，但以圖形化使用者介面正常運作。 這些應用程式必須在啟動時仔細探查標準控制碼的狀態，並使用 [**AttachConsole**](attachconsole.md)、 [**AllocConsole**](allocconsole.md)和 [**FreeConsole**](freeconsole.md) 來新增/移除主控台（如有需要）。

某些應用程式可能也會在繼承控制碼的類型上改變其行為。 您可以使用 [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype)來執行主控台、管道、檔案和其他專案之間的類型 Disambiguating。

### <a name="attachdetach-behavior"></a>附加/卸離行為

附加至新的主控台時，除非在進程建立期間指定了 **STARTF \_ USESTDHANDLES** ，否則一律會使用主控台控制碼來取代標準控制碼。

如果標準控制碼的現有值為 **Null**，或標準控制碼的現有值看起來像主控台 pseudohandle，控制碼就會取代為主控台控制碼。

當父系同時使用 [ **建立 \_ 新的 \_ 主控台** ] 和 [ **STARTF \_ USESTDHANDLES** ] 建立主控台進程時，除非標準控制碼的現有值為 **Null** 或主控台 pseudohandle，否則不會取代標準控制碼。

> [!NOTE]
>主控台處理常式 *必須* 以填滿的標準控點作為開頭，否則系統將會自動使用適當的控制碼來填滿新的主控台。 圖形化使用者介面 (GUI) 應用程式可以在沒有標準控制碼的情況下啟動，且不會自動填入。

## <a name="examples"></a>範例

如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ProcessEnv .h (via Winbase，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>另請參閱

[主控台功能](console-functions.md)

[主控台控制代碼](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetStdHandle**](setstdhandle.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

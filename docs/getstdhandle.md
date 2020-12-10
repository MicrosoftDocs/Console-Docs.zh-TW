---
title: GetStdHandle 函式
description: 擷取指定標準裝置的控制代碼 (標準輸入、標準輸出或標準錯誤)。
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
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420207"
---
# <a name="getstdhandle-function"></a>GetStdHandle 函式

擷取指定標準裝置的控制代碼 (標準輸入、標準輸出或標準錯誤)。

## <a name="syntax"></a>語法

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

## <a name="parameters"></a>參數

*nStdHandle* \[輸入\]  
標準裝置。 此參數可以是下列其中一個值。

| 值 | 意義 |
|-|-|
| **STD_INPUT_HANDLE** (DWORD) -10 | 標準輸入裝置。 一開始，這是主控台輸入緩衝區 `CONIN$`。 |
| **STD_OUTPUT_HANDLE** (DWORD) -11 | 標準輸出裝置。 一開始，這是作用中的主控台畫面緩衝區 `CONOUT$`。 |
| **STD_ERROR_HANDLE** (DWORD) -12 | 標準錯誤裝置。 一開始，這是作用中的主控台畫面緩衝區 `CONOUT$`。 |

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值是指定裝置的控制代碼，或是先前呼叫 [**SetStdHandle**](setstdhandle.md) 時所設定的重新導向控制代碼。 除非應用程式已使用 **SetStdHandle** 將標準控制代碼設定為具有較低存取權，否則控制代碼會具有 **GENERIC\_READ** 和 **GENERIC\_WRITE** 存取權限。

如果函式失敗，則傳回值是 **INVALID\_HANDLE\_VALUE**。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

如果應用程式沒有相關聯的標準控制代碼 (例如在互動式桌面上執行的服務)，而且尚未將其重新導向，則傳回值會是 **Null**。

## <a name="remarks"></a>備註

**GetStdHandle** 傳回的控制代碼可供需要讀取或寫入主控台的應用程式使用。 建立主控台時，標準輸入控制代碼是主控台輸入緩衝區的控制代碼，而標準輸出和標準錯誤控制代碼則是主控台作用中畫面緩衝區的控制代碼。 這些控制代碼可由 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 和 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 函式使用，或由任何存取主控台輸入緩衝區或畫面緩衝區的主控台函式使用 (例如 [**ReadConsoleInput**](readconsoleinput.md)、[**WriteConsole**](writeconsole.md)或 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函式)。

對 [**SetStdHandle**](setstdhandle.md) 發出的呼叫可能會將程序的標準控制代碼重新導向，在此情況下，**GetStdHandle** 會傳回重新導向的控制代碼。 如果標準控制代碼已重新導向，您可以在呼叫 [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) 函式時指定 `CONIN$` 值，以取得主控台輸入緩衝區的控制代碼。 同樣地，您可以指定 `CONOUT$` 值，以取得主控台作用中畫面緩衝區的控制代碼。

建立應用程式時，傳遞至連結器的 [ **/SUBSYSTEM**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem) 旗標設定會決定在 main 方法進入點上的程序標準控制代碼。 指定 **/SUBSYSTEM:CONSOLE** 會要求作業系統在啟動時以主控台工作階段填滿控制代碼 (如果父系尚未透過繼承來填滿標準控制代碼資料表)。 相反地， **/SUBSYSTEM:WINDOWS** 則是表示應用程式不需要主控台，而且很可能不會使用標準控制代碼。 如需有關控制代碼繼承的詳細資訊，請參閱 [**STARTF\_USESTDHANDLES**](https://docs.microsoft.com/windows/win32/api/processthreadsapi/ns-processthreadsapi-startupinfoa) 的文件。

有些應用程式會在其宣告的子系統界限外運作；例如， **/SUBSYSTEM:WINDOWS** 應用程式可能會檢查/使用標準控制代碼進行記錄或偵錯，但通常會搭配圖形使用者介面運作。 這些應用程式必須在啟動時仔細探查標準控制代碼的狀態，並使用 [**AttachConsole**](attachconsole.md)、[**AllocConsole**](allocconsole.md) 和 [**FreeConsole**](freeconsole.md) 來新增/移除主控台 (如有需要)。

某些應用程式也可能會改變其在所繼承控制代碼類型上的行為。 若要釐清主控台、管道、檔案和其他類型，可以使用 [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype) 來執行。

### <a name="attachdetach-behavior"></a>連結/卸離行為

連結至新的主控台時，除非已在程序建立期間指定了 **STARTF\_USESTDHANDLES**，否則一律會使用主控台控制代碼取代標準控制代碼。

如果標準控制代碼的現有值為 **Null**，或標準控制代碼的現有值看起來像主控台 pseudohandle，則控制代碼會取代為主控台控制代碼。

當父系同時使用 **CREATE\_NEW\_CONSOLE** 和 **STARTF\_USESTDHANDLES** 來建立主控台程序時，除非標準控制代碼的現有值為 **Null** 或主控台 pseudohandle，否則不會取代標準控制代碼。

> [!NOTE]
>主控台程序「必須」從填滿標準控制代碼開始，否則新的主控台會自動以適當的控制代碼填入。 圖形使用者介面 (GUI) 應用程式可以在沒有標準控制代碼的情況下啟動，而且不會自動填入。

## <a name="examples"></a>範例

如需範例，請參閱[讀取輸入緩衝區事件](reading-input-buffer-events.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | ProcessEnv.h (透過 Winbase.h，包括 Windows.h) |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

[主控台控制代碼](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetStdHandle**](setstdhandle.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

---
title: WriteConsole 函式
description: 從目前的游標位置開始，將字元字串寫入主控台螢幕緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/WriteConsole
- wincon/WriteConsole
- WriteConsole
- consoleapi/WriteConsoleA
- wincon/WriteConsoleA
- WriteConsoleA
- consoleapi/WriteConsoleW
- wincon/WriteConsoleW
- WriteConsoleW
MS-HAID:
- '\_win32\_writeconsole'
- base.writeconsole
- consoles.writeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1a13d9ef-75a9-49fd-9717-207f18612b59
topic_type:
- apiref
api_name:
- WriteConsole
- WriteConsoleA
- WriteConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 426aa6711e46e0d5cda1eb1b7dab7b2b0b7156d6
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420287"
---
# <a name="writeconsole-function"></a>WriteConsole 函式

從目前的游標位置開始，將字元字串寫入主控台螢幕緩衝區。

## <a name="syntax"></a>語法

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[in\]  
主控台螢幕緩衝區的控點。 控點必須具有 **GENERIC\_WRITE** 存取權限。 如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpBuffer* \[in\]  
緩衝區的指標，其中包含要寫入主控台螢幕緩衝區的字元。 這應該是 `WriteConsoleA` 的 `char` 陣列，或 `WriteConsoleW` 的 `wchar_t` 陣列。

*nNumberOfCharsToWrite* \[in\]  
要寫入的字元數。 如果指定字元數的總大小超過可用的堆積，則函式會因為 **ERROR\_NOT\_ENOUGH\_MEMORY** 而失敗。

*lpNumberOfCharsWritten* \[out, optional\]  
變數的指標，可接收實際寫入的字元數。

*lpReserved* 已保留；必須是 **NULL**。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

**WriteConsole** 函式會在目前游標位置將字元寫入主控台螢幕緩衝區。 游標位置會在寫入字元時前進。 [**SetConsoleCursorPosition**](setconsolecursorposition.md) 函式會設定目前的游標位置。

字元是使用與主控台螢幕緩衝區相關聯的前景和背景色彩屬性來撰寫。 [**SetConsoleTextAttribute**](setconsoletextattribute.md) 函式會變更這些色彩。 若要判斷目前的色彩屬性和目前的游標位置，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)。

所有會影響 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 函式行為的輸入模式，在 **WriteConsole** 上具有相同的效果。 若要擷取及設定主控台螢幕緩衝區的輸出模式，請使用 [**GetConsoleMode**](getconsolemode.md) 和 [**SetConsoleMode**](setconsolemode.md) 函式。

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

如果 **WriteConsole** 搭配會重新導向至檔案的標準控點使用，則會失敗。 如果應用程式處理可重新導向的多語系輸出，請判斷輸出控點是否為主控台控點 (其中一種方法是呼叫 [**GetConsoleMode**](getconsolemode.md) 函式並檢查其是否成功)。 如果控點是主控台控點，請呼叫 **WriteConsole**。 如果控點不是主控台控點，系統就會將輸出重新導向，而且您應該呼叫 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 來執行 I/O。 請務必在 Unicode 純文字檔案前面加上位元組順序標記。 如需詳細資訊，請參閱[使用位元組順序標記](https://msdn.microsoft.com/library/windows/desktop/dd374101)。

雖然應用程式可以使用 ANSI 模式的 **WriteConsole** 來寫入 ANSI 字元，但除非已啟用「ANSI 逸出」或「虛擬終端機」序列，否則主控台不提供支援。 如需詳細資訊和作業系統版本適用性，請參閱 [**主控台虛擬終端機序列**](console-virtual-terminal-sequences.md)。

若未啟用當虛擬終端機逸出序列，主控台函式可以提供對等的功能。 如需詳細資訊，請參閱 [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)、[**SetConsoleTextAttribute**](setconsoletextattribute.md) 和 [**GetConsoleCursorInfo**](getconsolecursorinfo.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | ConsoleApi.h (透過 WinCon.h，包括 Windows.h) |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode 與 ANSI 名稱 | **WriteConsoleW** (Unicode) 和 **WriteConsoleA** (ANSI) |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**GetConsoleMode**](getconsolemode.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[輸入和輸出方法](input-and-output-methods.md)

[**ReadConsole**](readconsole.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleMode**](setconsolemode.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleTextAttribute**](setconsoletextattribute.md)

[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

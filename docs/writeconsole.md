---
title: WriteConsole 函式
description: 從目前的游標位置開始，將字元字串寫入至主控台畫面緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
ms.openlocfilehash: de5138326c0800016cf5ca6e3232f032abcd01de
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059511"
---
# <a name="writeconsole-function"></a>WriteConsole 函式


從目前的游標位置開始，將字元字串寫入至主控台畫面緩衝區。

<a name="syntax"></a>語法
------

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

<a name="parameters"></a>參數
----------

*hConsoleOutput* \[在\]  
主控台螢幕緩衝區的控制碼。 控制碼必須有 **一般 \_ 寫入** 存取權限。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpBuffer* \[在\]  
包含要寫入主控台螢幕緩衝區之字元的緩衝區指標。

*nNumberOfCharsToWrite* \[在\]  
要寫入的字元數。 如果指定字元數的總大小超過可用的堆積，則函式會失敗，並出現 **錯誤， \_ \_ \_ 記憶體不足**。

*lpNumberOfCharsWritten* \[out、optional\]  
變數的指標，此變數會接收實際寫入的字元數。

*lpReserved*   
保護必須是 **Null**。

<a name="return-value"></a>傳回值
------------

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

<a name="remarks"></a>備註
-------

**WriteConsole**函式會在目前游標位置的主控台螢幕緩衝區寫入字元。 資料指標位置會隨著寫入字元而前進。 [**SetConsoleCursorPosition**](setconsolecursorposition.md)函式會設定目前的游標位置。

字元是使用與主控台螢幕緩衝區相關聯的前景和背景色彩屬性來撰寫。 [**SetConsoleTextAttribute**](setconsoletextattribute.md)函式會變更這些色彩。 若要判斷目前的色彩屬性和目前的資料指標位置，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)。

所有影響 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 函式行為的輸入模式在 **WriteConsole**上都有相同的效果。 若要取出和設定主控台螢幕緩衝區的輸出模式，請使用 [**GetConsoleMode**](getconsolemode.md) 和 [**SetConsoleMode**](setconsolemode.md) 函式。

**WriteConsole**函式會從主控台的目前字碼頁使用 Unicode 字元或 ANSI 字元。 主控台的字碼頁一開始預設為系統的 OEM 字碼頁。 若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 或 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函式，或使用 **chcp** 或 **mode con cp select =** 命令。

如果搭配重新導向至檔案的標準控制碼使用， **WriteConsole**就會失敗。 如果應用程式處理可重新導向的多語系輸出，請判斷輸出控制碼是否為主控台控制碼 (其中一種方法是呼叫 [**GetConsoleMode**](getconsolemode.md) 函式，並檢查它是否成功) 。 如果控制碼是主控台控制碼，請呼叫 **WriteConsole**。 如果控制碼不是主控台控制碼，系統就會將輸出重新導向，而您應該呼叫 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 來執行 i/o。 請務必在 Unicode 純文字檔前面加上位元組順序標記。 如需詳細資訊，請參閱 [使用位元組順序標記](https://msdn.microsoft.com/library/windows/desktop/dd374101)。

雖然應用程式可以使用 ANSI 模式的 **WriteConsole** 來撰寫 ansi 字元，但主控台並不支援 ansi escape 序列。 但是，有些函式會提供對等的功能。 如需詳細資訊，請參閱 [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)、 [**SetConsoleTextAttribute**](setconsoletextattribute.md)和 [**GetConsoleCursorInfo**](getconsolecursorinfo.md)。

<a name="requirements"></a>規格需求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>最低支援的用戶端</p></td>
<td><p>Windows 2000 Professional [僅限桌面應用程式]</p></td>
</tr>
<tr class="even">
<td><p>最低支援的伺服器</p></td>
<td><p>Windows 2000 伺服器 [僅限桌面應用程式]</p></td>
</tr>
<tr class="odd">
<td><p>標頭</p></td>
<td>ConsoleApi .h (via Wincon，包括 Windows .h) </td>
</tr>
<tr class="even">
<td><p>程式庫</p></td>
<td>Kernel32.dll .lib</td>
</tr>
<tr class="odd">
<td><p>DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
<td><p>Unicode 和 ANSI 名稱</p></td>
<td><p><strong>WriteConsoleW</strong> (Unicode) 和 <strong>WriteConsoleA</strong> (ANSI) </p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另請參閱


[主控台功能](console-functions.md)

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

 

 





---
title: ReadConsole 函式
description: 從主控台輸入緩衝區讀取字元輸入，並將它從緩衝區中移除。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi/ReadConsole
- wincon/ReadConsole
- ReadConsole
- consoleapi/ReadConsoleA
- wincon/ReadConsoleA
- ReadConsoleA
- consoleapi/ReadConsoleW
- wincon/ReadConsoleW
- ReadConsoleW
MS-HAID:
- '\_win32\_readconsole'
- base.readconsole
- consoles.readconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1aa9ecac-a9b9-4e6d-9206-7a57013de657
topic_type:
- apiref
api_name:
- ReadConsole
- ReadConsoleA
- ReadConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 16287bec8e690e5d70483d6e6055e6badaca40ce
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059058"
---
# <a name="readconsole-function"></a>ReadConsole 函式


從主控台輸入緩衝區讀取字元輸入，並將它從緩衝區中移除。

<a name="syntax"></a>語法
------

```C
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

<a name="parameters"></a>參數
----------

*hConsoleInput* \[在\]  
主控台輸入緩衝區的控制碼。 控制碼必須具有 **一般 \_ 讀取** 許可權。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpBuffer* \[擴展\]  
緩衝區的指標，此緩衝區會接收從主控台輸入緩衝區讀取的資料。

*nNumberOfCharsToRead* \[在\]  
要讀取的字元數。 *LpBuffer*參數所指向的緩衝區大小應該至少是 `nNumberOfCharsToRead * sizeof(TCHAR)` 位元組。

*lpNumberOfCharsRead* \[擴展\]  
變數的指標，此變數會接收實際讀取的字元數。

*pInputControl* \[在中，選擇性\]  
[**主控台 \_ READCONSOLE \_ 控制項**](console-readconsole-control.md)結構的指標，指定控制字元以表示讀取作業結束。 這個參數可以是 **Null**。

此參數預設需要 Unicode 輸入。 若為 ANSI 模式，請將此參數設定為 **Null**。

<a name="return-value"></a>傳回值
------------

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

<a name="remarks"></a>備註
-------

**ReadConsole** 會從主控台的輸入緩衝區讀取鍵盤輸入。 它的行為類似于 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 函式，不同之處在于它可以讀取 Unicode (寬字元) 或 ANSI 模式。 若要讓應用程式維持一組與這兩種模式相容的一組來源，請使用 **ReadConsole** 而非 **ReadFile**。 雖然 **ReadConsole** 只能搭配主控台輸入緩衝區控制碼使用，但是 **ReadFile** 可以搭配其他控制碼使用， (例如檔案或管道) 。 如果搭配已重新導向為主控台控制碼以外的標準控制碼使用， **ReadConsole**就會失敗。

所有影響 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 行為的輸入模式在 **ReadConsole**上都有相同的效果。 若要取得和設定主控台輸入緩衝區的輸入模式，請使用 [**GetConsoleMode**](getconsolemode.md) 和 [**SetConsoleMode**](setconsolemode.md) 函式。

如果輸入緩衝區包含鍵盤事件以外的輸入事件 (例如滑鼠事件或視窗大小的事件) ，則會捨棄這些事件。 只有使用 [**ReadConsoleInput**](readconsoleinput.md) 函數才能讀取這些事件。

此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。 主控台的字碼頁一開始預設為系統的 OEM 字碼頁。 若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 或 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函式，或使用 **chcp** 或 **mode con cp select =** 命令。

*PInputControl*參數可以用來從讀取中啟用中繼假喚醒，以回應[**主控台 \_ READCONSOLE \_ 控制**](console-readconsole-control.md)結構中指定的檔案完成控制字元。 這項功能需要啟用命令延伸模組、標準輸出控制碼是主控台輸出控制碼，而輸入則是 Unicode。

**Windows Server 2003 和 WINDOWS XP/2000：** 不支援中繼讀取功能。

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
<td><p><strong>ReadConsoleW</strong> (Unicode) 和 <strong>ReadConsoleA</strong> (ANSI) </p></td>
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

[**主控台 \_ READCONSOLE \_ 控制項**](console-readconsole-control.md)

[**GetConsoleMode**](getconsolemode.md)

[輸入和輸出方法](input-and-output-methods.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleMode**](setconsolemode.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsole**](writeconsole.md)

 

 





---
title: GetStdHandle 函式
description: " (標準輸入、標準輸出或標準錯誤) ，抓取指定標準裝置的控制碼。"
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
ms.openlocfilehash: 613aacf4052e8e3b38c0a3e254ac4dd2b55ced5d
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059082"
---
# <a name="getstdhandle-function"></a>GetStdHandle 函式


 (標準輸入、標準輸出或標準錯誤) ，抓取指定標準裝置的控制碼。

<a name="syntax"></a>語法
------

```C
HANDLE WINAPI GetStdHandle(
  _In_ DWORD nStdHandle
);
```

<a name="parameters"></a>參數
----------

*nStdHandle* \[在\]  
標準裝置。 這個參數可以是下列其中一個值。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>值</th>
<th>意義</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD) -10</td>
<td><p>標準輸入設備。 一開始，這是主控台輸入緩衝區 CONIN $。</p></td>
</tr>
<tr class="even">
<td><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD) -11</td>
<td><p>標準輸出裝置。 一開始，這是使用中的主控台畫面緩衝區 CONOUT $。</p></td>
</tr>
<tr class="odd">
<td><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD) -12</td>
<td><p>標準錯誤裝置。 一開始，這是使用中的主控台畫面緩衝區 CONOUT $。</p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a>傳回值
------------

如果函式成功，則傳回值是指定之裝置的控制碼，或先前呼叫 [**SetStdHandle**](setstdhandle.md)所設定的重新導向控制碼。 控制碼具有 **一般 \_ 讀取** 和 **一般 \_ 寫入** 存取權限，除非應用程式已使用 **SetStdHandle** 來設定較少存取的標準控制碼。

如果函式失敗，則傳回值是 **不正確 \_ 控制碼 \_ 值**。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

如果應用程式沒有相關聯的標準控制碼（例如在互動式桌面上執行的服務），而且尚未將它們重新導向，則傳回值為 **Null**。

<a name="remarks"></a>備註
-------

**GetStdHandle**所傳回的控制碼可供需要讀取或寫入主控台的應用程式使用。 建立主控台時，標準輸入控制碼是主控台輸入緩衝區的控制碼，而標準輸出和標準錯誤控制碼則是主控台的作用中螢幕緩衝區的控制碼。 這些控制碼可供 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 和 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 函式使用，或由任何可存取主控台輸入緩衝區或螢幕緩衝區的主控台函式使用 (例如， [**ReadConsoleInput**](readconsoleinput.md)、 [**WriteConsole**](writeconsole.md)或 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數) 。

呼叫 [**SetStdHandle**](setstdhandle.md)可能會重新導向進程的標準控制碼，在這種情況下， **GetStdHandle** 會傳回重新導向的控制碼。 如果已重新導向標準控制碼，您可以在 [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) 函式的呼叫中指定 CONIN $ 值，以取得主控台輸入緩衝區的控制碼。 同樣地，您可以指定 CONOUT $ 值，以取得主控台的作用中螢幕緩衝區的控制碼。

### <a name="span-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanspan-idattach_detach_behaviorspanattachdetach-behavior"></a><span id="Attach_detach_behavior"></span><span id="attach_detach_behavior"></span><span id="ATTACH_DETACH_BEHAVIOR"></span>附加/卸離行為

附加至新的主控台時，除非在進程建立期間指定了 **STARTF \_ USESTDHANDLES** ，否則一律會使用主控台控制碼來取代標準控制碼。

如果標準控制碼的現有值為 **Null**，或標準控制碼的現有值看起來像主控台 pseudohandle，控制碼就會取代為主控台控制碼。

當父系同時使用 [ **建立 \_ 新的 \_ 主控台** ] 和 [ **STARTF \_ USESTDHANDLES** ] 建立主控台進程時，除非標準控制碼的現有值為 Null 或主控台 pseudohandle，否則不會取代標準控制碼。

<a name="examples"></a>範例
--------

如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。

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
<td>ProcessEnv .h (via Winbase，包括 Windows .h) </td>
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
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另請參閱


[主控台功能](console-functions.md)

[主控台控制碼](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetStdHandle**](setstdhandle.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 





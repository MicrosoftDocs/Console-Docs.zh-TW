---
title: AllocConsole 函式
description: 請參閱 AllocConsole 函式的參考資訊，此函式會為呼叫進程配置新的主控台。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi/AllocConsole
- wincon/AllocConsole
- AllocConsole
MS-HAID:
- '\_win32\_allocconsole'
- base.allocconsole
- consoles.allocconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bdf3bf2f-8eb8-4ba6-bf3a-a67b29dffda2
topic_type:
- apiref
api_name:
- AllocConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 2e06cdc82c4e58dd09b99fa08bf4917ad37b552f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059391"
---
# <a name="allocconsole-function"></a>AllocConsole 函式


配置呼叫進程的新主控台。

<a name="syntax"></a>語法
------

```C
BOOL WINAPI AllocConsole(void);
```

<a name="parameters"></a>參數
----------

此函式沒有參數。

<a name="return-value"></a>傳回值
------------

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

<a name="remarks"></a>備註
-------

進程只能與一個主控台相關聯，因此，如果呼叫的進程已經有主控台， **AllocConsole** 函式就會失敗。 進程可以使用 [**FreeConsole**](freeconsole.md) 函式，從其目前的主控台卸離本身，然後呼叫 **AllocConsole** 來建立新的主控台或 [**AttachConsole**](attachconsole.md) ，以附加至另一個主控台。

如果呼叫進程建立子進程，則子系會繼承新的主控台。

**AllocConsole** 會初始化新主控台的標準輸入、標準輸出和標準錯誤控制碼。 標準輸入控制碼是主控台輸入緩衝區的控制碼，而標準輸出和標準錯誤控制碼則是主控台螢幕緩衝區的控制碼。 若要取出這些控制碼，請使用 [**GetStdHandle**](getstdhandle.md) 函數。

這項功能主要是由圖形化使用者介面 (GUI) 應用程式用來建立主控台視窗。 GUI 應用程式會在沒有主控台的情況下初始化。 主控台應用程式會使用主控台來初始化，除非它們建立為卸離的進程 (藉由使用卸**離的 \_ 進程**旗標) 來呼叫[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)函數。

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
<td>ConsoleApi3 .h (via Wincon，包括 Windows .h) </td>
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

[機](consoles.md)

[**AttachConsole**](attachconsole.md)

[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[**FreeConsole**](freeconsole.md)

[**GetStdHandle**](getstdhandle.md)

 

 





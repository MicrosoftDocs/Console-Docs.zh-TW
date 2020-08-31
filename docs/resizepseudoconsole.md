---
title: ResizePseudoConsole 函式
description: 請參閱 ResizePseudoConsole 函式的參考資訊，此函式會將 pseudoconsole 的內部緩衝區大小調整為指定的大小。
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api，conpty，pseudoconsole
f1_keywords:
- consoleapi/ResizePseudoConsole
- ResizePseudoConsole
topic_type:
- apiref
api_name:
- ResizePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a4f6ff773538eda4d4c84c4b0bac2e647f6b80d8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059443"
---
# <a name="resizepseudoconsole-function"></a>ResizePseudoConsole 函式


將 pseudoconsole 的內部緩衝區大小調整為指定的大小。

<a name="syntax"></a>語法
------

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

<a name="parameters"></a>參數
----------

*hPC* \[在\]  
由 [CreatePseudoConsole](createpseudoconsole.md)開啟之作用中 psuedoconsole 的控制碼。

*大小* \[在\]  
視窗/緩衝區的大小（以字元數為單位），將用於此 pseudoconsole 的內部緩衝區。 

<a name="return-value"></a>傳回值
------------

類型： **HRESULT**

如果這個方法成功，它會傳回 **S_OK**。 否則，它會傳回 **HRESULT** 錯誤碼。

<a name="remarks"></a>備註
-------

此函數可以調整 pseudoconsole 會話中的內部緩衝區大小，以符合終端機端上所用的視窗/緩衝區大小。 這可確保使用 [主控台](console-functions.md) 函式進行通訊的附加命令列介面 (CUI) 應用程式將會在其呼叫中傳回正確的維度。

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
<td><p>Windows 10 1809 [僅限桌面應用程式]</p></td>
</tr>
<tr class="even">
<td><p>最低支援的伺服器</p></td>
<td><p>Windows Server 2019 [僅限桌面應用程式]</p></td>
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
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另請參閱

[Pseudoconsoles](pseudoconsoles.md)

[**CreatePseudoConsole**](createpseudoconsole.md)

[**ClosePseudoConsole**](closepseudoconsole.md)

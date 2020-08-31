---
title: ClosePseudoConsole 函式
description: 請參閱 ClosePseudoConsole 函式的參考資訊，此函式會從指定的控制碼關閉 pseudoconsole。
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api，conpty，pseudoconsole
topic_type:
- apiref
api_name:
- ClosePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 0674fa9c02c54c9476e2844da69895905865d6f4
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059359"
---
# <a name="closepseudoconsole-function"></a>ClosePseudoConsole 函式


從給定的控制碼關閉 pseudoconsole。

<a name="syntax"></a>語法
------

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC 
);
```

<a name="parameters"></a>參數
----------

*hPC* \[在\]  
由 [CreatePseudoConsole](createpseudoconsole.md)開啟之作用中 psuedoconsole 的控制碼。

<a name="return-value"></a>傳回值
------------

無

<a name="remarks"></a>備註
-------

在關閉 pseudoconsole 時，附加至會話的用戶端應用程式也會終止。

`hOutput`當呼叫此 API 時，最後繪製的框架可能會從 pseudoconsole 抵達。 呼叫端應該會清空通道緩衝區中的這項資訊，並將其呈現或捨棄。 若無法清空緩衝區，可能會導致關閉呼叫無限期等候，直到它被清空或通道以另一種方式中斷為止。

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

[**ResizePseudoConsole**](resizepseudoconsole.md)

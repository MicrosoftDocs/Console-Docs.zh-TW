---
title: SetConsoleWindowInfo 函式
description: 設定主控台螢幕緩衝區視窗的目前大小和位置。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/SetConsoleWindowInfo
- wincon/SetConsoleWindowInfo
- SetConsoleWindowInfo
MS-HAID:
- '\_win32\_setconsolewindowinfo'
- base.setconsolewindowinfo
- consoles.setconsolewindowinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad16a8fe-ca91-41d6-93b1-8cce6d54b1da
topic_type:
- apiref
api_name:
- SetConsoleWindowInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: ae09434a1fc67902d2160f4e66890f4392eac3f8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059279"
---
# <a name="setconsolewindowinfo-function"></a>SetConsoleWindowInfo 函式


設定主控台螢幕緩衝區視窗的目前大小和位置。

<a name="syntax"></a>語法
------

```C
BOOL WINAPI SetConsoleWindowInfo(
  _In_       HANDLE     hConsoleOutput,
  _In_       BOOL       bAbsolute,
  _In_ const SMALL_RECT *lpConsoleWindow
);
```

<a name="parameters"></a>參數
----------

*hConsoleOutput* \[在\]  
主控台螢幕緩衝區的控制碼。 控制碼必須具有 **一般 \_ 讀取** 許可權。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*bAbsolute* \[在\]  
如果此參數為 **TRUE**，座標會指定視窗的新左上角和右下角。 如果為 **FALSE**，則座標相對於目前的視窗邊角座標。

*lpConsoleWindow* \[在\]  
[**小 \_ 矩形**](small-rect-str.md)結構的指標，指定視窗的新左上角和右下角。

<a name="return-value"></a>傳回值
------------

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

<a name="remarks"></a>備註
-------

如果指定的視窗矩形延伸超過主控台螢幕緩衝區的界限，則函式會失敗。 這表示，如果*bAbsolute*為 FALSE，則*LpConsoleWindow*矩形的**top**和**left**成員 (或計算的上和左座標，) 不能小於零。 同樣地， **底部** 和 **右邊** 的成員 (或計算的右下座標) 不能大於 (螢幕緩衝區高度– 1) 和 (螢幕緩衝區寬度-1) 。 如果 **右邊** 的成員 (或計算的右座標) 小於或等於 **左邊** 的成員 (或計算的左座標) 或 **底部** 成員 (或計算下座標) 小於或等於 **最上層** 成員 (或計算出的最上層座標) ，則函式也會失敗。

針對具有多個螢幕緩衝區的主控台，變更一個螢幕緩衝區的視窗位置並不會影響其他螢幕緩衝區的視窗位置。

若要判斷螢幕緩衝區視窗目前的大小和位置，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數。 這個函式也會根據目前的螢幕緩衝區大小、目前的字型大小和螢幕大小，傳回視窗的大小上限。 [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)函式會傳回目前的字型和螢幕大小的最大視窗大小，但不會考慮主控台畫面緩衝區的大小。

**SetConsoleWindowInfo** 可以用來滾動視窗矩形的位置，而不需要變更其大小。

<a name="examples"></a>範例
--------

如需範例，請參閱 [滾動螢幕緩衝區視窗](scrolling-a-screen-buffer-s-window.md)。

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
<td>ConsoleApi2 .h (via Wincon，包括 Windows .h) </td>
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

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[滾動螢幕緩衝區](scrolling-the-screen-buffer.md)

[**小型 \_ 矩形**](small-rect-str.md)

 

 





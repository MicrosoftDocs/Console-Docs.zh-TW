---
title: WriteConsoleOutput 函式
description: 將字元和色彩屬性資料寫入主控台螢幕緩衝區中指定之字元資料格的矩形區塊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/WriteConsoleOutput
- wincon/WriteConsoleOutput
- WriteConsoleOutput
- consoleapi2/WriteConsoleOutputA
- wincon/WriteConsoleOutputA
- WriteConsoleOutputA
- consoleapi2/WriteConsoleOutputW
- wincon/WriteConsoleOutputW
- WriteConsoleOutputW
MS-HAID:
- '\_win32\_writeconsoleoutput'
- base.writeconsoleoutput
- consoles.writeconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a98b8118-97ce-4dd4-a337-122d4a76f232
topic_type:
- apiref
api_name:
- WriteConsoleOutput
- WriteConsoleOutputA
- WriteConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e2f84f5c072a8404b129e27bec3464363b9dd3d0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059051"
---
# <a name="writeconsoleoutput-function"></a>WriteConsoleOutput 函式


將字元和色彩屬性資料寫入主控台螢幕緩衝區中指定之字元資料格的矩形區塊。 要寫入的資料是取自來源緩衝區中指定位置的相對大小矩形區塊。

<a name="syntax"></a>語法
------

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

<a name="parameters"></a>參數
----------

*hConsoleOutput* \[在\]  
主控台螢幕緩衝區的控制碼。 控制碼必須有 **一般 \_ 寫入** 存取權限。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpBuffer* \[在\]  
要寫入主控台螢幕緩衝區的資料。 此指標會被視為 [**CHAR \_ 資訊**](char-info-str.md) 結構之二維陣列的來源，其大小是由 *dwBufferSize* 參數所指定。

*dwBufferSize* \[在\]  
*LpBuffer*參數所指向的緩衝區大小（以字元資料格為限）。 [**COORD**](coord-str.md)結構的**X**成員是資料行的數目;**Y**成員是資料列的數目。

*dwBufferCoord* \[在\]  
*LpBuffer*參數所指向之緩衝區中左上角資料格的座標。 [**COORD**](coord-str.md)結構的**X**成員是資料行，而**Y**成員是資料列。

*lpWriteRegion* \[in、out\]  
[**小 \_ RECT**](small-rect-str.md)結構的指標。 在輸入時，結構成員會指定要寫入的主控台螢幕緩衝區矩形左上角和右下角的座標。 在輸出時，結構成員會指定所使用的實際矩形。

<a name="return-value"></a>傳回值
------------

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

<a name="remarks"></a>備註
-------

**WriteConsoleOutput** 會將來源緩衝區和目的畫面緩衝區視為二維陣列， (資料格的資料行和資料列) 。 *LpWriteRegion*參數所指向的矩形，可指定要在主控台螢幕緩衝區中寫入之區塊的大小與位置。 相同大小的矩形位於*lpBuffer*陣列中*dwBufferCoord*參數座標的左上角儲存格。 從這個矩形和來源緩衝區矩形交集的資料格中的資料， (其維度是由 *dwBufferSize* 參數指定，) 會寫入至目的地矩形。

目的地矩形中的資料格，其對應的來源位置超出來源緩衝區矩形的界限，因此不會受到寫入作業的影響。 換句話說，這些是沒有資料可供寫入的儲存格。

在 **WriteConsoleOutput** 傳回之前，它會將 *lpWriteRegion* 的成員設定為受寫入操作影響的實際螢幕緩衝區矩形。 這個矩形會反映目的地矩形中的儲存格，而來源緩衝區中有對應的資料格，因為 **WriteConsoleOutput** 會將目的地矩形的維度裁剪到主控台螢幕緩衝區的界限。

如果 *lpWriteRegion* 所指定的矩形完全落在主控台螢幕緩衝區的界限之外，或對應的矩形完全位於來源緩衝區的界限之外，則不會寫入任何資料。 在此情況下，函式會傳回 *lpWriteRegion* 參數集所指向之結構的成員，讓 **右邊** 的成員小於 **左邊**，或 **底部** 的成員小於 **頂端**。 若要判斷主控台螢幕緩衝區的大小，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數。

**WriteConsoleOutput** 不會影響資料指標的位置。

此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。 主控台的字碼頁一開始預設為系統的 OEM 字碼頁。 若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 或 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函式，或使用 **chcp** 或 **mode con cp select =** 命令。

<a name="examples"></a>範例
--------

如需範例，請參閱 [讀取和寫入字元和屬性的區塊](reading-and-writing-blocks-of-characters-and-attributes.md)。

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
<td><p>Unicode 和 ANSI 名稱</p></td>
<td><p><strong>WriteConsoleOutputW</strong> (Unicode) 和 <strong>WriteConsoleOutputA</strong> (ANSI) </p></td>
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

[**字元 \_ 資訊**](char-info-str.md)

[**COORD**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[低層級主控台輸出功能](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**小型 \_ 矩形**](small-rect-str.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)

 

 





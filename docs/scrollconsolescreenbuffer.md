---
title: ScrollConsoleScreenBuffer 函式
description: 請參閱 ScrollConsoleScreenBuffer 函式的參考資訊，此函式會在螢幕緩衝區中移動資料區塊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/ScrollConsoleScreenBuffer
- wincon/ScrollConsoleScreenBuffer
- ScrollConsoleScreenBuffer
- consoleapi2/ScrollConsoleScreenBufferA
- wincon/ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferA
- consoleapi2/ScrollConsoleScreenBufferW
- wincon/ScrollConsoleScreenBufferW
- ScrollConsoleScreenBufferW
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d78bf4c9-2314-466c-b617-619259c824b5
topic_type:
- apiref
api_name:
- ScrollConsoleScreenBuffer
- ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: f0dd67ecc28907913e10efa8c06a544656d08dc6
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059438"
---
# <a name="scrollconsolescreenbuffer-function"></a>ScrollConsoleScreenBuffer 函式


移動螢幕緩衝區中的資料區塊。 您可以藉由指定裁剪矩形來限制移動的效果，如此一來，裁剪矩形外的主控台螢幕緩衝區內容就不會變更。

<a name="syntax"></a>語法
------

```C
BOOL WINAPI ScrollConsoleScreenBuffer(
  _In_           HANDLE     hConsoleOutput,
  _In_     const SMALL_RECT *lpScrollRectangle,
  _In_opt_ const SMALL_RECT *lpClipRectangle,
  _In_           COORD      dwDestinationOrigin,
  _In_     const CHAR_INFO  *lpFill
);
```

<a name="parameters"></a>參數
----------

*hConsoleOutput* \[在\]  
主控台螢幕緩衝區的控制碼。 控制碼必須具有 **一般 \_ 讀取** 許可權。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpScrollRectangle* \[在\]  
[**小型 \_ 矩形**](small-rect-str.md)結構的指標，其成員指定要移動之主控台螢幕緩衝區矩形的左上角和右下角座標。

*lpClipRectangle* \[在中，選擇性\]  
[**小型 \_ 矩形**](small-rect-str.md)結構的指標，其成員會指定受捲軸影響的主控台螢幕緩衝區矩形左上角和右下角的座標。 此指標可以是 **Null**。

*dwDestinationOrigin* \[在\]  
[**COORD**](coord-str.md)結構，指定*lpScrollRectangle*內容新位置的左上角（以字元為單位）。

*lpFill* \[在\]  
字元 [** \_ 資訊**](char-info-str.md) 結構的指標，指定字元和色彩屬性，以用於填滿 *lpScrollRectangle* 和 *lpClipRectangle* 交集內的資料格，而這些資料格會在移動時保留空白。

<a name="return-value"></a>傳回值
------------

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

<a name="remarks"></a>備註
-------

**ScrollConsoleScreenBuffer** 會將螢幕緩衝區的矩形區域內容（由 *lpScrollRectangle* 參數指定）複製到主控台螢幕緩衝區的另一個區域。 目標矩形具有與 *lpScrollRectangle* 矩形相同的維度，其左上角位於 *dwDestinationOrigin* 參數所指定的座標上。 與目標矩形不重迭的 *lpScrollRectangle* 部分，會填入 *lpFill* 參數所指定的字元和色彩屬性。

裁剪矩形適用于在 *lpScrollRectangle* 矩形和目標矩形中所做的變更。 例如，如果裁剪矩形未包含已由 *lpFill*內容填滿的區域，則該區域的原始內容會保持不變。

如果捲軸或目的地區域延伸超過主控台螢幕緩衝區的維度，則會將其裁剪。 例如，如果 *lpScrollRectangle* 是 (0、0) 和 (19、19) 和 *dwDestinationOrigin* 為 (10，15) 的區域，則目標矩形是 (10、15) 和 (29、34) 所包含的區域。 但是，如果主控台畫面緩衝區的寬度為50個字元，且高達30個字元，則會將目標矩形裁剪成 (10、15) 和 (29，29) 。 如果參數指定[**小型的 \_ RECT**](small-rect-str.md)結構，則根據*lpClipRectangle*，也會裁剪主控台螢幕緩衝區的變更。 如果裁剪矩形指定為 (0、0) 和 (49、19) ，則只會進行在主控台螢幕緩衝區的該區域中發生的變更。

此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。 主控台的字碼頁一開始預設為系統的 OEM 字碼頁。 若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 或 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函式，或使用 **chcp** 或 **mode con cp select =** 命令。

<a name="examples"></a>範例
--------

如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。

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
<td><p><strong>ScrollConsoleScreenBufferW</strong> (Unicode) 和 <strong>ScrollConsoleScreenBufferA</strong> (ANSI) </p></td>
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


[**字元 \_ 資訊**](char-info-str.md)

[主控台功能](console-functions.md)

[**COORD**](coord-str.md)

[滾動螢幕緩衝區](scrolling-the-screen-buffer.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[**小型 \_ 矩形**](small-rect-str.md)

 

 





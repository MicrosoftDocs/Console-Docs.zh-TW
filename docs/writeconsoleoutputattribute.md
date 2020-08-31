---
title: WriteConsoleOutputAttribute 函式
description: 從指定的位置開始，將數個字元屬性複製到主控台螢幕緩衝區的連續儲存格。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/WriteConsoleOutputAttribute
- wincon/WriteConsoleOutputAttribute
- WriteConsoleOutputAttribute
MS-HAID:
- '\_win32\_writeconsoleoutputattribute'
- base.writeconsoleoutputattribute
- consoles.writeconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 52a9d6e5-072e-4411-9945-10bd3dd61e25
topic_type:
- apiref
api_name:
- WriteConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e7c684b2f450713eaa78730676a0148e9b090c79
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059510"
---
# <a name="writeconsoleoutputattribute-function"></a>WriteConsoleOutputAttribute 函式


從指定的位置開始，將數個字元屬性複製到主控台螢幕緩衝區的連續儲存格。

<a name="syntax"></a>語法
------

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

<a name="parameters"></a>參數
----------

*hConsoleOutput* \[在\]  
主控台螢幕緩衝區的控制碼。 控制碼必須有 **一般 \_ 寫入** 存取權限。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpAttribute* \[在\]  
要在寫入主控台螢幕緩衝區時使用的屬性。 如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#_win32_font_attributes)。

*nLength* \[在\]  
要將屬性複製到其中的螢幕緩衝區字元儲存格數目。

*dwWriteCoord* \[在\]  
[**COORD**](coord-str.md)結構，指定要將屬性寫入其中的主控台螢幕緩衝區中第一個資料格的字元座標。

*lpNumberOfAttrsWritten* \[擴展\]  
變數的指標，此變數會接收實際寫入主控台螢幕緩衝區的屬性數目。

<a name="return-value"></a>傳回值
------------

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

<a name="remarks"></a>備註
-------

如果要寫入的屬性數目超過主控台螢幕緩衝區中指定之資料列的結尾，則會將屬性寫入至下一個資料列。 如果要寫入的屬性數目超過主控台螢幕緩衝區的結尾，則會將屬性寫入至主控台畫面緩衝區的結尾。

寫入至的位置的字元值不會變更。

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

[**COORD**](coord-str.md)

[低層級主控台輸出功能](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)

 

 





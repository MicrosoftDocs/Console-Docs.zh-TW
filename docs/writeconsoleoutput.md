---
title: WriteConsoleOutput 函式
description: 將字元和色彩屬性資料寫入主控台螢幕緩衝區中指定之字元資料格的矩形區塊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
ms.openlocfilehash: 1f10285cfc5c671ac5d31b8a575e84b1fd0f6a14
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359028"
---
# <a name="writeconsoleoutput-function"></a>WriteConsoleOutput 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

將字元和色彩屬性資料寫入主控台螢幕緩衝區中指定之字元資料格的矩形區塊。 要寫入的資料是取自來源緩衝區中指定位置的相對大小矩形區塊。

## <a name="syntax"></a>語法

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[in\]  
主控台螢幕緩衝區的控點。 控點必須具有 **GENERIC\_WRITE** 存取權限。 如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpBuffer* \[in\]  
要寫入主控台螢幕緩衝區的資料。 此指標會被視為 [**CHAR \_ 資訊**](char-info-str.md) 結構之二維陣列的來源，其大小是由 *dwBufferSize* 參數所指定。

*dwBufferSize* \[在\]  
*LpBuffer* 參數所指向的緩衝區大小（以字元資料格為限）。 [**COORD**](coord-str.md)結構的 **X** 成員是資料行的數目;**Y** 成員是資料列的數目。

*dwBufferCoord* \[在\]  
*LpBuffer* 參數所指向之緩衝區中左上角資料格的座標。 [**COORD**](coord-str.md)結構的 **X** 成員是資料行，而 **Y** 成員是資料列。

*lpWriteRegion* \[in、out\]  
[**小 \_ RECT**](small-rect-str.md)結構的指標。 在輸入時，結構成員會指定要寫入的主控台螢幕緩衝區矩形左上角和右下角的座標。 在輸出時，結構成員會指定所使用的實際矩形。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

**WriteConsoleOutput** 會將來源緩衝區和目的畫面緩衝區視為二維陣列， (資料格的資料行和資料列) 。 *LpWriteRegion* 參數所指向的矩形，可指定要在主控台螢幕緩衝區中寫入之區塊的大小與位置。 相同大小的矩形位於 *lpBuffer* 陣列中 *dwBufferCoord* 參數座標的左上角儲存格。 從這個矩形和來源緩衝區矩形交集的資料格中的資料， (其維度是由 *dwBufferSize* 參數指定，) 會寫入至目的地矩形。

目的地矩形中的資料格，其對應的來源位置超出來源緩衝區矩形的界限，因此不會受到寫入作業的影響。 換句話說，這些是沒有資料可供寫入的儲存格。

在 **WriteConsoleOutput** 傳回之前，它會將 *lpWriteRegion* 的成員設定為受寫入操作影響的實際螢幕緩衝區矩形。 這個矩形會反映目的地矩形中的儲存格，而來源緩衝區中有對應的資料格，因為 **WriteConsoleOutput** 會將目的地矩形的維度裁剪到主控台螢幕緩衝區的界限。

如果 *lpWriteRegion* 所指定的矩形完全落在主控台螢幕緩衝區的界限之外，或對應的矩形完全位於來源緩衝區的界限之外，則不會寫入任何資料。 在此情況下，函式會傳回 *lpWriteRegion* 參數集所指向之結構的成員，讓 **右邊** 的成員小於 **左邊**，或 **底部** 的成員小於 **頂端**。 若要判斷主控台螢幕緩衝區的大小，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數。

**WriteConsoleOutput** 不會影響資料指標的位置。

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> 此 API 的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機等同于 **[文字格式](console-virtual-terminal-sequences.md#text-formatting)** 和資料 **[指標定位](console-virtual-terminal-sequences.md#cursor-positioning)** 順序。 將游標移至要插入的位置，套用所需的格式，並寫出文字。 建議您針對所有新的和進行中的開發，使用 _虛擬終端機序列_。

## <a name="examples"></a>範例

如需範例，請參閱 [讀取和寫入字元和屬性的區塊](reading-and-writing-blocks-of-characters-and-attributes.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode 與 ANSI 名稱 | **WriteConsoleOutputW** (Unicode) 和 **WriteConsoleOutputA** (ANSI)  |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

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
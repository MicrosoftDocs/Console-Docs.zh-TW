---
title: ReadConsoleOutput 函式
description: 從主控台螢幕緩衝區中的矩形字元資料格區塊讀取字元和色彩屬性資料，並將資料寫入目的地緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/ReadConsoleOutput
- wincon/ReadConsoleOutput
- ReadConsoleOutput
- consoleapi2/ReadConsoleOutputA
- wincon/ReadConsoleOutputA
- ReadConsoleOutputA
- consoleapi2/ReadConsoleOutputW
- wincon/ReadConsoleOutputW
- ReadConsoleOutputW
MS-HAID:
- '\_win32\_readconsoleoutput'
- base.readconsoleoutput
- consoles.readconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d1391684-6a8f-4b5e-9706-11970a957710
topic_type:
- apiref
api_name:
- ReadConsoleOutput
- ReadConsoleOutputA
- ReadConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c17f9c3b44ba0d64fcf47659cf24d08d5c76cfdc
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358728"
---
# <a name="readconsoleoutput-function"></a>ReadConsoleOutput 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

從主控台螢幕緩衝區中的矩形字元資料格區塊讀取字元和色彩屬性資料，而函式會將資料寫入目的緩衝區中指定位置的矩形區塊。

## <a name="syntax"></a>語法

```C
BOOL WINAPI ReadConsoleOutput(
  _In_    HANDLE      hConsoleOutput,
  _Out_   PCHAR_INFO  lpBuffer,
  _In_    COORD       dwBufferSize,
  _In_    COORD       dwBufferCoord,
  _Inout_ PSMALL_RECT lpReadRegion
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[in\]  
主控台螢幕緩衝區的控點。 控制代碼必須具有 **GENERIC\_READ** 存取權限。 如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpBuffer* \[擴展\]  
目的地緩衝區的指標，此緩衝區會接收從主控台螢幕緩衝區讀取的資料。 此指標會被視為 [**CHAR \_ 資訊**](char-info-str.md) 結構之二維陣列的來源，其大小是由 *dwBufferSize* 參數所指定。

*dwBufferSize* \[在\]  
*LpBuffer* 參數的大小，以字元儲存格為限。 [**COORD**](coord-str.md)結構的 **X** 成員是資料行的數目;**Y** 成員是資料列的數目。

*dwBufferCoord* \[在\]  
*LpBuffer* 參數中的左上角儲存格座標，可接收從主控台螢幕緩衝區讀取的資料。 [**COORD**](coord-str.md)結構的 **X** 成員是資料行，而 **Y** 成員是資料列。

*lpReadRegion* \[in、out\]  
[**小 \_ RECT**](small-rect-str.md)結構的指標。 在輸入時，結構成員會指定要讀取函式的主控台螢幕緩衝區矩形左上角和右下角的座標。 在輸出時，結構成員會指定所使用的實際矩形。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

**ReadConsoleOutput** 會將主控台畫面緩衝區和目的地緩衝區視為二維陣列 () 的字元資料格的資料行和資料列。 *LpReadRegion* 參數所指向的矩形，可指定要從主控台螢幕緩衝區讀取之區塊的大小與位置。 相同大小的目的地矩形位於 *lpBuffer* 陣列中 *dwBufferCoord* 參數座標的左上角儲存格。 從主控台螢幕緩衝區來源矩形的儲存格讀取的資料會複製到目的地緩衝區中的對應資料格。 如果對應的資料格超出目的緩衝區矩形的界限， (其維度是由 *dwBufferSize* 參數) 指定，則不會複製資料。

目的緩衝區中對應至不在主控台螢幕緩衝區界限內之座標的儲存格會保持不變。 換句話說，這些是沒有螢幕緩衝區資料可供讀取的儲存格。

在 **ReadConsoleOutput** 傳回之前，它會將 *lpReadRegion* 參數所指向之結構的成員設定為實際的螢幕緩衝區矩形，其儲存格已複製到目的緩衝區。 這個矩形會反映來源矩形中的儲存格，在目的緩衝區中已有對應的資料格，因為 **ReadConsoleOutput** 會裁剪來源矩形的維度，以符合主控台螢幕緩衝區的界限。

如果 *lpReadRegion* 所指定的矩形完全落在主控台螢幕緩衝區的界限之外，或對應的矩形完全位於目的緩衝區的界限之外，則不會複製任何資料。 在此情況下，函式會傳回 *lpReadRegion* 參數集所指向之結構的成員，讓 **右邊** 的成員小於 **左邊**，或 **底部** 的成員小於 **頂端**。 若要判斷主控台螢幕緩衝區的大小，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數。

**ReadConsoleOutput** 函式不會影響主控台畫面緩衝區的游標位置。 此函數不會變更控制台螢幕緩衝區的內容。

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

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
| Unicode 與 ANSI 名稱 | **ReadConsoleOutputW** (Unicode) 和 **ReadConsoleOutputA** (ANSI)  |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

[低層級主控台輸出功能](low-level-console-output-functions.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**小型 \_ 矩形**](small-rect-str.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**字元 \_ 資訊**](char-info-str.md)

[**COORD**](coord-str.md)
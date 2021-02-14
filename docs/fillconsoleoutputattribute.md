---
title: FillConsoleOutputAttribute 函式
description: 針對指定的字元資料格數目，設定從螢幕緩衝區中的指定座標開始的字元屬性。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/FillConsoleOutputAttribute
- wincon/FillConsoleOutputAttribute
- FillConsoleOutputAttribute
MS-HAID:
- '\_win32\_fillconsoleoutputattribute'
- base.fillconsoleoutputattribute
- consoles.fillconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 09440263-71c4-4b7a-8fc6-a2b4fcd677ff
topic_type:
- apiref
api_name:
- FillConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 8b88bfcc264d1370479eef300cea2868142fbb8c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357908"
---
# <a name="fillconsoleoutputattribute-function"></a>FillConsoleOutputAttribute 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

針對指定的字元資料格數目，設定從螢幕緩衝區中的指定座標開始的字元屬性。

## <a name="syntax"></a>語法

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[in\]  
主控台螢幕緩衝區的控點。 控點必須具有 **GENERIC\_WRITE** 存取權限。 如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*wAttribute* \[在\]  
寫入主控台螢幕緩衝區時要使用的屬性。 如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#character-attributes)。

*nLength* \[在\]  
要設定為指定之色彩屬性的字元儲存格數目。

*dwWriteCoord* \[在\]  
[**COORD**](coord-str.md)結構，指定要設定其屬性的第一個資料格的字元座標。

*lpNumberOfAttrsWritten* \[擴展\]  
變數的指標，此變數會接收實際設定其屬性的字元儲存格數目。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

如果要設定屬性的字元資料格數目延伸超過主控台螢幕緩衝區中指定之資料列的結尾，則會設定下一個資料列的資料格。 如果要寫入的資料格數目延伸超過主控台螢幕緩衝區的結尾，則資料格會寫入至主控台畫面緩衝區的結尾。

寫入至的位置的字元值不會變更。

> [!TIP]
> 不建議使用此 API，也不會有對等的特定 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。 不支援在可見視窗外填滿區域，而且會保留給終端機的歷程記錄空間。 使用新文字或色彩填滿可見區域的動作是透過 **[移動游標](console-virtual-terminal-sequences.md#cursor-positioning)**、 **[設定新屬性](console-virtual-terminal-sequences.md#text-formatting)**，然後撰寫該區域所需的文字，並在填滿填滿的長度時重複字元。 您可以接著撰寫所需的文字來填滿矩形區域，以需要額外的資料指標移動。 用戶端應用程式應該將自己的記憶體保留在畫面上，而且無法查詢遠端狀態。 如需詳細資訊，請參閱 **[傳統主控台與虛擬終端](classic-vs-vt.md)** 檔。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

[**COORD**](coord-str.md)

[**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)

[低層級主控台輸出功能](low-level-console-output-functions.md)

[**SetConsoleTextAttribute**](setconsoletextattribute.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)
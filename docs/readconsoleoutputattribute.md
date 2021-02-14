---
title: ReadConsoleOutputAttribute 函式
description: 從主控台螢幕緩衝區的連續儲存格（從指定的位置開始）複製指定數目的字元屬性。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/ReadConsoleOutputAttribute
- wincon/ReadConsoleOutputAttribute
- ReadConsoleOutputAttribute
MS-HAID:
- '\_win32\_readconsoleoutputattribute'
- base.readconsoleoutputattribute
- consoles.readconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c3e35779-a487-47f1-8d07-0d5fae99d54a
topic_type:
- apiref
api_name:
- ReadConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: bf140d9f6721196caa5f62a064ed434554067d62
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358689"
---
# <a name="readconsoleoutputattribute-function"></a>ReadConsoleOutputAttribute 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

從主控台螢幕緩衝區的連續儲存格（從指定的位置開始）複製指定數目的字元屬性。

## <a name="syntax"></a>語法

```C
BOOL WINAPI ReadConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPWORD  lpAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfAttrsRead
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[in\]  
主控台螢幕緩衝區的控點。 控制代碼必須具有 **GENERIC\_READ** 存取權限。 如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpAttribute* \[擴展\]  
緩衝區的指標，此緩衝區會接收主控台螢幕緩衝區所使用的屬性。

如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#character-attributes)。

*nLength* \[在\]  
要從中讀取的螢幕緩衝區字元儲存格數目。 *LpAttribute* 參數所指向的緩衝區大小應該是 `nLength * sizeof(WORD)` 。

*dwReadCoord* \[在\]  
要從中讀取的主控台螢幕緩衝區中第一個資料格的座標（以字元為單位）。 [**COORD**](coord-str.md)結構的 **X** 成員是資料行，而 **Y** 成員是資料列。

*lpNumberOfAttrsRead* \[擴展\]  
變數的指標，此變數會接收實際讀取的屬性數目。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

如果要讀取的屬性數目超出指定螢幕緩衝區資料列的結尾，則會從下一個資料列讀取屬性。 如果要讀取的屬性數目延伸超過主控台螢幕緩衝區的結尾，則會讀取最多至主控台畫面緩衝區結尾的屬性。

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

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

[低層級主控台輸出功能](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)
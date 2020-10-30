---
title: ReadConsoleOutputCharacter 函式
description: 從主控台螢幕緩衝區的連續資料格複製一些字元，從指定的位置開始。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/ReadConsoleOutputCharacter
- wincon/ReadConsoleOutputCharacter
- ReadConsoleOutputCharacter
- consoleapi2/ReadConsoleOutputCharacterA
- wincon/ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterA
- consoleapi2/ReadConsoleOutputCharacterW
- wincon/ReadConsoleOutputCharacterW
- ReadConsoleOutputCharacterW
MS-HAID:
- '\_win32\_readconsoleoutputcharacter'
- base.readconsoleoutputcharacter
- consoles.readconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f47464a9-6c59-4f15-abd0-be29ab515698
topic_type:
- apiref
api_name:
- ReadConsoleOutputCharacter
- ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: fa70841d5dccf3289807d29c67fab86e3b445279
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037718"
---
# <a name="readconsoleoutputcharacter-function"></a>ReadConsoleOutputCharacter 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

從主控台螢幕緩衝區的連續資料格複製一些字元，從指定的位置開始。

## <a name="syntax"></a>語法

```C
BOOL WINAPI ReadConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPTSTR  lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfCharsRead
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[在\]  
主控台螢幕緩衝區的控制碼。 控制碼必須具有 **一般 \_ 讀取** 許可權。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpCharacter* \[擴展\]  
緩衝區的指標，此緩衝區會接收從主控台螢幕緩衝區讀取的字元。

*nLength* \[在\]  
要從中讀取的螢幕緩衝區字元儲存格數目。 *LpCharacter* 參數所指向的緩衝區大小應該是 `nLength * sizeof(TCHAR)` 。

*dwReadCoord* \[在\]  
要從中讀取的主控台螢幕緩衝區中第一個資料格的座標（以字元為單位）。 [**COORD**](coord-str.md)結構的 **X** 成員是資料行，而 **Y** 成員是資料列。

*lpNumberOfCharsRead* \[擴展\]  
變數的指標，此變數會接收實際讀取的字元數。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

如果要讀取的字元數超出指定螢幕緩衝區資料列的結尾，則會從下一個資料列讀取字元。 如果要讀取的字元數超過主控台螢幕緩衝區的結尾，則會讀取主控台螢幕緩衝區結尾的字元。

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |
| Unicode 和 ANSI 名稱 | **ReadConsoleOutputCharacterW** (Unicode) 和 **ReadConsoleOutputCharacterA** (ANSI)  |

## <a name="see-also"></a>請參閱

[主控台功能](console-functions.md)

[**COORD**](coord-str.md)

[低層級主控台輸出功能](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)

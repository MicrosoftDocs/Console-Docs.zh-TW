---
title: SetConsoleCursorPosition 函式
description: 請參閱 SetConsoleCursorPosition 函式的參考資訊，此函式會在指定的主控台螢幕緩衝區中設定游標位置。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleCursorPosition
- wincon/SetConsoleCursorPosition
- SetConsoleCursorPosition
MS-HAID:
- '\_win32\_setconsolecursorposition'
- base.setconsolecursorposition
- consoles.setconsolecursorposition
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8e9abada-a64e-429f-8286-ced1169c7104
topic_type:
- apiref
api_name:
- SetConsoleCursorPosition
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c93fbf4b619b522a95af2b03a49d60ff6f880e7d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039366"
---
# <a name="setconsolecursorposition-function"></a>SetConsoleCursorPosition 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

設定指定的主控台螢幕緩衝區中的游標位置。

## <a name="syntax"></a>語法

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[在\]  
主控台螢幕緩衝區的控制碼。 控制碼必須具有 **一般 \_ 讀取** 許可權。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*dwCursorPosition* \[在\]  
指定新資料指標位置的 [**COORD**](coord-str.md) 結構（以字元為單位）。 座標是螢幕緩衝區字元資料格的資料行和資料列。 座標必須在主控台畫面緩衝區的界限內。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

資料指標位置會決定 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 或 [**WriteConsole**](writeconsole.md) 函數所寫入的字元，或由 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 或 [**ReadConsole**](readconsole.md) 函式所回應的位置。 若要判斷資料指標目前的位置，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數。

如果新的資料指標位置不在主控台畫面緩衝區視窗的界限內，則視窗來源會變更，使游標變成可見。

> [!TIP]
> 此 API 在 **[簡單資料指標定位](console-virtual-terminal-sequences.md#simple-cursor-positioning)** 和資料 **[指標定位](console-virtual-terminal-sequences.md#cursor-positioning)** 區段中，有相當的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。 使用「換行」、「換行」、「倒退鍵」和「索引標籤控制項」序列也可以協助資料指標的定位。

## <a name="examples"></a>範例

如需範例，請參閱 [使用 High-Level 輸入和輸出函數](using-the-high-level-input-and-output-functions.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>請參閱

[主控台功能](console-functions.md)

[主控台畫面緩衝區](console-screen-buffers.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleCursorInfo**](setconsolecursorinfo.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

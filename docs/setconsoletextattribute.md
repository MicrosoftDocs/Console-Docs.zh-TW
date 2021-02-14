---
title: SetConsoleTextAttribute 函式
description: 設定 WriteFile 或 WriteConsole 函式寫入主控台螢幕緩衝區的字元屬性，或由 ReadFile 或 ReadConsole 函式回顯的字元屬性。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleTextAttribute
- wincon/SetConsoleTextAttribute
- SetConsoleTextAttribute
MS-HAID:
- '\_win32\_setconsoletextattribute'
- base.setconsoletextattribute
- consoles.setconsoletextattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9fba5bb5-b999-4abd-ab39-7a63d58b8074
topic_type:
- apiref
api_name:
- SetConsoleTextAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: b08f4b0b628f4d20029b81873b4fc25077a11029
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358558"
---
# <a name="setconsoletextattribute-function"></a>SetConsoleTextAttribute 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

設定 [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) 或 [**WriteConsole**](writeconsole.md) 函式寫入主控台螢幕緩衝區的字元屬性，或由 [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) 或 [**ReadConsole**](readconsole.md) 函式回顯的字元屬性。 此函式會影響在函式呼叫後寫入的文字。

## <a name="syntax"></a>語法

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[in\]  
主控台螢幕緩衝區的控點。 控制代碼必須具有 **GENERIC\_READ** 存取權限。 如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*wAttributes* \[在\]  
[字元屬性](console-screen-buffers.md#character-attributes)。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

若要判斷螢幕緩衝區目前的色彩屬性，請呼叫 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數。

> [!TIP]
> 此 API 具有等同于 **[文字格式設定](console-virtual-terminal-sequences.md#text-formatting)** 順序的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。 建議您針對所有新的和進行中的開發，使用 _虛擬終端機序列_。

## <a name="examples"></a>範例

如需範例，請參閱 [使用 High-Level 輸入和輸出函數](using-the-high-level-input-and-output-functions.md)。

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

[主控台畫面緩衝區](console-screen-buffers.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)
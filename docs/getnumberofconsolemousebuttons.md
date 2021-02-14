---
title: GetNumberOfConsoleMouseButtons 函式
description: 抓取目前主控台使用之滑鼠上的按鈕數目。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- base.getnumberofconsolemousebuttons
- consoles.getnumberofconsolemousebuttons
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 4a2f936ac778b13985aa0c1d237c59e9f993d995
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358848"
---
# <a name="getnumberofconsolemousebuttons-function"></a>GetNumberOfConsoleMouseButtons 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

抓取目前主控台使用之滑鼠上的按鈕數目。

## <a name="syntax"></a>語法

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

## <a name="parameters"></a>參數

*lpNumberOfMouseButtons* \[擴展\]  
變數的指標，此變數會接收滑鼠按鍵的數目。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

當主控台收到滑鼠輸入時，會將包含 [**滑鼠 \_ 事件 \_ 記錄**](mouse-event-record-str.md)結構的 [**輸入 \_ 記錄**](input-record-str.md)結構放在主控台的輸入緩衝區中。 **滑鼠 \_ 事件 \_ 記錄** 的 **dwButtonState** 成員有位，表示每個滑鼠按鍵的狀態。 如果按鈕已關閉，則位為1，如果按鈕為開啟，則為0。 若要判斷重要位數，請使用 **GetNumberOfConsoleMouseButtons**。

> [!TIP]
> 不建議使用此 API，也不會有對等的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。 這種決策刻意將 Windows 平臺與其他作業系統對齊。 此狀態只會與本機使用者、會話和許可權內容相關。 使用此 API 時，透過跨平臺公用程式和傳輸（如 SSH）的應用程式遠端執行可能無法如預期般運作。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | ConsoleApi3 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

[主控台輸入緩衝區](console-input-buffer.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**輸入 \_ 記錄**](input-record-str.md)

[**滑鼠 \_ 事件 \_ 記錄**](mouse-event-record-str.md)
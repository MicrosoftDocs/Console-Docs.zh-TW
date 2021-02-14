---
title: GetConsoleScreenBufferInfo 函式
description: 請參閱 GetConsoleScreenBufferInfo 函式的參考資訊，此函式會抓取指定的主控台螢幕緩衝區的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfo
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 2f80f77b749fc9e9dc0aebf4507b0c41f589e40c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358908"
---
# <a name="getconsolescreenbufferinfo-function"></a>GetConsoleScreenBufferInfo 函式

抓取指定的主控台螢幕緩衝區的相關資訊。

## <a name="syntax"></a>語法

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[in\]  
主控台螢幕緩衝區的控點。 控制代碼必須具有 **GENERIC\_READ** 存取權限。 如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpConsoleScreenBufferInfo* \[擴展\]  
[**主控台 \_ 螢幕 \_ 緩衝區 \_**](console-screen-buffer-info-str.md)資訊結構的指標，此結構會接收主控台螢幕緩衝區資訊。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

您可以修改 [**主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊**](console-screen-buffer-info-str.md)結構的 **srWindow** 成員中所傳回的矩形，然後將其傳遞至 [**SetConsoleWindowInfo**](setconsolewindowinfo.md)函式，以在視窗中滾動主控台畫面緩衝區、變更視窗的大小，或兩者。

[**主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊**](console-screen-buffer-info-str.md)結構中傳回的所有座標都是在字元儲存格座標中，其中源 (0、0) 位於主控台螢幕緩衝區的左上角。

> [!TIP]
> 此 API 沒有對等的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。 嘗試繪製資料行、格線或填滿顯示以抓取視窗大小的應用程式，可能仍需要使用它。 此視窗狀態是由一般資料流程流程之外的 TTY/PTY/Pseudoconsole 所管理，而且通常會被視為用戶端應用程式無法調整的使用者特殊許可權。 您可以在 [**ReadConsoleInput**](readconsoleinput.md)上收到更新。

## <a name="examples"></a>範例

如需範例，請參閱 [滾動螢幕緩衝區視窗](scrolling-a-screen-buffer-s-window.md)。

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

[**主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊**](console-screen-buffer-info-str.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[視窗和螢幕緩衝區大小](window-and-screen-buffer-size.md)
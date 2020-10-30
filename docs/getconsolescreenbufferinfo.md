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
ms.openlocfilehash: 251fc71ef58840a962e5c1e09e88474959de27ae
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038766"
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

*hConsoleOutput* \[在\]  
主控台螢幕緩衝區的控制碼。 控制碼必須具有 **一般 \_ 讀取** 許可權。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpConsoleScreenBufferInfo* \[擴展\]  
[**主控台 \_ 螢幕 \_ 緩衝區 \_**](console-screen-buffer-info-str.md)資訊結構的指標，此結構會接收主控台螢幕緩衝區資訊。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

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
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>請參閱

[主控台功能](console-functions.md)

[**主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊**](console-screen-buffer-info-str.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[視窗和螢幕緩衝區大小](window-and-screen-buffer-size.md)

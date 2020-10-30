---
title: ReadConsoleInput 函式
description: 從主控台輸入緩衝區讀取資料，並將其從緩衝區中移除。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/ReadConsoleInput
- wincon/ReadConsoleInput
- ReadConsoleInput
- consoleapi/ReadConsoleInputA
- wincon/ReadConsoleInputA
- ReadConsoleInputA
- consoleapi/ReadConsoleInputW
- wincon/ReadConsoleInputW
- ReadConsoleInputW
MS-HAID:
- '\_win32\_readconsoleinput'
- base.readconsoleinput
- consoles.readconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5a9f7b18-cdea-4041-a377-5532d30e0105
topic_type:
- apiref
api_name:
- ReadConsoleInput
- ReadConsoleInputA
- ReadConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 38778931522dff8d1d000bb6f0ce13c2849d76db
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039486"
---
# <a name="readconsoleinput-function"></a>ReadConsoleInput 函式

從主控台輸入緩衝區讀取資料，並將其從緩衝區中移除。

## <a name="syntax"></a>語法

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## <a name="parameters"></a>參數

*hConsoleInput* \[在\]  
主控台輸入緩衝區的控制碼。 控制碼必須具有 **一般 \_ 讀取** 許可權。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpBuffer* \[擴展\]  
接收輸入緩衝區資料之 [**輸入 \_ 記錄**](input-record-str.md) 結構陣列的指標。

*nLength* \[在\]  
陣列元素中 *lpBuffer* 參數所指向的陣列大小。

*lpNumberOfEventsRead* \[擴展\]  
變數的指標，此變數會接收讀取的輸入記錄數目。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

如果 *nLength* 參數中要求的記錄數目超過緩衝區中的可用記錄數目，則會讀取可用的數目。 在至少讀取一個輸入記錄之前，函式不會傳回。

進程可以在其中一個 [等候](https://msdn.microsoft.com/library/windows/desktop/ms687069) 函式中指定主控台輸入緩衝區控制碼，以判斷何時有未讀取的主控台輸入。 當輸入緩衝區不是空的時，主控台輸入緩衝區控制碼的狀態就會收到信號。

若要判斷主控台輸入緩衝區中未讀取的輸入記錄數目，請使用 [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) 函數。 若要從主控台輸入緩衝區讀取輸入記錄，而不會影響未讀取的記錄數目，請使用 [**PeekConsoleInput**](peekconsoleinput.md) 函數。 若要捨棄主控台輸入緩衝區中的所有未讀取記錄，請使用 [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) 函式。

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="examples"></a>範例

如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |
| Unicode 和 ANSI 名稱 | **ReadConsoleInputW** (Unicode) 和 **ReadConsoleInputA** (ANSI)  |

## <a name="see-also"></a>請參閱

[主控台功能](console-functions.md)

[**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

[**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)

[**輸入 \_ 記錄**](input-record-str.md)

[低層級主控台輸入函式](low-level-console-input-functions.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleInput**](writeconsoleinput.md)

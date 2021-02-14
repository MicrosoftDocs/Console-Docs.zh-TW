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
ms.openlocfilehash: 06e784ebaebde2ed68ed17f75f4e54932aa463f5
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358718"
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
主控台輸入緩衝區的控制碼。 控制代碼必須具有 **GENERIC\_READ** 存取權限。 如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpBuffer* \[擴展\]  
接收輸入緩衝區資料之 [**輸入 \_ 記錄**](input-record-str.md) 結構陣列的指標。

*nLength* \[在\]  
陣列元素中 *lpBuffer* 參數所指向的陣列大小。

*lpNumberOfEventsRead* \[擴展\]  
變數的指標，此變數會接收讀取的輸入記錄數目。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

如果 *nLength* 參數中要求的記錄數目超過緩衝區中的可用記錄數目，則會讀取可用的數目。 在至少讀取一個輸入記錄之前，函式不會傳回。

進程可以在其中一個 [等候](/windows/win32/sync/wait-functions) 函式中指定主控台輸入緩衝區控制碼，以判斷何時有未讀取的主控台輸入。 當輸入緩衝區不是空的時，主控台輸入緩衝區控制碼的狀態就會收到信號。

若要判斷主控台輸入緩衝區中未讀取的輸入記錄數目，請使用 [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) 函數。 若要從主控台輸入緩衝區讀取輸入記錄，而不會影響未讀取的記錄數目，請使用 [**PeekConsoleInput**](peekconsoleinput.md) 函數。 若要捨棄主控台輸入緩衝區中的所有未讀取記錄，請使用 [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) 函式。

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="examples"></a>範例

如需範例，請參閱[讀取輸入緩衝區事件](reading-input-buffer-events.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | ConsoleApi.h (透過 WinCon.h，包括 Windows.h) |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode 與 ANSI 名稱 | **ReadConsoleInputW** (Unicode) 和 **ReadConsoleInputA** (ANSI)  |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

[**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

[**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)

[**輸入 \_ 記錄**](input-record-str.md)

[低層級主控台輸入函式](low-level-console-input-functions.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsole**](readconsole.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**WriteConsoleInput**](writeconsoleinput.md)
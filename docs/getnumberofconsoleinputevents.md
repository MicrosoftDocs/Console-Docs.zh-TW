---
title: GetNumberOfConsoleInputEvents 函式
description: 抓取主控台輸入緩衝區中未讀取的輸入記錄數目。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/GetNumberOfConsoleInputEvents
- wincon/GetNumberOfConsoleInputEvents
- GetNumberOfConsoleInputEvents
MS-HAID:
- '\_win32\_getnumberofconsoleinputevents'
- base.getnumberofconsoleinputevents
- consoles.getnumberofconsoleinputevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1083b4f1-8fa6-4054-a516-3b447c3b0130
topic_type:
- apiref
api_name:
- GetNumberOfConsoleInputEvents
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 622dc96598df9a851934c73645afb7691f77f1be
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358858"
---
# <a name="getnumberofconsoleinputevents-function"></a>GetNumberOfConsoleInputEvents 函式

抓取主控台輸入緩衝區中未讀取的輸入記錄數目。

## <a name="syntax"></a>語法

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

## <a name="parameters"></a>參數

*hConsoleInput* \[在\]  
主控台輸入緩衝區的控制碼。 控制代碼必須具有 **GENERIC\_READ** 存取權限。 如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpcNumberOfEvents* \[擴展\]  
變數的指標，此變數會接收主控台輸入緩衝區中未讀取的輸入記錄數目。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

**GetNumberOfConsoleInputEvents** 函式會報告輸入緩衝區中未讀取的輸入記錄總數，包括鍵盤、滑鼠和視窗大小的輸入記錄。 使用 [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) 或 [**ReadConsole**](readconsole.md) 函數的進程只能讀取鍵盤輸入。 使用 [**ReadConsoleInput**](readconsoleinput.md) 函數的進程可以讀取所有類型的輸入記錄。

進程可以在其中一個 [等候](/windows/win32/sync/wait-functions) 函式中指定主控台輸入緩衝區控制碼，以判斷何時有未讀取的主控台輸入。 當輸入緩衝區不是空的時，主控台輸入緩衝區控制碼的狀態就會收到信號。

若要從主控台輸入緩衝區讀取輸入記錄，而不會影響未讀取的記錄數目，請使用 [**PeekConsoleInput**](peekconsoleinput.md) 函數。 若要捨棄主控台輸入緩衝區中的所有未讀取記錄，請使用 [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) 函式。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | ConsoleApi.h (透過 WinCon.h，包括 Windows.h) |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

[**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

[低層級主控台輸入函式](low-level-console-input-functions.md)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsole**](readconsole.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)
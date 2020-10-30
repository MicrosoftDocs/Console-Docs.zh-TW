---
title: WriteConsoleInput 函式
description: 請參閱 WriteConsoleInput 函式的參考資訊，此函式會將資料直接寫入主控台輸入緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/WriteConsoleInput
- wincon/WriteConsoleInput
- WriteConsoleInput
- consoleapi2/WriteConsoleInputA
- wincon/WriteConsoleInputA
- WriteConsoleInputA
- consoleapi2/WriteConsoleInputW
- wincon/WriteConsoleInputW
- WriteConsoleInputW
MS-HAID:
- '\_win32\_writeconsoleinput'
- base.writeconsoleinput
- consoles.writeconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad06231f-5063-4aff-b14d-8df5e6e42430
topic_type:
- apiref
api_name:
- WriteConsoleInput
- WriteConsoleInputA
- WriteConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: dc2c7930ab76587edc9ae1991d4493c858b0ec30
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039286"
---
# <a name="writeconsoleinput-function"></a>WriteConsoleInput 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

將資料直接寫入主控台輸入緩衝區。

## <a name="syntax"></a>語法

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

## <a name="parameters"></a>參數

*hConsoleInput* \[在\]  
主控台輸入緩衝區的控制碼。 控制碼必須有 **一般 \_ 寫入** 存取權限。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpBuffer* \[在\]  
[**輸入 \_ 記錄**](input-record-str.md)結構陣列的指標，其中包含要寫入至輸入緩衝區的資料。

*nLength* \[在\]  
要寫入的輸入記錄數目。

*lpNumberOfEventsWritten* \[擴展\]  
變數的指標，此變數會接收實際寫入之輸入記錄的數目。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

**WriteConsoleInput** 會將輸入記錄放入緩衝區中任何暫止事件後方的輸入緩衝區。 視需要，輸入緩衝區會動態成長，以保存所寫入的事件數目。

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> 不建議使用此 API，也不會有對等的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。 這種決策刻意將 Windows 平臺與其他作業系統對齊。 這項作業會被視為這個緩衝區的 **[錯誤方式動詞](console-buffer-security-and-access-rights.md#wrong-way-verbs)** 。 使用此 API 時，透過跨平臺公用程式和傳輸（如 SSH）的應用程式遠端執行可能無法如預期般運作。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |
| Unicode 和 ANSI 名稱 | **WriteConsoleInputW** (Unicode) 和 **WriteConsoleInputA** (ANSI)  |

## <a name="see-also"></a>請參閱

[主控台功能](console-functions.md)

[**輸入 \_ 記錄**](input-record-str.md)

[低層級主控台輸入函式](low-level-console-input-functions.md)

[**MapVirtualKey**](https://msdn.microsoft.com/library/windows/desktop/ms646306)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**VkKeyScan**](https://msdn.microsoft.com/library/windows/desktop/ms646329)

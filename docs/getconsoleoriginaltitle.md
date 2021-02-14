---
title: GetConsoleOriginalTitle 函式
description: 請參閱 GetConsoleOriginalTitle 函式的參考資訊，此函式會抓取目前主控台視窗的原始標題。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 3c4fc202601cec9257b6cf95efdd460c64122b80
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358998"
---
# <a name="getconsoleoriginaltitle-function"></a>GetConsoleOriginalTitle 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

抓取目前主控台視窗的原始標題。

## <a name="syntax"></a>語法

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a>參數

*lpConsoleTitle* \[擴展\]  
緩衝區的指標，此緩衝區會接收以 null 終止的字串，其中包含原始標題。

*nSize* \[在\]  
*LpConsoleTitle* 緩衝區的大小（以字元為單位）。

## <a name="return-value"></a>傳回值

如果函式成功，傳回值就是複製到緩衝區的字串長度（以字元為單位）。

如果緩衝區不夠大，無法儲存標題，則傳回值為零，而 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 會傳回 **錯誤 \_ 成功**。

如果函式失敗，則傳回值為零，而 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror) 會傳回錯誤碼。

## <a name="remarks"></a>備註

若要設定主控台視窗的標題，請使用 [**SetConsoleTitle**](setconsoletitle.md) 函數。 若要取得目前的標題字串，請使用 [**GetConsoleTitle**](getconsoletitle.md) 函數。

若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0600 或更新版本。 如需詳細資訊，請參閱 [使用 Windows 標頭](/windows/win32/winprog/using-the-windows-headers)。

> [!TIP]
> 不建議使用此 API，也不會有對等的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。 這種決策刻意將 Windows 平臺與其他作業系統對齊。 使用此 API 時，透過跨平臺公用程式和傳輸（如 SSH）的應用程式遠端執行可能無法如預期般運作。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | \[僅限 Windows Vista 桌面應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2008 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |
| Unicode 與 ANSI 名稱 | **GetConsoleOriginalTitleW** (Unicode) 和 **GetConsoleOriginalTitleA** (ANSI)  |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

[**GetConsoleTitle**](getconsoletitle.md)

[**SetConsoleTitle**](setconsoletitle.md)
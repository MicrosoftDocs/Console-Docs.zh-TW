---
title: GetCurrentConsoleFontEx 函式
description: 請參閱 GetCurrentConsoleFontEx 函式的參考資訊，此函式會抓取有關目前使用之主控台字型的延伸資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetCurrentConsoleFontEx
- wincon/GetCurrentConsoleFontEx
- GetCurrentConsoleFontEx
MS-HAID:
- base.getcurrentconsolefontex
- consoles.getcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 97d8e730-4110-4be5-b099-0acc1b6f8eb5
topic_type:
- apiref
api_name:
- GetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: e7932d286723886f671be051294fcffb23155bf6
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358878"
---
# <a name="getcurrentconsolefontex-function"></a>GetCurrentConsoleFontEx 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

抓取有關目前主控台字型的延伸資訊。

## <a name="syntax"></a>語法

```C
BOOL WINAPI GetCurrentConsoleFontEx(
  _In_  HANDLE               hConsoleOutput,
  _In_  BOOL                 bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[in\]  
主控台螢幕緩衝區的控點。 控制代碼必須具有 **GENERIC\_READ** 存取權限。 如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*bMaximumWindow* \[在\]  
如果此參數為 **TRUE**，就會針對最大視窗大小抓取字型資訊。 如果此參數為 **FALSE**，則會針對目前的視窗大小抓取字型資訊。

*lpConsoleCurrentFontEx* \[擴展\]  
[**主控台 \_ 字型 \_ INFOEX**](console-font-infoex.md)結構的指標，此結構會接收要求的字型資訊。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | \[僅限 Windows Vista 桌面應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2008 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi3 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

[**主控台 \_ 字型 \_ INFOEX**](console-font-infoex.md)
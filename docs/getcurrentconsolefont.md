---
title: GetCurrentConsoleFont 函式
description: 針對指定的主控台螢幕緩衝區，抓取目前主控台字型的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetCurrentConsoleFont
- wincon/GetCurrentConsoleFont
- GetCurrentConsoleFont
MS-HAID:
- '\_win32\_getcurrentconsolefont'
- base.getcurrentconsolefont
- consoles.getcurrentconsolefont
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 347508ea-5c15-4568-b99f-1e7f5cdac8c1
topic_type:
- apiref
api_name:
- GetCurrentConsoleFont
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: b394f116a75e3c8fb7fddbdc3335e89fbca96652
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037856"
---
# <a name="getcurrentconsolefont-function"></a>GetCurrentConsoleFont 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

抓取目前主控台字型的相關資訊。

## <a name="syntax"></a>語法

```C
BOOL WINAPI GetCurrentConsoleFont(
  _In_  HANDLE             hConsoleOutput,
  _In_  BOOL               bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFO lpConsoleCurrentFont
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[在\]  
主控台螢幕緩衝區的控制碼。 控制碼必須具有 **一般 \_ 讀取** 許可權。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*bMaximumWindow* \[在\]  
如果此參數為 **TRUE** ，就會針對最大視窗大小抓取字型資訊。 如果此參數為 **FALSE** ，則會針對目前的視窗大小抓取字型資訊。

*lpConsoleCurrentFont* \[擴展\]  
[**主控台 \_ 字型 \_ 資訊**](console-font-info-str.md)結構的指標，此結構會接收要求的字型資訊。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0500 或更新版本。 如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | \[僅限 WINDOWS XP desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2003 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi3 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>請參閱

[主控台功能](console-functions.md)

[主控台畫面緩衝區](console-screen-buffers.md)

[**主控台 \_ 字型 \_ 資訊**](console-font-info-str.md)

[**GetConsoleFontSize**](getconsolefontsize.md)

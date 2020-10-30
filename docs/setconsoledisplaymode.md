---
title: SetConsoleDisplayMode 函式
description: 請參閱 SetConsoleDisplayMode 函式的參考資訊，此函式會設定指定的主控台螢幕緩衝區的顯示模式。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 52d7e50d7ced5615cb296c0590876e4604057e42
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039386"
---
# <a name="setconsoledisplaymode-function"></a>SetConsoleDisplayMode 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

設定指定之主控台螢幕緩衝區的顯示模式。

## <a name="syntax"></a>語法

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[在\]  
主控台螢幕緩衝區的控制碼。

*dwFlags* \[在\]  
主控台的顯示模式。 這個參數可以是下列一或多個值。

| 值 | 意義 |
|-|-|
| **CONSOLE_FULLSCREEN_MODE** 1 | 文字會以全螢幕模式顯示。 |
| **CONSOLE_WINDOWED_MODE** 2 | 文字會顯示在主控台視窗中。 |

*lpNewScreenBufferDimensions* \[out、optional\]  
[**COORD**](coord-str.md)結構的指標，此結構會接收螢幕緩衝區的新維度（以字元為單位）。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | \[僅限 WINDOWS XP desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2003 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi3 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>請參閱

[主控台功能](console-functions.md)

[主控台模式](console-modes.md)

[**GetConsoleDisplayMode**](getconsoledisplaymode.md)

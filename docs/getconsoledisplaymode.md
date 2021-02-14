---
title: GetConsoleDisplayMode 函式
description: 請參閱 GetConsoleDisplayMode 函式的參考資訊，此函數會抓取目前主控台的顯示模式。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 5b9ec78dc6fe5d7baa1a9af64010fd577f101c47
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358348"
---
# <a name="getconsoledisplaymode-function"></a>GetConsoleDisplayMode 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

抓取目前主控台的顯示模式。

## <a name="syntax"></a>語法

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

## <a name="parameters"></a>參數

*lpModeFlags* \[擴展\]  
主控台的顯示模式。 這個參數可以是下列一或多個值。

| 值 | 意義 |
|-|-|
| **CONSOLE_FULLSCREEN** 1 | 全螢幕主控台。 當視窗最大化時，主控台便會處於此模式。 到目前為止，轉換成全螢幕模式仍然可能失敗。 |
| **CONSOLE_FULLSCREEN_HARDWARE** 2 | 全螢幕主控台會直接與影片硬體通訊。 主控台處於 **CONSOLE_FULLSCREEN** 模式之後，就會設定此模式，以指出已完成轉換至全螢幕模式。 |

> [!NOTE]
> 在 Windows Vista 中，已將遷移圖形堆疊的轉換成100% 的全螢幕影片硬體模式，並將其轉換成 [WDDM](//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model)。 在較新版本的 Windows 中，產生的最大狀態 **CONSOLE_FULLSCREEN** 代表 frameless 視窗，該視窗會顯示為全螢幕，但無法獨佔控制硬體。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0500 或更新版本。 如需詳細資訊，請參閱 [使用 Windows 標頭](/windows/win32/winprog/using-the-windows-headers)。

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | \[僅限 WINDOWS XP desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2003 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi3 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

[主控台模式](console-modes.md)

[**SetConsoleDisplayMode**](setconsoledisplaymode.md)
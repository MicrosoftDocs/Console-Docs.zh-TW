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
ms.openlocfilehash: 74dc06cbb7ecadb0f86c4c4a992e3526be8ab74d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038056"
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
> 在 Windows Vista 中，已將遷移圖形堆疊的轉換成100% 的全螢幕影片硬體模式，並將其轉換成 [WDDM](https://docs.microsoft.com//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model)。 在較新版本的 Windows 中，產生的最大狀態 **CONSOLE_FULLSCREEN** 代表 frameless 視窗，該視窗會顯示為全螢幕，但無法獨佔控制硬體。

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

[主控台模式](console-modes.md)

[**SetConsoleDisplayMode**](setconsoledisplaymode.md)

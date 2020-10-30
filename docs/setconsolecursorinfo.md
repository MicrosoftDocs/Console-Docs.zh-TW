---
title: SetConsoleCursorInfo 函式
description: 為指定的主控台螢幕緩衝區設定資料指標的大小和可見度。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleCursorInfo
- wincon/SetConsoleCursorInfo
- SetConsoleCursorInfo
MS-HAID:
- '\_win32\_setconsolecursorinfo'
- base.setconsolecursorinfo
- consoles.setconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c98cbffb-18de-41e8-bba7-5fb46a0c5d25
topic_type:
- apiref
api_name:
- SetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4bbb14dd501d483f35fbce5e1a729eaf002b1579
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039396"
---
# <a name="setconsolecursorinfo-function"></a>SetConsoleCursorInfo 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

為指定的主控台螢幕緩衝區設定資料指標的大小和可見度。

## <a name="syntax"></a>語法

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[在\]  
主控台螢幕緩衝區的控制碼。 控制碼必須具有 **一般 \_ 讀取** 許可權。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpConsoleCursorInfo* \[在\]  
主控台資料指標 [**\_ \_ 資訊**](console-cursor-info-str.md) 結構的指標，此結構會提供主控台螢幕緩衝區之游標的新規格。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

當螢幕緩衝區的游標可見時，其外觀可能會有所不同，範圍從完全填滿字元儲存格到顯示為數據格底部的水平線條。 [**主控台資料 \_ 指標 \_ 資訊**](console-cursor-info-str.md)結構的 **dwSize** 成員會指定資料指標所填滿的字元資料格百分比。 如果這個成員小於1或大於100， **SetConsoleCursorInfo** 就會失敗。

> [!TIP]
> 此 API 在具有和順序的資料 **[指標可見度](console-virtual-terminal-sequences.md#cursor-visibility)** 區段中具有相當的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機 `^[[?25h` `^[[?25l` 。 

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>請參閱

[主控台功能](console-functions.md)

[主控台畫面緩衝區](console-screen-buffers.md)

[**主控台資料 \_ 指標 \_ 資訊**](console-cursor-info-str.md)

[**GetConsoleCursorInfo**](getconsolecursorinfo.md)

[**SetConsoleCursorPosition**](setconsolecursorposition.md)

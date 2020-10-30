---
title: SetConsoleScreenBufferInfoEx 函式
description: 將指定之主控台畫面緩衝區的擴充資訊設定為指定的緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleScreenBufferInfoEx
- wincon/SetConsoleScreenBufferInfoEx
- SetConsoleScreenBufferInfoEx
MS-HAID:
- base.setconsolescreenbufferinfoex
- consoles.setconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ff851144-eee9-4410-8fd1-28aa24fc25f1
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4a83c91a60a26d8e962efdf10b127e97beb70a7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039346"
---
# <a name="setconsolescreenbufferinfoex-function"></a>SetConsoleScreenBufferInfoEx 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

設定指定的主控台螢幕緩衝區的延伸資訊。

## <a name="syntax"></a>語法

```C
BOOL WINAPI SetConsoleScreenBufferInfoEx(
  _In_ HANDLE                        hConsoleOutput,
  _In_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[在\]  
主控台螢幕緩衝區的控制碼。 控制碼必須有 **一般 \_ 寫入** 存取權限。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpConsoleScreenBufferInfoEx* \[在\]  
[**主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX**](console-screen-buffer-infoex.md)結構，其中包含主控台螢幕緩衝區資訊。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

> [!TIP]
> 此 API 具有對等的部分 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。 資料 **[指標定位緩衝區](console-virtual-terminal-sequences.md#cursor-positioning)** 和 **[文字屬性](console-virtual-terminal-sequences.md#text-formatting)** 具有特定的順序對應。 Color 資料表無法設定，但是 **[擴充色彩](console-virtual-terminal-sequences.md#extended-colors)** 的可用範圍，通常是透過主控台函式所提供的 **[功能](console-functions.md)** 。 Popup 屬性沒有對等專案，因為快顯功能表是 **虛擬終端** 機世界中命令列用戶端應用程式的責任。 最後，視窗和全螢幕狀態的大小會被視為 **虛擬終端** 機世界中使用者所擁有的許可權，而且沒有對等的順序。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | \[僅限 Windows Vista 桌面應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2008 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>請參閱

[主控台功能](console-functions.md)

[**主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX**](console-screen-buffer-infoex.md)

[**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md)

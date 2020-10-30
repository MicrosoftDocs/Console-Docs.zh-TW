---
title: GetLargestConsoleWindowSize 函式
description: 根據目前的字型和顯示器的大小，抓取最大可能主控台視窗的大小。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/GetLargestConsoleWindowSize
- wincon/GetLargestConsoleWindowSize
- GetLargestConsoleWindowSize
MS-HAID:
- '\_win32\_getlargestconsolewindowsize'
- base.getlargestconsolewindowsize
- consoles.getlargestconsolewindowsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3e5897f3-4987-4a82-ab19-06c0b231ba67
topic_type:
- apiref
api_name:
- GetLargestConsoleWindowSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: ddaa4716886fccaaa87e86362719020eb2408765
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037836"
---
# <a name="getlargestconsolewindowsize-function"></a>GetLargestConsoleWindowSize 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

根據目前的字型和顯示器的大小，抓取最大可能主控台視窗的大小。

## <a name="syntax"></a>語法

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[在\]  
主控台螢幕緩衝區的控制碼。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值是 [**COORD**](coord-str.md)結構，可指定在最大可能的主控台視窗中， ( **Y** 成員) 的字元資料格資料行數目 ( **X** 成員) 和資料列。 否則，結構的成員為零。

若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

此函式不會考慮主控台螢幕緩衝區的大小，這表示傳回的視窗大小可能會大於主控台螢幕緩衝區的大小。 您可以使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函式來判斷主控台視窗的大小上限（指定目前的螢幕緩衝區大小、目前的字型和顯示大小）。

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

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

[**COORD**](coord-str.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[視窗和螢幕緩衝區大小](window-and-screen-buffer-size.md)

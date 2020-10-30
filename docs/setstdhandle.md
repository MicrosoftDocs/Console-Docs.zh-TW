---
title: SetStdHandle 函式
description: 設定指定標準裝置的控制碼 (標準輸入、標準輸出或標準錯誤) 。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 36531872df90239e2b909c80fb75ad3011280c78
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039296"
---
# <a name="setstdhandle-function"></a>SetStdHandle 函式

設定指定標準裝置的控制碼 (標準輸入、標準輸出或標準錯誤) 。

## <a name="syntax"></a>語法

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

## <a name="parameters"></a>參數

*nStdHandle* \[在\]  
要設定控制碼的標準裝置。 這個參數可以是下列其中一個值。

| 值 | 意義 |
|-|-|
| **STD_INPUT_HANDLE** (DWORD) -10 | 標準輸入設備。 一開始，這是主控台輸入緩衝區 `CONIN$` 。 |
| **STD_OUTPUT_HANDLE** (DWORD) -11 | 標準輸出裝置。 這一開始是使用中的主控台畫面緩衝區 `CONOUT$` 。 |
| **STD_ERROR_HANDLE** (DWORD) -12 | 標準錯誤裝置。 這一開始是使用中的主控台畫面緩衝區 `CONOUT$` 。 |

*hHandle* \[在\]  
標準裝置的控制碼。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

對 **SetStdHandle** 的呼叫可能會重新導向進程的標準控制碼，在這種情況下， [**GetStdHandle**](getstdhandle.md) 會傳回重新導向的控制碼。 如果已重新導向標準控制碼，您可以在 [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) 函式的呼叫中指定 CONIN $ 值，以取得主控台輸入緩衝區的控制碼。 同樣地，您可以指定 CONOUT $ 值，以取得主控台的作用中螢幕緩衝區的控制碼。

## <a name="examples"></a>範例

如需範例，請參閱 [使用重新導向的輸入和輸出建立子進程](https://msdn.microsoft.com/library/windows/desktop/ms682499)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ProcessEnv .h (via Winbase，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>請參閱

[主控台功能](console-functions.md)

[主控台控制代碼](console-handles.md)

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[**GetStdHandle**](getstdhandle.md)

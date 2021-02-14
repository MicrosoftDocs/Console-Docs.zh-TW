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
ms.openlocfilehash: 317acd84289e5138e1a947251e745077ba581083
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358508"
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

*nStdHandle* \[輸入\]  
要設定控制碼的標準裝置。 此參數可以是下列其中一個值。

| 值 | 意義 |
|-|-|
| **STD_INPUT_HANDLE** (DWORD) -10 | 標準輸入裝置。 一開始，這是主控台輸入緩衝區 `CONIN$`。 |
| **STD_OUTPUT_HANDLE** (DWORD) -11 | 標準輸出裝置。 一開始，這是作用中的主控台畫面緩衝區 `CONOUT$`。 |
| **STD_ERROR_HANDLE** (DWORD) -12 | 標準錯誤裝置。 一開始，這是作用中的主控台畫面緩衝區 `CONOUT$`。 |

*hHandle* \[在\]  
標準裝置的控制碼。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

對 **SetStdHandle** 的呼叫可能會重新導向進程的標準控制碼，在這種情況下， [**GetStdHandle**](getstdhandle.md) 會傳回重新導向的控制碼。 如果已重新導向標準控制碼，您可以在 [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) 函式的呼叫中指定 CONIN $ 值，以取得主控台輸入緩衝區的控制碼。 同樣地，您可以指定 CONOUT $ 值，以取得主控台的作用中螢幕緩衝區的控制碼。

## <a name="examples"></a>範例

如需範例，請參閱 [使用重新導向的輸入和輸出建立子進程](/windows/win32/procthread/creating-a-child-process-with-redirected-input-and-output)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | ProcessEnv.h (透過 Winbase.h，包括 Windows.h) |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

[主控台控制代碼](console-handles.md)

[**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[**GetStdHandle**](getstdhandle.md)
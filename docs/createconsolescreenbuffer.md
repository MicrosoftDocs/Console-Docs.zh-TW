---
title: CreateConsoleScreenBuffer 函式
description: CreateConsoleScreenBuffer 函式會建立 Windows 主控台的螢幕緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/CreateConsoleScreenBuffer
- wincon/CreateConsoleScreenBuffer
- CreateConsoleScreenBuffer
MS-HAID:
- '\_win32\_createconsolescreenbuffer'
- base.createconsolescreenbuffer
- consoles.createconsolescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98bb74e4-dad2-4615-9263-48ba778a06ff
topic_type:
- apiref
api_name:
- CreateConsoleScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0b8f5b33233f49167c67a47f33e5a95b8864f7bd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039128"
---
# <a name="createconsolescreenbuffer-function"></a>CreateConsoleScreenBuffer 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

建立主控台螢幕緩衝區。

## <a name="syntax"></a>語法

```C
HANDLE WINAPI CreateConsoleScreenBuffer(
  _In_             DWORD               dwDesiredAccess,
  _In_             DWORD               dwShareMode,
  _In_opt_   const SECURITY_ATTRIBUTES *lpSecurityAttributes,
  _In_             DWORD               dwFlags,
  _Reserved_       LPVOID              lpScreenBufferData
);
```

## <a name="parameters"></a>參數

*dwDesiredAccess* \[在\]  
主控台螢幕緩衝區的存取權。 如需存取權限的清單，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*dwShareMode* \[在\]  
這個參數可以是零，表示無法共用緩衝區，也可以是下列其中一個或多個值。

| 值 | 意義 |
|-|-|
| **FILE_SHARE_READ** 0x00000001 | 您可以在主控台螢幕緩衝區上執行其他開啟的作業，以進行讀取存取。 |
| **FILE_SHARE_WRITE** 0x00000002 | 您可以在主控台螢幕緩衝區上執行其他開啟的作業，以進行寫入存取。 |

*lpSecurityAttributes* \[在中，選擇性\]  
[**安全性 \_ 屬性**](https://msdn.microsoft.com/library/windows/desktop/aa379560)結構的指標，可判斷是否可由子進程繼承傳回的控制碼。 如果 *lpSecurityAttributes* 為 **Null** ，則無法繼承控制碼。 結構的 **lpSecurityDescriptor** 成員會指定新主控台螢幕緩衝區的安全描述項。 如果 *lpSecurityAttributes* 為 **Null** ，則主控台螢幕緩衝區會取得預設安全描述項。 主控台螢幕緩衝區之預設安全描述項中的 Acl 來自于建立者的主要或模擬權杖。

*dwFlags* \[在\]  
要建立的主控台螢幕緩衝區類型。 唯一支援的螢幕緩衝區類型是 **主控台 \_ TEXTMODE \_ 緩衝區** 。

*lpScreenBufferData*  
保護應為 **Null** 。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值是新主控台螢幕緩衝區的控制碼。

如果函式失敗，則傳回值是 **不正確 \_ 控制碼 \_ 值** 。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

主控台可以有多個螢幕緩衝區，但只能有一個使用中的螢幕緩衝區。 您可以存取非作用中的螢幕緩衝區以進行讀取和寫入，但是只會顯示作用中螢幕緩衝區。 若要讓新的螢幕緩衝區變成使用中的螢幕緩衝區，請使用 [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) 函式。

新建立的螢幕緩衝區會在呼叫此函式時，從現用螢幕緩衝區複製一些屬性。 行為如下所示：

- `Font` -從 active screen 緩衝區複製
- `Display Window Size` -從 active screen 緩衝區複製
- `Buffer Size` -符合 `Display Window Size` **未** 複製的 () 
- `Default Attributes` (色彩) -從現用螢幕緩衝區複製
- `Default Popup Attributes` (色彩) -從現用螢幕緩衝區複製

呼叫進程可以在任何需要控制主控台螢幕緩衝區的函式中使用傳回的控制碼，但受限於 *dwDesiredAccess* 參數所指定的存取限制。

呼叫進程可使用 [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) 函式來建立重複的螢幕緩衝區控制碼，此控制碼具有與原始控制碼不同的存取或可繼承。 不過， **DuplicateHandle** 無法用來建立對不同進程 (有效的重複項，但透過繼承) 除外。

若要關閉主控台畫面緩衝區控制碼，請使用 [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) 函數。

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a>範例

如需範例，請參閱 [讀取和寫入字元和屬性的區塊](reading-and-writing-blocks-of-characters-and-attributes.md)。

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

[**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211)

[**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**安全性 \_ 屬性**](https://msdn.microsoft.com/library/windows/desktop/aa379560)

[**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md)

[**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md)

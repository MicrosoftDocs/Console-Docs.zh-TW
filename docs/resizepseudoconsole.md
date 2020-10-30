---
title: ResizePseudoConsole 函式
description: 請參閱 ResizePseudoConsole 函式的參考資訊，此函式會將 pseudoconsole 的內部緩衝區大小調整為指定的大小。
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api，conpty，pseudoconsole
f1_keywords:
- consoleapi/ResizePseudoConsole
- ResizePseudoConsole
topic_type:
- apiref
api_name:
- ResizePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 0d5a4ff954c8ebea688573f23d3981ee9c5d7d2a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037536"
---
# <a name="resizepseudoconsole-function"></a>ResizePseudoConsole 函式

將 pseudoconsole 的內部緩衝區大小調整為指定的大小。

## <a name="syntax"></a>語法

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

## <a name="parameters"></a>參數

*hPC* \[在\]  
由 [CreatePseudoConsole](createpseudoconsole.md)開啟之作用中 pseudoconsole 的控制碼。

*大小* \[在\]  
視窗/緩衝區的大小（以字元數為單位），將用於此 pseudoconsole 的內部緩衝區。

## <a name="return-value"></a>傳回值

類型： **HRESULT**

如果這個方法成功，它會傳回 **S_OK** 。 否則，它會傳回 **HRESULT** 錯誤碼。

## <a name="remarks"></a>備註

此函數可以調整 pseudoconsole 會話中的內部緩衝區大小，以符合終端機端上所用的視窗/緩衝區大小。 這可確保使用 [主控台](console-functions.md) 函式進行通訊的附加 Command-Line 介面 (CUI) 應用程式將會在其呼叫中傳回正確的維度。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 10 2018 年10月更新 (1809 版) \[ 桌面應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2019 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>請參閱

[Pseudoconsoles](pseudoconsoles.md)

[**CreatePseudoConsole**](createpseudoconsole.md)

[**ClosePseudoConsole**](closepseudoconsole.md)

---
title: ClosePseudoConsole 函式
description: 請參閱 ClosePseudoConsole 函式的參考資訊，此函式會從指定的控制碼關閉 pseudoconsole。
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api，conpty，pseudoconsole
topic_type:
- apiref
api_name:
- ClosePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 067fa732f5badfe46ee6391c892aa037613cb4dd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037286"
---
# <a name="closepseudoconsole-function"></a>ClosePseudoConsole 函式

從給定的控制碼關閉 pseudoconsole。

## <a name="syntax"></a>語法

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC
);
```

## <a name="parameters"></a>參數

*hPC* \[在\]  
由 [CreatePseudoConsole](createpseudoconsole.md)開啟之作用中 pseudoconsole 的控制碼。

## <a name="return-value"></a>傳回值

無

## <a name="remarks"></a>備註

在關閉 pseudoconsole 時，附加至會話的用戶端應用程式也會終止。

當呼叫此 API 時，最後繪製的框架可能會抵達 `hOutput` 最初提供給 [CreatePsuedoConsole](createpseudoconsole.md) 的控制碼。 呼叫端應該會清空通道緩衝區中的這項資訊，並將其呈現或捨棄。 若無法清空緩衝區，可能會導致關閉呼叫無限期等候，直到它被清空或通道以另一種方式中斷為止。

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

[**ResizePseudoConsole**](resizepseudoconsole.md)

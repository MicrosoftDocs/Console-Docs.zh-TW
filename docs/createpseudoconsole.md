---
title: CreatePseudoConsole 函式
description: 請參閱 CreatePseudoConsole 函式的參考資訊，此函式會為呼叫進程配置新的 pseudoconsole。
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api，conpty，pseudoconsole
f1_keywords:
- consoleapi/CreatePseudoConsole
- CreatePseudoConsole
topic_type:
- apiref
api_name:
- CreatePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 91958b23348895f7454c9228e3c730d231dc4f0b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357938"
---
# <a name="createpseudoconsole-function"></a>CreatePseudoConsole 函式

為呼叫進程建立新的 pseudoconsole 物件。

## <a name="syntax"></a>語法

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

## <a name="parameters"></a>參數

*大小* \[在\]  
將在初始建立 pseudoconsole 時使用的視窗/緩衝區維度（以字元數為單位）。 這可以在稍後使用 [ResizePseudoConsole](resizepseudoconsole.md)進行調整。

*hInput* \[在\]  
表示使用者輸入至裝置之資料流程的開啟控制碼。 這目前僅限於 [同步](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) i/o。

*hOutput* \[在\]  
代表裝置應用程式輸出的資料流程的開啟控制碼。 這目前僅限於 [同步](/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) i/o。

*dwFlags* \[在\]  
這個值可以是下列值之一：

| 值 | 意義 |
|-|-|
| **0** | 執行標準 pseudoconsole 建立。 |
| **PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD) 1 | 建立的 pseudoconsole 會話將嘗試繼承父主控台的游標位置。 |

*phPC* \[擴展\]  
將接收新 pseudoconsole 裝置之控制碼的位置指標。

## <a name="return-value"></a>傳回值

類型： **HRESULT**

如果這個方法成功，它會傳回 **S_OK**。 否則，它會傳回 **HRESULT** 錯誤碼。

## <a name="remarks"></a>備註

這項功能主要是由應用程式嘗試作為命令列使用者介面的終端機視窗所使用 (CUI) 應用程式。 呼叫端會負責呈現輸出資料流程上的資訊，以及收集使用者輸入並將其序列化至輸入資料流程中。

編碼為 UTF-8 的輸入和輸出資料流程，包含以 [虛擬終端序列](console-virtual-terminal-sequences.md)交錯的純文字。

在輸出資料流程中，呼叫應用程式可以將 [虛擬終端機序列](console-virtual-terminal-sequences.md) 解碼為版面配置，並在顯示視窗中顯示純文字。

在輸入資料流程中，純文字代表使用者輸入的標準鍵盤按鍵。 更複雜的作業會以編碼控制鍵和滑鼠移動來表示，作為內嵌于此資料流程中的 [虛擬終端機序列](console-virtual-terminal-sequences.md) 。

當作業完成時，此函式所建立的控制碼必須在 [ClosePseudoConsole](closepseudoconsole.md) 中關閉。

如果使用 `PSEUDOCONSOLE_INHERIT_CURSOR` ，則呼叫的應用程式應該準備好在背景執行緒上以非同步方式回應資料指標狀態的要求，方法是轉送或解讀將在其上接收和回復的資料指標資訊要求 `hOutput` `hInput` 。 若未這麼做，可能會導致呼叫的應用程式在提出另一個 pseudoconsole 系統要求時停止回應。

## <a name="examples"></a>範例

如需使用此函數建立 pseudoconsole 會話的完整逐步解說，請參閱建立 [Pseudoconsole 會話](creating-a-pseudoconsole-session.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 10 2018 年10月更新 (1809 版) \[ 桌面應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2019 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi.h (透過 WinCon.h，包括 Windows.h) |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>另請參閱

[Pseudoconsoles](pseudoconsoles.md)

[建立 Pseudoconsole 工作階段](creating-a-pseudoconsole-session.md)

[**ResizePseudoConsole**](resizepseudoconsole.md)

[**ClosePseudoConsole**](closepseudoconsole.md)
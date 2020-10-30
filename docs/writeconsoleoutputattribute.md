---
title: WriteConsoleOutputAttribute 函式
description: 從指定的位置開始，將數個字元屬性複製到主控台螢幕緩衝區的連續儲存格。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/WriteConsoleOutputAttribute
- wincon/WriteConsoleOutputAttribute
- WriteConsoleOutputAttribute
MS-HAID:
- '\_win32\_writeconsoleoutputattribute'
- base.writeconsoleoutputattribute
- consoles.writeconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 52a9d6e5-072e-4411-9945-10bd3dd61e25
topic_type:
- apiref
api_name:
- WriteConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 04c7799cd98479d3b776b1933994b60f5ed9fc9f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039276"
---
# <a name="writeconsoleoutputattribute-function"></a>WriteConsoleOutputAttribute 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

從指定的位置開始，將數個字元屬性複製到主控台螢幕緩衝區的連續儲存格。

## <a name="syntax"></a>語法

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[在\]  
主控台螢幕緩衝區的控制碼。 控制碼必須有 **一般 \_ 寫入** 存取權限。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpAttribute* \[在\]  
要在寫入主控台螢幕緩衝區時使用的屬性。 如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#character-attributes)。

*nLength* \[在\]  
要將屬性複製到其中的螢幕緩衝區字元儲存格數目。

*dwWriteCoord* \[在\]  
[**COORD**](coord-str.md)結構，指定要將屬性寫入其中的主控台螢幕緩衝區中第一個資料格的字元座標。

*lpNumberOfAttrsWritten* \[擴展\]  
變數的指標，此變數會接收實際寫入主控台螢幕緩衝區的屬性數目。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

如果要寫入的屬性數目超過主控台螢幕緩衝區中指定之資料列的結尾，則會將屬性寫入至下一個資料列。 如果要寫入的屬性數目超過主控台螢幕緩衝區的結尾，則會將屬性寫入至主控台畫面緩衝區的結尾。

寫入至的位置的字元值不會變更。

> [!TIP]
> 此 API 的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機等同于 **[文字格式](console-virtual-terminal-sequences.md#text-formatting)** 和資料 **[指標定位](console-virtual-terminal-sequences.md#cursor-positioning)** 順序。 將游標移至要插入的位置，套用所需的格式，並寫出要填滿的文字。 沒有任何專案可將色彩套用至區域，也不會發出文字。 這項決策刻意讓 Windows 平臺與其他作業系統保持一致，而個別用戶端應用程式應記住自己的繪製狀態以進行進一步的操作。

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

[低層級主控台輸出功能](low-level-console-output-functions.md)

[**ReadConsoleOutput**](readconsoleoutput.md)

[**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md)

[**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md)

[**WriteConsoleOutput**](writeconsoleoutput.md)

[**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md)

---
title: ScrollConsoleScreenBuffer 函式
description: 請參閱 ScrollConsoleScreenBuffer 函式的參考資訊，此函式會在螢幕緩衝區中移動資料區塊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/ScrollConsoleScreenBuffer
- wincon/ScrollConsoleScreenBuffer
- ScrollConsoleScreenBuffer
- consoleapi2/ScrollConsoleScreenBufferA
- wincon/ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferA
- consoleapi2/ScrollConsoleScreenBufferW
- wincon/ScrollConsoleScreenBufferW
- ScrollConsoleScreenBufferW
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d78bf4c9-2314-466c-b617-619259c824b5
topic_type:
- apiref
api_name:
- ScrollConsoleScreenBuffer
- ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4ebe6efa246d627add041a5ef188fbb81294fb61
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039456"
---
# <a name="scrollconsolescreenbuffer-function"></a>ScrollConsoleScreenBuffer 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

移動螢幕緩衝區中的資料區塊。 您可以藉由指定裁剪矩形來限制移動的效果，如此一來，裁剪矩形外的主控台螢幕緩衝區內容就不會變更。

## <a name="syntax"></a>語法

```C
BOOL WINAPI ScrollConsoleScreenBuffer(
  _In_           HANDLE     hConsoleOutput,
  _In_     const SMALL_RECT *lpScrollRectangle,
  _In_opt_ const SMALL_RECT *lpClipRectangle,
  _In_           COORD      dwDestinationOrigin,
  _In_     const CHAR_INFO  *lpFill
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[在\]  
主控台螢幕緩衝區的控制碼。 控制碼必須具有 **一般 \_ 讀取** 許可權。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpScrollRectangle* \[在\]  
[**小型 \_ 矩形**](small-rect-str.md)結構的指標，其成員指定要移動之主控台螢幕緩衝區矩形的左上角和右下角座標。

*lpClipRectangle* \[在中，選擇性\]  
[**小型 \_ 矩形**](small-rect-str.md)結構的指標，其成員會指定受捲軸影響的主控台螢幕緩衝區矩形左上角和右下角的座標。 此指標可以是 **Null** 。

*dwDestinationOrigin* \[在\]  
[**COORD**](coord-str.md)結構，指定 *lpScrollRectangle* 內容新位置的左上角（以字元為單位）。

*lpFill* \[在\]  
字元 [**\_ 資訊**](char-info-str.md) 結構的指標，指定字元和色彩屬性，以用於填滿 *lpScrollRectangle* 和 *lpClipRectangle* 交集內的資料格，而這些資料格會在移動時保留空白。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

## <a name="remarks"></a>備註

**ScrollConsoleScreenBuffer** 會將螢幕緩衝區的矩形區域內容（由 *lpScrollRectangle* 參數指定）複製到主控台螢幕緩衝區的另一個區域。 目標矩形具有與 *lpScrollRectangle* 矩形相同的維度，其左上角位於 *dwDestinationOrigin* 參數所指定的座標上。 與目標矩形不重迭的 *lpScrollRectangle* 部分，會填入 *lpFill* 參數所指定的字元和色彩屬性。

裁剪矩形適用于在 *lpScrollRectangle* 矩形和目標矩形中所做的變更。 例如，如果裁剪矩形未包含已由 *lpFill* 內容填滿的區域，則該區域的原始內容會保持不變。

如果捲軸或目的地區域延伸超過主控台螢幕緩衝區的維度，則會將其裁剪。 例如，如果 *lpScrollRectangle* 是 (0、0) 和 (19、19) 和 *dwDestinationOrigin* 為 (10，15) 的區域，則目標矩形是 (10、15) 和 (29、34) 所包含的區域。 但是，如果主控台畫面緩衝區的寬度為50個字元，且高達30個字元，則會將目標矩形裁剪成 (10、15) 和 (29，29) 。 如果參數指定 [**小型的 \_ RECT**](small-rect-str.md)結構，則根據 *lpClipRectangle* ，也會裁剪主控台螢幕緩衝區的變更。 如果裁剪矩形指定為 (0、0) 和 (49、19) ，則只會進行在主控台螢幕緩衝區的該區域中發生的變更。

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> 不建議使用此 API，也不會有對等的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。 使用可近似于 **[滾動邊界](console-virtual-terminal-sequences.md#scrolling-margins)** 來修正畫面區域、將 **[游標定位](console-virtual-terminal-sequences.md#cursor-positioning)** 設定為區域外的使用中位置，以及使用分行符號來強制移動文字。 您可以藉由移動游標、 **[設定圖形屬性](console-virtual-terminal-sequences.md#text-formatting)** 和寫入一般文字來填滿剩餘的空間。

## <a name="examples"></a>範例

如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |
| Unicode 和 ANSI 名稱 | **ScrollConsoleScreenBufferW** (Unicode) 和 **ScrollConsoleScreenBufferA** (ANSI)  |

## <a name="see-also"></a>請參閱

[**字元 \_ 資訊**](char-info-str.md)

[主控台功能](console-functions.md)

[**COORD**](coord-str.md)

[滾動螢幕緩衝區](scrolling-the-screen-buffer.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**SetConsoleWindowInfo**](setconsolewindowinfo.md)

[**小型 \_ 矩形**](small-rect-str.md)

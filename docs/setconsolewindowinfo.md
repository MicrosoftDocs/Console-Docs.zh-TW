---
title: SetConsoleWindowInfo 函式
description: 設定主控台螢幕緩衝區視窗的目前大小和位置。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleWindowInfo
- wincon/SetConsoleWindowInfo
- SetConsoleWindowInfo
MS-HAID:
- '\_win32\_setconsolewindowinfo'
- base.setconsolewindowinfo
- consoles.setconsolewindowinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad16a8fe-ca91-41d6-93b1-8cce6d54b1da
topic_type:
- apiref
api_name:
- SetConsoleWindowInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: af3f9d63b01697a2ab0735014a4836d9ab11d8cf
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358528"
---
# <a name="setconsolewindowinfo-function"></a>SetConsoleWindowInfo 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

設定主控台螢幕緩衝區視窗的目前大小和位置。

## <a name="syntax"></a>語法

```C
BOOL WINAPI SetConsoleWindowInfo(
  _In_       HANDLE     hConsoleOutput,
  _In_       BOOL       bAbsolute,
  _In_ const SMALL_RECT *lpConsoleWindow
);
```

## <a name="parameters"></a>參數

*hConsoleOutput* \[in\]  
主控台螢幕緩衝區的控點。 控制代碼必須具有 **GENERIC\_READ** 存取權限。 如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*bAbsolute* \[在\]  
如果此參數為 **TRUE**，座標會指定視窗的新左上角和右下角。 如果為 **FALSE**，則座標相對於目前的視窗邊角座標。

*lpConsoleWindow* \[在\]  
[**小 \_ 矩形**](small-rect-str.md)結構的指標，指定視窗的新左上角和右下角。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回非零的值。

如果此函式失敗，則傳回值為零。 若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。

## <a name="remarks"></a>備註

如果指定的視窗矩形延伸超過主控台螢幕緩衝區的界限，則函式會失敗。 這表示，如果 *bAbsolute* 為 FALSE，則 *LpConsoleWindow* 矩形的 **top** 和 **left** 成員 (或計算的上和左座標，) 不能小於零。 同樣地， **底部** 和 **右邊** 的成員 (或計算的右下座標) 不能大於 (螢幕緩衝區高度– 1) 和 (螢幕緩衝區寬度-1) 。 如果 **右邊** 的成員 (或計算的右座標) 小於或等於 **左邊** 的成員 (或計算的左座標) 或 **底部** 成員 (或計算下座標) 小於或等於 **最上層** 成員 (或計算出的最上層座標) ，則函式也會失敗。

針對具有多個螢幕緩衝區的主控台，變更一個螢幕緩衝區的視窗位置並不會影響其他螢幕緩衝區的視窗位置。

若要判斷螢幕緩衝區視窗目前的大小和位置，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數。 這個函式也會根據目前的螢幕緩衝區大小、目前的字型大小和螢幕大小，傳回視窗的大小上限。 [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)函式會傳回目前的字型和螢幕大小的最大視窗大小，但不會考慮主控台畫面緩衝區的大小。

**SetConsoleWindowInfo** 可以用來滾動視窗矩形的位置，而不需要變更其大小。

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="examples"></a>範例

如需範例，請參閱 [滾動螢幕緩衝區視窗](scrolling-a-screen-buffer-s-window.md)。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | Windows 2000 Professional \[僅限傳統型應用程式\] |
| 最低支援的伺服器 | Windows 2000 Server \[僅限傳統型應用程式\] |
| 標頭 | ConsoleApi2 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>另請參閱

[主控台函式](console-functions.md)

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md)

[滾動螢幕緩衝區](scrolling-the-screen-buffer.md)

[**小型 \_ 矩形**](small-rect-str.md)
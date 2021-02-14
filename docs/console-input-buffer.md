---
title: 主控台輸入緩衝區
description: 每個主控台都有一個輸入緩衝區，其中包含輸入事件記錄的佇列。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_console\_input\_buffer'
- base.console\_input\_buffer
- consoles.console\_input\_buffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6e536658-8a27-478e-82ee-d1e11f351301
ms.openlocfilehash: d5d3604d3d4f2738af01ae1bc051c10af6249c62
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358108"
---
# <a name="console-input-buffer"></a>主控台輸入緩衝區

每個主控台都有一個輸入緩衝區，其中包含輸入事件記錄的佇列。 當主控台的視窗具有鍵盤焦點時，主控台會將每個輸入事件格式化 (例如單一按鍵、移動滑鼠，或是按下滑鼠按鍵，) 為它放在主控台輸入緩衝區中的輸入記錄。

應用程式可以使用 [高階主控台 i/o](high-level-console-input-and-output-functions.md)函式來間接存取主控台的輸入緩衝區，或直接使用 [低層級的主控台輸入功能](low-level-console-input-functions.md)來存取。 高層級輸入函式會篩選和處理輸入緩衝區中的資料，只傳回輸入字元的資料流程。 低層級的輸入函數可讓應用程式直接從主控台的輸入緩衝區讀取輸入記錄，或將輸入記錄放入輸入緩衝區。 若要開啟主控台輸入緩衝區的控制碼，請在 [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea)函數的呼叫中指定 **CONIN $** 值。

輸入記錄是一種結構，其中包含 (鍵盤、滑鼠、視窗調整大小、焦點或功能表) 事件時所發生之事件種類的相關資訊，以及事件的特定詳細資料。 [**輸入 \_ 記錄**](input-record-str.md)結構中的 **「事件種類」成員會** 指出記錄中包含哪一種類型的事件。

焦點和功能表事件都放在主控台的輸入緩衝區中，供系統內部使用，且應用程式應予以忽略。

## <a name="keyboard-events"></a>鍵盤事件

當按下或放開任何按鍵時，就會產生鍵盤事件;這包括控制項索引鍵。 不過，當按下並放開時，ALT 鍵對系統具有特殊意義，而不會與另一個字元合併，且不會傳遞至應用程式。 此外，如果輸入控制碼處於處理模式，則不會傳遞 CTRL + C 按鍵組合。

如果輸入事件是按鍵，[**輸入 \_ 記錄**](input-record-str.md)中的 **事件** 成員就是包含下列資訊的 [**關鍵 \_ 事件 \_ 記錄**](key-event-record-str.md)結構：

- 指出是否已按下或放開按鍵的布林值。
- 當索引鍵被關閉時，可以大於1的重複計數。
- 虛擬金鑰程式碼，以與裝置無關的方式識別指定的金鑰。
- 虛擬掃描程式碼，表示鍵盤硬體所產生的裝置相依值。
- 翻譯的 Unicode™或 ANSI 字元。
- 旗標變數，表示控制項索引鍵的狀態 (ALT、CTRL、SHIFT、NUM LOCK、SCROLL LOCK 和 CAPS LOCK 索引鍵) 並指出是否已按下增強的按鍵。 適用于 IBM® 101-金鑰和102金鑰鍵盤的增強金鑰為 )  (數位鍵台左邊的叢集中的 INS、DEL、HOME、END、PAGE UP、PAGE DOWN 和箭號，並在數位鍵台中輸入按鍵。

## <a name="mouse-events"></a>滑鼠事件

每當使用者移動滑鼠或按下或放開其中一個滑鼠按鍵時，就會產生滑鼠事件。 只有在符合下列條件時，滑鼠事件才會放在輸入緩衝區中：

- 主控台輸入模式設定為啟用 (預設模式) 的 **\_ 滑鼠 \_ 輸入** 。
- 主控台視窗具有鍵盤焦點。
- 滑鼠指標位於主控台視窗的框線內。

如果輸入事件是滑鼠事件，[**輸入 \_ 記錄**](input-record-str.md)中的 **事件** 成員就是包含下列資訊的 [**滑鼠 \_ 事件 \_ 記錄**](mouse-event-record-str.md)結構：

- 滑鼠指標在主控台螢幕緩衝區座標系統中的字元儲存格資料列和資料行的座標。
- 旗標變數，指出滑鼠按鍵的狀態。
- 旗標變數，表示控制項索引鍵的狀態 (ALT、CTRL、SHIFT、NUM LOCK、SCROLL LOCK 和 CAPS LOCK) 並指出是否已按下增強的按鍵。 適用于 IBM 101-金鑰和102鍵鍵盤的增強金鑰為數字鍵臺上左邊叢集中的 INS、DEL、HOME、END、PAGE UP、PAGE DOWN 和箭號，以及 (/) 並在數位鍵台中輸入按鍵。
- 旗標變數，指出事件是一般按鈕按下或按鈕釋放事件、滑鼠移動事件，還是第二次按一下按兩下事件。

> [!NOTE]
>滑鼠位置座標是以主控台畫面緩衝區為單位，而不是主控台視窗。 螢幕緩衝區可能已針對視窗進行滾動，因此視窗的左上角不一定是主控台螢幕緩衝區的 (0、0) 座標。 若要判斷相對於視窗座標系統的滑鼠座標，請從滑鼠位置座標減去視窗原點座標。 您可以使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函式來判斷視窗原始座標。

[**滑鼠 \_ 事件 \_ 記錄**](mouse-event-record-str.md)結構的 **dwButtonState** 成員具有對應至每個滑鼠按鍵的位。 如果按鈕已關閉，則位為1，如果按鈕為開啟，則為0。 **滑鼠 \_ 事件 \_ 記錄** 的 **dwEventFlags** 成員有0個值的按鈕發行事件，以及從1到0的按鈕位變更。 [**GetNumberOfConsoleMouseButtons**](getnumberofconsolemousebuttons.md)函式會捕獲滑鼠上的按鈕數目。

## <a name="buffer-resizing-events"></a>Buffer-Resizing 事件

主控台視窗的功能表可讓使用者變更活動畫面緩衝區的大小;這種變更會產生緩衝區調整大小的事件。 如果主控台的輸入模式設定為 **啟用 \_ 視窗 \_ 輸入** (也就是停用預設模式) ，則會將緩衝區調整大小的事件放在輸入緩衝區中。

如果輸入事件是緩衝區調整大小的事件，則 [**輸入 \_ 記錄**](input-record-str.md)的 **事件** 成員是包含主控台螢幕緩衝區新大小的 [**視窗 \_ 緩衝區 \_ 大小 \_ 記錄**](window-buffer-size-record-str.md)結構，以字元儲存格的資料行和資料清單示。

如果使用者減少了主控台螢幕緩衝區的大小，則會遺失緩衝區捨棄部分中的任何資料。

由於應用程式呼叫 [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) 函式而導致主控台螢幕緩衝區大小的變更，不會產生為緩衝區調整大小的事件。
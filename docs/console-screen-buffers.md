---
title: 主控台畫面緩衝區
description: 螢幕緩衝區是在主控台視窗中輸出之字元和色彩資料的二維陣列。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_console\_screen\_buffers'
- base.console\_screen\_buffers
- consoles.console\_screen\_buffers
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f94995fc-5f5f-4fcd-969d-7e10020634c2
ms.localizationpriority: high
ms.openlocfilehash: 4c5740be3b60d54f9e7b586b41e962a4102222a0
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420197"
---
# <a name="console-screen-buffers"></a>主控台畫面緩衝區

*螢幕緩衝區* 是在主控台視窗中輸出之字元和色彩資料的二維陣列。 主控台可以有多個螢幕緩衝區。 *活動畫面緩衝區* 是顯示在畫面上的緩衝區。

當系統建立新的主控台時，系統會建立一個螢幕緩衝區。 若要開啟主控台的主動螢幕緩衝區的控制碼，請在 [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)函數的呼叫中指定 **CONOUT $** 值。 進程可以使用 [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) 函式來建立其主控台的其他螢幕緩衝區。 新的螢幕緩衝區在 [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) 函式的呼叫中指定其控制碼之前，不會處於使用中狀態。 不過，您可以存取螢幕緩衝區以讀取和寫入它們是否為作用中或非使用中狀態。

每個螢幕緩衝區都有自己的二維字元資訊記錄陣列。 每個字元的資料會儲存在 [**CHAR \_ 資訊**](char-info-str.md) 結構中，指定 Unicode 或 ANSI 字元，以及顯示該字元的前景和背景色彩。

您可以針對每個螢幕緩衝區個別設定與螢幕緩衝區相關聯的數個屬性。 這表示變更主動螢幕緩衝區可能會對主控台視窗的外觀造成顯著的影響。 與螢幕緩衝區相關聯的屬性包括：

- 螢幕緩衝區大小，以字元的資料列和資料行。
- Text 屬性 (前景和背景色彩，以顯示 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 或 [**WriteConsole**](writeconsole.md) 函式) 所要寫入的文字。
- [視窗大小] 和 [位置] (顯示在主控台視窗) 的主控台螢幕緩衝區的矩形區域。
- 游標位置、外觀和可見度。
- 輸出模式 (**啟用 \_ 處理的 \_ 輸出** ，並 **\_ \_ 在 \_ EOL \_ 輸出) 啟用包裝** 。 如需主控台輸出模式的詳細資訊，請參閱 [高階主控台模式](high-level-console-modes.md)。

建立螢幕緩衝區時，它會在每個位置包含空白字元。 它的資料指標是可見的，位於緩衝區的原點 (0，0) ，而視窗的位置是在緩衝區原點的左上角。 主控台螢幕緩衝區的大小、視窗大小、文字屬性，以及游標的外觀是由使用者或系統預設值所決定。 若要取得與主控台螢幕緩衝區相關聯之各種屬性的目前值，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)、 [**GetConsoleCursorInfo**](getconsolecursorinfo.md)和 [**GetConsoleMode**](getconsolemode.md) 函式。

變更任何主控台螢幕緩衝區內容的應用程式，應該建立自己的螢幕緩衝區，或在啟動期間儲存繼承的螢幕緩衝區狀態，並在結束時將其還原。 需要此合作行為，以確保共用相同主控台會話的其他應用程式不受變更影響。

> [!TIP]
> 建議您盡可能使用替代的 [**緩衝區模式**](console-virtual-terminal-sequences.md#alternate-screen-buffer) ，而不是針對此用途建立第二個螢幕緩衝區。 **替代緩衝區模式** 提供遠端裝置與其他平臺之間的增強相容性。 如需詳細資訊，請參閱 [**傳統主控台 api 與虛擬終端**](classic-vs-vt.md) 機的討論。

## <a name="cursor-appearance-and-position"></a>游標外觀和位置

螢幕緩衝區的游標可以是可見或隱藏的。 當它顯示時，其外觀可能會有所不同，範圍從完全填滿字元儲存格到顯示為數據格底部的水平線條。 若要取得資料指標外觀和可見度的相關資訊，請使用 [**GetConsoleCursorInfo**](getconsolecursorinfo.md) 函數。 此函數會報告資料指標是否可見，並將資料指標的外觀描述為它所填滿的字元資料格的百分比。 若要設定資料指標的外觀和可見度，請使用 [**SetConsoleCursorInfo**](setconsolecursorinfo.md) 函數。

[高層級主控台 i/o](high-level-console-i-o.md)函式所寫入的字元會寫入目前的游標位置，然後將游標移到下一個位置。 若要判斷螢幕緩衝區座標系統中目前的資料指標位置，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)。 您可以使用 [**SetConsoleCursorPosition**](setconsolecursorposition.md) 來設定游標位置，進而控制高階 i/o 函式所寫入或送出之文字的位置。 如果您移動游標，則會覆寫新游標位置的文字。

> [!NOTE]
> 不建議使用低層級的函式來尋找游標位置。 如果需要進行先進的版面配置，建議使用 [虛擬終端機序列](console-virtual-terminal-sequences.md) 來查詢此位置。 如需有關偏好虛擬終端機序列的詳細資訊，請參閱 **[傳統功能與虛擬終端](classic-vs-vt.md)** 檔。

資料指標的位置、外觀和可見度是針對每個螢幕緩衝區個別設定。

## <a name="character-attributes"></a>字元屬性

字元屬性可以分為兩個類別： color 和 DBCS。 下列屬性定義于 `WinCon.h` 標頭檔中。

| 屬性 | 意義 |
|-|-|
| **前景 \_ 藍色** | 文字色彩包含藍色。 |
| **前景 \_ 綠色** | 文字色彩包含綠色。 |
| **前景 \_ 紅色** | 文字色彩包含紅色。 |
| **前景 \_ 濃度** | 文字色彩為更。 |
| **背景 \_ 藍色** | 背景色彩包含藍色。 |
| **背景 \_ 綠色** | 背景色彩包含綠色。 |
| **背景 \_ 紅色** | 背景色彩包含紅色。 |
| **背景 \_ 濃度** | 背景色彩為更。 |
| **常見的 \_ LVB \_ 前置 \_ 位元組** | 前置位元組。 |
| **一般 \_ LVB \_ 尾端 \_ 位元組** | 尾端位元組。 |
| **一般 \_ LVB \_ 方格 \_ 水準** | 上水準。 |
| **一般 \_ LVB \_ 方格 \_ LVERTICAL** | 左方垂直。 |
| **一般 \_ LVB \_ 方格 \_ RVERTICAL** | 右垂直。 |
| **一般 \_ LVB \_ 反轉 \_ 影片** | 反向前景和背景屬性。 |
| **一般 \_ LVB \_ 底線** | 強調。 |

前景屬性會指定文字色彩。 背景屬性會指定用來填滿儲存格背景的色彩。 其他屬性則與 [DBCS](https://msdn.microsoft.com/library/windows/desktop/dd317794)一起使用。

應用程式可以結合前景和背景常數來達成不同的色彩。 例如，下列組合會產生藍色背景的亮青文字。

`FOREGROUND_BLUE | FOREGROUND_GREEN | FOREGROUND_INTENSITY | BACKGROUND_BLUE`

如果未指定背景常數，則背景為黑色，而且如果未指定前景常數，則文字為黑色。 例如，下列組合會在白色背景上產生黑色文字。

`BACKGROUND_BLUE | BACKGROUND_GREEN | BACKGROUND_RED`

每個螢幕緩衝區字元資料格都會儲存用來繪製前景 (文字) 和該儲存格背景的色彩屬性。 應用程式可以個別設定每個字元資料格的色彩資料，並將資料儲存在每個資料格之 [**CHAR \_ 資訊**](char-info-str.md)結構的 **屬性** 成員中。 每個螢幕緩衝區目前的 text 屬性會用於高階函式所寫入或回顯的字元。

應用程式可以使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 來判斷螢幕緩衝區目前的 text 屬性，以及使用 [**SetConsoleTextAttribute**](setconsoletextattribute.md) 函數來設定字元屬性。 變更螢幕緩衝區的屬性不會影響先前撰寫的字元顯示。 這些文字屬性不會影響低層級主控台 i/o 函式所寫入的字元 (例如 [**WriteConsoleOutput**](writeconsoleoutput.md) 或 [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md) 函式) ，可針對每個寫入或保留屬性的資料格明確指定屬性。

> [!NOTE]
> 不建議使用低層級的函式來操作預設和特定的文字屬性。 建議使用 [虛擬終端順序](console-virtual-terminal-sequences.md) 來設定文字屬性。 如需有關偏好虛擬終端機序列的詳細資訊，請參閱 **[傳統功能與虛擬終端](classic-vs-vt.md)** 檔。

## <a name="font-attributes"></a>字型屬性

[**GetCurrentConsoleFont**](getcurrentconsolefont.md)函式會捕獲目前主控台字型的相關資訊。 儲存在 [**主控台 \_ 字型 \_ 資訊**](console-font-info-str.md) 結構中的資訊包含字型中每個字元的寬度和高度。

[**GetConsoleFontSize**](getconsolefontsize.md)函式會抓取指定的主控台螢幕緩衝區所使用的字型大小。

> [!NOTE]
> 不建議使用函數來尋找和操作字型資訊。 建議您以字型中立的方式操作命令列應用程式，以確保跨平臺相容性，以及與允許使用者自訂字型的主機環境相容。 如需使用者喜好設定和主機環境（包括終端機）的詳細資訊，請參閱 **[生態系統藍圖](ecosystem-roadmap.md)**。

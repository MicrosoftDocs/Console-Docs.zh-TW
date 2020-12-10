---
title: 主控台畫面緩衝區
description: 「畫面緩衝區」是主控台視窗輸出中字元和色彩資料的二維陣列。
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
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420197"
---
# <a name="console-screen-buffers"></a>主控台畫面緩衝區

「畫面緩衝區」是在主控台視窗輸出中字元和色彩資料的二維陣列。 主控台可以有多個畫面緩衝區。 「作用中的畫面緩衝區」是顯示在畫面上的緩衝區。

系統會在每次建立新的主控台時建立畫面緩衝區。 若要對主控台的作用中畫面緩衝區開啟控制代碼，請在對 [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) 函式的呼叫中，指定 **CONOUT$** 值。 程序可以使用 [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) 函式，為其主控台建立額外的畫面緩衝區。 若要讓新的畫面緩衝區開始作用，則必須在呼叫 [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) 函式時指定其控制代碼。 不過，無論畫面緩衝區是否在作用中，您都可以加以存取以進行讀取和寫入。

每個畫面緩衝區本身都有字元資訊記錄的二維陣列。 每個字元的資料會以 [**CHAR\_INFO**](char-info-str.md) 結構儲存，該結構可指定 Unicode 或 ANSI 字元，以及該字元顯示的前景和背景色彩。

您可以針對每個畫面緩衝區，個別設定與畫面緩衝區相關聯的一些屬性。 這表示變更作用中的畫面緩衝區對主控台視窗外觀可能會有很大的影響。 與畫面緩衝區相關聯的屬性包括：

- 畫面緩衝區大小 (字元資料列和資料行數目)。
- 文字屬性 (顯示 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 或 [**WriteConsole**](writeconsole.md) 函式所寫入文字的前景和背景色彩)。
- 視窗大小和位置 (在主控台視窗中顯示主控台畫面緩衝區的矩形區域)。
- 游標位置、外觀和可見度。
- 輸出模式 (**ENABLE\_PROCESSED\_OUTPUT** 和 **ENABLE\_WRAP\_AT\_EOL\_OUTPUT**)。 如需有關主控台輸出模式的詳細資訊，請參閱[高階主控台模式](high-level-console-modes.md)。

畫面緩衝區建立時，即會在每個位置包含空白字元。 其游標會顯示並放置在緩衝區的原點 (0,0)，而視窗左上角的位置會放在緩衝區的原點上。 主控台畫面緩衝區的大小、視窗大小、文字屬性以及游標的外觀，都是由使用者或系統預設值所決定。 若要擷取目前與主控台畫面緩衝區相關聯的各種屬性值，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)、[**GetConsoleCursorInfo**](getconsolecursorinfo.md) 和 [**GetConsoleMode**](getconsolemode.md) 函式。

應用程式若變更任何主控台畫面緩衝區屬性，則應該建立自己的畫面緩衝區，或在啟動期間儲存繼承的畫面緩衝區狀態，並在結束時將其還原。 此合作行為是必要的，因為要確保共用相同主控台工作階段的其他應用程式不會受到變更影響。

> [!TIP]
> 如果可能，建議您日後使用 [**替代緩衝區模式**](console-virtual-terminal-sequences.md#alternate-screen-buffer)來達成此目的，而不是建立第二個畫面緩衝區。 **替代緩衝區模式** 會在遠端裝置和其他平台之間提供更高的相容性。 如需詳細資訊，請參閱 [**傳統主控台 API 與虛擬終端機**](classic-vs-vt.md)上的討論。

## <a name="cursor-appearance-and-position"></a>游標外觀和位置

畫面緩衝區的游標可以顯示或隱藏。 當其顯示時，其外觀可能會有所不同，從完全填滿字元資料格到顯示為資料格底部水平線都是其範圍。 若要取得游標外觀和可見度的相關資訊，請使用 [**GetConsoleCursorInfo**](getconsolecursorinfo.md) 函式。 此函式會報告游標是否可見，並將游標的外觀描述為其所在字元資料格的百分比。 若要設定游標的外觀和可見度，請使用 [**SetConsoleCursorInfo**](setconsolecursorinfo.md) 函式。

[高階主控台 I/O 函式所撰寫的字元](high-level-console-i-o.md)會寫入目前的游標位置，並將游標往前移到下一個位置。 若要判斷目前畫面緩衝區座標系統中的游標位置，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)。 您可以使用 [**SetConsoleCursorPosition**](setconsolecursorposition.md) 來設定游標位置，進而控制高階 I/O 函式所撰寫或回應的文字位置。 如果您移動游標，則會覆寫新游標位置上的文字。

> [!NOTE]
> 不建議使用低階函式來尋找游標位置。 如果需要進行進階配置，建議使用[虛擬終端機序列](console-virtual-terminal-sequences.md)來查詢此位置。 如需有關為何偏好虛擬終端機序列的詳細資訊，請參閱 **[傳統函式與虛擬終端機](classic-vs-vt.md)** 文件。

游標的位置、外觀和可見度都會針對每個畫面緩衝區個別設定。

## <a name="character-attributes"></a>字元屬性

字元屬性可以分成兩個類別：色彩和 DBCS。 下列屬性會定義於 `WinCon.h` 標頭檔中。

| 屬性 | 意義 |
|-|-|
| **FOREGROUND\_BLUE** | 文字色彩包含藍色。 |
| **FOREGROUND\_GREEN** | 文字色彩包含綠色。 |
| **FOREGROUND\_RED** | 文字色彩包含紅色。 |
| **FOREGROUND\_INTENSITY** | 加深文字色彩。 |
| **BACKGROUND\_BLUE** | 背景色彩包含藍色。 |
| **BACKGROUND\_GREEN** | 背景色彩包含綠色。 |
| **BACKGROUND\_RED** | 背景色彩包含紅色。 |
| **BACKGROUND\_INTENSITY** | 加深背景色彩。 |
| **COMMON\_LVB\_LEADING\_BYTE** | 前置位元組。 |
| **COMMON\_LVB\_TRAILING\_BYTE** | 尾端位元組。 |
| **COMMON\_LVB\_GRID\_HORIZONTAL** | 水平置頂。 |
| **COMMON\_LVB\_GRID\_LVERTICAL** | 垂直靠左。 |
| **COMMON\_LVB\_GRID\_RVERTICAL** | 垂直靠右。 |
| **COMMON\_LVB\_REVERSE\_VIDEO** | 反轉前景和背景屬性。 |
| **COMMON\_LVB\_UNDERSCORE** | 底線。 |

前景屬性會指定文字色彩。 背景屬性會指定用來填滿資料格背景的色彩。 其他屬性會與 [DBCS](https://msdn.microsoft.com/library/windows/desktop/dd317794) 搭配使用。

應用程式可以結合前景和背景常數來達到不同的色彩。 例如，下列組合會在藍色背景上產生明亮的青色文字。

`FOREGROUND_BLUE | FOREGROUND_GREEN | FOREGROUND_INTENSITY | BACKGROUND_BLUE`

如果未指定背景常數，則背景會是黑色，如果未指定任何前景常數，則文字會是黑色。 例如，下列組合會在白色背景上產生黑色文字。

`BACKGROUND_BLUE | BACKGROUND_GREEN | BACKGROUND_RED`

每個畫面緩衝區字元資料格都會儲存色彩屬性，以用於繪製該儲存格的前景 (文字) 和背景色彩。 應用程式可以個別設定每個字元資料格的色彩資料，並針對每個資料格將該資料儲存為 [**CHAR\_INFO**](char-info-str.md) 結構的 **屬性** 成員。 每個畫面緩衝區目前的文字屬性之後都會用在高階函式所撰寫或回應的字元上。

應用程式可以使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 來判斷畫面緩衝區目前的文字屬性，以及使用 [**SetConsoleTextAttribute**](setconsoletextattribute.md) 函式來設定字元屬性。 變更畫面緩衝區的屬性並不會影響先前撰寫的字元顯示。 這些文字屬性不會影響低階主控台 I/O 函式所撰寫的字元 (例如 [**WriteConsoleOutput**](writeconsoleoutput.md) 或 [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md) 函式)，這些函式可明確指定每個資料格的屬性，或將屬性保留不變。

> [!NOTE]
> 不建議使用低階函式來操作預設和特定的文字屬性。 建議使用[虛擬終端機序列](console-virtual-terminal-sequences.md)來設定文字屬性。 如需有關為何偏好虛擬終端機序列的詳細資訊，請參閱 **[傳統函式與虛擬終端機](classic-vs-vt.md)** 文件。

## <a name="font-attributes"></a>字型屬性

[**GetCurrentConsoleFont**](getcurrentconsolefont.md) 函式會擷取目前主控台字型的相關資訊。 儲存在 [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) 結構中的資訊包含該字型的每個字元寬度和高度。

[**GetConsoleFontSize**](getconsolefontsize.md) 函式會擷取指定主控台畫面緩衝區所使用的字型大小。

> [!NOTE]
> 不建議使用函式來尋找和操作字型資訊。 建議使用中性字型操作命令列應用程式，以確保可與各平台及主機環境相容，進而允許使用者自訂字型。 如需有關使用者喜好設定和主機環境 (包括終端機) 的詳細資訊，請參閱 **[生態系統藍圖](ecosystem-roadmap.md)** 。

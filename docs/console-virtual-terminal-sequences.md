---
title: 主控台虛擬終端機序列
description: 虛擬終端機序列是可在寫入至輸出資料流時控制游標移動、色彩/字型模式和其他作業的控制字元序列。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: 29c1cc65db5e20c35ca0aaf6dc58c6e485d0edc6
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358128"
---
# <a name="console-virtual-terminal-sequences"></a>主控台虛擬終端機序列


虛擬終端機序列是可在寫入至輸出資料流時控制游標移動、色彩/字型模式和其他作業的控制字元序列。 只要設定適當模式，輸入資料流上也可以接收序列來回應輸出資料流的查詢資訊序列或作為使用者輸入的編碼。

您可以使用 [**GetConsoleMode**](getconsolemode.md) 和 [**SetConsoleMode**](setconsolemode.md) 函式來設定此行為。 本文件最後會包含啟用虛擬終端機行為的建議方式範例。

下列序列的行為是以 VT100 和衍生的終端機模擬器技術為基礎，特別是 xterm 終端機模擬器。 如需有關終端機序列的詳細資訊，請參閱 <http://vt100.net> 和 <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>。

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>輸出序列


寫入至輸出資料流時，如果使用 [**SetConsoleMode**](setconsolemode.md) 函式在畫面緩衝區控制代碼上設定 ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING 旗標，則主控台主機會攔截下列終端機序列。 請注意，針對寫入任何資料列中最後一個資料行的字元，使用 DISABLE\_NEWLINE\_AUTO\_RETURN 旗標有助於模擬其他終端機模擬器的游標定位和捲動行為。

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>簡單的游標定位


在下列所有描述中，ESC 一律是十六進位值 0x1B。 終端機序列中不會包含任何空格。 如需如何在實務中使用這些序列的範例，請參閱本主題結尾處的[範例](#example)。

下表描述直接在 ESC 字元之後使用單一動作命令的簡單逸出序列，並。 這些序列沒有參數，而且會立即生效。

此資料表中的所有命令通常等同於呼叫 [**SetConsoleCursorPosition**](setconsolecursorposition.md) 主控台 API 來放置游標。

游標移動會由目前的檢視區繫結至緩衝區中。 將不會發生捲動 (如果適用)。


| 順序 | 速記法 | 行為 |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| ESC A | CUU | 游標向上移 1 個位置 |
| ESC B | CUD | 游標向下移 1 個位置 |
| ESC C | CUF | 游標向前 (右) 移 1 個位置 |
| ESC D | CUB | 游標向後 (左) 移 1 個位置 |
| ESC M | RI | 反向索引 – 執行 \\n 的反向作業，將游標向上移動一行並維持水準位置，可視需要捲動緩衝區\* |
| ESC 7 | DECSC | 將游標位置儲存在記憶體中\*\* |
| ESC 8 | DECSR | 從記憶體還原游標位置\*\* |



> [!NOTE]
>\* 如果有設定捲動邊界，邊界內的 RI 只會捲動邊界的內容，並讓檢視區保持不變。 (請參閱捲動邊界)
>
>\*\*在第一次使用儲存命令之前，記憶體中不會儲存任何值。 存取儲存值的唯一方法是使用還原命令。

## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>游標定位


下表包含控制序列引導器 (Control Sequence Introducer，CSI) 類型的序列。 所有 CSI 序列都是以 ESC (0x1B) 開頭，後面接著 \[ (左括弧 (0x5B))，而且可能包含可變長度的參數來指定每項作業的詳細資訊。 這會以速記法 &lt;n&gt; 表示。 下列每個資料表都會依功能分組，並在每個資料表下方說明群組的運作方式。

除非另有註明，否則所有參數皆適用下列規則：

- &lt;n&gt; 代表要移動的距離，而且屬於選擇性參數
- 如果 &lt;n&gt; 省略或等於 0，則會將其視為 1
- &lt;n&gt; 不能大於 32,767 (最大 short 值)
- &lt;n&gt; 不可以是負數

本節中的所有命令通常等同於呼叫 [**SetConsoleCursorPosition**](setconsolecursorposition.md)主控台 API。

游標移動會由目前的檢視區繫結至緩衝區中。 將不會發生捲動 (如果適用)。


| 順序 | 程式碼 | 描述 | 行為 |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; A | CUU | 游標向上移 | 游標向上移 &lt;n&gt; 個位置 |
| ESC \[ &lt;n&gt; B | CUD | 游標向下移 | 游標向下移 &lt;n&gt; 個位置 |
| ESC \[ &lt;n&gt; C | CUF | 游標向前移 | 游標向前 (右) 移 &lt;n&gt; 個位置 |
| ESC \[ &lt;n&gt; D | CUB | 游標向後移 | 游標向後 (左) 移 &lt;n&gt; 個位置 |
| ESC \[ &lt;n&gt; E | CNL | 游標移到下一行 | 游標從目前位置向下移動 &lt;n&gt; 行 |
| ESC \[ &lt;n&gt; F | CPL | 游標移到上一行 | 游標從目前位置向上移動 &lt;n&gt; 行 |
| ESC \[ &lt;n&gt; G | CHA | 游標水平移到絕對位置 | 游標水平移至目前這一行中的第 &lt;n&gt; 個位置 |
| ESC \[ &lt;n&gt; d | VPA | 游標垂直移動到行的絕對位置 | 游標垂直移至目前資料行中的第 &lt;n&gt; 個位置 |
| ESC \[ &lt;y&gt; ; &lt;x&gt; H | CUP | 游標位置 | \*游標移到檢視區中的 &lt;x&gt;; &lt;y&gt; 座標，其中 &lt;x&gt; 是 &lt;y&gt; 行的資料行 |
| ESC \[ &lt;y&gt; ; &lt;x&gt; f | HVP | 水平垂直位置 | \*游標移到檢視區中的 &lt;x&gt;; &lt;y&gt; 座標，其中 &lt;x&gt; 是 &lt;y&gt; 行的資料行 |
| ESC \[ s | ANSISYSSC | 儲存游標 – Ansi.sys 模擬 | \*\*在沒有參數的情況下，執行儲存游標作業 (如同 DECSC) |
| ESC \[ u | ANSISYSSC | 還原游標 – Ansi.sys 模擬 | \*\*在沒有參數的情況下，執行還原游標作業 (如同 DECRC) |



> [!NOTE]
>\*&lt;x&gt; 和 &lt;y&gt; 參數與上述的 &lt;n&gt; 具有相同限制。 如果省略 &lt;x&gt; 和 &lt;y&gt;，則會設為 1;1。
>
>\*\*您可以在 <https://msdn.microsoft.com/library/cc722862.aspx> 上找到 ANSI.sys 的歷程記錄文件，並針對便利性/相容性需求來加以實作。



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>游標可見度


下列命令會控制游標的可見度和其閃爍狀態。 DECTCEM 序列通常等同於呼叫 [**SetConsoleCursorInfo**](setconsolecursorinfo.md) 主控台 API 來切換游標可見度。


| 順序 | 程式碼 | 描述 | 行為 |
|---------------|---------|------------------------------|---------------------------|
| ESC \[ ? 12 h | ATT160 | 文字游標啟用閃爍 | 啟動游標閃爍 |
| ESC \[ ? 12 l | ATT160 | 文字游標停用閃爍 | 停止游標閃爍 |
| ESC \[ ? 25 h | DECTCEM | 文字游標啟用模式顯示 | 顯示游標 |
| ESC \[ ? 25 l | DECTCEM | 文字游標啟用模式隱藏 | 隱藏游標 |

> [!TIP]
> 啟用序列的結尾是小寫 H 字元 (`h`)，而停用序列的結尾則是小寫 L 字元 (`l`)。

## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>檢視區定位


本節中的所有命令通常等同於呼叫 [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 主控台 API 來移動主控台緩衝區的內容。

**注意** 命令名稱會造成誤導。 捲動 (Scroll) 是指文字在作業期間移動的方向，而不是檢視區要移動的方式。




| 順序 | 程式碼 | 描述 | 行為 |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; S | SU | 向上捲動 | 文字向上捲動 &lt;n&gt; 個位置。 也稱為「向下平移」，新行會從畫面底部填入 |
| ESC \[ &lt;n&gt; T | SD | 向下捲動 | 向下捲動 &lt;n&gt; 個位置。 也稱為「向上平移」，新行會從畫面頂端填入 |



文字會從游標所在的那一行開始移動。 如果游標位於檢視區的中間資料列上，則向上捲動會移動此檢視區的下半部，並在底部插入空白行。 向下捲動會移動檢視區資料列的上半部，並在頂端插入新行。

另外，要注意的是，向上和向下捲動也會受到捲動邊界的影響。 向上和向下捲動不會影響捲動邊界以外的任何行。

&lt;n&gt; 的預設值是 1，而且可以選擇性地省略此值。

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>文字修改


本節中的所有命令通常等同於呼叫 [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)、[**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) 和 [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 主控台 API 來修改文字緩衝區內容。


| 順序 | 程式碼 | 描述 | 行為 |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; @ | ICH | 插入字元 | 在目前的游標位置上插入 &lt;n&gt; 個空格，並將所有現有的文字移至右方。 移至畫面右側的現有文字會移除。 |
| ESC \[ &lt;n&gt; P | DCH | 刪除字元 | 刪除目前游標位置上的 &lt;n&gt; 個字元，從畫面右側邊緣移入空白字元。 |
| ESC \[ &lt;n&gt; X | ECH | 清除字元 | 藉由以空白字元覆寫的方式，從目前的游標位置清除 &lt;n&gt; 個字元。 |
| ESC \[ &lt;n&gt; L | IL | 插入行 | 將 &lt;n&gt; 行插入游標位置上的緩衝區。 游標所在的行和其下方的行將會向下移動。 |
| ESC \[ &lt;n&gt; M | DL | 刪除行 | 從緩衝區中刪除 &lt;n&gt; 行，從游標所在的資料列開始。 |



> [!NOTE]
>針對 IL 和 DL，只有捲動邊界 (請參閱捲動邊界) 中的行會受到影響。 如果未設定邊界，則預設的邊界框線為目前的檢視區。 如果行會在邊界下方移動，則會遭到捨棄。 刪除行時，邊界底部會插入空白行，而檢視區外的行則不會受到影響。

針對每個序列，如果省略 &lt;n&gt;，則預設值為0。



在下列命令中，參數 &lt;n&gt; 具有 3 個有效值：

- 0 會從目前的游標位置 (包含該位置) 清除到行/顯示畫面的結尾
- 1 會從行/顯示畫面的開頭清除到目前的游標位置 (包含該位置)
- 2 清除整行/整個顯示畫面


| 順序 | 程式碼 | 描述 | 行為 |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| ESC \[ &lt;n&gt; J | ED | 清除顯示畫面 | 以空白字元取代 &lt;n&gt; 所指定的目前檢視區/畫面中的所有文字 |
| ESC \[ &lt;n&gt; K | EL | 清除行 | 以空白字元取代 &lt;n&gt; 所指定游標所在行上的所有文字 |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>文字格式


本節中的所有命令通常等同於呼叫 [**SetConsoleTextAttribute**](setconsoletextattribute.md) 主控台 API，用於調整未來所有主控台輸出文字緩衝區的寫入格式。

此命令是特別的，因為下面的 &lt;n&gt; 位置可以接受 0 到 16 的參數 (以分號分隔)。

若未指定任何參數，則會將其視為等同於一個參數 0。


| 順序 | 程式碼 | 描述 | 行為 |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| ESC \[ &lt;n&gt; m | SGR | 設定圖形轉譯 | 依據 &lt;n&gt; 所指定的內容設定畫面的格式和文字 |



下表的值可以在 &lt;n&gt; 中用來代表不同的格式化模式。

格式化模式會從左至右套用。 套用競爭格式化選項會使最右邊的選項具有優先權。

針對指定色彩的選項，這些色彩會依照主控台色彩表中的定義使用，您可以使用 [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API 加以修改。 如果將資料表修改為讓資料表中的「藍色」位置顯示 RGB 色度的紅色，則對 **前景藍色** 發出的所有呼叫都會顯示該紅色色彩，直到另有變更為止。


| 值 | 描述 | 行為 |
|-------|---------------------------|--------------------------------------------------------------------|
| 0 | 預設 | 在修改前將所有屬性都設回為預設狀態 |
| 1 | 濃厚/明亮 | 將亮度/飽和度旗標套用至前景色彩 |
| 22 | 無粗體/亮色 | 移除前景色彩的亮度/濃度旗標 |
| 4 | Underline | 加底線 |
| 24 | 沒有底線 | 移除底線 |
| 7 | 負 | 交換前景和背景色彩 |
| 27 | 正面 (非負面) | 讓前景/背景回到一般狀態 |
| 30 | 前景黑色 | 將非濃厚/明亮的黑色套用至前景 |
| 31 | 前景紅色 | 將非濃厚/明亮的紅色套用至前景 |
| 32 | 前景綠色 | 將非濃厚/明亮的綠色套用至前景 |
| 33 | 前景黃色 | 將非濃厚/明亮的黃色套用至前景 |
| 34 | 前景藍色 | 將非濃厚/明亮的藍色套用至前景 |
| 35 | 前景洋紅色 | 將非濃厚/明亮的洋紅色套用至前景 |
| 36 | 前景青色 | 將非濃厚/明亮的青色套用至前景 |
| 37 | 前景白色 | 將非濃厚/明亮的白色套用至前景 |
| 38 | 前景擴充 | 將擴充的色彩值套用至前景 (請參閱下列詳細資料) |
| 39 | 前景預設值 | 僅套用預設的前景部分 (請參閱 0) |
| 40 | 背景黑色 | 將非濃厚/明亮的黑色套用至背景 |
| 41 | 背景紅色 | 將非濃厚/明亮的紅色套用至背景 |
| 42 | 背景綠色 | 將非濃厚/明亮的綠色套用至背景 |
| 43 | 背景黃色 | 將非濃厚/明亮的黃色套用至背景 |
| 44 | 背景藍色 | 將非濃厚/明亮的藍色套用至背景 |
| 45 | 背景洋紅色 | 將非濃厚/明亮的洋紅色套用至背景 |
| 46 | 背景青色 | 將非濃厚/明亮的青色套用至背景 |
| 47 | 背景白色 | 將非濃厚/明亮的白色套用至背景 |
| 48 | 背景擴充 | 將擴充的色彩值套用至背景 (請參閱下列詳細資料) |
| 49 | 背景預設值 | 僅套用預設的背景部分 (請參閱0) |
| 90 | 明亮前景黑色 | 將濃厚/明亮的亮黑色套用至前景 |
| 91 | 明亮前景紅色 | 將濃厚/明亮的紅色套用至前景 |
| 92 | 明亮前景綠色 | 將濃厚/明亮的綠色套用至前景 |
| 93 | 明亮前景黃色 | 將濃厚/明亮的黃色套用至前景 |
| 94 | 明亮前景藍色 | 將濃厚/明亮的藍色套用至前景 |
| 95 | 明亮前景洋紅色 | 將濃厚/明亮的洋紅色套用至前景 |
| 96 | 明亮前景青色 | 將濃厚/明亮的青色套用至前景 |
| 97 | 明亮前景白色 | 將濃厚/明亮的白色套用至前景 |
| 100 | 明亮的背景黑色 | 將濃厚/明亮的黑色套用至背景 |
| 101 | 明亮背景紅色 | 將濃厚/明亮的紅色套用至背景 |
| 102 | 明亮背景綠色 | 將濃厚/明亮的綠色套用至背景 |
| 103 | 明亮的背景黃色 | 將濃厚/明亮的黃色套用至背景 |
| 104 | 明亮背景藍色 | 將濃厚/明亮的藍色套用至背景 |
| 105 | 明亮背景洋紅色 | 將濃厚/明亮的洋紅色套用至背景 |
| 106 | 明亮背景青色 | 將濃厚/明亮的青色套用至背景 |
| 107 | 明亮背景白色 | 將濃厚/明亮的白色套用至背景 |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>擴充的色彩

某些虛擬終端機模擬器支援的色彩調色板多於 Windows 主控台所提供的 16 種色彩。 針對這些擴充的色彩，Windows 主控台會從現有的 16 色表格中選擇最接近的色彩來顯示。 不同於上述的一般 SGR 值，擴充的值會根據下表，在使用最初的指示器之後取用額外的參數。


| SGR 子序列 | 說明 |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| 38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt; | 將前景色彩設為 &lt;r&gt;、&lt;g&gt;、&lt;b&gt; 參數中指定的 RGB 值\* |
| 48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt; | 將背景色彩設為以 &lt;r&gt;、&lt;g&gt;、&lt;b&gt; 參數指定的 RGB 值\* |
| 38 ; 5 ; &lt;s&gt; | 將前景色彩設為 88 或 256 色彩表中的 &lt;s&gt; 索引\* |
| 48 ; 5 ; &lt;s&gt; | 將背景色彩設為 88 或 256 色彩表中的 &lt;s&gt; 索引\* |



\*在內部維護以進行比較的 88 和 256 色調色盤，是以 xterm 終端機模擬器為基礎。 目前無法修改比較/進位表。


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>畫面色彩


下列命令可讓應用程式將畫面色彩調色盤值設定為任何 RGB 值。

RGB 值應該是 `0` 和 `ff` 之間的十六進位值，並以正斜線字元 (例如 `rgb:1/24/86`) 分隔。

請注意，此序列是一個 OSC (作業系統命令) 序列，而不是類似於列出許多其他序列的 CSI，因此開頭為 "\\x1b\]"，而不是 "\\x1b\["。


| 順序 | 描述 | 行為 |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC | 修改畫面色彩 | 將畫面色彩調色盤索引 &lt;i&gt; 設定為 &lt;r&gt;、&lt;g&gt;、&lt;b&gt; 中指定的 RGB 值 |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>模式變更


這些是控制輸入模式的序列。 有兩組不同的輸入模式：游標按鍵模式和鍵盤按鍵模式。 游標按鍵模式會控制由方向鍵及 Home 與 End 所發出的序列，而鍵盤按鍵模式會控制主要由 Numpad 上按鍵及功能鍵所發出的序列。

這些模式中的每一個都是簡單的布林值設定 – 游標按鍵模式是標準 (預設) 或應用程式，而鍵盤按鍵模式則是數字 (預設值) 或應用程式。

請參閱 [游標按鍵] 和 [Numpad 與功能鍵] 區段，以了解在這些模式中發出的序列。


| 順序 | 程式碼 | 描述 | 行為 |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| ESC = | DECKPAM | 啟用鍵盤應用程式模式 | 鍵盤按鍵會發出其應用程式模式序列。 |
| ESC &gt; | DECKPNM | 啟用鍵盤數字模式 | 鍵盤按鍵會發出其數字模式序列。 |
| ESC \[ ? 1 小時 | DECCKM | 啟用游標按鍵應用程式模式 | 鍵盤按鍵會發出其應用程式模式序列。 |
| ESC \[ ? 1 l | DECCKM | 停用游標按鍵應用程式模式 (使用標準模式) | 鍵盤按鍵會發出其數字模式序列。 |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>查詢狀態


本節中的所有命令通常等同於呼叫 Get\* 主控台 API，用於取得目前主控台緩衝區狀態的狀態資訊。

> [!NOTE]
>若已設定 ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING，當這些查詢在輸出資料流上完成辨識後，就會立即將其回應發出至主控台輸入資料流。 ENABLE\_VIRTUAL\_TERMINAL\_INPUT 旗標不會套用至查詢命令，因為已假設執行查詢的應用程式一律要收到回覆。




| 順序 | 程式碼 | 描述 | 行為 |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| ESC \[ 6 n | DECXCPR | 回報游標位置 | 將游標位置發出為：ESC \[ &lt;r&gt; ; &lt;c&gt; R，其中 &lt;R&gt; = 游標資料列，而 &lt;c&gt; = 游標資料行 |
| ESC \[ 0 c | DA | 裝置屬性 | 回報終端機身分識別。 將會發出 “\\x1b\[?1;0c”，指出「沒有選項的 VT101」。 |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tab


雖然視窗主控台在傳統上預期 Tab 會是專屬的八個字元寬，但使用特定序列的 \*nix 應用程式可以操控主控台視窗中 Tab 停止的位置，以最佳化應用程式的游標移動。

下列序列可讓應用程式設定主控台視窗中 Tab 的停止位置、將這些位置移除，以及在這些位置之間瀏覽。


| 順序 | 程式碼 | 描述 | 行為 |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC H | HTS | 水平 Tab 設定 | 在游標所在的目前資料行中設定 Tab 停止點。 |
| ESC \[ &lt;n&gt; I | CHT | 游標水平 (向前) Tab | 使游標前進至下一個資料行 (在相同的資料列中)，並使用 Tab 停止點。 如果不再有 Tab 停止點，則移至資料列中的最後一個資料行。 如果游標在最後一個資料行中，則移至下一個資料列的第一個資料行。 |
| ESC \[ &lt;n&gt; Z | CBT | 游標向後 Tab | 使游標移至上一個資料行 (在相同的資料列中)，並使用 Tab 停止點。 如果不再有 Tab 停止點，則將游標移至第一個資料行。 如果游標在第一個資料行中，則不移動游標。 |
| ESC \[ 0 g | TBC | Tab 清除 (目前的資料行) | 清除目前資料行中的 Tab 停止點 (如果有的話)。 沒有的話，則不會執行任何動作。 |
| ESC \[ 3 g | TBC | Tab 清除 (所有資料行) | 清除所有目前設定的 Tab 停止點。 |



- 對於 CHT 和 CBT，&lt;n&gt; 是選擇性參數 (預設值 = 1)，表示要讓游標在指定的方向前進多少次。
- 如果沒有透過 HTS 設定的 Tab 停止點，CHT 和 CBT 會將視窗的第一個和最後一個資料行視為唯一的兩個 Tab 停止點。
- 使用 HTS 設定 Tab 停止點也會讓主控台瀏覽至 TAB (0x09, ‘\\t’) 字元輸出上的下一個 Tab 停止點，其方式與 CHT 相同。

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>指定字元集


下列序列可讓程式變更作用中字元集的對應。 這可讓程式發出 7 位元的 ASCII 字元，但會在終端機畫面本身將其顯示為其他字符。 目前唯一支援的兩個字元集是 ASCII (預設值) 和 DEC 特殊圖形字元集。 如需 DEC 特殊圖形字元集所代表的所有字元清單，請參閱 <http://vt100.net/docs/vt220-rm/table2-4.html>。


| 順序 | 描述 | 行為 |
|----------|--------------------------------------------|-------------------------------|
| ESC ( 0 | 指定字元集 – DEC 線條繪圖 | 啟用 DEC 線條繪圖模式 |
| ESC ( B | 指定字元集 – US ASCII | 啟用 ASCII 模式 (預設值) |



值得注意的是，DEC 線條繪圖模式會用來在主控台應用程式中繪製框線。 下表顯示 ASCII 字元與線條繪圖字元的對應。


| Hex | ASCII | DEC 線條繪圖 |
|------|-------|------------------|
| 0x6a | j | ┘ |
| 0x6b | k | ┐ |
| 0x6c | l | ┌ |
| 0x6d | m | └ |
| 0x6e | n | ┼ |
| 0x71 | q | ─ |
| 0x74 | t | ├ |
| 0x75 | u | ┤ |
| 0x76 | v | ┴ |
| 0x77 | w | ┬ |
| 0x78 | x | │ |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>捲動邊界


下列序列可讓程式設定受到捲動作業影響的畫面「捲動區域」。 這是資料列的子集，會在畫面以其他方式捲動 (例如 ‘\\n’ 或 RI) 時進行調整。 這些邊界也會影響插入行 (IL) 和刪除行 (DL) 及向上捲動 (SU) 和向下捲動 (SD) 所修改的資料列。

如果畫面有個部分不會在畫面其餘部分填滿時捲動，例如應用程式頂端有標題列或底部有狀態列，則特別適用捲動邊界。

DECSTBM 有兩個選擇性參數：&lt;t&gt; 和 &lt;b&gt;，可用來指定代表捲動區域頂端和底部幾行的資料列 (含)。 如果省略參數，&lt;t&gt; 會預設為1，而 &lt;b&gt; 會預設為目前檢視區的高度。

捲動邊界是為每個緩衝區設定的，所以很重要的是，替代緩衝區和主要緩衝區會維持不同的捲動邊界設定 (因此，替代緩衝區中的全畫面應用程式不會妨礙到主要緩衝區的邊界)。


| 順序 | 程式碼 | 描述 | 行為 |
|--------------------------------|---------|----------------------|------------------------------------------------|
| ESC \[ &lt;t&gt; ; &lt;b&gt; r | DECSTBM | 設定捲動區域 | 設定檢視區的 VT 捲動邊界。 |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>視窗標題


下列命令可讓應用程式將主控台視窗的標題設定為指定的 &lt;字串&gt; 參數。 字串必須小於 255 個字元才能被接受。 這相當於以指定字串呼叫 SetConsoleTitle。

請注意，這些序列是 OSC (作業系統命令) 序列，而不是類似於列出許多其他序列的 CSI，因此開頭為 "\\x1b\]"，而不是 "\\x1b\["。


| 順序 | 描述 | 行為 |
|-------------------------------|---------------------------|----------------------------------------------------|
| ESC \] 0 ; &lt;字串&gt; BEL | 設定圖示和視窗標題 | 將主控台視窗的標題設定為 &lt;字串&gt;。 |
| ESC \] 2 ; &lt;字串&gt; BEL | 設定 Window 標題 | 將主控台視窗的標題設定為 &lt;字串&gt;。 |



此處的終止字元是 “Bell” 字元：‘\\x07’

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>替代畫面緩衝區


\*Nix 樣式應用程式通常會使用替代畫面緩衝區，讓其可修改緩衝區的完整內容，而不會影響到將其啟動的應用程式。 替代緩衝區完全是視窗的維度，沒有任何回捲區域。

如需此行為的範例，請考慮從 bash 啟動 Vim 的時機。 Vim 會使用整個畫面來編輯檔案，然後返回 bash 會讓原始緩衝區保持不變。


| 順序 | 描述 | 行為 |
|--------------------|-----------------------------|--------------------------------------------|
| ESC \[ ? 1 0 4 9 h | 使用替代畫面緩衝區 | 切換至新的替代畫面緩衝區。 |
| ESC \[ ? 1 0 4 9 l | 使用主要畫面緩衝區 | 切換至主要緩衝區。 |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>視窗寬度


您可以使用下列序列來控制主控台視窗的寬度。 這些序列大致等同於呼叫 SetConsoleScreenBufferInfoEx 主控台 API 來設定視窗寬度。


| 順序 | 程式碼 | 描述 | 行為 |
|--------------|---------|------------------------------|---------------------------------------------|
| ESC \[ ? 3 h | DECCOLM | 將資料行數目設定為 132 | 將主控台寬度設定為 132 個資料行寬。 |
| ESC \[ ? 3 l | DECCOLM | 將資料行數目設定為 80 | 將主控台寬度設定為 80 個資料行寬。 |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>軟重設


您可以使用下列序列將某些屬性重設為預設值。下列屬性會重設為下列預設值 (也會列出控制這些屬性的序列)：

- 游標可見度：可見 (DECTEM)
- 數字鍵盤：數字模式 (DECNKM)
- 游標按鍵模式：標準模式 (DECCKM)
- 頂端和底部邊界：頂端 = 1、底端 = 主控台高度 (DECSTBM)
- 字元集：US ASCII
- 圖形轉譯：預設/關閉 (SGR)
- 儲存游標狀態：首頁位置 (0,0) (DECSC)


| 順序 | 程式碼 | 描述 | 行為 |
|------------|--------|-------------|----------------------------------------------------|
| ESC \[ ! p | DECSTR | 軟重設 | 將特定的終端機設定重設為預設值。 |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>輸入序列


如果使用 SetConsoleMode 旗標在輸入緩衝區控制代碼上設定 ENABLE\_VIRTUAL\_TERMINAL\_INPUT 旗標，則主控台主機會在輸入資料流上發出下列終端機序列。

有兩種內部模式可控制針對指定輸入鍵發出的序列：游標按鍵模式和鍵盤按鍵模式。 這會在 [模式變更] 區段中加以說明。

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>游標按鍵


| 答案 | 正常模式 | 應用程式模式 |
|-------------|-------------|------------------|
| 向上箭號 | ESC \[ A | ESC O A |
| 向下箭號 | ESC \[ B | ESC O B |
| 向右鍵 | ESC \[ C | ESC O C |
| 向左鍵 | ESC \[ D | ESC O D |
| 家庭 | ESC \[ H | ESC O H |
| 結束 | ESC \[ F | ESC O F |



此外，如果按下 Ctrl 鍵和這其中任何一個鍵，則會改為發出下列序列 (不論游標按鍵模式為何)：


| 答案 | 任何模式 |
|--------------------|----------------|
| Ctrl + 向上鍵 | ESC \[ 1 ; 5 A |
| Ctrl + 向下鍵 | ESC \[ 1 ; 5 B |
| Ctrl + 向右鍵 | ESC \[ 1 ; 5 C |
| Ctrl + 向左鍵 | ESC \[ 1 ; 5 D |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad 與功能鍵


| 答案 | 順序 |
|-----------|--------------|
| 退格鍵 | 0x7f (DEL) |
| 暫停 | 0x1a (SUB) |
| 逸出 | 0x1b (ESC) |
| 插入 | ESC \[ 2 ~ |
| 刪除 | ESC \[ 3 ~ |
| Page Up | ESC \[ 5 ~ |
| Page Down | ESC \[ 6 ~ |
| F1 | ESC O P |
| F2 | ESC O Q |
| F3 | ESC O R |
| F4 | ESC O S |
| F5 | ESC \[ 1 5 ~ |
| F6 | ESC \[ 1 7 ~ |
| F7 | ESC \[ 1 8 ~ |
| F8 | ESC \[ 1 9 ~ |
| F9 | ESC \[ 2 0 ~ |
| F10 | ESC \[ 2 1 ~ |
| F11 | ESC \[ 2 3 ~ |
| F12 | ESC \[ 2 4 ~ |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>輔助按鍵

Alt 的處理方式是在序列前方加上 escape：ESC &lt;c&gt;，其中 &lt;c&gt; 是作業系統所傳遞的字元。 Alt+Ctrl 的處理方式相同，不同之處在於作業系統會將 &lt;c&gt; 鍵預先轉移至適當的控制字元，以轉送至應用程式。

傳遞的 Ctrl 通常會與從系統中收到的完全相同。 這通常是移到控制字元保留空間 (0x0-0x1f) 中的單一字元。 例如，Ctrl+@ (0x40) 變成 NUL (0x00)，Ctrl+\[ (0x5b) 變成 ESC (0x1b) 等等。有幾個 Ctrl 鍵組合會根據下表來特別處理：


| 答案 | 順序 |
|--------------------|----------------|
| Ctrl + 空格鍵 | 0x00 (NUL) |
| Ctrl + 向上鍵 | ESC \[ 1 ; 5 A |
| Ctrl + 向下鍵 | ESC \[ 1 ; 5 B |
| Ctrl + 向右鍵 | ESC \[ 1 ; 5 C |
| Ctrl + 向左鍵 | ESC \[ 1 ; 5 D |



> [!NOTE]
>左側 <kbd>Ctrl</kbd> + 右側 <kbd>Alt</kbd> 會視為 AltGr。 兩者同時出現時，則會將這兩者移除，並將系統所呈現的字元 Unicode 值傳遞到目標。 系統會根據目前的系統輸入設定，預先轉譯 AltGr 值。



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>範例


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span id="example"></span><span id="EXAMPLE"></span>SGR 終端機序列的範例

下列程式碼提供幾個文字格式化的範例。

```C
#include <stdio.h>
#include <wchar.h>
#include <windows.h>

int main()
{
    // Set output mode to handle virtual terminal sequences
    HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
    if (hOut == INVALID_HANDLE_VALUE)
    {
        return GetLastError();
    }

    DWORD dwMode = 0;
    if (!GetConsoleMode(hOut, &dwMode))
    {
        return GetLastError();
    }

    dwMode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;
    if (!SetConsoleMode(hOut, dwMode))
    {
        return GetLastError();
    }

    // Try some Set Graphics Rendition (SGR) terminal escape sequences
    wprintf(L"\x1b[31mThis text has a red foreground using SGR.31.\r\n");
    wprintf(L"\x1b[1mThis text has a bright (bold) red foreground using SGR.1 to affect the previous color setting.\r\n");
    wprintf(L"\x1b[mThis text has returned to default colors using SGR.0 implicitly.\r\n");
    wprintf(L"\x1b[34;46mThis text shows the foreground and background change at the same time.\r\n");
    wprintf(L"\x1b[0mThis text has returned to default colors using SGR.0 explicitly.\r\n");
    wprintf(L"\x1b[31;32;33;34;35;36;101;102;103;104;105;106;107mThis text attempts to apply many colors in the same command. Note the colors are applied from left to right so only the right-most option of foreground cyan (SGR.36) and background bright white (SGR.107) is effective.\r\n");
    wprintf(L"\x1b[39mThis text has restored the foreground color only.\r\n");
    wprintf(L"\x1b[49mThis text has restored the background color only.\r\n");

    return 0;
}
```

> [!NOTE]
>在上述範例中，字串 '`\x1b[31m`' 是 **ESC \[ &lt;n&gt; m** 的實作，&lt;n&gt; 為 31。



下圖顯示先前程式碼範例的輸出。

![使用 sgr 命令的主控台輸出](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>啟用虛擬終端處理的範例

下列程式碼提供為應用程式啟用虛擬終端處理的建議方式範例。 範例的目的是要示範：

1. 現有模式應一律透過 GetConsoleMode 取得，並在使用 SetConsoleMode 設定之前進行分析。

2. 檢查 SetConsoleMode 是否傳回 `0` 及 GetLastError 是否傳回 STATUS\_INVALID\_PARAMETER 是目前在下層系統上執行時所要判斷的機制。 應用程式若收到 STATUS\_INVALID\_PARAMETER 且在位元欄位中有一個較新的主控台模式旗標，則應以適當方式降低行為層級，然後再試一次。

```C
#include <stdio.h>
#include <wchar.h>
#include <windows.h>

int main()
{
    // Set output mode to handle virtual terminal sequences
    HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
    if (hOut == INVALID_HANDLE_VALUE)
    {
        return false;
    }
    HANDLE hIn = GetStdHandle(STD_INPUT_HANDLE);
    if (hIn == INVALID_HANDLE_VALUE)
    {
        return false;
    }

    DWORD dwOriginalOutMode = 0;
    DWORD dwOriginalInMode = 0;
    if (!GetConsoleMode(hOut, &dwOriginalOutMode))
    {
        return false;
    }
    if (!GetConsoleMode(hIn, &dwOriginalInMode))
    {
        return false;
    }

    DWORD dwRequestedOutModes = ENABLE_VIRTUAL_TERMINAL_PROCESSING | DISABLE_NEWLINE_AUTO_RETURN;
    DWORD dwRequestedInModes = ENABLE_VIRTUAL_TERMINAL_INPUT;

    DWORD dwOutMode = dwOriginalOutMode | dwRequestedOutModes;
    if (!SetConsoleMode(hOut, dwOutMode))
    {
        // we failed to set both modes, try to step down mode gracefully.
        dwRequestedOutModes = ENABLE_VIRTUAL_TERMINAL_PROCESSING;
        dwOutMode = dwOriginalOutMode | dwRequestedOutModes;
        if (!SetConsoleMode(hOut, dwOutMode))
        {
            // Failed to set any VT mode, can't do anything here.
            return -1;
        }
    }

    DWORD dwInMode = dwOriginalInMode | ENABLE_VIRTUAL_TERMINAL_INPUT;
    if (!SetConsoleMode(hIn, dwInMode))
    {
        // Failed to set VT input mode, can't do anything here.
        return -1;
    }

    return 0;
}
```

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>選取年度更新功能的範例

下列範例是使用各種逸出序列來操作緩衝區且更健全的程式碼範例，並且會強調 Windows 10 年度更新版中新增的功能。

此範例會使用替代畫面緩衝區、操控 Tab 停止點、設定捲動邊界及變更字元集。

```C
// System headers
#include <windows.h>

// Standard library C-style
#include <wchar.h>
#include <stdlib.h>
#include <stdio.h>

#define ESC "\x1b"
#define CSI "\x1b["

bool EnableVTMode()
{
    // Set output mode to handle virtual terminal sequences
    HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
    if (hOut == INVALID_HANDLE_VALUE)
    {
        return false;
    }

    DWORD dwMode = 0;
    if (!GetConsoleMode(hOut, &dwMode))
    {
        return false;
    }

    dwMode |= ENABLE_VIRTUAL_TERMINAL_PROCESSING;
    if (!SetConsoleMode(hOut, dwMode))
    {
        return false;
    }
    return true;
}

void PrintVerticalBorder()
{
    printf(ESC "(0"); // Enter Line drawing mode
    printf(CSI "104;93m"); // bright yellow on bright blue
    printf("x"); // in line drawing mode, \x78 -> \u2502 "Vertical Bar"
    printf(CSI "0m"); // restore color
    printf(ESC "(B"); // exit line drawing mode
}

void PrintHorizontalBorder(COORD const Size, bool fIsTop)
{
    printf(ESC "(0"); // Enter Line drawing mode
    printf(CSI "104;93m"); // Make the border bright yellow on bright blue
    printf(fIsTop ? "l" : "m"); // print left corner 

    for (int i = 1; i < Size.X - 1; i++)
        printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

    printf(fIsTop ? "k" : "j"); // print right corner
    printf(CSI "0m");
    printf(ESC "(B"); // exit line drawing mode
}

void PrintStatusLine(const char* const pszMessage, COORD const Size)
{
    printf(CSI "%d;1H", Size.Y);
    printf(CSI "K"); // clear the line
    printf(pszMessage);
}

int __cdecl wmain(int argc, WCHAR* argv[])
{
    argc; // unused
    argv; // unused
    //First, enable VT mode
    bool fSuccess = EnableVTMode();
    if (!fSuccess)
    {
        printf("Unable to enter VT processing mode. Quitting.\n");
        return -1;
    }
    HANDLE hOut = GetStdHandle(STD_OUTPUT_HANDLE);
    if (hOut == INVALID_HANDLE_VALUE)
    {
        printf("Couldn't get the console handle. Quitting.\n");
        return -1;
    }

    CONSOLE_SCREEN_BUFFER_INFO ScreenBufferInfo;
    GetConsoleScreenBufferInfo(hOut, &ScreenBufferInfo);
    COORD Size;
    Size.X = ScreenBufferInfo.srWindow.Right - ScreenBufferInfo.srWindow.Left + 1;
    Size.Y = ScreenBufferInfo.srWindow.Bottom - ScreenBufferInfo.srWindow.Top + 1;

    // Enter the alternate buffer
    printf(CSI "?1049h");

    // Clear screen, tab stops, set, stop at columns 16, 32
    printf(CSI "1;1H");
    printf(CSI "2J"); // Clear screen

    int iNumTabStops = 4; // (0, 20, 40, width)
    printf(CSI "3g"); // clear all tab stops
    printf(CSI "1;20H"); // Move to column 20
    printf(ESC "H"); // set a tab stop

    printf(CSI "1;40H"); // Move to column 40
    printf(ESC "H"); // set a tab stop

    // Set scrolling margins to 3, h-2
    printf(CSI "3;%dr", Size.Y - 2);
    int iNumLines = Size.Y - 4;

    printf(CSI "1;1H");
    printf(CSI "102;30m");
    printf("Windows 10 Anniversary Update - VT Example");
    printf(CSI "0m");

    // Print a top border - Yellow
    printf(CSI "2;1H");
    PrintHorizontalBorder(Size, true);

    // // Print a bottom border
    printf(CSI "%d;1H", Size.Y - 1);
    PrintHorizontalBorder(Size, false);

    wchar_t wch;

    // draw columns
    printf(CSI "3;1H");
    int line = 0;
    for (line = 0; line < iNumLines * iNumTabStops; line++)
    {
        PrintVerticalBorder();
        if (line + 1 != iNumLines * iNumTabStops) // don't advance to next line if this is the last line
            printf("\t"); // advance to next tab stop

    }

    PrintStatusLine("Press any key to see text printed between tab stops.", Size);
    wch = _getwch();

    // Fill columns with output
    printf(CSI "3;1H");
    for (line = 0; line < iNumLines; line++)
    {
        int tab = 0;
        for (tab = 0; tab < iNumTabStops - 1; tab++)
        {
            PrintVerticalBorder();
            printf("line=%d", line);
            printf("\t"); // advance to next tab stop
        }
        PrintVerticalBorder();// print border at right side
        if (line + 1 != iNumLines)
            printf("\t"); // advance to next tab stop, (on the next line)
    }

    PrintStatusLine("Press any key to demonstrate scroll margins", Size);
    wch = _getwch();

    printf(CSI "3;1H");
    for (line = 0; line < iNumLines * 2; line++)
    {
        printf(CSI "K"); // clear the line
        int tab = 0;
        for (tab = 0; tab < iNumTabStops - 1; tab++)
        {
            PrintVerticalBorder();
            printf("line=%d", line);
            printf("\t"); // advance to next tab stop
        }
        PrintVerticalBorder(); // print border at right side
        if (line + 1 != iNumLines * 2)
        {
            printf("\n"); //Advance to next line. If we're at the bottom of the margins, the text will scroll.
            printf("\r"); //return to first col in buffer
        }
    }

    PrintStatusLine("Press any key to exit", Size);
    wch = _getwch();

    // Exit the alternate buffer
    printf(CSI "?1049l");

}
```

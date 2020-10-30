---
title: 主控台虛擬終端機序列
description: 虛擬終端機序列是控制字元序列，可以控制資料指標移動、色彩/字型模式，以及寫入輸出資料流程時的其他作業。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: 45ee5518ec8ea2da840d2a4442efd9e0d4346526
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039146"
---
# <a name="console-virtual-terminal-sequences"></a>主控台虛擬終端機序列


虛擬終端機序列是控制字元序列，可以控制資料指標移動、色彩/字型模式，以及寫入輸出資料流程時的其他作業。 當設定適當的模式時，也可以在輸入資料流程上接收序列，以回應輸出資料流程查詢資訊序列或使用者輸入的編碼。

您可以使用 [**GetConsoleMode**](getconsolemode.md) 和 [**SetConsoleMode**](setconsolemode.md) 函數來設定此行為。 本檔的結尾包含啟用虛擬終端行為的建議方式範例。

下列順序的行為取決於 VT100 和衍生的終端機模擬器技術，尤其是 xterm 終端機模擬器。 您可以在和 at 找到終端機序列的詳細資訊 <http://vt100.net> <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html> 。

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>輸出序列


如果使用 SetConsoleMode 函式在 \_ \_ \_ 螢幕緩衝區控制碼上設定 [**SetConsoleMode**](setconsolemode.md)了 [啟用虛擬終端處理] 旗標，則在寫入輸出資料流程時，主控台主機會攔截下列終端機序列。 請注意，「停 \_ 用分行符號自動傳回」旗標在 \_ \_ 模擬其他終端機模擬器的資料指標定位和滾動行為時，可能也很有用，因為這些字元是寫入任何資料列中的最後一個資料行。

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>簡單的資料指標定位


在下列所有說明中，ESC 一律是十六進位值0x1B。 終端機序列中不包含任何空格。 如需如何在實務中使用這些順序的範例，請參閱本主題結尾處的 [範例](#example) 。

下表說明在 ESC 字元之後直接使用單一動作命令的簡單 escape 序列。 這些序列沒有任何參數，且會立即生效。

此表格中的所有命令通常等同于呼叫 [**SetConsoleCursorPosition**](setconsolecursorposition.md) 主控台 API 來放置游標。

資料指標移動會由目前的資料區系結到緩衝區。 如果沒有可用的) ， (滾動。


| 順序 | 速記 | 行為 |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| ESC A | CUU | 游標向上1 |
| ESC B | 反芻 | 資料指標向下1 |
| ESC C | CUF | 向前 (右) 的向前快轉資料指標1 |
| ESC D | 幼 崽 | 將游標向左 (左) 1 |
| ESC M | RI | 反向索引–執行 n 的反向運算 \\ 、將游標向上移動一行、維持水準位置、視需要滾動緩衝區\* |
| ESC 7 | DECSC | 將游標位置儲存在記憶體中\*\* |
| ESC 8 | DECSR | 從記憶體還原資料指標位置\*\* |



> [!NOTE]
>\* 如果有設定捲軸邊界，則邊界內的 RI 只會滾動邊界的內容，並讓此區保持不變。  (請參閱滾動邊界) 
>
>\*\*在第一次使用 save 命令之前，記憶體中不會儲存任何值。 存取儲存值的唯一方法是使用 restore 命令。

## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>資料指標定位


下表包含控制順序 Introducer (CSI) 類型序列。 所有 CSI 序列都以 ESC 開頭 (0x1B) 接著 \[ (左括弧、0x5B) ，而且可能包含變數長度的參數，以指定每項作業的詳細資訊。 這會以速記 &lt; n 表示 &gt; 。 下表依功能分組，每個資料表都說明群組的運作方式。

針對所有參數，除非另有說明，否則適用下列規則：

- &lt;n &gt; 代表要移動的距離，而且是選擇性參數
- 如果 &lt; &gt; 省略 n 或等於0，則會將它視為1
- &lt;n &gt; 不能大於 32767 (最大短值) 
- &lt;n &gt; 不可以是負數

此區段中的所有命令通常等同于呼叫 [**SetConsoleCursorPosition**](setconsolecursorposition.md) 主控台 API。

資料指標移動會由目前的資料區系結到緩衝區。 如果沒有可用的) ， (滾動。


| 順序 | 程式碼 | 描述 | 行為 |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt; n &gt; A | CUU | Cursor Up | 依 n 的游標 &lt;&gt; |
| ESC \[ &lt; n &gt; B | 反芻 | 游標向下 | 向下游標向下 &lt; n&gt; |
| ESC \[ &lt; n &gt; C | CUF | 向前資料指標 | 向前 (右) 的向前快轉資料指標 &lt; n&gt; |
| ESC \[ &lt; n &gt; D | 幼 崽 | 游標向後 | 將游標向左 (左) &lt; n&gt; |
| ESC \[ &lt; n &gt; E | CNL | 游標下一行 | &lt;從目前位置將游標向下移 n &gt; 行 |
| ESC \[ &lt; n &gt; F | Cpl | 資料指標上一行 | &lt; &gt; 從目前的位置將游標向上移 n 行 |
| ESC \[ &lt; n &gt; G | CHA | 資料指標水準絕對 | 資料指標會 &lt; &gt; 在目前的行中水準移至 n 個位置 |
| ESC \[ &lt; n &gt; d | VPA | 垂直行位置絕對 | 游標移至 &lt; 目前資料 &gt; 行中的第 n 個位置 |
| ESC \[ &lt; y &gt; ; &lt;x &gt; H | 杯 | 游標位置 | \*游標移至 &lt; x &gt; ; &lt;在 &gt; 視口內的 y 座標，其中 &lt; x &gt; 是 &lt; y &gt; 行的資料行 |
| ESC \[ &lt; y &gt; ; &lt;x &gt; f | HVP | 水準垂直位置 | \*游標移至 &lt; x &gt; ; &lt;在 &gt; 視口內的 y 座標，其中 &lt; x &gt; 是 &lt; y &gt; 行的資料行 |
| ESC \[ s | ANSISYSSC | 儲存資料指標– Ansi.sys 模擬 | \*\*如果沒有參數，會執行儲存資料指標作業，例如 DECSC |
| ESC \[ u | ANSISYSSC | 還原資料指標– Ansi.sys 模擬 | \*\*如果沒有參數，則會執行還原資料指標作業，例如 DECRC |



> [!NOTE]
>\*&lt;x &gt; 和 &lt; y &gt; 參數的限制與上述的 &lt; 相同 &gt; 。 如果 &lt; &gt; 省略 x 和 &lt; y，則 &gt; 會設為 1; 1。
>
>\*\* 您可以在中找到ANSI.sys 的歷程記錄檔 <https://msdn.microsoft.com/library/cc722862.aspx> ，並且為了方便/相容性而實行。



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>資料指標可見度


下列命令控制資料指標的可見度和其閃爍狀態。 DECTCEM 序列通常等同于呼叫 [**SetConsoleCursorInfo**](setconsolecursorinfo.md) 主控台 API 來切換資料指標可見度。


| 順序 | 程式碼 | 描述 | 行為 |
|---------------|---------|------------------------------|---------------------------|
| ESC \[ ？ 12小時 | ATT160 | 文字游標啟用閃爍 | 開始游標閃爍 |
| ESC \[ ？ 12 l | ATT160 | 文字游標停用閃爍 | 停止閃爍游標 |
| ESC \[ ？ 25 h | DECTCEM | 文字游標啟用模式顯示 | 顯示資料指標 |
| ESC \[ ？ 25 l | DECTCEM | 文字游標啟用模式隱藏 | 隱藏游標 |

> [!TIP]
> 啟用序列以小寫 H 字元結尾 (`h`) ，而停用序列則以小寫 L 字元結尾 (`l`) 。

## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>視口定位


此區段中的所有命令通常等同于呼叫 [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 主控台 API 來移動主控台緩衝區的內容。

**注意** 命令名稱會誤導。 「滾動」指的是文字在作業期間移動的方向，而不是「表面」移動的方式。




| 順序 | 程式碼 | 描述 | 行為 |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| ESC \[ &lt; n &gt; S | SU | 向上捲動 | 將文字向上滾動 &lt; n &gt; 。 也稱為「下移線」，新行會從畫面底部填滿 |
| ESC \[ &lt; n &gt; T | SD | 向下捲動 | 向下移動 &lt; n &gt; 。 也稱為「向上移動」，從畫面頂端填滿新行 |



從游標所在的那一行開始移動文字。 如果游標位於資料中心的中間資料列上，則會向上移動以移動區的下半部，並在底部插入空白行。 向下鍵會移動該資料列的上半部，並在頂端插入新行。

另外一點要注意的是，滾動邊界也會影響向上和向下。 向上和向下鍵不會影響滾動邊界以外的任何行。

N 的預設值 &lt; &gt; 為1，而且可以選擇性地省略值。

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>文字修改


本節中的所有命令通常等同于呼叫 [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)、 [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)和 [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 主控台 api 來修改文字緩衝區內容。


| 順序 | 程式碼 | 描述 | 行為 |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC \[ &lt; n&gt; @ | Ich | 插入字元 | &lt; &gt; 在目前游標位置插入 n 個空格，並將所有現有的文字移至右邊。 已移除將畫面離開右邊的文字。 |
| ESC \[ &lt; n &gt; P | DCH | 刪除字元 | 在 &lt; &gt; 目前游標位置刪除 n 個字元，從畫面的右邊緣將空白字元移位。 |
| ESC \[ &lt; n &gt; X | ECH | 清除字元 | &lt; &gt; 使用空白字元覆寫，以清除目前游標位置的 n 個字元。 |
| ESC \[ &lt; n &gt; L | IL | 插入行 | 將 &lt; n &gt; 行插入緩衝區的游標位置。 游標所在的線條和其下的行，將會向下移動。 |
| ESC \[ &lt; n &gt; M | DL | 刪除行 | &lt; &gt; 從緩衝區刪除 n 行，從資料指標所在的資料列開始。 |



> [!NOTE]
>針對 IL 和 DL，只有滾動邊界中的線條 (看到滾動邊界) 會受到影響。 如果未設定邊界，則預設邊界框線為目前的區。 如果線條會在邊界下方移位，則會捨棄它們。 當刪除線條時，會在邊界底部插入空白行，而不會影響來自區外的行。

針對每個序列，如果省略，則預設值為 n，預設值為 &lt; &gt; 0。



針對下列命令，參數 &lt; n &gt; 有3個有效值：

- 0會從目前的游標位置清除 (內含) 至行/顯示器的結尾
- 1從行/上顯示的開頭清除，直到和包含目前的游標位置
- 2清除整行/顯示


| 順序 | 程式碼 | 描述 | 行為 |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| ESC \[ &lt; n &gt; J | ED | 顯示中的清除 | &lt;以空白字元取代由 n 指定的目前視口/screen 中的所有文字 &gt; |
| ESC \[ &lt; n &gt; K | 音 | 行清除 | 將行上的所有文字取代為 &lt; n &gt; 以空白字元指定的游標 |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>文字格式設定


本節中的所有命令通常等同于呼叫 [**SetConsoleTextAttribute**](setconsoletextattribute.md) 主控台 api，以調整所有未來寫入至主控台輸出文字緩衝區的格式。

此命令的特殊之處是 &lt; ， &gt; 以下 n 位置可以接受0到16個參數（以分號分隔）。

如果未指定任何參數，則會將它視為與單一0參數相同。


| 順序 | 程式碼 | 描述 | 行為 |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| ESC \[ &lt; n &gt; m | SGR | 設定圖形轉譯 | 設定螢幕和文字的格式，如 n 所指定 &lt;&gt; |



下表的值可以在 n 中用 &lt; &gt; 來代表不同的格式模式。

格式化模式會從左至右套用。 套用競爭的格式化選項會導致最適合的選項優先。

針對指定色彩的選項，將會使用可使用 [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API 修改的主控台色彩表中定義的色彩。 如果資料表已修改為讓資料表中的「藍色」位置顯示 RGB 的紅色陰影，則 **前景藍色** 的所有呼叫都會顯示紅色色彩，直到另有變更為止。


| 值 | 描述 | 行為 |
|-------|---------------------------|--------------------------------------------------------------------|
| 0 | 預設 | 在修改之前，將所有屬性都傳回預設狀態 |
| 1 | 粗體/亮色 | 將亮度/濃度旗標套用至前景色彩 |
| 4 | Underline | 加底線 |
| 24 | 無底線 | 移除底線 |
| 7 | 負 | 交換前景和背景色彩 |
| 27 | 正面 (沒有負)  | 傳回法線的前景/背景 |
| 30 | 前景黑色 | 將非粗體/亮黑色套用至前景 |
| 31 | 前景紅色 | 將非粗體/亮紅色套用至前景 |
| 32 | 前景綠色 | 將非粗體/亮綠套用至前景 |
| 33 | 前景黃色 | 將非粗體/亮黃色套用至前景 |
| 34 | 前景藍色 | 將非粗體/亮藍套用至前景 |
| 35 | 前景洋紅 | 將非粗體/亮洋紅色套用至前景 |
| 36 | 前景青色 | 將非粗體/亮青套用至前景 |
| 37 | 前景白色 | 將非粗體/亮色套用至前景 |
| 38 | 延伸前景 | 將擴充的色彩值套用到前景 (請參閱以下詳細資料)  |
| 39 | 前景預設值 | 只套用預設值的前景部分 (請參閱 0)  |
| 40 | 黑色背景 | 將非粗體/亮黑色套用至背景 |
| 41 | 背景紅色 | 將非粗體/亮紅色套用至背景 |
| 42 | 背景綠色 | 在背景中套用非粗體/亮綠 |
| 43 | 背景黃色 | 將非粗體/亮黃色套用至背景 |
| 44 | 背景藍色 | 將非粗體/亮藍套用至背景 |
| 45 | 背景洋紅 | 將非粗體/明亮的洋紅色套用至背景 |
| 46 | 背景青色 | 將非粗體/亮青套用至背景 |
| 47 | 背景白色 | 將非粗體/亮色套用至背景 |
| 48 | 背景擴充 | 將擴充的色彩值套用至背景 (請參閱以下詳細資料)  |
| 49 | 背景預設值 | 只套用預設值的背景部分 (請參閱 0)  |
| 90 | 亮黑色前景黑色 | 將粗體字/亮黑色套用至前景 |
| 91 | 亮紅色前景紅色 | 將粗體/亮紅色套用至前景 |
| 92 | 亮綠前景綠色 | 將粗體/亮綠套用至前景 |
| 93 | 亮黃色前景 | 將粗體/亮黃色套用至前景 |
| 94 | 亮藍色前景 | 將粗體/亮藍色套用至前景 |
| 95 | 亮鮮前景洋紅 | 將粗體/亮洋紅色套用至前景 |
| 96 | 明亮的前景青色 | 將粗體/亮青套用至前景 |
| 97 | 亮亮前景白色 | 將粗體字/亮色套用至前景 |
| 100 | 亮黑色背景 | 將粗體字/亮黑色套用至背景 |
| 101 | 亮紅色背景紅色 | 將粗體/亮紅色套用至背景 |
| 102 | 亮綠背景綠色 | 將粗體/亮綠套用至背景 |
| 103 | 亮黃背景黃色 | 將粗體/亮黃色套用至背景 |
| 104 | 明亮的背景藍色 | 將粗體/亮藍色套用至背景 |
| 105 | 鮮鮮深的洋紅 | 將粗體字/亮紅色套用至背景 |
| 106 | 鮮鮮色青色 | 將粗體/亮青套用至背景 |
| 107 | 亮色背景白色 | 將粗體字/亮色套用至背景 |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>擴充色彩

某些虛擬終端模擬器支援的色彩調色板，大於 Windows 主控台所提供的16種色彩。 針對這些擴充的色彩，Windows 主控台將會從現有的16色資料表選擇最接近的適當色彩來顯示。 不同于上述的一般 SGR 值，擴充值會根據下表，在初始指標之後取用額外的參數。


| SGR 子序列 | 描述 |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| 38;二級 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt; | 將前景色彩設定為 &lt; r &gt; 、 &lt; g &gt; 、 &lt; b &gt; 參數中指定的 RGB 值\* |
| 48;二級 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt; | 將背景色彩設定為 &lt; r &gt; 、 &lt; g &gt; 、 &lt; b &gt; 參數中指定的 RGB 值\* |
| 38;.5 &lt;s&gt; | &lt; &gt; 在88或256色彩表中將前景色彩設定為 s 索引\* |
| 48;.5 &lt;s&gt; | 將背景色彩設定 &lt; 為 &gt; 88 或256色彩表中的 s 索引\* |



\*為了進行比較，內部維護的88和256色調色板是以 xterm 終端機模擬器為基礎。 目前無法修改比較/四捨五入資料表。


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>螢幕色彩


下列命令可讓應用程式將螢幕顏色選擇區值設定為任何 RGB 值。

RGB 值應該是和之間的十六進位 `0` 值 `ff` ，並以正斜線字元分隔 (例如 `rgb:1/24/86`) 。

請注意，此順序是一種 .OSC 「作業系統命令」順序，而不是類似許多其他序列的 CSI，因此以 "x1b" 為開頭 \\ \] ，而不是 " \\ x1b \[ "。


| 順序 | 描述 | 行為 |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| ESC \] 4; &lt;i &gt; ; rgb： &lt; r &gt;  /  &lt; g &gt;  /  &lt; b &gt; ESC | 修改螢幕色彩 | 將螢幕色彩調色板索引 &lt; i 設定 &gt; 為 &lt; r &gt; 、 &lt; g &gt; 、 &lt; b 中指定的 RGB 值&gt; |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>模式變更


這些是控制輸入模式的序列。 有兩組不同的輸入模式，也就是資料指標索引鍵模式和鍵盤按鍵模式。 資料指標索引鍵模式控制方向鍵以及 Home 和 End 所發出的序列，而鍵盤按鍵模式則是控制 numpad 上的索引鍵所發出的序列，以及函式金鑰。

這些模式中的每一個都是簡單的布林值設定，也就是資料指標索引鍵模式是標準 (預設) 或應用程式，而鍵盤按鍵模式則是數位 (預設) 或應用程式。

請參閱資料指標索引鍵和 Numpad & 函式金鑰區段，以瞭解這些模式發出的順序。


| 順序 | 程式碼 | 描述 | 行為 |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| ESC = | DECKPAM | 啟用鍵台應用程式模式 | 鍵盤按鍵會發出其應用程式模式序列。 |
| Esc &gt; | DECKPNM | 啟用數位鍵數位模式 | 鍵盤按鍵會發出其數值模式序列。 |
| ESC \[ ？ 1 小時 | DECCKM | 啟用資料指標索引鍵應用程式模式 | 鍵盤按鍵會發出其應用程式模式序列。 |
| ESC \[ ？ 1 l | DECCKM | 停用資料指標索引鍵應用程式模式 (使用正常模式)  | 鍵盤按鍵會發出其數值模式序列。 |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>查詢狀態


此區段中的所有命令通常等同于呼叫 Get \* 主控台 api，以取得目前主控台緩衝區狀態的狀態資訊。

> [!NOTE]
>這些查詢會在輸出資料流程上辨識時，立即將回應發出至主控台輸入資料流程，同時 \_ 設定啟用虛擬 \_ 終端 \_ 處理。 「啟用 \_ 虛擬 \_ 終端機輸入」旗標不適 \_ 用於查詢命令，因為它會假設讓查詢的應用程式一律要接收回複。




| 順序 | 程式碼 | 描述 | 行為 |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| ESC \[ 6 n | DECXCPR | 報表資料指標位置 | 將游標位置發出為： ESC \[ &lt; r &gt; ; &lt;&gt; &lt; r = 資料指標資料 &gt; &lt; 列和 c = 資料指標資料行 &gt; 的 c r |
| ESC \[ 0 c | 大 | 裝置屬性 | 報告終端機身分識別。 將發出 " \\ x1b \[ ？ 1; 0c"，指出「沒有選項的 VT101」。 |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>標籤


雖然 windows 主控台傳統上的索引標籤只會有八個字元，但使用 \* 特定序列的 nix 應用程式可以操控定位點在主控台視窗內的位置，以優化應用程式的資料指標移動。

下列順序可讓應用程式設定主控台視窗內的索引標籤停用位置、移除它們，並在其間進行導覽。


| 順序 | 程式碼 | 描述 | 行為 |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ESC H | 高溫 超導 | 水準索引標籤集合 | 在資料指標所在的目前資料行中設定制表位。 |
| ESC \[ &lt; n &gt; I | CHT | 資料指標水準 (向前) 索引標籤 | 將資料指標前進到相同資料列中的下一個資料行 () ，並使用 tab 鍵停止。 如果沒有其他索引標籤停止，請移至資料列中的最後一個資料行。 如果資料指標位於最後一個資料行中，請移至下一個資料列的第一個資料行。 |
| ESC \[ &lt; n &gt; Z | Cbt | 游標向後索引標籤 | 將資料指標移到相同資料列中的上一個資料行 () ，並使用 tab 鍵停止。 如果沒有其他索引標籤停止，請將游標移至第一個資料行。 如果資料指標在第一個資料行中，則不會移動資料指標。 |
| ESC \[ 0 g | Tbc | Tab 鍵清除 (目前的資料行)  | 清除目前資料行中的定位停駐點（如果有的話）。 否則不會執行任何動作。 |
| ESC \[ 3 g | Tbc | Tab 清除 (所有資料行)  | 清除目前設定的所有制表位。 |



- 針對 CHT 和 CBT， &lt; n &gt; 是選擇性參數， (預設值 = 1) 指出將游標朝指定的方向前進多少次。
- 如果沒有透過 HTS 設定的定位停駐點，CHT 和 CBT 會將視窗的第一個和最後一個資料行視為唯一的兩個索引標籤。
- 使用 HTS 設定索引標籤停止也會使主控台以與 \\ CHT 相同的方式，在索引標籤 (0x09 ' t ' ) 字元的輸出上流覽至下一個定位停駐點。

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>指定字元集


下列順序可讓程式變更現用字元集對應。 這可讓程式發出7位 ASCII 字元，但會在終端機畫面本身將它們顯示為其他圖像。 目前，只有兩個支援的字元集是 ASCII (預設) 和 DEC 特殊圖形字元集。 請參閱 <http://vt100.net/docs/vt220-rm/table2-4.html> ，以取得 DEC 特殊圖形字元集所表示的所有字元清單。


| 順序 | 描述 | 行為 |
|----------|--------------------------------------------|-------------------------------|
| ESC ( 0 | 指定字元集– DEC 線條繪圖 | 啟用 DEC 折線圖繪製模式 |
| ESC ( B | 指定字元集– US ASCII | 啟用 ASCII 模式 (預設值)  |



值得注意的是，DEC 線條繪圖模式用於在主控台應用程式中繪製框線。 下表顯示哪些 ASCII 字元對應到哪些線條繪圖字元。


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




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>滾動邊界


下列順序可讓程式設定受滾動作業影響之畫面的「捲動區域」。 這是在螢幕以其他方式（例如，在 ' \\ n ' 或 RI）上滾動時所調整的資料列子集。 這些邊界也會影響插入行 (IL) 和刪除行 (DL) 所修改的資料列，DL、向上快移 (SU) 並向下 SD (。

當填滿畫面的其餘部分，例如在應用程式底部有標題列或狀態列時，滾動邊界特別適用于螢幕的一部分，而不會滾動。

針對 DECSTBM，有兩個選擇性參數 &lt; t &gt; 和 &lt; b &gt; ，用來指定代表捲軸區域頂端和底部行（含）的資料列。 如果省略參數，則 &lt; &gt; 預設值為1， &lt; b &gt; 預設為目前的視口高度。

滾動邊界是每個緩衝區，因此重要的是，替代緩衝區和主要緩衝區會維護個別的滾動邊界設定 (因此，替代緩衝區中的全螢幕應用程式將不會損害主要緩衝區的邊界) 。


| 順序 | 程式碼 | 描述 | 行為 |
|--------------------------------|---------|----------------------|------------------------------------------------|
| ESC \[ &lt; t &gt; ; &lt;b &gt; r | DECSTBM | 設定捲動區域 | 設定區的 VT 滾動邊界。 |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>視窗標題


下列命令可讓應用程式將主控台視窗的標題設定為指定的 &lt; 字串 &gt; 參數。 字串必須小於255個字元才能接受。 這相當於使用指定的字串來呼叫 SetConsoleTitle。

請注意，這些順序是「作業系統命令」順序，而不是類似許多其他序列的 CSI，因此其開頭為 " \\ x1b \] "，而不是 " \\ x1b \[ "。


| 順序 | 描述 | 行為 |
|-------------------------------|---------------------------|----------------------------------------------------|
| ESC \] 0; &lt;字串 &gt; below | 設定圖示和視窗標題 | 將主控台視窗的標題設定為 &lt; 字串 &gt; 。 |
| ESC \] 2; &lt;字串 &gt; below | 設定視窗標題 | 將主控台視窗的標題設定為 &lt; 字串 &gt; 。 |



此處的終止字元是 "鐘" 字元，' \\ x07 '

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>替代螢幕緩衝區


\*Nix 樣式應用程式通常會利用替代的螢幕緩衝區，讓他們可以修改緩衝區的整個內容，而不會影響啟動它們的應用程式。 替代緩衝區完全是視窗的維度，不含任何回卷區域。

如需此行為的範例，請考慮從 bash 啟動 vim 的時機。 Vim 會使用整個畫面來編輯檔案，然後返回 bash 將原始緩衝區保持不變。


| 順序 | 描述 | 行為 |
|--------------------|-----------------------------|--------------------------------------------|
| ESC \[ ？ 1 0 4 9 h | 使用替代螢幕緩衝區 | 切換至新的替代螢幕緩衝區。 |
| ESC \[ ？ 1 0 4 9 l | 使用主畫面緩衝區 | 切換至主要緩衝區。 |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>視窗寬度


下列順序可以用來控制主控台視窗的寬度。 它們大致上等同于呼叫 SetConsoleScreenBufferInfoEx 主控台 API 來設定視窗寬度。


| 順序 | 程式碼 | 描述 | 行為 |
|--------------|---------|------------------------------|---------------------------------------------|
| ESC \[ ？ 3小時 | DECCOLM | 將資料行數目設定為132 | 將主控台寬度設定為132的資料行寬。 |
| ESC \[ ？ 3 l | DECCOLM | 將資料行數目設定為80 | 將主控台寬度設定為80的資料行寬。 |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>軟重設


您可以使用下列順序，將某些屬性重設為預設值。下列屬性會重設為下列預設值 (也列出了控制這些屬性的順序) ：

- 資料指標可見度：可見的 (DECTEM) 
- 數位鍵台：數位模式 (DECNKM) 
- 資料指標索引鍵模式：標準模式 (DECCKM) 
- 上邊界和下邊界： Top = 1、下 = 主控台高度 (DECSTBM) 
- 字元集：美國 ASCII
- 圖形轉譯：預設/關閉 (SGR) 
- 儲存資料指標狀態： Home position (0，0)  (DECSC) 


| 順序 | 程式碼 | 描述 | 行為 |
|------------|--------|-------------|----------------------------------------------------|
| ESC \[ ！ p | DECSTR | 軟重設 | 將某些終端機設定重設為預設值。 |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>輸入序列


如果 \_ \_ \_ 使用 SetConsoleMode 旗標在輸入緩衝區控制碼上設定啟用虛擬終端機輸入旗標，則在輸入資料流程上的主控台主機會發出下列終端機序列。

有兩種內部模式，可控制要針對指定的輸入索引鍵、資料指標索引鍵模式和鍵盤按鍵模式發出哪些順序。 這些會在 [模式變更] 區段中描述。

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>資料指標索引鍵


| 答案 | 標準模式 | 應用程式模式 |
|-------------|-------------|------------------|
| 向上箭號 | ESC \[ A | ESC O A |
| 向下箭號 | ESC \[ B | ESC O B |
| 向右鍵 | ESC \[ C | ESC O C |
| 向左鍵 | ESC \[ D | ESC O D |
| 首頁 | ESC \[ H | ESC O H |
| 結束 | ESC \[ F | ESC O F |



此外，如果按下任何鍵的 Ctrl 鍵，則會改為發出下列順序，而不論資料指標索引鍵模式為何：


| 答案 | 任何模式 |
|--------------------|----------------|
| Ctrl + 向上鍵 | ESC \[ 1; 5 A |
| Ctrl + 向下鍵 | ESC \[ 1; 5 B |
| Ctrl + 向右鍵 | ESC \[ 1; 5 C |
| Ctrl + 向左鍵 | ESC \[ 1; 5 D |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad & 功能金鑰


| 答案 | 順序 |
|-----------|--------------|
| 退格鍵 | 0x7f (DEL)  |
| 暫停 | 0x1a (子)  |
| 逸出 | 0x1b (ESC)  |
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



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>修飾 符

Alt 的處理方式是在序列前面加上 escape： ESC &lt; c， &gt; 其中 &lt; c &gt; 是作業系統傳遞的字元。 Alt + Ctrl 的處理方式相同，不同之處在于作業系統會將 c 鍵預先移位 &lt; &gt; 到適當的控制字元，以轉送至應用程式。

Ctrl 通常會與系統所收到的完全一樣傳遞。 這通常是將單一字元向下移動到控制字元保留空間 (0x0-0x1f) 。 例如，Ctrl + @ (0x40) 變成 NUL (0x00) 、Ctrl + \[ (0x5b) 會變成 ESC (0x1b) 等等。系統會根據下表，特別處理一些 Ctrl 鍵組合：


| 答案 | 順序 |
|--------------------|----------------|
| Ctrl + 空格鍵 | 0x00 (NUL)  |
| Ctrl + 向上鍵 | ESC \[ 1; 5 A |
| Ctrl + 向下鍵 | ESC \[ 1; 5 B |
| Ctrl + 向右鍵 | ESC \[ 1; 5 C |
| Ctrl + 向左鍵 | ESC \[ 1; 5 D |



> [!NOTE]
>左 <kbd>Ctrl</kbd> + 右 <kbd>Alt</kbd> 會視為 AltGr。 當兩者同時出現時，它們將會被移除，而系統所呈現字元的 Unicode 值將會傳遞至目標。 系統會根據目前的系統輸入設定，預先轉譯 AltGr 值。



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>樣品


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span id="example"></span><span id="EXAMPLE"></span>SGR 終端機序列的範例

下列程式碼提供數個文字格式的範例。

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
>在上述範例中，字串 ' `\x1b[31m` ' 是以 n 到31的方式執行 **ESC \[ &lt; n &gt; m** &lt; &gt; 。



下圖顯示先前程式碼範例的輸出。

![使用 sgr 命令的主控台輸出](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>啟用虛擬終端處理的範例

下列程式碼提供針對應用程式啟用虛擬終端處理的建議方式範例。 範例的目的是要示範：

1. 在使用 SetConsoleMode 設定之前，應該一律先透過 GetConsoleMode 抓取現有的模式並進行分析。

2. 檢查 SetConsoleMode 是否傳回 `0` ，以及 GetLastError 傳回狀態 \_ 無效 \_ 的參數是否為目前的機制，以判斷何時在下層系統上執行。 \_ \_ 使用位欄位中其中一個較新的主控台模式旗標來接收狀態無效參數的應用程式應該會正常地降低行為，並再試一次。

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

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>選取周年更新功能的範例

下列範例是以更健全的程式碼範例使用各種不同的 escape 序列來管理緩衝區，並強調 Windows 10 的周年更新中新增的功能。

此範例會使用替代的螢幕緩衝區、操作索引標籤停止、設定滾動邊界，以及變更字元集。

```C
//
// Copyright (C) Microsoft. All rights reserved.
//
#define DEFINE_CONSOLEV2_PROPERTIES

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
 printf(fIsTop? "l" : "m"); // print left corner 

 for (int i = 1; i < Size.X - 1; i++) 
 printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

 printf(fIsTop? "k" : "j"); // print right corner
 printf(CSI "0m");
 printf(ESC "(B"); // exit line drawing mode
}

void PrintStatusLine(char* const pszMessage, COORD const Size)
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
 printf(CSI "3;%dr", Size.Y-2);
 int iNumLines = Size.Y - 4;

 printf(CSI "1;1H");
 printf(CSI "102;30m");
 printf("Windows 10 Anniversary Update - VT Example"); 
 printf(CSI "0m");

 // Print a top border - Yellow
 printf(CSI "2;1H");
 PrintHorizontalBorder(Size, true);

 // // Print a bottom border
 printf(CSI "%d;1H", Size.Y-1);
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
 for (tab = 0; tab < iNumTabStops-1; tab++)
 {
 PrintVerticalBorder();
 printf("line=%d", line);
 printf("\t"); // advance to next tab stop
 }
 PrintVerticalBorder();// print border at right side
 if (line+1 != iNumLines)
 printf("\t"); // advance to next tab stop, (on the next line)
 }

 PrintStatusLine("Press any key to demonstrate scroll margins", Size);
 wch = _getwch();

 printf(CSI "3;1H"); 
 for (line = 0; line < iNumLines * 2; line++)
 {
 printf(CSI "K"); // clear the line
 int tab = 0;
 for (tab = 0; tab < iNumTabStops-1; tab++)
 {
 PrintVerticalBorder();
 printf("line=%d", line);
 printf("\t"); // advance to next tab stop
 }
 PrintVerticalBorder(); // print border at right side
 if (line+1 != iNumLines * 2)
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









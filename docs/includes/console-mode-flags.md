---
ms.openlocfilehash: fd8ccdcd4c86ee51ea14c5db6092982a1f4a0f7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038639"
---
如果 *hConsoleHandle* 參數是輸入控制碼，此模式可以是下列一或多個值。 建立主控台時，預設會啟用 [ **啟用 \_ 視窗 \_ 輸入]** 以外的所有輸入模式。

| 值 | 意義 |
|-|-|
| **ENABLE_ECHO_INPUT** 0x0004 | **[ReadFile](https://msdn.microsoft.com/library/windows/desktop/aa365467)** 或 **[ReadConsole](../readconsole.md)** 函式讀取的字元會在讀取時寫入至作用中螢幕緩衝區。 只有在同時啟用 **ENABLE_LINE_INPUT** 模式時，才能使用這個模式。 |
| **ENABLE_INSERT_MODE** 0x0020 | 啟用時，在主控台視窗中輸入的文字將會插入目前的游標位置，並且不會覆寫該位置後面的所有文字。 停用時，將會覆寫下列所有文字。 |
| **ENABLE_LINE_INPUT** 0x0002 | 只有在讀取換行字元時，才會傳回 **[ReadFile](https://msdn.microsoft.com/library/windows/desktop/aa365467)** 或 **[ReadConsole](../readconsole.md)** 函數。 如果停用此模式，則函式會在有一或多個字元可用時傳回。 |
| **ENABLE_MOUSE_INPUT** 0x0010 | 如果滑鼠指標位於主控台視窗的框線內，且視窗具有鍵盤焦點，則滑鼠移動和按下按鈕所產生的滑鼠事件會放置在輸入緩衝區中。 這些事件會由 **[ReadFile](https://msdn.microsoft.com/library/windows/desktop/aa365467)** 或 **[ReadConsole](../readconsole.md)** 捨棄，即使啟用此模式也是如此。 |
| **ENABLE_PROCESSED_INPUT** 0x0001 | CTRL + C 是由系統處理，而不是放在輸入緩衝區中。 如果 **[ReadFile](https://msdn.microsoft.com/library/windows/desktop/aa365467)** 或 **[ReadConsole](../readconsole.md)** 正在讀取輸入緩衝區，則系統會處理其他控制索引鍵，而不會在 **ReadFile** 或 **ReadConsole** 緩衝區中傳回。 如果也啟用了 **ENABLE_LINE_INPUT** 模式，則倒退鍵、換行字元和換行字元會由系統處理。 |
| **ENABLE_QUICK_EDIT_MODE** 0x0040 | 這個旗標可讓使用者使用滑鼠來選取和編輯文字。<br /><br />若要啟用此模式，請使用 `ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS` 。 若要停用此模式，請使用不含此旗標的 **ENABLE_EXTENDED_FLAGS** 。 |
| **ENABLE_WINDOW_INPUT** 0x0008 | 變更控制台螢幕緩衝區大小的使用者互動會在主控台的輸入緩衝區中報告。 您可以使用 **[ReadConsoleInput](../readconsoleinput.md)** 函式，而不是使用 **[ReadFile](https://msdn.microsoft.com/library/windows/desktop/aa365467)** 或 **[ReadConsole](../readconsole.md)** 的應用程式，從輸入緩衝區讀取這些事件的相關資訊。 |
| **ENABLE_VIRTUAL_TERMINAL_INPUT** 0x0200 | 設定此旗標會指示虛擬終端處理引擎將主控台視窗收到的使用者輸入轉換為 **[主控台虛擬終端機序列](../console-virtual-terminal-sequences.md)** ，可透過 **[WriteFile](https://msdn.microsoft.com/library/windows/desktop/aa365747)** 或 **[WriteConsole](../writeconsole.md)** 函式由支援的應用程式抓取。<br /><br />此旗標的一般用法是與輸出控制碼上的 ENABLE_VIRTUAL_TERMINAL_PROCESSING 搭配使用，以連接至透過虛擬終端機序列獨佔通訊的應用程式。 |

如果 *hConsoleHandle* 參數是螢幕緩衝區控制碼，此模式可以是下列其中一個或多個值。 建立螢幕緩衝區時，預設會啟用這兩種輸出模式。

| 值 | 意義 |
|-|-|
| **ENABLE_PROCESSED_OUTPUT** 0x0001 | **[WriteFile](https://msdn.microsoft.com/library/windows/desktop/aa365747)** 或 **[WriteConsole](../writeconsole.md)** 函式或 **[ReadFile](https://msdn.microsoft.com/library/windows/desktop/aa365467)** 或 **[ReadConsole](../readconsole.md)** 函式所寫入的字元會針對 ASCII 控制序列進行剖析，並執行正確的動作。 會處理倒退鍵、定位字元、鐘、換行字元和換行字元。 |
| **ENABLE_WRAP_AT_EOL_OUTPUT** 0x0002 | 使用 **[WriteFile](https://msdn.microsoft.com/library/windows/desktop/aa365747)** 或 **[WriteConsole](../writeconsole.md)** 或使用 **[ReadFile](https://msdn.microsoft.com/library/windows/desktop/aa365467)** 或 **[ReadConsole](../readconsole.md)** 來進行寫入時，資料指標會在到達目前資料列的結尾時移至下一個資料列的開頭。 這會使主控台視窗中顯示的資料列在游標前進到視窗中的最後一個資料列之後自動向上滾動。 它也會使主控台畫面緩衝區的內容 (。當游標前進到主控台螢幕緩衝區中的最後一個資料列之後，/discarding 主控台畫面緩衝區的頂端資料列) 。 如果停用此模式，則會以任何後續字元覆寫資料列中的最後一個字元。 |
| **ENABLE_VIRTUAL_TERMINAL_PROCESSING** 0x0004 | 使用 **[WriteFile](https://msdn.microsoft.com/library/windows/desktop/aa365747)** 或 **[WriteConsole](../writeconsole.md)** 進行寫入時，會剖析字元，以控制資料指標移動、色彩/字型模式，以及可透過現有的主控台 api 執行的類似控制字元序列。 如需詳細資訊，請參閱 **[主控台虛擬終端機序列](../console-virtual-terminal-sequences.md)** 。 |
| **DISABLE_NEWLINE_AUTO_RETURN** 0x0008 | 使用 **[WriteFile](https://msdn.microsoft.com/library/windows/desktop/aa365747)** 或 **[WriteConsole](../writeconsole.md)** 進行寫入時，會將額外的狀態加入至行尾換行，以延遲游標移動和緩衝區滾動作業。<br /><br />一般來說，當 **ENABLE_WRAP_AT_EOL_OUTPUT** 設定且文字到達行尾時，游標會立即移到下一行，而且緩衝區的內容會以一行滾動。 相較于設定此旗標，捲軸操作和游標移動會延遲到下一個字元抵達為止。 書寫的字元將列印在行的最後一個位置，而游標會維持在此字元的上方，就像 **ENABLE_WRAP_AT_EOL_OUTPUT** 是 off 一樣，但是下一個可列印的字元將會列印成 **ENABLE_WRAP_AT_EOL_OUTPUT** 開啟。 不會進行覆寫。 明確地說，游標會迅速往下移動到下一行，視需要執行捲軸、列印字元，然後將游標前移一個位置。<br /><br />此旗標的一般用法是與設定 **ENABLE_VIRTUAL_TERMINAL_PROCESSING** 搭配使用，以更好的方式模擬終端機模擬器，也就是在螢幕上寫入最後一個字元 (。/in 右下角) 不觸發立即滾動的行為，是所要的行為。 |
| **ENABLE_LVB_GRID_WORLDWIDE** 0x0010 | 撰寫字元屬性（包括 **[WriteConsoleOutput](../writeconsoleoutput.md)** 和 **[WriteConsoleOutputAttribute](../writeconsoleoutputattribute.md)** ）的 api，可讓您使用 **[字元屬性](../console-screen-buffers.md#character-attributes)** 的旗標來調整文字的前景和背景色彩。 此外，使用 COMMON_LVB 前置詞指定了 DBCS 旗標的範圍。 在過去，這些旗標只會在中文、日文和韓文語言的 DBCS 字碼頁中正常進行。<br /><br />除了開頭的位元組和尾端的位元組旗標以外，其餘的旗標描述線條繪製和反向影片 (）。/swap 前景和背景色彩) 可能有助於其他語言強調輸出的部分。<br /><br />設定此主控台模式旗標，可讓您在每個語言的每個字碼頁中使用這些屬性。<br /><br />預設為關閉，以維持與過去利用主控台忽略這些旗標的已知應用程式之間的相容性，這些旗標會在非 CJK 電腦上略過這些旗標，以基於自己的目的或意外的方式儲存這些欄位中的位。<br /><br />請注意，使用 ENABLE_VIRTUAL_TERMINAL_PROCESSING 模式可能會導致設定 LVB 格線和反向影片旗標，但如果連結的應用程式透過 **[主控台虛擬終端機序列](../console-virtual-terminal-sequences.md)** 要求底線或反向影片，則此旗標仍會關閉。 |

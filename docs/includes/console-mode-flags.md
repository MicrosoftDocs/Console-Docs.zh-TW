---
ms.openlocfilehash: fd8ccdcd4c86ee51ea14c5db6092982a1f4a0f7f
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "93038639"
---
如果 *hConsoleHandle* 參數是輸入控點，則模式可以是下列其中一或多個值。 建立主控台時，預設會啟用除了 **ENABLE\_WINDOW\_INPUT** 以外的所有輸入模式。

| 值 | 意義 |
|-|-|
| **ENABLE_ECHO_INPUT** 0x0004 | **[ReadFile](https://msdn.microsoft.com/library/windows/desktop/aa365467)** 或 **[ReadConsole](../readconsole.md)** 函式所讀取的字元會在讀取時寫入至使用中螢幕緩衝區。 只有在同時啟用 **ENABLE_LINE_INPUT** 模式時，才可使用此模式。 |
| **ENABLE_INSERT_MODE** 0x0020 | 若已啟用，在主控台視窗中輸入的文字將會插入於目前的游標位置，而該位置後面的所有文字不會遭到覆寫。 若已停用，將會覆寫下列所有文字。 |
| **ENABLE_LINE_INPUT** 0x0002 | 只有在讀取歸位字元時， **[ReadFile](https://msdn.microsoft.com/library/windows/desktop/aa365467)** 或 **[ReadConsole](../readconsole.md)** 函式才會傳回。 若已停用此模式，函式會在有一或多個字元可用時傳回。 |
| **ENABLE_MOUSE_INPUT** 0x0010 | 如果滑鼠指標位於主控台視窗的邊界內，而此視窗具有鍵盤焦點，則滑鼠移動和按下按鈕所產生的滑鼠事件會放在輸入緩衝區中。 **[ReadFile](https://msdn.microsoft.com/library/windows/desktop/aa365467)** 或 **[ReadConsole](../readconsole.md)** 會捨棄這些事件，即使已啟用此模式也一樣。 |
| **ENABLE_PROCESSED_INPUT** 0x0001 | CTRL+C 是由系統處理，而且不會放在輸入緩衝區中。 如果 **[ReadFile](https://msdn.microsoft.com/library/windows/desktop/aa365467)** 或 **[ReadConsole](../readconsole.md)** 正在讀取輸入緩衝區，則其他 Ctrl 鍵會由系統處理，而不會在 **ReadFile** 或 **ReadConsole** 緩衝區中傳回。 如果同時啟用了 **ENABLE_LINE_INPUT** 模式，則系統會處理退格鍵、歸位字元和換行字元。 |
| **ENABLE_QUICK_EDIT_MODE** 0x0040 | 此旗標可讓使用者使用滑鼠來選取和編輯文字。<br /><br />若要啟用此模式，請使用 `ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS`。 若要停用此模式，請使用不含此旗標的 **ENABLE_EXTENDED_FLAGS**。 |
| **ENABLE_WINDOW_INPUT** 0x0008 | 變更控制台螢幕緩衝區大小的使用者互動會在主控台的輸入緩衝區中回報。 應用程式可以使用 **[ReadConsoleInput](../readconsoleinput.md)** 函式從輸入緩衝區讀取這些事件的相關資訊，但不能使用 **[ReadFile](https://msdn.microsoft.com/library/windows/desktop/aa365467)** 或 **[ReadConsole](../readconsole.md)** 來讀取。 |
| **ENABLE_VIRTUAL_TERMINAL_INPUT** 0x0200 | 設定此旗標會指示虛擬終端機處理引擎將主控台視窗收到的使用者輸入轉換成 **[主控台虛擬終端機序列](../console-virtual-terminal-sequences.md)** ，其可由支援應用程式透過 **[WriteFile](https://msdn.microsoft.com/library/windows/desktop/aa365747)** 或 **[WriteConsole](../writeconsole.md)** 函式來擷取。<br /><br />此旗標的典型用法是要搭配輸出控點上的 ENABLE_VIRTUAL_TERMINAL_PROCESSING 使用，以連線到透過虛擬終端機序列獨佔通訊的應用程式。 |

如果 *hConsoleHandle* 參數是螢幕緩衝區控點，則模式可以是下列其中一或多個值。 建立螢幕緩衝區時，預設會啟用這兩種輸出模式。

| 值 | 意義 |
|-|-|
| **ENABLE_PROCESSED_OUTPUT** 0x0001 | 由 **[WriteFile](https://msdn.microsoft.com/library/windows/desktop/aa365747)** 或 **[WriteConsole](../writeconsole.md)** 函式寫入的字元，或由 **[ReadFile](https://msdn.microsoft.com/library/windows/desktop/aa365467)** 或 **[ReadConsole](../readconsole.md)** 函式所回應的字元會針對 ASCII 控制序列進行剖析，並執行正確的動作。 系統會處理退格鍵、定位字元、鈴字元、歸位字元和換行字元。 |
| **ENABLE_WRAP_AT_EOL_OUTPUT** 0x0002 | 使用 **[WriteFile](https://msdn.microsoft.com/library/windows/desktop/aa365747)** 或 **[WriteConsole](../writeconsole.md)** 寫入或使用 **[ReadFile](https://msdn.microsoft.com/library/windows/desktop/aa365467)** 或 **[ReadConsole](../readconsole.md)** 回應時，游標會在到達目前資料列的結尾時移至下一個資料列的開頭。 這會導致主控台視窗中顯示的資料列在游標前進超過視窗中最後一個資料列時，自動向上捲動。 也會在游標前進超過主控台螢幕緩衝區中最後一個資料列時，導致主控台螢幕緩衝區的內容向上捲動 (捨棄主控台螢幕緩衝區的頂端資料列)。 如果停用此模式，則會以任何後續字元覆寫資料列中的最後一個字元。 |
| **ENABLE_VIRTUAL_TERMINAL_PROCESSING** 0x0004 | 使用 **[WriteFile](https://msdn.microsoft.com/library/windows/desktop/aa365747)** 或 **[WriteConsole](../writeconsole.md)** 寫入時，系統會針對 VT100 和類似的控制字元序列剖析字元，而這些序列可控制游標移動、色彩/字型模式，以及其他也可透過現有主控台 API 執行的作業。 如需詳細資訊，請參閱 **[主控台虛擬終端機序列](../console-virtual-terminal-sequences.md)** 。 |
| **DISABLE_NEWLINE_AUTO_RETURN** 0x0008 | 使用 **[WriteFile](https://msdn.microsoft.com/library/windows/desktop/aa365747)** 或 **[WriteConsole](../writeconsole.md)** 寫入時，這會將其他狀態新增至行尾換行，以延遲游標移動和緩衝區捲動作業。<br /><br />通常已設定 **ENABLE_WRAP_AT_EOL_OUTPUT** 且文字到達行尾時，游標會立即移至下一行，而緩衝區的內容會向上捲動一行。 相較於設定此旗標，捲動作業和游標移動會延遲到下一個字元抵達為止。 寫入的字元會列印在行的最後一個位置，而游標會繼續留在此字元上方 (猶如 **ENABLE_WRAP_AT_EOL_OUTPUT** 已關閉)，但下一個可列印的字元會列印 (猶如 **ENABLE_WRAP_AT_EOL_OUTPUT** 已開啟)。 不會發生覆寫。 具體而言，游標會快速前進到下一行，必要時會執行捲動，列印字元，且游標會前進一個位置。<br /><br />此旗標的典型用法是要搭配 **ENABLE_VIRTUAL_TERMINAL_PROCESSING** 設定使用，更完善地模擬終端機模擬器，而在其中於螢幕上寫入最後一個字元 (在右下角) 而不觸發立即捲動則是想要的行為。 |
| **ENABLE_LVB_GRID_WORLDWIDE** 0x0010 | 可供寫入字元屬性 (包括 **[WriteConsoleOutput](../writeconsoleoutput.md)** 和 **[WriteConsoleOutputAttribute](../writeconsoleoutputattribute.md)** ) 的 API 允許從 **[字元屬性](../console-screen-buffers.md#character-attributes)** 使用旗標，以調整文字的前景和背景色彩。 此外，已使用 COMMON_LVB 前置詞指定了 DBCS 旗標的範圍。 過去，這些旗標只會在中文、日文和韓文的 DBCS 字碼頁中運作。<br /><br />除了前置位元組和尾端位元組旗標以外，其餘描述線條繪製和反轉影片 (交換前景和背景色彩) 的旗標都有助於其他語言強調輸出的部分。<br /><br />設定此主控台模式旗標可讓您在每種語言的每個字碼頁中使用這些屬性。<br /><br />此旗標預設為關閉，來與過去利用主控台的已知應用程式維持相容，而在非 CJK 電腦上忽略這些旗標，可針對自己的目的或意外地在這些欄位中儲存位元。<br /><br />請注意，使用 ENABLE_VIRTUAL_TERMINAL_PROCESSING 模式可能導致設定 LVB 格線和反轉影片旗標，而當附加的應用程式透過 **[主控台虛擬終端機序列](../console-virtual-terminal-sequences.md)** 要求加底線或倒轉影片時，此旗標仍會關閉。 |

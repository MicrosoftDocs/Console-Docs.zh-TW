---
title: GetConsoleMode 函式
description: 抓取主控台之輸入緩衝區的目前輸入模式，或主控台螢幕緩衝區目前的輸出模式。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi/GetConsoleMode
- wincon/GetConsoleMode
- GetConsoleMode
MS-HAID:
- '\_win32\_getconsolemode'
- base.getconsolemode
- consoles.getconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 49adf618-196d-4490-93ca-cd177807f58e
topic_type:
- apiref
api_name:
- GetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a2d18ed191d1d82cc54c3277aa38badb0aedb630
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059139"
---
# <a name="getconsolemode-function"></a>GetConsoleMode 函式


抓取主控台之輸入緩衝區的目前輸入模式，或主控台螢幕緩衝區目前的輸出模式。

<a name="syntax"></a>語法
------

```C
BOOL WINAPI GetConsoleMode(
  _In_  HANDLE  hConsoleHandle,
  _Out_ LPDWORD lpMode
);
```

<a name="parameters"></a>參數
----------

*hConsoleHandle* \[在\]  
主控台輸入緩衝區或主控台螢幕緩衝區的控制碼。 控制碼必須具有 **一般 \_ 讀取** 許可權。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpMode* \[擴展\]  
變數的指標，此變數會接收指定緩衝區的目前模式。

如果 *hConsoleHandle* 參數是輸入控制碼，此模式可以是下列一或多個值。 建立主控台時，預設會啟用 [ **啟用 \_ 視窗 \_ 輸入]** 以外的所有輸入模式。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>值</th>
<th>意義</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="ENABLE_ECHO_INPUT"></span><span id="enable_echo_input"></span>
<strong>ENABLE_ECHO_INPUT</strong> 0x0004</td>
<td><p><a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a>或<a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>函式讀取的字元會在讀取時寫入至作用中螢幕緩衝區。 只有在同時啟用 <strong>ENABLE_LINE_INPUT</strong> 模式時，才能使用這個模式。</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_INSERT_MODE"></span><span id="enable_insert_mode"></span>
<strong>ENABLE_INSERT_MODE</strong> 0x0020</td>
<td><p>啟用時，在主控台視窗中輸入的文字將會插入目前的游標位置，並且不會覆寫該位置後面的所有文字。 停用時，將會覆寫下列所有文字。</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_LINE_INPUT"></span><span id="enable_line_input"></span>
<strong>ENABLE_LINE_INPUT</strong> 0x0002</td>
<td><p>只有在讀取換行字元時，才會傳回 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> 或 <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> 函數。 如果停用此模式，則函式會在有一或多個字元可用時傳回。</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_MOUSE_INPUT"></span><span id="enable_mouse_input"></span>
<strong>ENABLE_MOUSE_INPUT</strong> 0x0010</td>
<td><p>如果滑鼠指標位於主控台視窗的框線內，且視窗具有鍵盤焦點，則滑鼠移動和按下按鈕所產生的滑鼠事件會放置在輸入緩衝區中。 這些事件會由 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> 或 <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>捨棄，即使啟用此模式也是如此。</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_PROCESSED_INPUT"></span><span id="enable_processed_input"></span>
<strong>ENABLE_PROCESSED_INPUT</strong> 0x0001</td>
<td><p>CTRL + C 是由系統處理，而不是放在輸入緩衝區中。 如果 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> 或 <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>正在讀取輸入緩衝區，則系統會處理其他控制索引鍵，而不會在 <strong>ReadFile</strong> 或 <strong>ReadConsole</strong> 緩衝區中傳回。 如果也啟用了 <strong>ENABLE_LINE_INPUT</strong> 模式，則倒退鍵、換行字元和換行字元會由系統處理。</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_QUICK_EDIT_MODE"></span><span id="enable_quick_edit_mode"></span>
<strong>ENABLE_QUICK_EDIT_MODE</strong> 0x0040</td>
<td><p>這個旗標可讓使用者使用滑鼠來選取和編輯文字。</p>
<p>若要啟用此模式，請使用 <code>ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS</code> 。 若要停用此模式，請使用不含此旗標的 <strong>ENABLE_EXTENDED_FLAGS</strong> 。</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_WINDOW_INPUT"></span><span id="enable_window_input"></span>
<strong>ENABLE_WINDOW_INPUT</strong> 0x0008</td>
<td><p>變更控制台螢幕緩衝區大小的使用者互動會在主控台&#39;s 輸入緩衝區中報告。 您可以使用 <a href="readconsoleinput.md" data-raw-source="[&lt;strong&gt;ReadConsoleInput&lt;/strong&gt;](readconsoleinput.md)"><strong>ReadConsoleInput</strong></a> 函式，而不是使用 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> 或 <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>的應用程式，從輸入緩衝區讀取這些事件的相關資訊。</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_VIRTUAL_TERMINAL_INPUT"></span><span id="enable_virtual_terminal_input"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_INPUT</strong> 0x0200</td>
<td><p>設定此旗標會指示虛擬終端處理引擎將主控台視窗收到的使用者輸入轉換為 <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">主控台虛擬終端機序列</a> ，可透過 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> 或 <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> 函式由支援的應用程式抓取。</p>
<p>此旗標的一般用法是與輸出控制碼上的 ENABLE_VIRTUAL_TERMINAL_PROCESSING 搭配使用，以連接至透過虛擬終端機序列獨佔通訊的應用程式。</p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

如果 *hConsoleHandle* 參數是螢幕緩衝區控制碼，此模式可以是下列其中一個或多個值。 建立螢幕緩衝區時，預設會啟用這兩種輸出模式。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>值</th>
<th>意義</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="ENABLE_PROCESSED_OUTPUT"></span><span id="enable_processed_output"></span>
<strong>ENABLE_PROCESSED_OUTPUT</strong> 0x0001</td>
<td><p><a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a>或<a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>函式或<a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a>或<a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>函式所寫入的字元會針對 ASCII 控制序列進行剖析，並執行正確的動作。 會處理倒退鍵、定位字元、鐘、換行字元和換行字元。</p></td>
</tr>
<tr class="even">
<td><span id="ENABLE_WRAP_AT_EOL_OUTPUT"></span><span id="enable_wrap_at_eol_output"></span>
<strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong> 0x0002</td>
<td><p>使用 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> 或 <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> 或使用 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> 或 <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>來進行寫入時，資料指標會在到達目前資料列的結尾時移至下一個資料列的開頭。 這會使主控台視窗中顯示的資料列在游標前進到視窗中的最後一個資料列之後自動向上滾動。 它也會使主控台畫面緩衝區的內容 (捨棄主控台畫面緩衝區的頂端列，) 當游標前進到主控台螢幕緩衝區中的最後一個資料列之後。 如果停用此模式，則會以任何後續字元覆寫資料列中的最後一個字元。</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_VIRTUAL_TERMINAL_PROCESSING"></span><span id="enable_virtual_terminal_processing"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_PROCESSING</strong> 0x0004</td>
<td><p>使用 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> 或 <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>進行寫入時，會剖析字元，以控制資料指標移動、色彩/字型模式，以及可透過現有的主控台 api 執行的類似控制字元序列。 如需詳細資訊，請參閱 <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">主控台虛擬終端機序列</a>。</p></td>
</tr>
<tr class="even">
<td><span id="DISABLE_NEWLINE_AUTO_RETURN"></span><span id="disable_newline_auto_return"></span>
<strong>DISABLE_NEWLINE_AUTO_RETURN</strong> 0x0008</td>
<td><p>使用 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> 或 <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>進行寫入時，會將額外的狀態加入至行尾換行，以延遲游標移動和緩衝區滾動作業。</p>
<p>一般來說，當 ENABLE_WRAP_AT_EOL_OUTPUT 設定且文字到達行尾時，游標會立即移到下一行，而且緩衝區的內容會以一行滾動。 相較于設定此旗標，捲軸操作和游標移動會延遲到下一個字元抵達為止。 書寫的字元將列印在行的最後一個位置，而游標會維持在此字元的上方，就像 ENABLE_WRAP_AT_EOL_OUTPUT 是 off 一樣，但是下一個可列印的字元將會列印成 ENABLE_WRAP_AT_EOL_OUTPUT 開啟。 不會進行覆寫。 明確地說，游標會迅速往下移動到下一行，視需要執行捲軸、列印字元，然後將游標前移一個位置。</p>
<p>此旗標的一般用法是與設定 ENABLE_VIRTUAL_TERMINAL_PROCESSING 搭配使用，以更好的方式模擬終端機模擬器，也就是在右下) 角將畫面上的最後一個字元寫入 (，而不觸發立即滾動的行為是想要的行為。</p></td>
</tr>
<tr class="odd">
<td><span id="ENABLE_LVB_GRID_WORLDWIDE"></span><span id="enable_lvb_grid_worldwide"></span>
<strong>ENABLE_LVB_GRID_WORLDWIDE</strong> 0x0010</td>
<td><p>撰寫字元屬性（包括 <a href="writeconsoleoutput.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutput&lt;/strong&gt;](writeconsoleoutput.md)"><strong>WriteConsoleOutput</strong></a> 和 <a href="writeconsoleoutputattribute.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutputAttribute&lt;/strong&gt;](writeconsoleoutputattribute.md)"><strong>WriteConsoleOutputAttribute</strong></a> ）的 api，可讓您使用 <a href="https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes" data-raw-source="[character attributes](https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes)">字元屬性</a> 的旗標來調整文字的前景和背景色彩。 此外，使用 COMMON_LVB 前置詞指定了 DBCS 旗標的範圍。 在過去，這些旗標只會在中文、日文和韓文語言的 DBCS 字碼頁中正常進行。</p>
<p>除了開頭的位元組和尾端的位元組旗標以外，其餘的旗標描述線條繪製和反向影片 (交換前景和背景色彩) 可能有助於其他語言強調輸出的部分。</p>
<p>設定此主控台模式旗標，可讓您在每個語言的每個字碼頁中使用這些屬性。</p>
<p>預設為關閉，以維持與過去利用主控台忽略這些旗標的已知應用程式之間的相容性，這些旗標會在非 CJK 電腦上略過這些旗標，以基於自己的目的或意外的方式儲存這些欄位中的位。</p>
<p>請注意，使用 ENABLE_VIRTUAL_TERMINAL_PROCESSING 模式可能會導致設定 LVB 格線和反向影片旗標，但如果連結的應用程式透過 <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">主控台虛擬終端機序列</a>要求底線或反向影片，則此旗標仍會關閉。</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="return-value"></a>傳回值
------------

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

<a name="remarks"></a>備註
-------

主控台包含輸入緩衝區和一或多個螢幕緩衝區。 主控台緩衝區的模式會決定主控台在輸入或輸出 (i/o) 作業時的行為。 有一組旗標常數用於輸入控制碼，而另一組則是與螢幕緩衝區 (輸出) 控制碼一起使用。 設定一個螢幕緩衝區的輸出模式，並不會影響其他螢幕緩衝區的輸出模式。

「 **啟用 \_ 行 \_ 輸入** 」和「 **啟用 \_ ECHO \_ 輸入** 」模式只會影響使用 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 或 [**ReadConsole**](readconsole.md) 從主控台的輸入緩衝區讀取的進程。 同樣地， **啟用 \_ 處理的 \_ 輸入** 模式主要會影響 **ReadFile** 和 **ReadConsole** 使用者，不同之處在于它也會決定在輸入緩衝區中是否報告 CTRL + C 輸入 (由 [**ReadConsoleInput**](readconsoleinput.md) 函式讀取) 或傳遞給應用程式所定義的函式。

[ **啟用 \_ 視窗 \_ 輸入]** 和 [ **啟用 \_ 滑鼠 \_ 輸入** ] 模式會決定是否要在輸入緩衝區中報告與視窗調整大小和滑鼠動作相關的使用者互動。 這些事件可由 [**ReadConsoleInput**](readconsoleinput.md)讀取，但一律會依 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 和 [**ReadConsole**](readconsole.md)進行篩選。

在** \_ \_ \_ EOL \_ 輸出**模式下**啟用已處理的 \_ \_ 輸出**和啟用 WRAP，只會影響使用[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)或[**ReadConsole**](readconsole.md)和[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)或[**WriteConsole**](writeconsole.md)的進程。

若要變更控制台的 i/o 模式，請呼叫 [**SetConsoleMode**](setconsolemode.md) 函式。

<a name="examples"></a>範例
--------

如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。

<a name="requirements"></a>規格需求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>最低支援的用戶端</p></td>
<td><p>Windows 2000 Professional [僅限桌面應用程式]</p></td>
</tr>
<tr class="even">
<td><p>最低支援的伺服器</p></td>
<td><p>Windows 2000 伺服器 [僅限桌面應用程式]</p></td>
</tr>
<tr class="odd">
<td><p>標頭</p></td>
<td>ConsoleApi .h (via Wincon，包括 Windows .h) </td>
</tr>
<tr class="even">
<td><p>程式庫</p></td>
<td>Kernel32.dll .lib</td>
</tr>
<tr class="odd">
<td><p>DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另請參閱


[主控台功能](console-functions.md)

[主控台模式](console-modes.md)

[**ReadConsole**](readconsole.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[**SetConsoleMode**](setconsolemode.md)

[**WriteConsole**](writeconsole.md)

[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 





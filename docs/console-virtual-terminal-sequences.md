---
title: 主控台虛擬終端機序列
description: 虛擬終端機序列是控制字元序列，可以控制資料指標移動、色彩/字型模式，以及寫入輸出資料流程時的其他作業。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: A5C553A5-FD84-4D16-A814-EDB3B8699B91
ms.openlocfilehash: d05aa6f44cc97478d4eb2aba25587b2506e84a98
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059254"
---
# <a name="console-virtual-terminal-sequences"></a><span data-ttu-id="a3744-104">主控台虛擬終端機序列</span><span class="sxs-lookup"><span data-stu-id="a3744-104">Console Virtual Terminal Sequences</span></span>


<span data-ttu-id="a3744-105">虛擬終端機序列是控制字元序列，可以控制資料指標移動、色彩/字型模式，以及寫入輸出資料流程時的其他作業。</span><span class="sxs-lookup"><span data-stu-id="a3744-105">Virtual terminal sequences are control character sequences that can control cursor movement, color/font mode, and other operations when written to the output stream.</span></span> <span data-ttu-id="a3744-106">當設定適當的模式時，也可以在輸入資料流程上接收序列，以回應輸出資料流程查詢資訊序列或使用者輸入的編碼。</span><span class="sxs-lookup"><span data-stu-id="a3744-106">Sequences may also be received on the input stream in response to an output stream query information sequence or as an encoding of user input when the appropriate mode is set.</span></span>

<span data-ttu-id="a3744-107">您可以使用 [**GetConsoleMode**](getconsolemode.md) 和 [**SetConsoleMode**](setconsolemode.md) 函數來設定此行為。</span><span class="sxs-lookup"><span data-stu-id="a3744-107">You can use [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions to configure this behavior.</span></span> <span data-ttu-id="a3744-108">本檔的結尾包含啟用虛擬終端行為的建議方式範例。</span><span class="sxs-lookup"><span data-stu-id="a3744-108">A sample of the suggested way to enable virtual terminal behaviors is included at the end of this document.</span></span>

<span data-ttu-id="a3744-109">下列順序的行為取決於 VT100 和衍生的終端機模擬器技術，尤其是 xterm 終端機模擬器。</span><span class="sxs-lookup"><span data-stu-id="a3744-109">The behavior of the following sequences is based on the VT100 and derived terminal emulator technologies, most specifically the xterm terminal emulator.</span></span> <span data-ttu-id="a3744-110">您可以在和 at 找到終端機序列的詳細資訊 <http://vt100.net> <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html> 。</span><span class="sxs-lookup"><span data-stu-id="a3744-110">More information about terminal sequences can be found at <http://vt100.net> and at <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span></span>

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span data-ttu-id="a3744-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>輸出序列</span><span class="sxs-lookup"><span data-stu-id="a3744-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Output Sequences</span></span>


<span data-ttu-id="a3744-112">如果使用 SetConsoleMode 函式在 \_ \_ \_ 螢幕緩衝區控制碼上設定[**SetConsoleMode**](setconsolemode.md)了 [啟用虛擬終端處理] 旗標，則在寫入輸出資料流程時，主控台主機會攔截下列終端機序列。</span><span class="sxs-lookup"><span data-stu-id="a3744-112">The following terminal sequences are intercepted by the console host when written into the output stream, if the ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING flag is set on the screen buffer handle using the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="a3744-113">請注意，「停 \_ 用分行符號自動傳回」旗標在 \_ \_ 模擬其他終端機模擬器的資料指標定位和滾動行為時，可能也很有用，因為這些字元是寫入任何資料列中的最後一個資料行。</span><span class="sxs-lookup"><span data-stu-id="a3744-113">Note that the DISABLE\_NEWLINE\_AUTO\_RETURN flag may also be useful in emulating the cursor positioning and scrolling behavior of other terminal emulators in relation to characters written to the final column in any row.</span></span>

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span data-ttu-id="a3744-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>簡單的資料指標定位</span><span class="sxs-lookup"><span data-stu-id="a3744-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Simple Cursor Positioning</span></span>


<span data-ttu-id="a3744-115">在下列所有說明中，ESC 一律是十六進位值0x1B。</span><span class="sxs-lookup"><span data-stu-id="a3744-115">In all of the following descriptions, ESC is always the hexadecimal value 0x1B.</span></span> <span data-ttu-id="a3744-116">終端機序列中不包含任何空格。</span><span class="sxs-lookup"><span data-stu-id="a3744-116">No spaces are to be included in terminal sequences.</span></span> <span data-ttu-id="a3744-117">如需如何在實務中使用這些順序的範例，請參閱本主題結尾處的 [範例](#example) 。</span><span class="sxs-lookup"><span data-stu-id="a3744-117">For an example of how these sequences are used in practice, please see the [example](#example) at the end of this topic.</span></span>

<span data-ttu-id="a3744-118">下表說明在 ESC 字元之後直接使用單一動作命令的簡單 escape 序列。</span><span class="sxs-lookup"><span data-stu-id="a3744-118">The following table describes simple escape sequences with a single action command directly after the ESC character.</span></span> <span data-ttu-id="a3744-119">這些序列沒有任何參數，且會立即生效。</span><span class="sxs-lookup"><span data-stu-id="a3744-119">These sequences have no parameters and take effect immediately.</span></span>

<span data-ttu-id="a3744-120">此表格中的所有命令通常等同于呼叫 [**SetConsoleCursorPosition**](setconsolecursorposition.md) 主控台 API 來放置游標。</span><span class="sxs-lookup"><span data-stu-id="a3744-120">All commands in this table are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API to place the cursor.</span></span>

<span data-ttu-id="a3744-121">資料指標移動會由目前的資料區系結到緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a3744-121">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="a3744-122">如果沒有可用的) ， (滾動。</span><span class="sxs-lookup"><span data-stu-id="a3744-122">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="a3744-123">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-123">Sequence</span></span> | <span data-ttu-id="a3744-124">速記</span><span class="sxs-lookup"><span data-stu-id="a3744-124">Shorthand</span></span> | <span data-ttu-id="a3744-125">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-125">Behavior</span></span>                                                                                                                                      |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a3744-126">ESC A</span><span class="sxs-lookup"><span data-stu-id="a3744-126">ESC A</span></span>    | <span data-ttu-id="a3744-127">CUU</span><span class="sxs-lookup"><span data-stu-id="a3744-127">CUU</span></span>       | <span data-ttu-id="a3744-128">游標向上1</span><span class="sxs-lookup"><span data-stu-id="a3744-128">Cursor Up by 1</span></span>                                                                                                                                |
| <span data-ttu-id="a3744-129">ESC B</span><span class="sxs-lookup"><span data-stu-id="a3744-129">ESC B</span></span>    | <span data-ttu-id="a3744-130">反芻</span><span class="sxs-lookup"><span data-stu-id="a3744-130">CUD</span></span>       | <span data-ttu-id="a3744-131">資料指標向下1</span><span class="sxs-lookup"><span data-stu-id="a3744-131">Cursor Down by 1</span></span>                                                                                                                              |
| <span data-ttu-id="a3744-132">ESC C</span><span class="sxs-lookup"><span data-stu-id="a3744-132">ESC C</span></span>    | <span data-ttu-id="a3744-133">CUF</span><span class="sxs-lookup"><span data-stu-id="a3744-133">CUF</span></span>       | <span data-ttu-id="a3744-134">向前 (右) 的向前快轉資料指標1</span><span class="sxs-lookup"><span data-stu-id="a3744-134">Cursor Forward (Right) by 1</span></span>                                                                                                                   |
| <span data-ttu-id="a3744-135">ESC D</span><span class="sxs-lookup"><span data-stu-id="a3744-135">ESC D</span></span>    | <span data-ttu-id="a3744-136">幼 崽</span><span class="sxs-lookup"><span data-stu-id="a3744-136">CUB</span></span>       | <span data-ttu-id="a3744-137">將游標向左 (左) 1</span><span class="sxs-lookup"><span data-stu-id="a3744-137">Cursor Backward (Left) by 1</span></span>                                                                                                                   |
| <span data-ttu-id="a3744-138">ESC M</span><span class="sxs-lookup"><span data-stu-id="a3744-138">ESC M</span></span>    | <span data-ttu-id="a3744-139">RI</span><span class="sxs-lookup"><span data-stu-id="a3744-139">RI</span></span>        | <span data-ttu-id="a3744-140">反向索引–執行 n 的反向運算 \\ 、將游標向上移動一行、維持水準位置、視需要滾動緩衝區\*</span><span class="sxs-lookup"><span data-stu-id="a3744-140">Reverse Index – Performs the reverse operation of \\n, moves cursor up one line, maintains horizontal position, scrolls buffer if necessary\*</span></span> |
| <span data-ttu-id="a3744-141">ESC 7</span><span class="sxs-lookup"><span data-stu-id="a3744-141">ESC 7</span></span>    | <span data-ttu-id="a3744-142">DECSC</span><span class="sxs-lookup"><span data-stu-id="a3744-142">DECSC</span></span>     | <span data-ttu-id="a3744-143">將游標位置儲存在記憶體中\*\*</span><span class="sxs-lookup"><span data-stu-id="a3744-143">Save Cursor Position in Memory\*\*</span></span>                                                                                                            |
| <span data-ttu-id="a3744-144">ESC 8</span><span class="sxs-lookup"><span data-stu-id="a3744-144">ESC 8</span></span>    | <span data-ttu-id="a3744-145">DECSR</span><span class="sxs-lookup"><span data-stu-id="a3744-145">DECSR</span></span>     | <span data-ttu-id="a3744-146">從記憶體還原資料指標位置\*\*</span><span class="sxs-lookup"><span data-stu-id="a3744-146">Restore Cursor Position from Memory\*\*</span></span>                                                                                                       |



<span data-ttu-id="a3744-147">**注意**</span><span class="sxs-lookup"><span data-stu-id="a3744-147">**Note**</span></span>  
<span data-ttu-id="a3744-148">\* 如果有設定捲軸邊界，則邊界內的 RI 只會滾動邊界的內容，並讓此區保持不變。</span><span class="sxs-lookup"><span data-stu-id="a3744-148">\* If there are scroll margins set, RI inside the margins will scroll only the contents of the margins, and leave the viewport unchanged.</span></span> <span data-ttu-id="a3744-149"> (請參閱滾動邊界) </span><span class="sxs-lookup"><span data-stu-id="a3744-149">(See Scrolling Margins)</span></span>

<span data-ttu-id="a3744-150">\*\*在第一次使用 save 命令之前，記憶體中不會儲存任何值。</span><span class="sxs-lookup"><span data-stu-id="a3744-150">\*\*There will be no value saved in memory until the first use of the save command.</span></span> <span data-ttu-id="a3744-151">存取儲存值的唯一方法是使用 restore 命令。</span><span class="sxs-lookup"><span data-stu-id="a3744-151">The only way to access the saved value is with the restore command.</span></span>



## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span data-ttu-id="a3744-152"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>資料指標定位</span><span class="sxs-lookup"><span data-stu-id="a3744-152"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursor Positioning</span></span>


<span data-ttu-id="a3744-153">下表包含控制順序 Introducer (CSI) 類型序列。</span><span class="sxs-lookup"><span data-stu-id="a3744-153">The following tables encompass Control Sequence Introducer (CSI) type sequences.</span></span> <span data-ttu-id="a3744-154">所有 CSI 序列都以 ESC 開頭 (0x1B) 接著 \[ (左括弧、0x5B) ，而且可能包含變數長度的參數，以指定每項作業的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a3744-154">All CSI sequences start with ESC (0x1B) followed by \[ (left bracket, 0x5B) and may contain parameters of variable length to specify more information for each operation.</span></span> <span data-ttu-id="a3744-155">這會以速記 &lt; n 表示 &gt; 。</span><span class="sxs-lookup"><span data-stu-id="a3744-155">This will be represented by the shorthand &lt;n&gt;.</span></span> <span data-ttu-id="a3744-156">下表依功能分組，每個資料表都說明群組的運作方式。</span><span class="sxs-lookup"><span data-stu-id="a3744-156">Each table below is grouped by functionality with notes below each table explaining how the group works.</span></span>

<span data-ttu-id="a3744-157">針對所有參數，除非另有說明，否則適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="a3744-157">For all parameters, the following rules apply unless otherwise noted:</span></span>

- <span data-ttu-id="a3744-158">&lt;n &gt; 代表要移動的距離，而且是選擇性參數</span><span class="sxs-lookup"><span data-stu-id="a3744-158">&lt;n&gt; represents the distance to move and is an optional parameter</span></span>
- <span data-ttu-id="a3744-159">如果 &lt; &gt; 省略 n 或等於0，則會將它視為1</span><span class="sxs-lookup"><span data-stu-id="a3744-159">If &lt;n&gt; is omitted or equals 0, it will be treated as a 1</span></span>
- <span data-ttu-id="a3744-160">&lt;n &gt; 不能大於 32767 (最大短值) </span><span class="sxs-lookup"><span data-stu-id="a3744-160">&lt;n&gt; cannot be larger than 32,767 (maximum short value)</span></span>
- <span data-ttu-id="a3744-161">&lt;n &gt; 不可以是負數</span><span class="sxs-lookup"><span data-stu-id="a3744-161">&lt;n&gt; cannot be negative</span></span>

<span data-ttu-id="a3744-162">此區段中的所有命令通常等同于呼叫 [**SetConsoleCursorPosition**](setconsolecursorposition.md) 主控台 API。</span><span class="sxs-lookup"><span data-stu-id="a3744-162">All commands in this section are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API.</span></span>

<span data-ttu-id="a3744-163">資料指標移動會由目前的資料區系結到緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a3744-163">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="a3744-164">如果沒有可用的) ， (滾動。</span><span class="sxs-lookup"><span data-stu-id="a3744-164">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="a3744-165">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-165">Sequence</span></span>                       | <span data-ttu-id="a3744-166">程式碼</span><span class="sxs-lookup"><span data-stu-id="a3744-166">Code</span></span>      | <span data-ttu-id="a3744-167">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-167">Description</span></span>                         | <span data-ttu-id="a3744-168">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-168">Behavior</span></span>                                                                                                                   |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a3744-169">ESC \[ &lt; n &gt; A</span><span class="sxs-lookup"><span data-stu-id="a3744-169">ESC \[ &lt;n&gt; A</span></span>             | <span data-ttu-id="a3744-170">CUU</span><span class="sxs-lookup"><span data-stu-id="a3744-170">CUU</span></span>       | <span data-ttu-id="a3744-171">Cursor Up</span><span class="sxs-lookup"><span data-stu-id="a3744-171">Cursor Up</span></span>                           | <span data-ttu-id="a3744-172">依 n 的游標 &lt;&gt;</span><span class="sxs-lookup"><span data-stu-id="a3744-172">Cursor up by &lt;n&gt;</span></span>                                                                                                     |
| <span data-ttu-id="a3744-173">ESC \[ &lt; n &gt; B</span><span class="sxs-lookup"><span data-stu-id="a3744-173">ESC \[ &lt;n&gt; B</span></span>             | <span data-ttu-id="a3744-174">反芻</span><span class="sxs-lookup"><span data-stu-id="a3744-174">CUD</span></span>       | <span data-ttu-id="a3744-175">游標向下</span><span class="sxs-lookup"><span data-stu-id="a3744-175">Cursor Down</span></span>                         | <span data-ttu-id="a3744-176">向下游標向下 &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="a3744-176">Cursor down by &lt;n&gt;</span></span>                                                                                                   |
| <span data-ttu-id="a3744-177">ESC \[ &lt; n &gt; C</span><span class="sxs-lookup"><span data-stu-id="a3744-177">ESC \[ &lt;n&gt; C</span></span>             | <span data-ttu-id="a3744-178">CUF</span><span class="sxs-lookup"><span data-stu-id="a3744-178">CUF</span></span>       | <span data-ttu-id="a3744-179">向前資料指標</span><span class="sxs-lookup"><span data-stu-id="a3744-179">Cursor Forward</span></span>                      | <span data-ttu-id="a3744-180">向前 (右) 的向前快轉資料指標 &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="a3744-180">Cursor forward (Right) by &lt;n&gt;</span></span>                                                                                        |
| <span data-ttu-id="a3744-181">ESC \[ &lt; n &gt; D</span><span class="sxs-lookup"><span data-stu-id="a3744-181">ESC \[ &lt;n&gt; D</span></span>             | <span data-ttu-id="a3744-182">幼 崽</span><span class="sxs-lookup"><span data-stu-id="a3744-182">CUB</span></span>       | <span data-ttu-id="a3744-183">游標向後</span><span class="sxs-lookup"><span data-stu-id="a3744-183">Cursor Backward</span></span>                     | <span data-ttu-id="a3744-184">將游標向左 (左) &lt; n&gt;</span><span class="sxs-lookup"><span data-stu-id="a3744-184">Cursor backward (Left) by &lt;n&gt;</span></span>                                                                                        |
| <span data-ttu-id="a3744-185">ESC \[ &lt; n &gt; E</span><span class="sxs-lookup"><span data-stu-id="a3744-185">ESC \[ &lt;n&gt; E</span></span>             | <span data-ttu-id="a3744-186">CNL</span><span class="sxs-lookup"><span data-stu-id="a3744-186">CNL</span></span>       | <span data-ttu-id="a3744-187">游標下一行</span><span class="sxs-lookup"><span data-stu-id="a3744-187">Cursor Next Line</span></span>                    | <span data-ttu-id="a3744-188">資料指標向下移 &lt; 至 &gt; 區中 n 行的開頭</span><span class="sxs-lookup"><span data-stu-id="a3744-188">Cursor down to beginning of &lt;n&gt;th line in the viewport</span></span>                                                               |
| <span data-ttu-id="a3744-189">ESC \[ &lt; n &gt; F</span><span class="sxs-lookup"><span data-stu-id="a3744-189">ESC \[ &lt;n&gt; F</span></span>             | <span data-ttu-id="a3744-190">Cpl</span><span class="sxs-lookup"><span data-stu-id="a3744-190">CPL</span></span>       | <span data-ttu-id="a3744-191">資料指標上一行</span><span class="sxs-lookup"><span data-stu-id="a3744-191">Cursor Previous Line</span></span>                | <span data-ttu-id="a3744-192">資料指標最多可 &lt; &gt; 在資料區的第 n 行開頭</span><span class="sxs-lookup"><span data-stu-id="a3744-192">Cursor up to beginning of &lt;n&gt;th line in the viewport</span></span>                                                                 |
| <span data-ttu-id="a3744-193">ESC \[ &lt; n &gt; G</span><span class="sxs-lookup"><span data-stu-id="a3744-193">ESC \[ &lt;n&gt; G</span></span>             | <span data-ttu-id="a3744-194">CHA</span><span class="sxs-lookup"><span data-stu-id="a3744-194">CHA</span></span>       | <span data-ttu-id="a3744-195">資料指標水準絕對</span><span class="sxs-lookup"><span data-stu-id="a3744-195">Cursor Horizontal Absolute</span></span>          | <span data-ttu-id="a3744-196">資料指標會 &lt; &gt; 在目前的行中水準移至 n 個位置</span><span class="sxs-lookup"><span data-stu-id="a3744-196">Cursor moves to &lt;n&gt;th position horizontally in the current line</span></span>                                                      |
| <span data-ttu-id="a3744-197">ESC \[ &lt; n &gt; d</span><span class="sxs-lookup"><span data-stu-id="a3744-197">ESC \[ &lt;n&gt; d</span></span>             | <span data-ttu-id="a3744-198">VPA</span><span class="sxs-lookup"><span data-stu-id="a3744-198">VPA</span></span>       | <span data-ttu-id="a3744-199">垂直行位置絕對</span><span class="sxs-lookup"><span data-stu-id="a3744-199">Vertical Line Position Absolute</span></span>     | <span data-ttu-id="a3744-200">游標移至 &lt; 目前資料 &gt; 行中的第 n 個位置</span><span class="sxs-lookup"><span data-stu-id="a3744-200">Cursor moves to the &lt;n&gt;th position vertically in the current column</span></span>                                                  |
| <span data-ttu-id="a3744-201">ESC \[ &lt; y &gt; ; &lt;x &gt; H</span><span class="sxs-lookup"><span data-stu-id="a3744-201">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span></span> | <span data-ttu-id="a3744-202">杯</span><span class="sxs-lookup"><span data-stu-id="a3744-202">CUP</span></span>       | <span data-ttu-id="a3744-203">游標位置</span><span class="sxs-lookup"><span data-stu-id="a3744-203">Cursor Position</span></span>                     | <span data-ttu-id="a3744-204">\*游標移至 &lt; x &gt; ; &lt;在 &gt; 視口內的 y 座標，其中 &lt; x &gt; 是 &lt; y &gt; 行的資料行</span><span class="sxs-lookup"><span data-stu-id="a3744-204">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="a3744-205">ESC \[ &lt; y &gt; ; &lt;x &gt; f</span><span class="sxs-lookup"><span data-stu-id="a3744-205">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span></span> | <span data-ttu-id="a3744-206">HVP</span><span class="sxs-lookup"><span data-stu-id="a3744-206">HVP</span></span>       | <span data-ttu-id="a3744-207">水準垂直位置</span><span class="sxs-lookup"><span data-stu-id="a3744-207">Horizontal Vertical Position</span></span>        | <span data-ttu-id="a3744-208">\*游標移至 &lt; x &gt; ; &lt;在 &gt; 視口內的 y 座標，其中 &lt; x &gt; 是 &lt; y &gt; 行的資料行</span><span class="sxs-lookup"><span data-stu-id="a3744-208">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="a3744-209">ESC \[ s</span><span class="sxs-lookup"><span data-stu-id="a3744-209">ESC \[ s</span></span>                       | <span data-ttu-id="a3744-210">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="a3744-210">ANSISYSSC</span></span> | <span data-ttu-id="a3744-211">儲存資料指標– Ansi.sys 模擬</span><span class="sxs-lookup"><span data-stu-id="a3744-211">Save Cursor – Ansi.sys emulation</span></span>    | <span data-ttu-id="a3744-212">\*\*如果沒有參數，會執行儲存資料指標作業，例如 DECSC</span><span class="sxs-lookup"><span data-stu-id="a3744-212">\*\*With no parameters, performs a save cursor operation like DECSC</span></span>                                                        |
| <span data-ttu-id="a3744-213">ESC \[ u</span><span class="sxs-lookup"><span data-stu-id="a3744-213">ESC \[ u</span></span>                       | <span data-ttu-id="a3744-214">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="a3744-214">ANSISYSSC</span></span> | <span data-ttu-id="a3744-215">還原資料指標– Ansi.sys 模擬</span><span class="sxs-lookup"><span data-stu-id="a3744-215">Restore Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="a3744-216">\*\*如果沒有參數，則會執行還原資料指標作業，例如 DECRC</span><span class="sxs-lookup"><span data-stu-id="a3744-216">\*\*With no parameters, performs a restore cursor operation like DECRC</span></span>                                                     |



<span data-ttu-id="a3744-217">**注意**</span><span class="sxs-lookup"><span data-stu-id="a3744-217">**Note**</span></span>  
<span data-ttu-id="a3744-218">\*&lt;x &gt; 和 &lt; y &gt; 參數的限制與上述的 &lt; 相同 &gt; 。</span><span class="sxs-lookup"><span data-stu-id="a3744-218">\*&lt;x&gt; and &lt;y&gt; parameters have the same limitations as &lt;n&gt; above.</span></span> <span data-ttu-id="a3744-219">如果 &lt; &gt; 省略 x 和 &lt; y，則 &gt; 會設為 1; 1。</span><span class="sxs-lookup"><span data-stu-id="a3744-219">If &lt;x&gt; and &lt;y&gt; are omitted, they will be set to 1;1.</span></span>

<span data-ttu-id="a3744-220">\*\* 您可以在中找到ANSI.sys 的歷程記錄檔 <https://msdn.microsoft.com/library/cc722862.aspx> ，並且為了方便/相容性而實行。</span><span class="sxs-lookup"><span data-stu-id="a3744-220">\*\*ANSI.sys historical documentation can be found at <https://msdn.microsoft.com/library/cc722862.aspx> and is implemented for convenience/compatibility.</span></span>



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span data-ttu-id="a3744-221"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>資料指標可見度</span><span class="sxs-lookup"><span data-stu-id="a3744-221"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursor Visibility</span></span>


<span data-ttu-id="a3744-222">下列命令控制資料指標的可見度和其閃爍狀態。</span><span class="sxs-lookup"><span data-stu-id="a3744-222">The following commands control the visibility of the cursor and its blinking state.</span></span> <span data-ttu-id="a3744-223">DECTCEM 序列通常等同于呼叫 [**SetConsoleCursorInfo**](setconsolecursorinfo.md) 主控台 API 來切換資料指標可見度。</span><span class="sxs-lookup"><span data-stu-id="a3744-223">The DECTCEM sequences are generally equivalent to calling [**SetConsoleCursorInfo**](setconsolecursorinfo.md) console API to toggle cursor visibility.</span></span>


| <span data-ttu-id="a3744-224">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-224">Sequence</span></span>      | <span data-ttu-id="a3744-225">程式碼</span><span class="sxs-lookup"><span data-stu-id="a3744-225">Code</span></span>    | <span data-ttu-id="a3744-226">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-226">Description</span></span>                  | <span data-ttu-id="a3744-227">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-227">Behavior</span></span>                  |
|---------------|---------|------------------------------|---------------------------|
| <span data-ttu-id="a3744-228">ESC \[ ？</span><span class="sxs-lookup"><span data-stu-id="a3744-228">ESC \[ ?</span></span> <span data-ttu-id="a3744-229">12小時</span><span class="sxs-lookup"><span data-stu-id="a3744-229">12 h</span></span> | <span data-ttu-id="a3744-230">ATT160</span><span class="sxs-lookup"><span data-stu-id="a3744-230">ATT160</span></span>  | <span data-ttu-id="a3744-231">文字游標啟用閃爍</span><span class="sxs-lookup"><span data-stu-id="a3744-231">Text Cursor Enable Blinking</span></span>  | <span data-ttu-id="a3744-232">開始游標閃爍</span><span class="sxs-lookup"><span data-stu-id="a3744-232">Start the cursor blinking</span></span> |
| <span data-ttu-id="a3744-233">ESC \[ ？</span><span class="sxs-lookup"><span data-stu-id="a3744-233">ESC \[ ?</span></span> <span data-ttu-id="a3744-234">12 l</span><span class="sxs-lookup"><span data-stu-id="a3744-234">12 l</span></span> | <span data-ttu-id="a3744-235">ATT160</span><span class="sxs-lookup"><span data-stu-id="a3744-235">ATT160</span></span>  | <span data-ttu-id="a3744-236">文字游標停用閃爍</span><span class="sxs-lookup"><span data-stu-id="a3744-236">Text Cursor Disable Blinking</span></span>  | <span data-ttu-id="a3744-237">停止閃爍游標</span><span class="sxs-lookup"><span data-stu-id="a3744-237">Stop blinking the cursor</span></span>  |
| <span data-ttu-id="a3744-238">ESC \[ ？</span><span class="sxs-lookup"><span data-stu-id="a3744-238">ESC \[ ?</span></span> <span data-ttu-id="a3744-239">25 h</span><span class="sxs-lookup"><span data-stu-id="a3744-239">25 h</span></span> | <span data-ttu-id="a3744-240">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="a3744-240">DECTCEM</span></span> | <span data-ttu-id="a3744-241">文字游標啟用模式顯示</span><span class="sxs-lookup"><span data-stu-id="a3744-241">Text Cursor Enable Mode Show</span></span> | <span data-ttu-id="a3744-242">顯示資料指標</span><span class="sxs-lookup"><span data-stu-id="a3744-242">Show the cursor</span></span>           |
| <span data-ttu-id="a3744-243">ESC \[ ？</span><span class="sxs-lookup"><span data-stu-id="a3744-243">ESC \[ ?</span></span> <span data-ttu-id="a3744-244">25 l</span><span class="sxs-lookup"><span data-stu-id="a3744-244">25 l</span></span> | <span data-ttu-id="a3744-245">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="a3744-245">DECTCEM</span></span> | <span data-ttu-id="a3744-246">文字游標啟用模式隱藏</span><span class="sxs-lookup"><span data-stu-id="a3744-246">Text Cursor Enable Mode Hide</span></span> | <span data-ttu-id="a3744-247">隱藏游標</span><span class="sxs-lookup"><span data-stu-id="a3744-247">Hide the cursor</span></span>           |



## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span data-ttu-id="a3744-248"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>視口定位</span><span class="sxs-lookup"><span data-stu-id="a3744-248"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Viewport Positioning</span></span>


<span data-ttu-id="a3744-249">此區段中的所有命令通常等同于呼叫 [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 主控台 API 來移動主控台緩衝區的內容。</span><span class="sxs-lookup"><span data-stu-id="a3744-249">All commands in this section are generally equivalent to calling [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console API to move the contents of the console buffer.</span></span>

<span data-ttu-id="a3744-250">**注意**  命令名稱會誤導。</span><span class="sxs-lookup"><span data-stu-id="a3744-250">**Caution**  The command names are misleading.</span></span> <span data-ttu-id="a3744-251">「滾動」指的是文字在作業期間移動的方向，而不是「表面」移動的方式。</span><span class="sxs-lookup"><span data-stu-id="a3744-251">Scroll refers to which direction the text moves during the operation, not which way the viewport would seem to move.</span></span>




| <span data-ttu-id="a3744-252">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-252">Sequence</span></span>           | <span data-ttu-id="a3744-253">程式碼</span><span class="sxs-lookup"><span data-stu-id="a3744-253">Code</span></span> | <span data-ttu-id="a3744-254">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-254">Description</span></span> | <span data-ttu-id="a3744-255">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-255">Behavior</span></span>                                                                                             |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a3744-256">ESC \[ &lt; n &gt; S</span><span class="sxs-lookup"><span data-stu-id="a3744-256">ESC \[ &lt;n&gt; S</span></span> | <span data-ttu-id="a3744-257">SU</span><span class="sxs-lookup"><span data-stu-id="a3744-257">SU</span></span>   | <span data-ttu-id="a3744-258">向上捲動</span><span class="sxs-lookup"><span data-stu-id="a3744-258">Scroll Up</span></span>   | <span data-ttu-id="a3744-259">將文字向上滾動 &lt; n &gt; 。</span><span class="sxs-lookup"><span data-stu-id="a3744-259">Scroll text up by &lt;n&gt;.</span></span> <span data-ttu-id="a3744-260">也稱為「下移線」，新行會從畫面底部填滿</span><span class="sxs-lookup"><span data-stu-id="a3744-260">Also known as pan down, new lines fill in from the bottom of the screen</span></span> |
| <span data-ttu-id="a3744-261">ESC \[ &lt; n &gt; T</span><span class="sxs-lookup"><span data-stu-id="a3744-261">ESC \[ &lt;n&gt; T</span></span> | <span data-ttu-id="a3744-262">SD</span><span class="sxs-lookup"><span data-stu-id="a3744-262">SD</span></span>   | <span data-ttu-id="a3744-263">向下捲動</span><span class="sxs-lookup"><span data-stu-id="a3744-263">Scroll Down</span></span> | <span data-ttu-id="a3744-264">向下移動 &lt; n &gt; 。</span><span class="sxs-lookup"><span data-stu-id="a3744-264">Scroll down by &lt;n&gt;.</span></span> <span data-ttu-id="a3744-265">也稱為「向上移動」，從畫面頂端填滿新行</span><span class="sxs-lookup"><span data-stu-id="a3744-265">Also known as pan up, new lines fill in from the top of the screen</span></span>         |



<span data-ttu-id="a3744-266">從游標所在的那一行開始移動文字。</span><span class="sxs-lookup"><span data-stu-id="a3744-266">The text is moved starting with the line the cursor is on.</span></span> <span data-ttu-id="a3744-267">如果游標位於資料中心的中間資料列上，則會向上移動以移動區的下半部，並在底部插入空白行。</span><span class="sxs-lookup"><span data-stu-id="a3744-267">If the cursor is on the middle row of the viewport, then scroll up would move the bottom half of the viewport, and insert blank lines at the bottom.</span></span> <span data-ttu-id="a3744-268">向下鍵會移動該資料列的上半部，並在頂端插入新行。</span><span class="sxs-lookup"><span data-stu-id="a3744-268">Scroll down would move the top half of the viewport’s rows, and insert new lines at the top.</span></span>

<span data-ttu-id="a3744-269">另外一點要注意的是，滾動邊界也會影響向上和向下。</span><span class="sxs-lookup"><span data-stu-id="a3744-269">Also important to note is scroll up and down are also affected by the scrolling margins.</span></span> <span data-ttu-id="a3744-270">向上和向下鍵不會影響滾動邊界以外的任何行。</span><span class="sxs-lookup"><span data-stu-id="a3744-270">Scroll up and down won’t affect any lines outside the scrolling margins.</span></span>

<span data-ttu-id="a3744-271">N 的預設值 &lt; &gt; 為1，而且可以選擇性地省略值。</span><span class="sxs-lookup"><span data-stu-id="a3744-271">The default value for &lt;n&gt; is 1, and the value can be optionally omitted.</span></span>

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span data-ttu-id="a3744-272"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>文字修改</span><span class="sxs-lookup"><span data-stu-id="a3744-272"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Text Modification</span></span>


<span data-ttu-id="a3744-273">本節中的所有命令通常等同于呼叫 [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)、 [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md)和 [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 主控台 api 來修改文字緩衝區內容。</span><span class="sxs-lookup"><span data-stu-id="a3744-273">All commands in this section are generally equivalent to calling [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md), and [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console APIs to modify the text buffer contents.</span></span>


| <span data-ttu-id="a3744-274">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-274">Sequence</span></span>           | <span data-ttu-id="a3744-275">程式碼</span><span class="sxs-lookup"><span data-stu-id="a3744-275">Code</span></span> | <span data-ttu-id="a3744-276">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-276">Description</span></span>      | <span data-ttu-id="a3744-277">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-277">Behavior</span></span>                                                                                                                                          |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a3744-278">ESC \[ &lt; n&gt; @</span><span class="sxs-lookup"><span data-stu-id="a3744-278">ESC \[ &lt;n&gt; @</span></span> | <span data-ttu-id="a3744-279">Ich</span><span class="sxs-lookup"><span data-stu-id="a3744-279">ICH</span></span>  | <span data-ttu-id="a3744-280">插入字元</span><span class="sxs-lookup"><span data-stu-id="a3744-280">Insert Character</span></span> | <span data-ttu-id="a3744-281">&lt; &gt; 在目前游標位置插入 n 個空格，並將所有現有的文字移至右邊。</span><span class="sxs-lookup"><span data-stu-id="a3744-281">Insert &lt;n&gt; spaces at the current cursor position, shifting all existing text to the right.</span></span> <span data-ttu-id="a3744-282">已移除將畫面離開右邊的文字。</span><span class="sxs-lookup"><span data-stu-id="a3744-282">Text exiting the screen to the right is removed.</span></span> |
| <span data-ttu-id="a3744-283">ESC \[ &lt; n &gt; P</span><span class="sxs-lookup"><span data-stu-id="a3744-283">ESC \[ &lt;n&gt; P</span></span> | <span data-ttu-id="a3744-284">DCH</span><span class="sxs-lookup"><span data-stu-id="a3744-284">DCH</span></span>  | <span data-ttu-id="a3744-285">刪除字元</span><span class="sxs-lookup"><span data-stu-id="a3744-285">Delete Character</span></span> | <span data-ttu-id="a3744-286">在 &lt; &gt; 目前游標位置刪除 n 個字元，從畫面的右邊緣將空白字元移位。</span><span class="sxs-lookup"><span data-stu-id="a3744-286">Delete &lt;n&gt; characters at the current cursor position, shifting in space characters from the right edge of the screen.</span></span>                       |
| <span data-ttu-id="a3744-287">ESC \[ &lt; n &gt; X</span><span class="sxs-lookup"><span data-stu-id="a3744-287">ESC \[ &lt;n&gt; X</span></span> | <span data-ttu-id="a3744-288">ECH</span><span class="sxs-lookup"><span data-stu-id="a3744-288">ECH</span></span>  | <span data-ttu-id="a3744-289">清除字元</span><span class="sxs-lookup"><span data-stu-id="a3744-289">Erase Character</span></span>  | <span data-ttu-id="a3744-290">&lt; &gt; 使用空白字元覆寫，以清除目前游標位置的 n 個字元。</span><span class="sxs-lookup"><span data-stu-id="a3744-290">Erase &lt;n&gt; characters from the current cursor position by overwriting them with a space character.</span></span>                                           |
| <span data-ttu-id="a3744-291">ESC \[ &lt; n &gt; L</span><span class="sxs-lookup"><span data-stu-id="a3744-291">ESC \[ &lt;n&gt; L</span></span> | <span data-ttu-id="a3744-292">IL</span><span class="sxs-lookup"><span data-stu-id="a3744-292">IL</span></span>   | <span data-ttu-id="a3744-293">插入行</span><span class="sxs-lookup"><span data-stu-id="a3744-293">Insert Line</span></span>      | <span data-ttu-id="a3744-294">將 &lt; n &gt; 行插入緩衝區的游標位置。</span><span class="sxs-lookup"><span data-stu-id="a3744-294">Inserts &lt;n&gt; lines into the buffer at the cursor position.</span></span> <span data-ttu-id="a3744-295">游標所在的線條和其下的行，將會向下移動。</span><span class="sxs-lookup"><span data-stu-id="a3744-295">The line the cursor is on, and lines below it, will be shifted downwards.</span></span>         |
| <span data-ttu-id="a3744-296">ESC \[ &lt; n &gt; M</span><span class="sxs-lookup"><span data-stu-id="a3744-296">ESC \[ &lt;n&gt; M</span></span> | <span data-ttu-id="a3744-297">DL</span><span class="sxs-lookup"><span data-stu-id="a3744-297">DL</span></span>   | <span data-ttu-id="a3744-298">刪除行</span><span class="sxs-lookup"><span data-stu-id="a3744-298">Delete Line</span></span>      | <span data-ttu-id="a3744-299">&lt; &gt; 從緩衝區刪除 n 行，從資料指標所在的資料列開始。</span><span class="sxs-lookup"><span data-stu-id="a3744-299">Deletes &lt;n&gt; lines from the buffer, starting with the row the cursor is on.</span></span>                                                                  |



<span data-ttu-id="a3744-300">**注意**</span><span class="sxs-lookup"><span data-stu-id="a3744-300">**Note**</span></span>  
<span data-ttu-id="a3744-301">針對 IL 和 DL，只有滾動邊界中的線條 (看到滾動邊界) 會受到影響。</span><span class="sxs-lookup"><span data-stu-id="a3744-301">For IL and DL, only the lines in the scrolling margins (see Scrolling Margins) are affected.</span></span> <span data-ttu-id="a3744-302">如果未設定邊界，則預設邊界框線為目前的區。</span><span class="sxs-lookup"><span data-stu-id="a3744-302">If no margins are set, the default margin borders are the current viewport.</span></span> <span data-ttu-id="a3744-303">如果線條會在邊界下方移位，則會捨棄它們。</span><span class="sxs-lookup"><span data-stu-id="a3744-303">If lines would be shifted below the margins, they are discarded.</span></span> <span data-ttu-id="a3744-304">當刪除線條時，會在邊界底部插入空白行，而不會影響來自區外的行。</span><span class="sxs-lookup"><span data-stu-id="a3744-304">When lines are deleted, blank lines are inserted at the bottom of the margins, lines from outside the viewport are never affected.</span></span>

<span data-ttu-id="a3744-305">針對每個序列，如果省略，則預設值為 n，預設值為 &lt; &gt; 0。</span><span class="sxs-lookup"><span data-stu-id="a3744-305">For each of the sequences, the default value for &lt;n&gt; if it is omitted is 0.</span></span>



<span data-ttu-id="a3744-306">針對下列命令，參數 &lt; n &gt; 有3個有效值：</span><span class="sxs-lookup"><span data-stu-id="a3744-306">For the following commands, the parameter &lt;n&gt; has 3 valid values:</span></span>

- <span data-ttu-id="a3744-307">0會從目前的游標位置清除 (內含) 至行/顯示器的結尾</span><span class="sxs-lookup"><span data-stu-id="a3744-307">0 erases from the current cursor position (inclusive) to the end of the line/display</span></span>
- <span data-ttu-id="a3744-308">1從行/上顯示的開頭清除，直到和包含目前的游標位置</span><span class="sxs-lookup"><span data-stu-id="a3744-308">1 erases from the beginning of the line/display up to and including the current cursor position</span></span>
- <span data-ttu-id="a3744-309">2清除整行/顯示</span><span class="sxs-lookup"><span data-stu-id="a3744-309">2 erases the entire line/display</span></span>


| <span data-ttu-id="a3744-310">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-310">Sequence</span></span>           | <span data-ttu-id="a3744-311">程式碼</span><span class="sxs-lookup"><span data-stu-id="a3744-311">Code</span></span> | <span data-ttu-id="a3744-312">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-312">Description</span></span>      | <span data-ttu-id="a3744-313">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-313">Behavior</span></span>                                                                                     |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="a3744-314">ESC \[ &lt; n &gt; J</span><span class="sxs-lookup"><span data-stu-id="a3744-314">ESC \[ &lt;n&gt; J</span></span> | <span data-ttu-id="a3744-315">ED</span><span class="sxs-lookup"><span data-stu-id="a3744-315">ED</span></span>   | <span data-ttu-id="a3744-316">顯示中的清除</span><span class="sxs-lookup"><span data-stu-id="a3744-316">Erase in Display</span></span> | <span data-ttu-id="a3744-317">&lt;以空白字元取代由 n 指定的目前視口/screen 中的所有文字 &gt;</span><span class="sxs-lookup"><span data-stu-id="a3744-317">Replace all text in the current viewport/screen specified by &lt;n&gt; with space characters</span></span> |
| <span data-ttu-id="a3744-318">ESC \[ &lt; n &gt; K</span><span class="sxs-lookup"><span data-stu-id="a3744-318">ESC \[ &lt;n&gt; K</span></span> | <span data-ttu-id="a3744-319">音</span><span class="sxs-lookup"><span data-stu-id="a3744-319">EL</span></span>   | <span data-ttu-id="a3744-320">行清除</span><span class="sxs-lookup"><span data-stu-id="a3744-320">Erase in Line</span></span>    | <span data-ttu-id="a3744-321">將行上的所有文字取代為 &lt; n &gt; 以空白字元指定的游標</span><span class="sxs-lookup"><span data-stu-id="a3744-321">Replace all text on the line with the cursor specified by &lt;n&gt; with space characters</span></span>    |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span data-ttu-id="a3744-322"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>文字格式設定</span><span class="sxs-lookup"><span data-stu-id="a3744-322"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Text Formatting</span></span>


<span data-ttu-id="a3744-323">本節中的所有命令通常等同于呼叫 [**SetConsoleTextAttribute**](setconsoletextattribute.md) 主控台 api，以調整所有未來寫入至主控台輸出文字緩衝區的格式。</span><span class="sxs-lookup"><span data-stu-id="a3744-323">All commands in this section are generally equivalent to calling [**SetConsoleTextAttribute**](setconsoletextattribute.md) console APIs to adjust the formatting of all future writes to the console output text buffer.</span></span>

<span data-ttu-id="a3744-324">此命令的特殊之處是 &lt; ， &gt; 以下 n 位置可以接受0到16個參數（以分號分隔）。</span><span class="sxs-lookup"><span data-stu-id="a3744-324">This command is special in that the &lt;n&gt; position below can accept between 0 and 16 parameters separated by semicolons.</span></span>

<span data-ttu-id="a3744-325">如果未指定任何參數，則會將它視為與單一0參數相同。</span><span class="sxs-lookup"><span data-stu-id="a3744-325">When no parameters are specified, it is treated the same as a single 0 parameter.</span></span>


| <span data-ttu-id="a3744-326">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-326">Sequence</span></span>           | <span data-ttu-id="a3744-327">程式碼</span><span class="sxs-lookup"><span data-stu-id="a3744-327">Code</span></span> | <span data-ttu-id="a3744-328">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-328">Description</span></span>            | <span data-ttu-id="a3744-329">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-329">Behavior</span></span>                                                        |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| <span data-ttu-id="a3744-330">ESC \[ &lt; n &gt; m</span><span class="sxs-lookup"><span data-stu-id="a3744-330">ESC \[ &lt;n&gt; m</span></span> | <span data-ttu-id="a3744-331">SGR</span><span class="sxs-lookup"><span data-stu-id="a3744-331">SGR</span></span>  | <span data-ttu-id="a3744-332">設定圖形轉譯</span><span class="sxs-lookup"><span data-stu-id="a3744-332">Set Graphics Rendition</span></span> | <span data-ttu-id="a3744-333">設定螢幕和文字的格式，如 n 所指定 &lt;&gt;</span><span class="sxs-lookup"><span data-stu-id="a3744-333">Set the format of the screen and text as specified by &lt;n&gt;</span></span> |



<span data-ttu-id="a3744-334">下表的值可以在 n 中用 &lt; &gt; 來代表不同的格式模式。</span><span class="sxs-lookup"><span data-stu-id="a3744-334">The following table of values can be used in &lt;n&gt; to represent different formatting modes.</span></span>

<span data-ttu-id="a3744-335">格式化模式會從左至右套用。</span><span class="sxs-lookup"><span data-stu-id="a3744-335">Formatting modes are applied from left to right.</span></span> <span data-ttu-id="a3744-336">套用競爭的格式化選項會導致最適合的選項優先。</span><span class="sxs-lookup"><span data-stu-id="a3744-336">Applying competing formatting options will result in the right-most option taking precedence.</span></span>

<span data-ttu-id="a3744-337">針對指定色彩的選項，將會使用可使用 [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API 修改的主控台色彩表中定義的色彩。</span><span class="sxs-lookup"><span data-stu-id="a3744-337">For options that specify colors, the colors will be used as defined in the console color table which can be modified using the [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API.</span></span> <span data-ttu-id="a3744-338">如果資料表已修改為讓資料表中的「藍色」位置顯示 RGB 的紅色陰影，則 **前景藍色** 的所有呼叫都會顯示紅色色彩，直到另有變更為止。</span><span class="sxs-lookup"><span data-stu-id="a3744-338">If the table is modified to make the “blue” position in the table display an RGB shade of red, then all calls to **Foreground Blue** will display that red color until otherwise changed.</span></span>


| <span data-ttu-id="a3744-339">值</span><span class="sxs-lookup"><span data-stu-id="a3744-339">Value</span></span> | <span data-ttu-id="a3744-340">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-340">Description</span></span>               | <span data-ttu-id="a3744-341">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-341">Behavior</span></span>                                                           |
|-------|---------------------------|--------------------------------------------------------------------|
| <span data-ttu-id="a3744-342">0</span><span class="sxs-lookup"><span data-stu-id="a3744-342">0</span></span>     | <span data-ttu-id="a3744-343">預設</span><span class="sxs-lookup"><span data-stu-id="a3744-343">Default</span></span>                   | <span data-ttu-id="a3744-344">在修改之前，將所有屬性都傳回預設狀態</span><span class="sxs-lookup"><span data-stu-id="a3744-344">Returns all attributes to the default state prior to modification</span></span>  |
| <span data-ttu-id="a3744-345">1</span><span class="sxs-lookup"><span data-stu-id="a3744-345">1</span></span>     | <span data-ttu-id="a3744-346">粗體/亮色</span><span class="sxs-lookup"><span data-stu-id="a3744-346">Bold/Bright</span></span>               | <span data-ttu-id="a3744-347">將亮度/濃度旗標套用至前景色彩</span><span class="sxs-lookup"><span data-stu-id="a3744-347">Applies brightness/intensity flag to foreground color</span></span>              |
| <span data-ttu-id="a3744-348">4</span><span class="sxs-lookup"><span data-stu-id="a3744-348">4</span></span>     | <span data-ttu-id="a3744-349">Underline</span><span class="sxs-lookup"><span data-stu-id="a3744-349">Underline</span></span>                 | <span data-ttu-id="a3744-350">加底線</span><span class="sxs-lookup"><span data-stu-id="a3744-350">Adds underline</span></span>                                                     |
| <span data-ttu-id="a3744-351">24</span><span class="sxs-lookup"><span data-stu-id="a3744-351">24</span></span>    | <span data-ttu-id="a3744-352">無底線</span><span class="sxs-lookup"><span data-stu-id="a3744-352">No underline</span></span>              | <span data-ttu-id="a3744-353">移除底線</span><span class="sxs-lookup"><span data-stu-id="a3744-353">Removes underline</span></span>                                                  |
| <span data-ttu-id="a3744-354">7</span><span class="sxs-lookup"><span data-stu-id="a3744-354">7</span></span>     | <span data-ttu-id="a3744-355">負</span><span class="sxs-lookup"><span data-stu-id="a3744-355">Negative</span></span>                  | <span data-ttu-id="a3744-356">交換前景和背景色彩</span><span class="sxs-lookup"><span data-stu-id="a3744-356">Swaps foreground and background colors</span></span>                             |
| <span data-ttu-id="a3744-357">27</span><span class="sxs-lookup"><span data-stu-id="a3744-357">27</span></span>    | <span data-ttu-id="a3744-358">正面 (沒有負) </span><span class="sxs-lookup"><span data-stu-id="a3744-358">Positive (No negative)</span></span>    | <span data-ttu-id="a3744-359">傳回法線的前景/背景</span><span class="sxs-lookup"><span data-stu-id="a3744-359">Returns foreground/background to normal</span></span>                            |
| <span data-ttu-id="a3744-360">30</span><span class="sxs-lookup"><span data-stu-id="a3744-360">30</span></span>    | <span data-ttu-id="a3744-361">前景黑色</span><span class="sxs-lookup"><span data-stu-id="a3744-361">Foreground Black</span></span>          | <span data-ttu-id="a3744-362">將非粗體/亮黑色套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-362">Applies non-bold/bright black to foreground</span></span>                        |
| <span data-ttu-id="a3744-363">31</span><span class="sxs-lookup"><span data-stu-id="a3744-363">31</span></span>    | <span data-ttu-id="a3744-364">前景紅色</span><span class="sxs-lookup"><span data-stu-id="a3744-364">Foreground Red</span></span>            | <span data-ttu-id="a3744-365">將非粗體/亮紅色套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-365">Applies non-bold/bright red to foreground</span></span>                          |
| <span data-ttu-id="a3744-366">32</span><span class="sxs-lookup"><span data-stu-id="a3744-366">32</span></span>    | <span data-ttu-id="a3744-367">前景綠色</span><span class="sxs-lookup"><span data-stu-id="a3744-367">Foreground Green</span></span>          | <span data-ttu-id="a3744-368">將非粗體/亮綠套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-368">Applies non-bold/bright green to foreground</span></span>                        |
| <span data-ttu-id="a3744-369">33</span><span class="sxs-lookup"><span data-stu-id="a3744-369">33</span></span>    | <span data-ttu-id="a3744-370">前景黃色</span><span class="sxs-lookup"><span data-stu-id="a3744-370">Foreground Yellow</span></span>         | <span data-ttu-id="a3744-371">將非粗體/亮黃色套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-371">Applies non-bold/bright yellow to foreground</span></span>                       |
| <span data-ttu-id="a3744-372">34</span><span class="sxs-lookup"><span data-stu-id="a3744-372">34</span></span>    | <span data-ttu-id="a3744-373">前景藍色</span><span class="sxs-lookup"><span data-stu-id="a3744-373">Foreground Blue</span></span>           | <span data-ttu-id="a3744-374">將非粗體/亮藍套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-374">Applies non-bold/bright blue to foreground</span></span>                         |
| <span data-ttu-id="a3744-375">35</span><span class="sxs-lookup"><span data-stu-id="a3744-375">35</span></span>    | <span data-ttu-id="a3744-376">前景洋紅</span><span class="sxs-lookup"><span data-stu-id="a3744-376">Foreground Magenta</span></span>        | <span data-ttu-id="a3744-377">將非粗體/亮洋紅色套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-377">Applies non-bold/bright magenta to foreground</span></span>                      |
| <span data-ttu-id="a3744-378">36</span><span class="sxs-lookup"><span data-stu-id="a3744-378">36</span></span>    | <span data-ttu-id="a3744-379">前景青色</span><span class="sxs-lookup"><span data-stu-id="a3744-379">Foreground Cyan</span></span>           | <span data-ttu-id="a3744-380">將非粗體/亮青套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-380">Applies non-bold/bright cyan to foreground</span></span>                         |
| <span data-ttu-id="a3744-381">37</span><span class="sxs-lookup"><span data-stu-id="a3744-381">37</span></span>    | <span data-ttu-id="a3744-382">前景白色</span><span class="sxs-lookup"><span data-stu-id="a3744-382">Foreground White</span></span>          | <span data-ttu-id="a3744-383">將非粗體/亮色套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-383">Applies non-bold/bright white to foreground</span></span>                        |
| <span data-ttu-id="a3744-384">38</span><span class="sxs-lookup"><span data-stu-id="a3744-384">38</span></span>    | <span data-ttu-id="a3744-385">延伸前景</span><span class="sxs-lookup"><span data-stu-id="a3744-385">Foreground Extended</span></span>       | <span data-ttu-id="a3744-386">將擴充的色彩值套用到前景 (請參閱以下詳細資料) </span><span class="sxs-lookup"><span data-stu-id="a3744-386">Applies extended color value to the foreground (see details below)</span></span> |
| <span data-ttu-id="a3744-387">39</span><span class="sxs-lookup"><span data-stu-id="a3744-387">39</span></span>    | <span data-ttu-id="a3744-388">前景預設值</span><span class="sxs-lookup"><span data-stu-id="a3744-388">Foreground Default</span></span>        | <span data-ttu-id="a3744-389">只套用預設值的前景部分 (請參閱 0) </span><span class="sxs-lookup"><span data-stu-id="a3744-389">Applies only the foreground portion of the defaults (see 0)</span></span>        |
| <span data-ttu-id="a3744-390">40</span><span class="sxs-lookup"><span data-stu-id="a3744-390">40</span></span>    | <span data-ttu-id="a3744-391">黑色背景</span><span class="sxs-lookup"><span data-stu-id="a3744-391">Background Black</span></span>          | <span data-ttu-id="a3744-392">將非粗體/亮黑色套用至背景</span><span class="sxs-lookup"><span data-stu-id="a3744-392">Applies non-bold/bright black to background</span></span>                        |
| <span data-ttu-id="a3744-393">41</span><span class="sxs-lookup"><span data-stu-id="a3744-393">41</span></span>    | <span data-ttu-id="a3744-394">背景紅色</span><span class="sxs-lookup"><span data-stu-id="a3744-394">Background Red</span></span>            | <span data-ttu-id="a3744-395">將非粗體/亮紅色套用至背景</span><span class="sxs-lookup"><span data-stu-id="a3744-395">Applies non-bold/bright red to background</span></span>                          |
| <span data-ttu-id="a3744-396">42</span><span class="sxs-lookup"><span data-stu-id="a3744-396">42</span></span>    | <span data-ttu-id="a3744-397">背景綠色</span><span class="sxs-lookup"><span data-stu-id="a3744-397">Background Green</span></span>          | <span data-ttu-id="a3744-398">在背景中套用非粗體/亮綠</span><span class="sxs-lookup"><span data-stu-id="a3744-398">Applies non-bold/bright green to background</span></span>                        |
| <span data-ttu-id="a3744-399">43</span><span class="sxs-lookup"><span data-stu-id="a3744-399">43</span></span>    | <span data-ttu-id="a3744-400">背景黃色</span><span class="sxs-lookup"><span data-stu-id="a3744-400">Background Yellow</span></span>         | <span data-ttu-id="a3744-401">將非粗體/亮黃色套用至背景</span><span class="sxs-lookup"><span data-stu-id="a3744-401">Applies non-bold/bright yellow to background</span></span>                       |
| <span data-ttu-id="a3744-402">44</span><span class="sxs-lookup"><span data-stu-id="a3744-402">44</span></span>    | <span data-ttu-id="a3744-403">背景藍色</span><span class="sxs-lookup"><span data-stu-id="a3744-403">Background Blue</span></span>           | <span data-ttu-id="a3744-404">將非粗體/亮藍套用至背景</span><span class="sxs-lookup"><span data-stu-id="a3744-404">Applies non-bold/bright blue to background</span></span>                         |
| <span data-ttu-id="a3744-405">45</span><span class="sxs-lookup"><span data-stu-id="a3744-405">45</span></span>    | <span data-ttu-id="a3744-406">背景洋紅</span><span class="sxs-lookup"><span data-stu-id="a3744-406">Background Magenta</span></span>        | <span data-ttu-id="a3744-407">將非粗體/明亮的洋紅色套用至背景</span><span class="sxs-lookup"><span data-stu-id="a3744-407">Applies non-bold/bright magenta to background</span></span>                      |
| <span data-ttu-id="a3744-408">46</span><span class="sxs-lookup"><span data-stu-id="a3744-408">46</span></span>    | <span data-ttu-id="a3744-409">背景青色</span><span class="sxs-lookup"><span data-stu-id="a3744-409">Background Cyan</span></span>           | <span data-ttu-id="a3744-410">將非粗體/亮青套用至背景</span><span class="sxs-lookup"><span data-stu-id="a3744-410">Applies non-bold/bright cyan to background</span></span>                         |
| <span data-ttu-id="a3744-411">47</span><span class="sxs-lookup"><span data-stu-id="a3744-411">47</span></span>    | <span data-ttu-id="a3744-412">背景白色</span><span class="sxs-lookup"><span data-stu-id="a3744-412">Background White</span></span>          | <span data-ttu-id="a3744-413">將非粗體/亮色套用至背景</span><span class="sxs-lookup"><span data-stu-id="a3744-413">Applies non-bold/bright white to background</span></span>                        |
| <span data-ttu-id="a3744-414">48</span><span class="sxs-lookup"><span data-stu-id="a3744-414">48</span></span>    | <span data-ttu-id="a3744-415">背景擴充</span><span class="sxs-lookup"><span data-stu-id="a3744-415">Background Extended</span></span>       | <span data-ttu-id="a3744-416">將擴充的色彩值套用至背景 (請參閱以下詳細資料) </span><span class="sxs-lookup"><span data-stu-id="a3744-416">Applies extended color value to the background (see details below)</span></span> |
| <span data-ttu-id="a3744-417">49</span><span class="sxs-lookup"><span data-stu-id="a3744-417">49</span></span>    | <span data-ttu-id="a3744-418">背景預設值</span><span class="sxs-lookup"><span data-stu-id="a3744-418">Background Default</span></span>        | <span data-ttu-id="a3744-419">只套用預設值的背景部分 (請參閱 0) </span><span class="sxs-lookup"><span data-stu-id="a3744-419">Applies only the background portion of the defaults (see 0)</span></span>        |
| <span data-ttu-id="a3744-420">90</span><span class="sxs-lookup"><span data-stu-id="a3744-420">90</span></span>    | <span data-ttu-id="a3744-421">亮黑色前景黑色</span><span class="sxs-lookup"><span data-stu-id="a3744-421">Bright Foreground Black</span></span>   | <span data-ttu-id="a3744-422">將粗體字/亮黑色套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-422">Applies bold/bright black to foreground</span></span>                            |
| <span data-ttu-id="a3744-423">91</span><span class="sxs-lookup"><span data-stu-id="a3744-423">91</span></span>    | <span data-ttu-id="a3744-424">亮紅色前景紅色</span><span class="sxs-lookup"><span data-stu-id="a3744-424">Bright Foreground Red</span></span>     | <span data-ttu-id="a3744-425">將粗體/亮紅色套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-425">Applies bold/bright red to foreground</span></span>                              |
| <span data-ttu-id="a3744-426">92</span><span class="sxs-lookup"><span data-stu-id="a3744-426">92</span></span>    | <span data-ttu-id="a3744-427">亮綠前景綠色</span><span class="sxs-lookup"><span data-stu-id="a3744-427">Bright Foreground Green</span></span>   | <span data-ttu-id="a3744-428">將粗體/亮綠套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-428">Applies bold/bright green to foreground</span></span>                            |
| <span data-ttu-id="a3744-429">93</span><span class="sxs-lookup"><span data-stu-id="a3744-429">93</span></span>    | <span data-ttu-id="a3744-430">亮黃色前景</span><span class="sxs-lookup"><span data-stu-id="a3744-430">Bright Foreground Yellow</span></span>  | <span data-ttu-id="a3744-431">將粗體/亮黃色套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-431">Applies bold/bright yellow to foreground</span></span>                           |
| <span data-ttu-id="a3744-432">94</span><span class="sxs-lookup"><span data-stu-id="a3744-432">94</span></span>    | <span data-ttu-id="a3744-433">亮藍色前景</span><span class="sxs-lookup"><span data-stu-id="a3744-433">Bright Foreground Blue</span></span>    | <span data-ttu-id="a3744-434">將粗體/亮藍色套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-434">Applies bold/bright blue to foreground</span></span>                             |
| <span data-ttu-id="a3744-435">95</span><span class="sxs-lookup"><span data-stu-id="a3744-435">95</span></span>    | <span data-ttu-id="a3744-436">亮鮮前景洋紅</span><span class="sxs-lookup"><span data-stu-id="a3744-436">Bright Foreground Magenta</span></span> | <span data-ttu-id="a3744-437">將粗體/亮洋紅色套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-437">Applies bold/bright magenta to foreground</span></span>                          |
| <span data-ttu-id="a3744-438">96</span><span class="sxs-lookup"><span data-stu-id="a3744-438">96</span></span>    | <span data-ttu-id="a3744-439">明亮的前景青色</span><span class="sxs-lookup"><span data-stu-id="a3744-439">Bright Foreground Cyan</span></span>    | <span data-ttu-id="a3744-440">將粗體/亮青套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-440">Applies bold/bright cyan to foreground</span></span>                             |
| <span data-ttu-id="a3744-441">97</span><span class="sxs-lookup"><span data-stu-id="a3744-441">97</span></span>    | <span data-ttu-id="a3744-442">亮亮前景白色</span><span class="sxs-lookup"><span data-stu-id="a3744-442">Bright Foreground White</span></span>   | <span data-ttu-id="a3744-443">將粗體字/亮色套用至前景</span><span class="sxs-lookup"><span data-stu-id="a3744-443">Applies bold/bright white to foreground</span></span>                            |
| <span data-ttu-id="a3744-444">100</span><span class="sxs-lookup"><span data-stu-id="a3744-444">100</span></span>   | <span data-ttu-id="a3744-445">亮黑色背景</span><span class="sxs-lookup"><span data-stu-id="a3744-445">Bright Background Black</span></span>   | <span data-ttu-id="a3744-446">將粗體字/亮黑色套用至背景</span><span class="sxs-lookup"><span data-stu-id="a3744-446">Applies bold/bright black to background</span></span>                            |
| <span data-ttu-id="a3744-447">101</span><span class="sxs-lookup"><span data-stu-id="a3744-447">101</span></span>   | <span data-ttu-id="a3744-448">亮紅色背景紅色</span><span class="sxs-lookup"><span data-stu-id="a3744-448">Bright Background Red</span></span>     | <span data-ttu-id="a3744-449">將粗體/亮紅色套用至背景</span><span class="sxs-lookup"><span data-stu-id="a3744-449">Applies bold/bright red to background</span></span>                              |
| <span data-ttu-id="a3744-450">102</span><span class="sxs-lookup"><span data-stu-id="a3744-450">102</span></span>   | <span data-ttu-id="a3744-451">亮綠背景綠色</span><span class="sxs-lookup"><span data-stu-id="a3744-451">Bright Background Green</span></span>   | <span data-ttu-id="a3744-452">將粗體/亮綠套用至背景</span><span class="sxs-lookup"><span data-stu-id="a3744-452">Applies bold/bright green to background</span></span>                            |
| <span data-ttu-id="a3744-453">103</span><span class="sxs-lookup"><span data-stu-id="a3744-453">103</span></span>   | <span data-ttu-id="a3744-454">亮黃背景黃色</span><span class="sxs-lookup"><span data-stu-id="a3744-454">Bright Background Yellow</span></span>  | <span data-ttu-id="a3744-455">將粗體/亮黃色套用至背景</span><span class="sxs-lookup"><span data-stu-id="a3744-455">Applies bold/bright yellow to background</span></span>                           |
| <span data-ttu-id="a3744-456">104</span><span class="sxs-lookup"><span data-stu-id="a3744-456">104</span></span>   | <span data-ttu-id="a3744-457">明亮的背景藍色</span><span class="sxs-lookup"><span data-stu-id="a3744-457">Bright Background Blue</span></span>    | <span data-ttu-id="a3744-458">將粗體/亮藍色套用至背景</span><span class="sxs-lookup"><span data-stu-id="a3744-458">Applies bold/bright blue to background</span></span>                             |
| <span data-ttu-id="a3744-459">105</span><span class="sxs-lookup"><span data-stu-id="a3744-459">105</span></span>   | <span data-ttu-id="a3744-460">鮮鮮深的洋紅</span><span class="sxs-lookup"><span data-stu-id="a3744-460">Bright Background Magenta</span></span> | <span data-ttu-id="a3744-461">將粗體字/亮紅色套用至背景</span><span class="sxs-lookup"><span data-stu-id="a3744-461">Applies bold/bright magenta to background</span></span>                          |
| <span data-ttu-id="a3744-462">106</span><span class="sxs-lookup"><span data-stu-id="a3744-462">106</span></span>   | <span data-ttu-id="a3744-463">鮮鮮色青色</span><span class="sxs-lookup"><span data-stu-id="a3744-463">Bright Background Cyan</span></span>    | <span data-ttu-id="a3744-464">將粗體/亮青套用至背景</span><span class="sxs-lookup"><span data-stu-id="a3744-464">Applies bold/bright cyan to background</span></span>                             |
| <span data-ttu-id="a3744-465">107</span><span class="sxs-lookup"><span data-stu-id="a3744-465">107</span></span>   | <span data-ttu-id="a3744-466">亮色背景白色</span><span class="sxs-lookup"><span data-stu-id="a3744-466">Bright Background White</span></span>   | <span data-ttu-id="a3744-467">將粗體字/亮色套用至背景</span><span class="sxs-lookup"><span data-stu-id="a3744-467">Applies bold/bright white to background</span></span>                            |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span data-ttu-id="a3744-468"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>擴充色彩</span><span class="sxs-lookup"><span data-stu-id="a3744-468"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Extended Colors</span></span>

<span data-ttu-id="a3744-469">某些虛擬終端模擬器支援的色彩調色板，大於 Windows 主控台所提供的16種色彩。</span><span class="sxs-lookup"><span data-stu-id="a3744-469">Some virtual terminal emulators support a palette of colors greater than the 16 colors provided by the Windows Console.</span></span> <span data-ttu-id="a3744-470">針對這些擴充的色彩，Windows 主控台將會從現有的16色資料表選擇最接近的適當色彩來顯示。</span><span class="sxs-lookup"><span data-stu-id="a3744-470">For these extended colors, the Windows Console will choose the nearest appropriate color from the existing 16 color table for display.</span></span> <span data-ttu-id="a3744-471">不同于上述的一般 SGR 值，擴充值會根據下表，在初始指標之後取用額外的參數。</span><span class="sxs-lookup"><span data-stu-id="a3744-471">Unlike typical SGR values above, the extended values will consume additional parameters after the initial indicator according to the table below.</span></span>


| <span data-ttu-id="a3744-472">SGR 子序列</span><span class="sxs-lookup"><span data-stu-id="a3744-472">SGR Subsequence</span></span>                            | <span data-ttu-id="a3744-473">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-473">Description</span></span>                                                                                 |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="a3744-474">38;二級 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="a3744-474">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="a3744-475">將前景色彩設定為 &lt; r &gt; 、 &lt; g &gt; 、 &lt; b &gt; 參數中指定的 RGB 值\*</span><span class="sxs-lookup"><span data-stu-id="a3744-475">Set foreground color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="a3744-476">48;二級 &lt;r &gt; ; &lt;g &gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="a3744-476">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="a3744-477">將背景色彩設定為 &lt; r &gt; 、 &lt; g &gt; 、 &lt; b &gt; 參數中指定的 RGB 值\*</span><span class="sxs-lookup"><span data-stu-id="a3744-477">Set background color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="a3744-478">38;.5 &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="a3744-478">38 ; 5 ; &lt;s&gt;</span></span>                         | <span data-ttu-id="a3744-479">&lt; &gt; 在88或256色彩表中將前景色彩設定為 s 索引\*</span><span class="sxs-lookup"><span data-stu-id="a3744-479">Set foreground color to &lt;s&gt; index in 88 or 256 color table\*</span></span>                          |
| <span data-ttu-id="a3744-480">48;.5 &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="a3744-480">48 ; 5 ; &lt;s&gt;</span></span>                         | <span data-ttu-id="a3744-481">將背景色彩設定 &lt; 為 &gt; 88 或256色彩表中的 s 索引\*</span><span class="sxs-lookup"><span data-stu-id="a3744-481">Set background color to &lt;s&gt; index in 88 or 256 color table\*</span></span>                          |



<span data-ttu-id="a3744-482">\*為了進行比較，內部維護的88和256色調色板是以 xterm 終端機模擬器為基礎。</span><span class="sxs-lookup"><span data-stu-id="a3744-482">\*The 88 and 256 color palettes maintained internally for comparison are based from the xterm terminal emulator.</span></span> <span data-ttu-id="a3744-483">目前無法修改比較/四捨五入資料表。</span><span class="sxs-lookup"><span data-stu-id="a3744-483">The comparison/rounding tables cannot be modified at this time.</span></span>


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span data-ttu-id="a3744-484"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>螢幕色彩</span><span class="sxs-lookup"><span data-stu-id="a3744-484"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Screen Colors</span></span>


<span data-ttu-id="a3744-485">下列命令可讓應用程式將螢幕顏色選擇區值設定為任何 RGB 值。</span><span class="sxs-lookup"><span data-stu-id="a3744-485">The following command allows the application to set the screen colors palette values to any RGB value.</span></span>

<span data-ttu-id="a3744-486">RGB 值應該是和之間的十六進位 `0` 值 `ff` ，並以正斜線字元分隔 (例如 `rgb:1/24/86`) 。</span><span class="sxs-lookup"><span data-stu-id="a3744-486">The RGB values should be hexadecimal values between `0` and `ff`, and separated by the forward-slash character (e.g. `rgb:1/24/86`).</span></span>

<span data-ttu-id="a3744-487">請注意，此順序是一種 .OSC 「作業系統命令」順序，而不是類似許多其他序列的 CSI，因此以 "x1b" 為開頭 \\ \] ，而不是 " \\ x1b \[ "。</span><span class="sxs-lookup"><span data-stu-id="a3744-487">Note that this sequence is an OSC “Operating system command” sequence, and not a CSI like many of the other sequences listed, and as such start with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="a3744-488">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-488">Sequence</span></span>                                                           | <span data-ttu-id="a3744-489">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-489">Description</span></span>          | <span data-ttu-id="a3744-490">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-490">Behavior</span></span>                                                                                                     |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a3744-491">ESC \] 4; &lt;i &gt; ; rgb： &lt; r &gt;  /  &lt; g &gt;  /  &lt; b &gt; ESC</span><span class="sxs-lookup"><span data-stu-id="a3744-491">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span></span> | <span data-ttu-id="a3744-492">修改螢幕色彩</span><span class="sxs-lookup"><span data-stu-id="a3744-492">Modify Screen Colors</span></span> | <span data-ttu-id="a3744-493">將螢幕色彩調色板索引 &lt; i 設定 &gt; 為 &lt; r &gt; 、 &lt; g &gt; 、 &lt; b 中指定的 RGB 值&gt;</span><span class="sxs-lookup"><span data-stu-id="a3744-493">Sets the screen color palette index &lt;i&gt; to the RGB values specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt;</span></span> |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span data-ttu-id="a3744-494"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>模式變更</span><span class="sxs-lookup"><span data-stu-id="a3744-494"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Mode Changes</span></span>


<span data-ttu-id="a3744-495">這些是控制輸入模式的序列。</span><span class="sxs-lookup"><span data-stu-id="a3744-495">These are sequences that control the input modes.</span></span> <span data-ttu-id="a3744-496">有兩組不同的輸入模式，也就是資料指標索引鍵模式和鍵盤按鍵模式。</span><span class="sxs-lookup"><span data-stu-id="a3744-496">There are two different sets of input modes, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="a3744-497">資料指標索引鍵模式控制方向鍵以及 Home 和 End 所發出的序列，而鍵盤按鍵模式則是控制 numpad 上的索引鍵所發出的序列，以及函式金鑰。</span><span class="sxs-lookup"><span data-stu-id="a3744-497">The Cursor Keys Mode controls the sequences that are emitted by the arrow keys as well as Home and End, while the Keypad Keys Mode controls the sequences emitted by the keys on the numpad primarily, as well as the function keys.</span></span>

<span data-ttu-id="a3744-498">這些模式中的每一個都是簡單的布林值設定，也就是資料指標索引鍵模式是標準 (預設) 或應用程式，而鍵盤按鍵模式則是數位 (預設) 或應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3744-498">Each of these modes are simple boolean settings – the Cursor Keys Mode is either Normal (default) or Application, and the Keypad Keys Mode is either Numeric (default) or Application.</span></span>

<span data-ttu-id="a3744-499">請參閱資料指標索引鍵和 Numpad & 函式金鑰區段，以瞭解這些模式發出的順序。</span><span class="sxs-lookup"><span data-stu-id="a3744-499">See the Cursor Keys and Numpad & Function Keys sections for the sequences emitted in these modes.</span></span>


| <span data-ttu-id="a3744-500">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-500">Sequence</span></span>     | <span data-ttu-id="a3744-501">程式碼</span><span class="sxs-lookup"><span data-stu-id="a3744-501">Code</span></span>    | <span data-ttu-id="a3744-502">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-502">Description</span></span>                                            | <span data-ttu-id="a3744-503">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-503">Behavior</span></span>                                                |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| <span data-ttu-id="a3744-504">ESC =</span><span class="sxs-lookup"><span data-stu-id="a3744-504">ESC =</span></span>        | <span data-ttu-id="a3744-505">DECKPAM</span><span class="sxs-lookup"><span data-stu-id="a3744-505">DECKPAM</span></span> | <span data-ttu-id="a3744-506">啟用鍵台應用程式模式</span><span class="sxs-lookup"><span data-stu-id="a3744-506">Enable Keypad Application Mode</span></span>                         | <span data-ttu-id="a3744-507">鍵盤按鍵會發出其應用程式模式序列。</span><span class="sxs-lookup"><span data-stu-id="a3744-507">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="a3744-508">Esc &gt;</span><span class="sxs-lookup"><span data-stu-id="a3744-508">ESC &gt;</span></span>     | <span data-ttu-id="a3744-509">DECKPNM</span><span class="sxs-lookup"><span data-stu-id="a3744-509">DECKPNM</span></span> | <span data-ttu-id="a3744-510">啟用數位鍵數位模式</span><span class="sxs-lookup"><span data-stu-id="a3744-510">Enable Keypad Numeric Mode</span></span>                             | <span data-ttu-id="a3744-511">鍵盤按鍵會發出其數值模式序列。</span><span class="sxs-lookup"><span data-stu-id="a3744-511">Keypad keys will emit their Numeric Mode sequences.</span></span>     |
| <span data-ttu-id="a3744-512">ESC \[ ？</span><span class="sxs-lookup"><span data-stu-id="a3744-512">ESC \[ ?</span></span> <span data-ttu-id="a3744-513">1 小時</span><span class="sxs-lookup"><span data-stu-id="a3744-513">1 h</span></span> | <span data-ttu-id="a3744-514">DECCKM</span><span class="sxs-lookup"><span data-stu-id="a3744-514">DECCKM</span></span>  | <span data-ttu-id="a3744-515">啟用資料指標索引鍵應用程式模式</span><span class="sxs-lookup"><span data-stu-id="a3744-515">Enable Cursor Keys Application Mode</span></span>                    | <span data-ttu-id="a3744-516">鍵盤按鍵會發出其應用程式模式序列。</span><span class="sxs-lookup"><span data-stu-id="a3744-516">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="a3744-517">ESC \[ ？</span><span class="sxs-lookup"><span data-stu-id="a3744-517">ESC \[ ?</span></span> <span data-ttu-id="a3744-518">1 l</span><span class="sxs-lookup"><span data-stu-id="a3744-518">1 l</span></span> | <span data-ttu-id="a3744-519">DECCKM</span><span class="sxs-lookup"><span data-stu-id="a3744-519">DECCKM</span></span>  | <span data-ttu-id="a3744-520">停用資料指標索引鍵應用程式模式 (使用正常模式) </span><span class="sxs-lookup"><span data-stu-id="a3744-520">Disable Cursor Keys Application Mode (use Normal Mode)</span></span> | <span data-ttu-id="a3744-521">鍵盤按鍵會發出其數值模式序列。</span><span class="sxs-lookup"><span data-stu-id="a3744-521">Keypad keys will emit their Numeric Mode sequences.</span></span>     |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span data-ttu-id="a3744-522"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>查詢狀態</span><span class="sxs-lookup"><span data-stu-id="a3744-522"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Query State</span></span>


<span data-ttu-id="a3744-523">此區段中的所有命令通常等同于呼叫 Get \* 主控台 api，以取得目前主控台緩衝區狀態的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="a3744-523">All commands in this section are generally equivalent to calling Get\* console APIs to retrieve status information about the current console buffer state.</span></span>

<span data-ttu-id="a3744-524">**注意**  這些查詢會在輸出資料流程上辨識時，立即將回應發出至主控台輸入資料流程，同時 \_ 設定啟用虛擬 \_ 終端 \_ 處理。</span><span class="sxs-lookup"><span data-stu-id="a3744-524">**Note**  These queries will emit their responses into the console input stream immediately after being recognized on the output stream while ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING is set.</span></span> <span data-ttu-id="a3744-525">「啟用 \_ 虛擬 \_ 終端機輸入」旗標不適 \_ 用於查詢命令，因為它會假設讓查詢的應用程式一律要接收回複。</span><span class="sxs-lookup"><span data-stu-id="a3744-525">The ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag does not apply to query commands as it is assumed that an application making the query will always want to receive the reply.</span></span>




| <span data-ttu-id="a3744-526">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-526">Sequence</span></span>   | <span data-ttu-id="a3744-527">程式碼</span><span class="sxs-lookup"><span data-stu-id="a3744-527">Code</span></span>    | <span data-ttu-id="a3744-528">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-528">Description</span></span>            | <span data-ttu-id="a3744-529">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-529">Behavior</span></span>                                                                                                               |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a3744-530">ESC \[ 6 n</span><span class="sxs-lookup"><span data-stu-id="a3744-530">ESC \[ 6 n</span></span> | <span data-ttu-id="a3744-531">DECXCPR</span><span class="sxs-lookup"><span data-stu-id="a3744-531">DECXCPR</span></span> | <span data-ttu-id="a3744-532">報表資料指標位置</span><span class="sxs-lookup"><span data-stu-id="a3744-532">Report Cursor Position</span></span> | <span data-ttu-id="a3744-533">將游標位置發出為： ESC \[ &lt; r &gt; ; &lt;&gt; &lt; r = 資料指標資料 &gt; &lt; 列和 c = 資料指標資料行 &gt; 的 c r</span><span class="sxs-lookup"><span data-stu-id="a3744-533">Emit the cursor position as: ESC \[ &lt;r&gt; ; &lt;c&gt; R Where &lt;r&gt; = cursor row and &lt;c&gt; = cursor column</span></span> |
| <span data-ttu-id="a3744-534">ESC \[ 0 c</span><span class="sxs-lookup"><span data-stu-id="a3744-534">ESC \[ 0 c</span></span> | <span data-ttu-id="a3744-535">大</span><span class="sxs-lookup"><span data-stu-id="a3744-535">DA</span></span>      | <span data-ttu-id="a3744-536">裝置屬性</span><span class="sxs-lookup"><span data-stu-id="a3744-536">Device Attributes</span></span>      | <span data-ttu-id="a3744-537">報告終端機身分識別。</span><span class="sxs-lookup"><span data-stu-id="a3744-537">Report the terminal identity.</span></span> <span data-ttu-id="a3744-538">將發出 " \\ x1b \[ ？ 1; 0c"，指出「沒有選項的 VT101」。</span><span class="sxs-lookup"><span data-stu-id="a3744-538">Will emit “\\x1b\[?1;0c”, indicating "VT101 with No Options".</span></span>                            |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span data-ttu-id="a3744-539"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>標籤</span><span class="sxs-lookup"><span data-stu-id="a3744-539"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabs</span></span>


<span data-ttu-id="a3744-540">雖然 windows 主控台傳統上的索引標籤只會有八個字元，但使用 \* 特定序列的 nix 應用程式可以操控定位點在主控台視窗內的位置，以優化應用程式的資料指標移動。</span><span class="sxs-lookup"><span data-stu-id="a3744-540">While the windows console traditionally expects tabs to be exclusively eight characters wide, \*nix applications utilizing certain sequences can manipulate where the tab stops are within the console windows to optimize cursor movement by the application.</span></span>

<span data-ttu-id="a3744-541">下列順序可讓應用程式設定主控台視窗內的索引標籤停用位置、移除它們，並在其間進行導覽。</span><span class="sxs-lookup"><span data-stu-id="a3744-541">The following sequences allow an application to set the tab stop locations within the console window, remove them, and navigate between them.</span></span>


| <span data-ttu-id="a3744-542">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-542">Sequence</span></span>           | <span data-ttu-id="a3744-543">程式碼</span><span class="sxs-lookup"><span data-stu-id="a3744-543">Code</span></span> | <span data-ttu-id="a3744-544">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-544">Description</span></span>                     | <span data-ttu-id="a3744-545">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-545">Behavior</span></span>                                                                                                                                                                                                                    |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a3744-546">ESC H</span><span class="sxs-lookup"><span data-stu-id="a3744-546">ESC H</span></span>              | <span data-ttu-id="a3744-547">高溫 超導</span><span class="sxs-lookup"><span data-stu-id="a3744-547">HTS</span></span>  | <span data-ttu-id="a3744-548">水準索引標籤集合</span><span class="sxs-lookup"><span data-stu-id="a3744-548">Horizontal Tab Set</span></span>              | <span data-ttu-id="a3744-549">在資料指標所在的目前資料行中設定制表位。</span><span class="sxs-lookup"><span data-stu-id="a3744-549">Sets a tab stop in the current column the cursor is in.</span></span>                                                                                                                                                                     |
| <span data-ttu-id="a3744-550">ESC \[ &lt; n &gt; I</span><span class="sxs-lookup"><span data-stu-id="a3744-550">ESC \[ &lt;n&gt; I</span></span> | <span data-ttu-id="a3744-551">CHT</span><span class="sxs-lookup"><span data-stu-id="a3744-551">CHT</span></span>  | <span data-ttu-id="a3744-552">資料指標水準 (向前) 索引標籤</span><span class="sxs-lookup"><span data-stu-id="a3744-552">Cursor Horizontal (Forward) Tab</span></span> | <span data-ttu-id="a3744-553">將資料指標前進到相同資料列中的下一個資料行 () ，並使用 tab 鍵停止。</span><span class="sxs-lookup"><span data-stu-id="a3744-553">Advance the cursor to the next column (in the same row) with a tab stop.</span></span> <span data-ttu-id="a3744-554">如果沒有其他索引標籤停止，請移至資料列中的最後一個資料行。</span><span class="sxs-lookup"><span data-stu-id="a3744-554">If there are no more tab stops, move to the last column in the row.</span></span> <span data-ttu-id="a3744-555">如果資料指標位於最後一個資料行中，請移至下一個資料列的第一個資料行。</span><span class="sxs-lookup"><span data-stu-id="a3744-555">If the cursor is in the last column, move to the first column of the next row.</span></span> |
| <span data-ttu-id="a3744-556">ESC \[ &lt; n &gt; Z</span><span class="sxs-lookup"><span data-stu-id="a3744-556">ESC \[ &lt;n&gt; Z</span></span> | <span data-ttu-id="a3744-557">Cbt</span><span class="sxs-lookup"><span data-stu-id="a3744-557">CBT</span></span>  | <span data-ttu-id="a3744-558">游標向後索引標籤</span><span class="sxs-lookup"><span data-stu-id="a3744-558">Cursor Backwards Tab</span></span>            | <span data-ttu-id="a3744-559">將資料指標移到相同資料列中的上一個資料行 () ，並使用 tab 鍵停止。</span><span class="sxs-lookup"><span data-stu-id="a3744-559">Move the cursor to the previous column (in the same row) with a tab stop.</span></span> <span data-ttu-id="a3744-560">如果沒有其他索引標籤停止，請將游標移至第一個資料行。</span><span class="sxs-lookup"><span data-stu-id="a3744-560">If there are no more tab stops, moves the cursor to the first column.</span></span> <span data-ttu-id="a3744-561">如果資料指標在第一個資料行中，則不會移動資料指標。</span><span class="sxs-lookup"><span data-stu-id="a3744-561">If the cursor is in the first column, doesn’t move the cursor.</span></span>              |
| <span data-ttu-id="a3744-562">ESC \[ 0 g</span><span class="sxs-lookup"><span data-stu-id="a3744-562">ESC \[ 0 g</span></span>         | <span data-ttu-id="a3744-563">Tbc</span><span class="sxs-lookup"><span data-stu-id="a3744-563">TBC</span></span>  | <span data-ttu-id="a3744-564">Tab 鍵清除 (目前的資料行) </span><span class="sxs-lookup"><span data-stu-id="a3744-564">Tab Clear (current column)</span></span>      | <span data-ttu-id="a3744-565">清除目前資料行中的定位停駐點（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="a3744-565">Clears the tab stop in the current column, if there is one.</span></span> <span data-ttu-id="a3744-566">否則不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="a3744-566">Otherwise does nothing.</span></span>                                                                                                                                         |
| <span data-ttu-id="a3744-567">ESC \[ 3 g</span><span class="sxs-lookup"><span data-stu-id="a3744-567">ESC \[ 3 g</span></span>         | <span data-ttu-id="a3744-568">Tbc</span><span class="sxs-lookup"><span data-stu-id="a3744-568">TBC</span></span>  | <span data-ttu-id="a3744-569">Tab 清除 (所有資料行) </span><span class="sxs-lookup"><span data-stu-id="a3744-569">Tab Clear (all columns)</span></span>         | <span data-ttu-id="a3744-570">清除目前設定的所有制表位。</span><span class="sxs-lookup"><span data-stu-id="a3744-570">Clears all currently set tab stops.</span></span>                                                                                                                                                                                         |



- <span data-ttu-id="a3744-571">針對 CHT 和 CBT， &lt; n &gt; 是選擇性參數， (預設值 = 1) 指出將游標朝指定的方向前進多少次。</span><span class="sxs-lookup"><span data-stu-id="a3744-571">For both CHT and CBT, &lt;n&gt; is an optional parameter that (default=1) indicating how many times to advance the cursor in the specified direction.</span></span>
- <span data-ttu-id="a3744-572">如果沒有透過 HTS 設定的定位停駐點，CHT 和 CBT 會將視窗的第一個和最後一個資料行視為唯一的兩個索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a3744-572">If there are no tab stops set via HTS, CHT and CBT will treat the first and last columns of the window as the only two tab stops.</span></span>
- <span data-ttu-id="a3744-573">使用 HTS 設定索引標籤停止也會使主控台以與 \\ CHT 相同的方式，在索引標籤 (0x09 ' t ' ) 字元的輸出上流覽至下一個定位停駐點。</span><span class="sxs-lookup"><span data-stu-id="a3744-573">Using HTS to set a tab stop will also cause the console to navigate to the next tab stop on the output of a TAB (0x09, ‘\\t’) character, in the same manner as CHT.</span></span>

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span data-ttu-id="a3744-574"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>指定字元集</span><span class="sxs-lookup"><span data-stu-id="a3744-574"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designate Character Set</span></span>


<span data-ttu-id="a3744-575">下列順序可讓程式變更現用字元集對應。</span><span class="sxs-lookup"><span data-stu-id="a3744-575">The following sequences allow a program to change the active character set mapping.</span></span> <span data-ttu-id="a3744-576">這可讓程式發出7位 ASCII 字元，但會在終端機畫面本身將它們顯示為其他圖像。</span><span class="sxs-lookup"><span data-stu-id="a3744-576">This allows a program to emit 7-bit ASCII characters, but have them displayed as other glyphs on the terminal screen itself.</span></span> <span data-ttu-id="a3744-577">目前，只有兩個支援的字元集是 ASCII (預設) 和 DEC 特殊圖形字元集。</span><span class="sxs-lookup"><span data-stu-id="a3744-577">Currently, the only two supported character sets are ASCII (default) and the DEC Special Graphics Character Set.</span></span> <span data-ttu-id="a3744-578">請參閱 <http://vt100.net/docs/vt220-rm/table2-4.html> ，以取得 DEC 特殊圖形字元集所表示的所有字元清單。</span><span class="sxs-lookup"><span data-stu-id="a3744-578">See <http://vt100.net/docs/vt220-rm/table2-4.html> for a listing of all of the characters represented by the DEC Special Graphics Character Set.</span></span>


| <span data-ttu-id="a3744-579">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-579">Sequence</span></span> | <span data-ttu-id="a3744-580">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-580">Description</span></span>                                | <span data-ttu-id="a3744-581">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-581">Behavior</span></span>                      |
|----------|--------------------------------------------|-------------------------------|
| <span data-ttu-id="a3744-582">ESC ( 0</span><span class="sxs-lookup"><span data-stu-id="a3744-582">ESC ( 0</span></span>  | <span data-ttu-id="a3744-583">指定字元集– DEC 線條繪圖</span><span class="sxs-lookup"><span data-stu-id="a3744-583">Designate Character Set – DEC Line Drawing</span></span> | <span data-ttu-id="a3744-584">啟用 DEC 折線圖繪製模式</span><span class="sxs-lookup"><span data-stu-id="a3744-584">Enables DEC Line Drawing Mode</span></span> |
| <span data-ttu-id="a3744-585">ESC ( B</span><span class="sxs-lookup"><span data-stu-id="a3744-585">ESC ( B</span></span>  | <span data-ttu-id="a3744-586">指定字元集– US ASCII</span><span class="sxs-lookup"><span data-stu-id="a3744-586">Designate Character Set – US ASCII</span></span>         | <span data-ttu-id="a3744-587">啟用 ASCII 模式 (預設值) </span><span class="sxs-lookup"><span data-stu-id="a3744-587">Enables ASCII Mode (Default)</span></span>  |



<span data-ttu-id="a3744-588">值得注意的是，DEC 線條繪圖模式用於在主控台應用程式中繪製框線。</span><span class="sxs-lookup"><span data-stu-id="a3744-588">Notably, the DEC Line Drawing mode is used for drawing borders in console applications.</span></span> <span data-ttu-id="a3744-589">下表顯示哪些 ASCII 字元對應到哪些線條繪圖字元。</span><span class="sxs-lookup"><span data-stu-id="a3744-589">The following table shows what ASCII character maps to which line drawing character.</span></span>


| <span data-ttu-id="a3744-590">Hex</span><span class="sxs-lookup"><span data-stu-id="a3744-590">Hex</span></span>  | <span data-ttu-id="a3744-591">ASCII</span><span class="sxs-lookup"><span data-stu-id="a3744-591">ASCII</span></span> | <span data-ttu-id="a3744-592">DEC 線條繪圖</span><span class="sxs-lookup"><span data-stu-id="a3744-592">DEC Line Drawing</span></span> |
|------|-------|------------------|
| <span data-ttu-id="a3744-593">0x6a</span><span class="sxs-lookup"><span data-stu-id="a3744-593">0x6a</span></span> | <span data-ttu-id="a3744-594">j</span><span class="sxs-lookup"><span data-stu-id="a3744-594">j</span></span>     | <span data-ttu-id="a3744-595">┘</span><span class="sxs-lookup"><span data-stu-id="a3744-595">┘</span></span>                |
| <span data-ttu-id="a3744-596">0x6b</span><span class="sxs-lookup"><span data-stu-id="a3744-596">0x6b</span></span> | <span data-ttu-id="a3744-597">K</span><span class="sxs-lookup"><span data-stu-id="a3744-597">k</span></span>     | <span data-ttu-id="a3744-598">┐</span><span class="sxs-lookup"><span data-stu-id="a3744-598">┐</span></span>                |
| <span data-ttu-id="a3744-599">0x6c</span><span class="sxs-lookup"><span data-stu-id="a3744-599">0x6c</span></span> | <span data-ttu-id="a3744-600">l</span><span class="sxs-lookup"><span data-stu-id="a3744-600">l</span></span>     | <span data-ttu-id="a3744-601">┌</span><span class="sxs-lookup"><span data-stu-id="a3744-601">┌</span></span>                |
| <span data-ttu-id="a3744-602">0x6d</span><span class="sxs-lookup"><span data-stu-id="a3744-602">0x6d</span></span> | <span data-ttu-id="a3744-603">m</span><span class="sxs-lookup"><span data-stu-id="a3744-603">m</span></span>     | <span data-ttu-id="a3744-604">└</span><span class="sxs-lookup"><span data-stu-id="a3744-604">└</span></span>                |
| <span data-ttu-id="a3744-605">0x6e</span><span class="sxs-lookup"><span data-stu-id="a3744-605">0x6e</span></span> | <span data-ttu-id="a3744-606">n</span><span class="sxs-lookup"><span data-stu-id="a3744-606">n</span></span>     | <span data-ttu-id="a3744-607">┼</span><span class="sxs-lookup"><span data-stu-id="a3744-607">┼</span></span>                |
| <span data-ttu-id="a3744-608">0x71</span><span class="sxs-lookup"><span data-stu-id="a3744-608">0x71</span></span> | <span data-ttu-id="a3744-609">q</span><span class="sxs-lookup"><span data-stu-id="a3744-609">q</span></span>     | <span data-ttu-id="a3744-610">─</span><span class="sxs-lookup"><span data-stu-id="a3744-610">─</span></span>                |
| <span data-ttu-id="a3744-611">0x74</span><span class="sxs-lookup"><span data-stu-id="a3744-611">0x74</span></span> | <span data-ttu-id="a3744-612">t</span><span class="sxs-lookup"><span data-stu-id="a3744-612">t</span></span>     | <span data-ttu-id="a3744-613">├</span><span class="sxs-lookup"><span data-stu-id="a3744-613">├</span></span>                |
| <span data-ttu-id="a3744-614">0x75</span><span class="sxs-lookup"><span data-stu-id="a3744-614">0x75</span></span> | <span data-ttu-id="a3744-615">u</span><span class="sxs-lookup"><span data-stu-id="a3744-615">u</span></span>     | <span data-ttu-id="a3744-616">┤</span><span class="sxs-lookup"><span data-stu-id="a3744-616">┤</span></span>                |
| <span data-ttu-id="a3744-617">0x76</span><span class="sxs-lookup"><span data-stu-id="a3744-617">0x76</span></span> | <span data-ttu-id="a3744-618">v</span><span class="sxs-lookup"><span data-stu-id="a3744-618">v</span></span>     | <span data-ttu-id="a3744-619">┴</span><span class="sxs-lookup"><span data-stu-id="a3744-619">┴</span></span>                |
| <span data-ttu-id="a3744-620">0x77</span><span class="sxs-lookup"><span data-stu-id="a3744-620">0x77</span></span> | <span data-ttu-id="a3744-621">w</span><span class="sxs-lookup"><span data-stu-id="a3744-621">w</span></span>     | <span data-ttu-id="a3744-622">┬</span><span class="sxs-lookup"><span data-stu-id="a3744-622">┬</span></span>                |
| <span data-ttu-id="a3744-623">0x78</span><span class="sxs-lookup"><span data-stu-id="a3744-623">0x78</span></span> | <span data-ttu-id="a3744-624">x</span><span class="sxs-lookup"><span data-stu-id="a3744-624">x</span></span>     | <span data-ttu-id="a3744-625">│</span><span class="sxs-lookup"><span data-stu-id="a3744-625">│</span></span>                |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span data-ttu-id="a3744-626"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>滾動邊界</span><span class="sxs-lookup"><span data-stu-id="a3744-626"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scrolling Margins</span></span>


<span data-ttu-id="a3744-627">下列順序可讓程式設定受滾動作業影響之畫面的「捲動區域」。</span><span class="sxs-lookup"><span data-stu-id="a3744-627">The following sequences allow a program to configure the “scrolling region” of the screen that is affected by scrolling operations.</span></span> <span data-ttu-id="a3744-628">這是在螢幕以其他方式（例如，在 ' \\ n ' 或 RI）上滾動時所調整的資料列子集。</span><span class="sxs-lookup"><span data-stu-id="a3744-628">This is a subset of the rows that are adjusted when the screen would otherwise scroll, for example, on a ‘\\n’ or RI.</span></span> <span data-ttu-id="a3744-629">這些邊界也會影響插入行 (IL) 和刪除行 (DL) 所修改的資料列，DL、向上快移 (SU) 並向下 SD (。</span><span class="sxs-lookup"><span data-stu-id="a3744-629">These margins also affect the rows modified by Insert Line (IL) and Delete Line (DL), Scroll Up (SU) and Scroll Down (SD).</span></span>

<span data-ttu-id="a3744-630">當填滿畫面的其餘部分，例如在應用程式底部有標題列或狀態列時，滾動邊界特別適用于螢幕的一部分，而不會滾動。</span><span class="sxs-lookup"><span data-stu-id="a3744-630">The scrolling margins can be especially useful for having a portion of the screen that doesn’t scroll when the rest of the screen is filled, such as having a title bar at the top or a status bar at the bottom of your application.</span></span>

<span data-ttu-id="a3744-631">針對 DECSTBM，有兩個選擇性參數 &lt; t &gt; 和 &lt; b &gt; ，用來指定代表捲軸區域頂端和底部行（含）的資料列。</span><span class="sxs-lookup"><span data-stu-id="a3744-631">For DECSTBM, there are two optional parameters, &lt;t&gt; and &lt;b&gt;, which are used to specify the rows that represent the top and bottom lines of the scroll region, inclusive.</span></span> <span data-ttu-id="a3744-632">如果省略參數，則 &lt; &gt; 預設值為1， &lt; b &gt; 預設為目前的視口高度。</span><span class="sxs-lookup"><span data-stu-id="a3744-632">If the parameters are omitted, &lt;t&gt; defaults to 1 and &lt;b&gt; defaults to the current viewport height.</span></span>

<span data-ttu-id="a3744-633">滾動邊界是每個緩衝區，因此重要的是，替代緩衝區和主要緩衝區會維護個別的滾動邊界設定 (因此，替代緩衝區中的全螢幕應用程式將不會損害主要緩衝區的邊界) 。</span><span class="sxs-lookup"><span data-stu-id="a3744-633">Scrolling margins are per-buffer, so importantly, the Alternate Buffer and Main Buffer maintain separate scrolling margins settings (so a full screen application in the alternate buffer will not poison the main buffer’s margins).</span></span>


| <span data-ttu-id="a3744-634">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-634">Sequence</span></span>                       | <span data-ttu-id="a3744-635">程式碼</span><span class="sxs-lookup"><span data-stu-id="a3744-635">Code</span></span>    | <span data-ttu-id="a3744-636">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-636">Description</span></span>          | <span data-ttu-id="a3744-637">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-637">Behavior</span></span>                                       |
|--------------------------------|---------|----------------------|------------------------------------------------|
| <span data-ttu-id="a3744-638">ESC \[ &lt; t &gt; ; &lt;b &gt; r</span><span class="sxs-lookup"><span data-stu-id="a3744-638">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span></span> | <span data-ttu-id="a3744-639">DECSTBM</span><span class="sxs-lookup"><span data-stu-id="a3744-639">DECSTBM</span></span> | <span data-ttu-id="a3744-640">設定捲動區域</span><span class="sxs-lookup"><span data-stu-id="a3744-640">Set Scrolling Region</span></span> | <span data-ttu-id="a3744-641">設定區的 VT 滾動邊界。</span><span class="sxs-lookup"><span data-stu-id="a3744-641">Sets the VT scrolling margins of the viewport.</span></span> |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span data-ttu-id="a3744-642"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>視窗標題</span><span class="sxs-lookup"><span data-stu-id="a3744-642"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Window Title</span></span>


<span data-ttu-id="a3744-643">下列命令可讓應用程式將主控台視窗的標題設定為指定的 &lt; 字串 &gt; 參數。</span><span class="sxs-lookup"><span data-stu-id="a3744-643">The following commands allows the application to set the title of the console window to the given &lt;string&gt; parameter.</span></span> <span data-ttu-id="a3744-644">字串必須小於255個字元才能接受。</span><span class="sxs-lookup"><span data-stu-id="a3744-644">The string must be less than 255 characters to be accepted.</span></span> <span data-ttu-id="a3744-645">這相當於使用指定的字串來呼叫 SetConsoleTitle。</span><span class="sxs-lookup"><span data-stu-id="a3744-645">This is equivalent to calling SetConsoleTitle with the given string.</span></span>

<span data-ttu-id="a3744-646">請注意，這些順序是「作業系統命令」順序，而不是類似許多其他序列的 CSI，因此其開頭為 " \\ x1b \] "，而不是 " \\ x1b \[ "。</span><span class="sxs-lookup"><span data-stu-id="a3744-646">Note that these sequences are OSC “Operating system command” sequences, and not a CSI like many of the other sequences listed, and as such starts with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="a3744-647">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-647">Sequence</span></span>                      | <span data-ttu-id="a3744-648">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-648">Description</span></span>               | <span data-ttu-id="a3744-649">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-649">Behavior</span></span>                                           |
|-------------------------------|---------------------------|----------------------------------------------------|
| <span data-ttu-id="a3744-650">ESC \] 0; &lt;字串 &gt; below</span><span class="sxs-lookup"><span data-stu-id="a3744-650">ESC \] 0 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="a3744-651">設定圖示和視窗標題</span><span class="sxs-lookup"><span data-stu-id="a3744-651">Set Icon and Window Title</span></span> | <span data-ttu-id="a3744-652">將主控台視窗的標題設定為 &lt; 字串 &gt; 。</span><span class="sxs-lookup"><span data-stu-id="a3744-652">Sets the console window’s title to &lt;string&gt;.</span></span> |
| <span data-ttu-id="a3744-653">ESC \] 2; &lt;字串 &gt; below</span><span class="sxs-lookup"><span data-stu-id="a3744-653">ESC \] 2 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="a3744-654">設定視窗標題</span><span class="sxs-lookup"><span data-stu-id="a3744-654">Set Window Title</span></span>          | <span data-ttu-id="a3744-655">將主控台視窗的標題設定為 &lt; 字串 &gt; 。</span><span class="sxs-lookup"><span data-stu-id="a3744-655">Sets the console window’s title to &lt;string&gt;.</span></span> |



<span data-ttu-id="a3744-656">此處的終止字元是 "鐘" 字元，' \\ x07 '</span><span class="sxs-lookup"><span data-stu-id="a3744-656">The terminating character here is the “Bell” character, ‘\\x07’</span></span>

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span data-ttu-id="a3744-657"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>替代螢幕緩衝區</span><span class="sxs-lookup"><span data-stu-id="a3744-657"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternate Screen Buffer</span></span>


<span data-ttu-id="a3744-658">\*Nix 樣式應用程式通常會利用替代的螢幕緩衝區，讓他們可以修改緩衝區的整個內容，而不會影響啟動它們的應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3744-658">\*Nix style applications often utilize an alternate screen buffer, so that they can modify the entire contents of the buffer, without affecting the application that started them.</span></span> <span data-ttu-id="a3744-659">替代緩衝區完全是視窗的維度，不含任何回卷區域。</span><span class="sxs-lookup"><span data-stu-id="a3744-659">The alternate buffer is exactly the dimensions of the window, without any scrollback region.</span></span>

<span data-ttu-id="a3744-660">如需此行為的範例，請考慮從 bash 啟動 vim 的時機。</span><span class="sxs-lookup"><span data-stu-id="a3744-660">For an example of this behavior, consider when vim is launched from bash.</span></span> <span data-ttu-id="a3744-661">Vim 會使用整個畫面來編輯檔案，然後返回 bash 將原始緩衝區保持不變。</span><span class="sxs-lookup"><span data-stu-id="a3744-661">Vim uses the entirety of the screen to edit the file, then returning to bash leaves the original buffer unchanged.</span></span>


| <span data-ttu-id="a3744-662">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-662">Sequence</span></span>           | <span data-ttu-id="a3744-663">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-663">Description</span></span>                 | <span data-ttu-id="a3744-664">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-664">Behavior</span></span>                                   |
|--------------------|-----------------------------|--------------------------------------------|
| <span data-ttu-id="a3744-665">ESC \[ ？</span><span class="sxs-lookup"><span data-stu-id="a3744-665">ESC \[ ?</span></span> <span data-ttu-id="a3744-666">1 0 4 9 h</span><span class="sxs-lookup"><span data-stu-id="a3744-666">1 0 4 9 h</span></span> | <span data-ttu-id="a3744-667">使用替代螢幕緩衝區</span><span class="sxs-lookup"><span data-stu-id="a3744-667">Use Alternate Screen Buffer</span></span> | <span data-ttu-id="a3744-668">切換至新的替代螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a3744-668">Switches to a new alternate screen buffer.</span></span> |
| <span data-ttu-id="a3744-669">ESC \[ ？</span><span class="sxs-lookup"><span data-stu-id="a3744-669">ESC \[ ?</span></span> <span data-ttu-id="a3744-670">1 0 4 9 l</span><span class="sxs-lookup"><span data-stu-id="a3744-670">1 0 4 9 l</span></span> | <span data-ttu-id="a3744-671">使用主畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="a3744-671">Use Main Screen Buffer</span></span>      | <span data-ttu-id="a3744-672">切換至主要緩衝區。</span><span class="sxs-lookup"><span data-stu-id="a3744-672">Switches to the main buffer.</span></span>               |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span data-ttu-id="a3744-673"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>視窗寬度</span><span class="sxs-lookup"><span data-stu-id="a3744-673"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Window Width</span></span>


<span data-ttu-id="a3744-674">下列順序可以用來控制主控台視窗的寬度。</span><span class="sxs-lookup"><span data-stu-id="a3744-674">The following sequences can be used to control the width of the console window.</span></span> <span data-ttu-id="a3744-675">它們大致上等同于呼叫 SetConsoleScreenBufferInfoEx 主控台 API 來設定視窗寬度。</span><span class="sxs-lookup"><span data-stu-id="a3744-675">They are roughly equivalent to the calling the SetConsoleScreenBufferInfoEx console API to set the window width.</span></span>


| <span data-ttu-id="a3744-676">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-676">Sequence</span></span>     | <span data-ttu-id="a3744-677">程式碼</span><span class="sxs-lookup"><span data-stu-id="a3744-677">Code</span></span>    | <span data-ttu-id="a3744-678">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-678">Description</span></span>                  | <span data-ttu-id="a3744-679">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-679">Behavior</span></span>                                    |
|--------------|---------|------------------------------|---------------------------------------------|
| <span data-ttu-id="a3744-680">ESC \[ ？</span><span class="sxs-lookup"><span data-stu-id="a3744-680">ESC \[ ?</span></span> <span data-ttu-id="a3744-681">3小時</span><span class="sxs-lookup"><span data-stu-id="a3744-681">3 h</span></span> | <span data-ttu-id="a3744-682">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="a3744-682">DECCOLM</span></span> | <span data-ttu-id="a3744-683">將資料行數目設定為132</span><span class="sxs-lookup"><span data-stu-id="a3744-683">Set Number of Columns to 132</span></span> | <span data-ttu-id="a3744-684">將主控台寬度設定為132的資料行寬。</span><span class="sxs-lookup"><span data-stu-id="a3744-684">Sets the console width to 132 columns wide.</span></span> |
| <span data-ttu-id="a3744-685">ESC \[ ？</span><span class="sxs-lookup"><span data-stu-id="a3744-685">ESC \[ ?</span></span> <span data-ttu-id="a3744-686">3 l</span><span class="sxs-lookup"><span data-stu-id="a3744-686">3 l</span></span> | <span data-ttu-id="a3744-687">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="a3744-687">DECCOLM</span></span> | <span data-ttu-id="a3744-688">將資料行數目設定為80</span><span class="sxs-lookup"><span data-stu-id="a3744-688">Set Number of Columns to 80</span></span>  | <span data-ttu-id="a3744-689">將主控台寬度設定為80的資料行寬。</span><span class="sxs-lookup"><span data-stu-id="a3744-689">Sets the console width to 80 columns wide.</span></span>  |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span data-ttu-id="a3744-690"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>軟重設</span><span class="sxs-lookup"><span data-stu-id="a3744-690"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Soft Reset</span></span>


<span data-ttu-id="a3744-691">您可以使用下列順序，將某些屬性重設為預設值。下列屬性會重設為下列預設值 (也列出了控制這些屬性的順序) ：</span><span class="sxs-lookup"><span data-stu-id="a3744-691">The following sequence can be used to reset certain properties to their default values.The following properties are reset to the following default values (also listed are the sequences that control those properties):</span></span>

- <span data-ttu-id="a3744-692">資料指標可見度：可見的 (DECTEM) </span><span class="sxs-lookup"><span data-stu-id="a3744-692">Cursor visibility: visible (DECTEM)</span></span>
- <span data-ttu-id="a3744-693">數位鍵台：數位模式 (DECNKM) </span><span class="sxs-lookup"><span data-stu-id="a3744-693">Numeric Keypad: Numeric Mode (DECNKM)</span></span>
- <span data-ttu-id="a3744-694">資料指標索引鍵模式：標準模式 (DECCKM) </span><span class="sxs-lookup"><span data-stu-id="a3744-694">Cursor Keys Mode: Normal Mode (DECCKM)</span></span>
- <span data-ttu-id="a3744-695">上邊界和下邊界： Top = 1、下 = 主控台高度 (DECSTBM) </span><span class="sxs-lookup"><span data-stu-id="a3744-695">Top and Bottom Margins: Top=1, Bottom=Console height (DECSTBM)</span></span>
- <span data-ttu-id="a3744-696">字元集：美國 ASCII</span><span class="sxs-lookup"><span data-stu-id="a3744-696">Character Set: US ASCII</span></span>
- <span data-ttu-id="a3744-697">圖形轉譯：預設/關閉 (SGR) </span><span class="sxs-lookup"><span data-stu-id="a3744-697">Graphics Rendition: Default/Off (SGR)</span></span>
- <span data-ttu-id="a3744-698">儲存資料指標狀態： Home position (0，0)  (DECSC) </span><span class="sxs-lookup"><span data-stu-id="a3744-698">Save cursor state: Home position (0,0) (DECSC)</span></span>


| <span data-ttu-id="a3744-699">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-699">Sequence</span></span>   | <span data-ttu-id="a3744-700">程式碼</span><span class="sxs-lookup"><span data-stu-id="a3744-700">Code</span></span>   | <span data-ttu-id="a3744-701">描述</span><span class="sxs-lookup"><span data-stu-id="a3744-701">Description</span></span> | <span data-ttu-id="a3744-702">行為</span><span class="sxs-lookup"><span data-stu-id="a3744-702">Behavior</span></span>                                           |
|------------|--------|-------------|----------------------------------------------------|
| <span data-ttu-id="a3744-703">ESC \[ ！</span><span class="sxs-lookup"><span data-stu-id="a3744-703">ESC \[ !</span></span> <span data-ttu-id="a3744-704">p</span><span class="sxs-lookup"><span data-stu-id="a3744-704">p</span></span> | <span data-ttu-id="a3744-705">DECSTR</span><span class="sxs-lookup"><span data-stu-id="a3744-705">DECSTR</span></span> | <span data-ttu-id="a3744-706">軟重設</span><span class="sxs-lookup"><span data-stu-id="a3744-706">Soft Reset</span></span>  | <span data-ttu-id="a3744-707">將某些終端機設定重設為預設值。</span><span class="sxs-lookup"><span data-stu-id="a3744-707">Reset certain terminal settings to their defaults.</span></span> |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span data-ttu-id="a3744-708"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>輸入序列</span><span class="sxs-lookup"><span data-stu-id="a3744-708"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Input Sequences</span></span>


<span data-ttu-id="a3744-709">如果 \_ \_ \_ 使用 SetConsoleMode 旗標在輸入緩衝區控制碼上設定啟用虛擬終端機輸入旗標，則在輸入資料流程上的主控台主機會發出下列終端機序列。</span><span class="sxs-lookup"><span data-stu-id="a3744-709">The following terminal sequences are emitted by the console host on the input stream if the ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag is set on the input buffer handle using the SetConsoleMode flag.</span></span>

<span data-ttu-id="a3744-710">有兩種內部模式，可控制要針對指定的輸入索引鍵、資料指標索引鍵模式和鍵盤按鍵模式發出哪些順序。</span><span class="sxs-lookup"><span data-stu-id="a3744-710">There are two internal modes that control which sequences are emitted for the given input keys, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="a3744-711">這些會在 [模式變更] 區段中描述。</span><span class="sxs-lookup"><span data-stu-id="a3744-711">These are described in the Mode Changes section.</span></span>

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span data-ttu-id="a3744-712"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>資料指標索引鍵</span><span class="sxs-lookup"><span data-stu-id="a3744-712"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Cursor Keys</span></span>


| <span data-ttu-id="a3744-713">答案</span><span class="sxs-lookup"><span data-stu-id="a3744-713">Key</span></span>         | <span data-ttu-id="a3744-714">標準模式</span><span class="sxs-lookup"><span data-stu-id="a3744-714">Normal Mode</span></span> | <span data-ttu-id="a3744-715">應用程式模式</span><span class="sxs-lookup"><span data-stu-id="a3744-715">Application Mode</span></span> |
|-------------|-------------|------------------|
| <span data-ttu-id="a3744-716">向上箭號</span><span class="sxs-lookup"><span data-stu-id="a3744-716">Up Arrow</span></span>    | <span data-ttu-id="a3744-717">ESC \[ A</span><span class="sxs-lookup"><span data-stu-id="a3744-717">ESC \[ A</span></span>    | <span data-ttu-id="a3744-718">ESC O A</span><span class="sxs-lookup"><span data-stu-id="a3744-718">ESC O A</span></span>          |
| <span data-ttu-id="a3744-719">向下箭號</span><span class="sxs-lookup"><span data-stu-id="a3744-719">Down Arrow</span></span>  | <span data-ttu-id="a3744-720">ESC \[ B</span><span class="sxs-lookup"><span data-stu-id="a3744-720">ESC \[ B</span></span>    | <span data-ttu-id="a3744-721">ESC O B</span><span class="sxs-lookup"><span data-stu-id="a3744-721">ESC O B</span></span>          |
| <span data-ttu-id="a3744-722">向右鍵</span><span class="sxs-lookup"><span data-stu-id="a3744-722">Right Arrow</span></span> | <span data-ttu-id="a3744-723">ESC \[ C</span><span class="sxs-lookup"><span data-stu-id="a3744-723">ESC \[ C</span></span>    | <span data-ttu-id="a3744-724">ESC O C</span><span class="sxs-lookup"><span data-stu-id="a3744-724">ESC O C</span></span>          |
| <span data-ttu-id="a3744-725">向左鍵</span><span class="sxs-lookup"><span data-stu-id="a3744-725">Left Arrow</span></span>  | <span data-ttu-id="a3744-726">ESC \[ D</span><span class="sxs-lookup"><span data-stu-id="a3744-726">ESC \[ D</span></span>    | <span data-ttu-id="a3744-727">ESC O D</span><span class="sxs-lookup"><span data-stu-id="a3744-727">ESC O D</span></span>          |
| <span data-ttu-id="a3744-728">首頁</span><span class="sxs-lookup"><span data-stu-id="a3744-728">Home</span></span>        | <span data-ttu-id="a3744-729">ESC \[ H</span><span class="sxs-lookup"><span data-stu-id="a3744-729">ESC \[ H</span></span>    | <span data-ttu-id="a3744-730">ESC O H</span><span class="sxs-lookup"><span data-stu-id="a3744-730">ESC O H</span></span>          |
| <span data-ttu-id="a3744-731">結束</span><span class="sxs-lookup"><span data-stu-id="a3744-731">End</span></span>         | <span data-ttu-id="a3744-732">ESC \[ F</span><span class="sxs-lookup"><span data-stu-id="a3744-732">ESC \[ F</span></span>    | <span data-ttu-id="a3744-733">ESC O F</span><span class="sxs-lookup"><span data-stu-id="a3744-733">ESC O F</span></span>          |



<span data-ttu-id="a3744-734">此外，如果按下任何鍵的 Ctrl 鍵，則會改為發出下列順序，而不論資料指標索引鍵模式為何：</span><span class="sxs-lookup"><span data-stu-id="a3744-734">Additionally, if Ctrl is pressed with any of these keys, the following sequences are emitted instead, regardless of the Cursor Keys Mode:</span></span>


| <span data-ttu-id="a3744-735">答案</span><span class="sxs-lookup"><span data-stu-id="a3744-735">Key</span></span>                | <span data-ttu-id="a3744-736">任何模式</span><span class="sxs-lookup"><span data-stu-id="a3744-736">Any Mode</span></span>       |
|--------------------|----------------|
| <span data-ttu-id="a3744-737">Ctrl + 向上鍵</span><span class="sxs-lookup"><span data-stu-id="a3744-737">Ctrl + Up Arrow</span></span>    | <span data-ttu-id="a3744-738">ESC \[ 1; 5 A</span><span class="sxs-lookup"><span data-stu-id="a3744-738">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="a3744-739">Ctrl + 向下鍵</span><span class="sxs-lookup"><span data-stu-id="a3744-739">Ctrl + Down Arrow</span></span>  | <span data-ttu-id="a3744-740">ESC \[ 1; 5 B</span><span class="sxs-lookup"><span data-stu-id="a3744-740">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="a3744-741">Ctrl + 向右鍵</span><span class="sxs-lookup"><span data-stu-id="a3744-741">Ctrl + Right Arrow</span></span> | <span data-ttu-id="a3744-742">ESC \[ 1; 5 C</span><span class="sxs-lookup"><span data-stu-id="a3744-742">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="a3744-743">Ctrl + 向左鍵</span><span class="sxs-lookup"><span data-stu-id="a3744-743">Ctrl + Left Arrow</span></span>  | <span data-ttu-id="a3744-744">ESC \[ 1; 5 D</span><span class="sxs-lookup"><span data-stu-id="a3744-744">ESC \[ 1 ; 5 D</span></span> |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span data-ttu-id="a3744-745"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad & 功能金鑰</span><span class="sxs-lookup"><span data-stu-id="a3744-745"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad & Function Keys</span></span>


| <span data-ttu-id="a3744-746">答案</span><span class="sxs-lookup"><span data-stu-id="a3744-746">Key</span></span>       | <span data-ttu-id="a3744-747">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-747">Sequence</span></span>     |
|-----------|--------------|
| <span data-ttu-id="a3744-748">退格鍵</span><span class="sxs-lookup"><span data-stu-id="a3744-748">Backspace</span></span> | <span data-ttu-id="a3744-749">0x7f (DEL) </span><span class="sxs-lookup"><span data-stu-id="a3744-749">0x7f (DEL)</span></span>   |
| <span data-ttu-id="a3744-750">暫停</span><span class="sxs-lookup"><span data-stu-id="a3744-750">Pause</span></span>     | <span data-ttu-id="a3744-751">0x1a (子) </span><span class="sxs-lookup"><span data-stu-id="a3744-751">0x1a (SUB)</span></span>   |
| <span data-ttu-id="a3744-752">逸出</span><span class="sxs-lookup"><span data-stu-id="a3744-752">Escape</span></span>    | <span data-ttu-id="a3744-753">0x1b (ESC) </span><span class="sxs-lookup"><span data-stu-id="a3744-753">0x1b (ESC)</span></span>   |
| <span data-ttu-id="a3744-754">插入</span><span class="sxs-lookup"><span data-stu-id="a3744-754">Insert</span></span>    | <span data-ttu-id="a3744-755">ESC \[ 2 ~</span><span class="sxs-lookup"><span data-stu-id="a3744-755">ESC \[ 2 ~</span></span>   |
| <span data-ttu-id="a3744-756">刪除</span><span class="sxs-lookup"><span data-stu-id="a3744-756">Delete</span></span>    | <span data-ttu-id="a3744-757">ESC \[ 3 ~</span><span class="sxs-lookup"><span data-stu-id="a3744-757">ESC \[ 3 ~</span></span>   |
| <span data-ttu-id="a3744-758">Page Up</span><span class="sxs-lookup"><span data-stu-id="a3744-758">Page Up</span></span>   | <span data-ttu-id="a3744-759">ESC \[ 5 ~</span><span class="sxs-lookup"><span data-stu-id="a3744-759">ESC \[ 5 ~</span></span>   |
| <span data-ttu-id="a3744-760">Page Down</span><span class="sxs-lookup"><span data-stu-id="a3744-760">Page Down</span></span> | <span data-ttu-id="a3744-761">ESC \[ 6 ~</span><span class="sxs-lookup"><span data-stu-id="a3744-761">ESC \[ 6 ~</span></span>   |
| <span data-ttu-id="a3744-762">F1</span><span class="sxs-lookup"><span data-stu-id="a3744-762">F1</span></span>        | <span data-ttu-id="a3744-763">ESC O P</span><span class="sxs-lookup"><span data-stu-id="a3744-763">ESC O P</span></span>      |
| <span data-ttu-id="a3744-764">F2</span><span class="sxs-lookup"><span data-stu-id="a3744-764">F2</span></span>        | <span data-ttu-id="a3744-765">ESC O Q</span><span class="sxs-lookup"><span data-stu-id="a3744-765">ESC O Q</span></span>      |
| <span data-ttu-id="a3744-766">F3</span><span class="sxs-lookup"><span data-stu-id="a3744-766">F3</span></span>        | <span data-ttu-id="a3744-767">ESC O R</span><span class="sxs-lookup"><span data-stu-id="a3744-767">ESC O R</span></span>      |
| <span data-ttu-id="a3744-768">F4</span><span class="sxs-lookup"><span data-stu-id="a3744-768">F4</span></span>        | <span data-ttu-id="a3744-769">ESC O S</span><span class="sxs-lookup"><span data-stu-id="a3744-769">ESC O S</span></span>      |
| <span data-ttu-id="a3744-770">F5</span><span class="sxs-lookup"><span data-stu-id="a3744-770">F5</span></span>        | <span data-ttu-id="a3744-771">ESC \[ 1 5 ~</span><span class="sxs-lookup"><span data-stu-id="a3744-771">ESC \[ 1 5 ~</span></span> |
| <span data-ttu-id="a3744-772">F6</span><span class="sxs-lookup"><span data-stu-id="a3744-772">F6</span></span>        | <span data-ttu-id="a3744-773">ESC \[ 1 7 ~</span><span class="sxs-lookup"><span data-stu-id="a3744-773">ESC \[ 1 7 ~</span></span> |
| <span data-ttu-id="a3744-774">F7</span><span class="sxs-lookup"><span data-stu-id="a3744-774">F7</span></span>        | <span data-ttu-id="a3744-775">ESC \[ 1 8 ~</span><span class="sxs-lookup"><span data-stu-id="a3744-775">ESC \[ 1 8 ~</span></span> |
| <span data-ttu-id="a3744-776">F8</span><span class="sxs-lookup"><span data-stu-id="a3744-776">F8</span></span>        | <span data-ttu-id="a3744-777">ESC \[ 1 9 ~</span><span class="sxs-lookup"><span data-stu-id="a3744-777">ESC \[ 1 9 ~</span></span> |
| <span data-ttu-id="a3744-778">F9</span><span class="sxs-lookup"><span data-stu-id="a3744-778">F9</span></span>        | <span data-ttu-id="a3744-779">ESC \[ 2 0 ~</span><span class="sxs-lookup"><span data-stu-id="a3744-779">ESC \[ 2 0 ~</span></span> |
| <span data-ttu-id="a3744-780">F10</span><span class="sxs-lookup"><span data-stu-id="a3744-780">F10</span></span>       | <span data-ttu-id="a3744-781">ESC \[ 2 1 ~</span><span class="sxs-lookup"><span data-stu-id="a3744-781">ESC \[ 2 1 ~</span></span> |
| <span data-ttu-id="a3744-782">F11</span><span class="sxs-lookup"><span data-stu-id="a3744-782">F11</span></span>       | <span data-ttu-id="a3744-783">ESC \[ 2 3 ~</span><span class="sxs-lookup"><span data-stu-id="a3744-783">ESC \[ 2 3 ~</span></span> |
| <span data-ttu-id="a3744-784">F12</span><span class="sxs-lookup"><span data-stu-id="a3744-784">F12</span></span>       | <span data-ttu-id="a3744-785">ESC \[ 2 4 ~</span><span class="sxs-lookup"><span data-stu-id="a3744-785">ESC \[ 2 4 ~</span></span> |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span data-ttu-id="a3744-786"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>修飾 符</span><span class="sxs-lookup"><span data-stu-id="a3744-786"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifiers</span></span>

<span data-ttu-id="a3744-787">Alt 的處理方式是在序列前面加上 escape： ESC &lt; c， &gt; 其中 &lt; c &gt; 是作業系統傳遞的字元。</span><span class="sxs-lookup"><span data-stu-id="a3744-787">Alt is treated by prefixing the sequence with an escape: ESC &lt;c&gt; where &lt;c&gt; is the character passed by the operating system.</span></span> <span data-ttu-id="a3744-788">Alt + Ctrl 的處理方式相同，不同之處在于作業系統會將 c 鍵預先移位 &lt; &gt; 到適當的控制字元，以轉送至應用程式。</span><span class="sxs-lookup"><span data-stu-id="a3744-788">Alt+Ctrl is handled the same way except that the operating system will have pre-shifted the &lt;c&gt; key to the appropriate control character which will be relayed to the application.</span></span>

<span data-ttu-id="a3744-789">Ctrl 通常會與系統所收到的完全一樣傳遞。</span><span class="sxs-lookup"><span data-stu-id="a3744-789">Ctrl is generally passed through exactly as received from the system.</span></span> <span data-ttu-id="a3744-790">這通常是將單一字元向下移動到控制字元保留空間 (0x0-0x1f) 。</span><span class="sxs-lookup"><span data-stu-id="a3744-790">This is typically a single character shifted down into the control character reserved space (0x0-0x1f).</span></span> <span data-ttu-id="a3744-791">例如，Ctrl + @ (0x40) 變成 NUL (0x00) 、Ctrl + \[ (0x5b) 會變成 ESC (0x1b) 等等。系統會根據下表，特別處理一些 Ctrl 鍵組合：</span><span class="sxs-lookup"><span data-stu-id="a3744-791">For example, Ctrl+@ (0x40) becomes NUL (0x00), Ctrl+\[ (0x5b) becomes ESC (0x1b), etc. A few Ctrl key combinations are treated specially according to the following table:</span></span>


| <span data-ttu-id="a3744-792">答案</span><span class="sxs-lookup"><span data-stu-id="a3744-792">Key</span></span>                | <span data-ttu-id="a3744-793">順序</span><span class="sxs-lookup"><span data-stu-id="a3744-793">Sequence</span></span>       |
|--------------------|----------------|
| <span data-ttu-id="a3744-794">Ctrl + 空格鍵</span><span class="sxs-lookup"><span data-stu-id="a3744-794">Ctrl + Space</span></span>       | <span data-ttu-id="a3744-795">0x00 (NUL) </span><span class="sxs-lookup"><span data-stu-id="a3744-795">0x00 (NUL)</span></span>     |
| <span data-ttu-id="a3744-796">Ctrl + 向上鍵</span><span class="sxs-lookup"><span data-stu-id="a3744-796">Ctrl + Up Arrow</span></span>    | <span data-ttu-id="a3744-797">ESC \[ 1; 5 A</span><span class="sxs-lookup"><span data-stu-id="a3744-797">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="a3744-798">Ctrl + 向下鍵</span><span class="sxs-lookup"><span data-stu-id="a3744-798">Ctrl + Down Arrow</span></span>  | <span data-ttu-id="a3744-799">ESC \[ 1; 5 B</span><span class="sxs-lookup"><span data-stu-id="a3744-799">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="a3744-800">Ctrl + 向右鍵</span><span class="sxs-lookup"><span data-stu-id="a3744-800">Ctrl + Right Arrow</span></span> | <span data-ttu-id="a3744-801">ESC \[ 1; 5 C</span><span class="sxs-lookup"><span data-stu-id="a3744-801">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="a3744-802">Ctrl + 向左鍵</span><span class="sxs-lookup"><span data-stu-id="a3744-802">Ctrl + Left Arrow</span></span>  | <span data-ttu-id="a3744-803">ESC \[ 1; 5 D</span><span class="sxs-lookup"><span data-stu-id="a3744-803">ESC \[ 1 ; 5 D</span></span> |



<span data-ttu-id="a3744-804">**注意**  左 Ctrl + 右 Alt 會視為 AltGr。</span><span class="sxs-lookup"><span data-stu-id="a3744-804">**Note**  Left Ctrl + Right Alt is treated as AltGr.</span></span> <span data-ttu-id="a3744-805">當兩者同時出現時，它們將會被移除，而系統所呈現字元的 Unicode 值將會傳遞至目標。</span><span class="sxs-lookup"><span data-stu-id="a3744-805">When both are seen together, they will be stripped and the Unicode value of the character presented by the system will be passed into the target.</span></span> <span data-ttu-id="a3744-806">系統會根據目前的系統輸入設定，預先轉譯 AltGr 值。</span><span class="sxs-lookup"><span data-stu-id="a3744-806">The system will pre-translate AltGr values according to the current system input settings.</span></span>



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span data-ttu-id="a3744-807"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>樣品</span><span class="sxs-lookup"><span data-stu-id="a3744-807"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Samples</span></span>


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span data-ttu-id="a3744-808"><span id="example"></span><span id="EXAMPLE"></span>SGR 終端機序列的範例</span><span class="sxs-lookup"><span data-stu-id="a3744-808"><span id="example"></span><span id="EXAMPLE"></span>Example of SGR terminal sequences</span></span>

<span data-ttu-id="a3744-809">下列程式碼提供數個文字格式的範例。</span><span class="sxs-lookup"><span data-stu-id="a3744-809">The following code provides several examples of text formatting.</span></span>

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

<span data-ttu-id="a3744-810">**注意**  在上述範例中，字串 ' `\x1b[31m` ' 是以 n 到31的方式執行 **ESC \[ &lt; n &gt; m** &lt; &gt; 。</span><span class="sxs-lookup"><span data-stu-id="a3744-810">**Note**  In the previous example, the string '`\x1b[31m`' is the implementation of **ESC \[ &lt;n&gt; m** with &lt;n&gt; being 31.</span></span>



<span data-ttu-id="a3744-811">下圖顯示先前程式碼範例的輸出。</span><span class="sxs-lookup"><span data-stu-id="a3744-811">The following graphic shows the output of the previous code example.</span></span>

![使用 sgr 命令的主控台輸出](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span data-ttu-id="a3744-813"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>啟用虛擬終端處理的範例</span><span class="sxs-lookup"><span data-stu-id="a3744-813"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Example of Enabling Virtual Terminal Processing</span></span>

<span data-ttu-id="a3744-814">下列程式碼提供針對應用程式啟用虛擬終端處理的建議方式範例。</span><span class="sxs-lookup"><span data-stu-id="a3744-814">The following code provides an example of the recommended way to enable virtual terminal processing for an application.</span></span> <span data-ttu-id="a3744-815">範例的目的是要示範：</span><span class="sxs-lookup"><span data-stu-id="a3744-815">The intent of the sample is to demonstrate:</span></span>

1. <span data-ttu-id="a3744-816">在使用 SetConsoleMode 設定之前，應該一律先透過 GetConsoleMode 抓取現有的模式並進行分析。</span><span class="sxs-lookup"><span data-stu-id="a3744-816">The existing mode should always be retrieved via GetConsoleMode and analyzed before being set with SetConsoleMode.</span></span>

2. <span data-ttu-id="a3744-817">檢查 SetConsoleMode 是否傳回 `0` ，以及 GetLastError 傳回狀態 \_ 無效 \_ 的參數是否為目前的機制，以判斷何時在下層系統上執行。</span><span class="sxs-lookup"><span data-stu-id="a3744-817">Checking whether SetConsoleMode returns `0` and GetLastError returns STATUS\_INVALID\_PARAMETER is the current mechanism to determine when running on a down-level system.</span></span> <span data-ttu-id="a3744-818">\_ \_ 使用位欄位中其中一個較新的主控台模式旗標來接收狀態無效參數的應用程式應該會正常地降低行為，並再試一次。</span><span class="sxs-lookup"><span data-stu-id="a3744-818">An application receiving STATUS\_INVALID\_PARAMETER with one of the newer console mode flags in the bit field should gracefully degrade behavior and try again.</span></span>

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

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span data-ttu-id="a3744-819"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>選取周年更新功能的範例</span><span class="sxs-lookup"><span data-stu-id="a3744-819"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Example of Select Anniversary Update Features</span></span>

<span data-ttu-id="a3744-820">下列範例是以更健全的程式碼範例使用各種不同的 escape 序列來管理緩衝區，並強調 Windows 10 的周年更新中新增的功能。</span><span class="sxs-lookup"><span data-stu-id="a3744-820">The following example is intended to be a more robust example of code using a variety of escape sequences to manipulate the buffer, with an emphasis on the features added in the Anniversary Update for Windows 10.</span></span>

<span data-ttu-id="a3744-821">此範例會使用替代的螢幕緩衝區、操作索引標籤停止、設定滾動邊界，以及變更字元集。</span><span class="sxs-lookup"><span data-stu-id="a3744-821">This example makes use of the alternate screen buffer, manipulating tab stops, setting scrolling margins, and changing the character set.</span></span>

```C
//
//    Copyright (C) Microsoft.  All rights reserved.
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
    printf(ESC "(0");       // Enter Line drawing mode
    printf(CSI "104;93m");   // bright yellow on bright blue
    printf("x");            // in line drawing mode, \x78 -> \u2502 "Vertical Bar"
    printf(CSI "0m");       // restore color
    printf(ESC "(B");       // exit line drawing mode
}

void PrintHorizontalBorder(COORD const Size, bool fIsTop)
{
    printf(ESC "(0");       // Enter Line drawing mode
    printf(CSI "104;93m");  // Make the border bright yellow on bright blue
    printf(fIsTop? "l" : "m"); // print left corner 

    for (int i = 1; i < Size.X - 1; i++) 
        printf("q"); // in line drawing mode, \x71 -> \u2500 "HORIZONTAL SCAN LINE-5"

    printf(fIsTop? "k" : "j"); // print right corner
    printf(CSI "0m");
    printf(ESC "(B");       // exit line drawing mode
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
    Size.Y = ScreenBufferInfo.srWindow.Bottom -  ScreenBufferInfo.srWindow.Top + 1;

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









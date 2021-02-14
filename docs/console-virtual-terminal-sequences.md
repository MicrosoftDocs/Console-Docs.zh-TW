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
# <a name="console-virtual-terminal-sequences"></a><span data-ttu-id="32be2-104">主控台虛擬終端機序列</span><span class="sxs-lookup"><span data-stu-id="32be2-104">Console Virtual Terminal Sequences</span></span>


<span data-ttu-id="32be2-105">虛擬終端機序列是可在寫入至輸出資料流時控制游標移動、色彩/字型模式和其他作業的控制字元序列。</span><span class="sxs-lookup"><span data-stu-id="32be2-105">Virtual terminal sequences are control character sequences that can control cursor movement, color/font mode, and other operations when written to the output stream.</span></span> <span data-ttu-id="32be2-106">只要設定適當模式，輸入資料流上也可以接收序列來回應輸出資料流的查詢資訊序列或作為使用者輸入的編碼。</span><span class="sxs-lookup"><span data-stu-id="32be2-106">Sequences may also be received on the input stream in response to an output stream query information sequence or as an encoding of user input when the appropriate mode is set.</span></span>

<span data-ttu-id="32be2-107">您可以使用 [**GetConsoleMode**](getconsolemode.md) 和 [**SetConsoleMode**](setconsolemode.md) 函式來設定此行為。</span><span class="sxs-lookup"><span data-stu-id="32be2-107">You can use [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions to configure this behavior.</span></span> <span data-ttu-id="32be2-108">本文件最後會包含啟用虛擬終端機行為的建議方式範例。</span><span class="sxs-lookup"><span data-stu-id="32be2-108">A sample of the suggested way to enable virtual terminal behaviors is included at the end of this document.</span></span>

<span data-ttu-id="32be2-109">下列序列的行為是以 VT100 和衍生的終端機模擬器技術為基礎，特別是 xterm 終端機模擬器。</span><span class="sxs-lookup"><span data-stu-id="32be2-109">The behavior of the following sequences is based on the VT100 and derived terminal emulator technologies, most specifically the xterm terminal emulator.</span></span> <span data-ttu-id="32be2-110">如需有關終端機序列的詳細資訊，請參閱 <http://vt100.net> 和 <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>。</span><span class="sxs-lookup"><span data-stu-id="32be2-110">More information about terminal sequences can be found at <http://vt100.net> and at <http://invisible-island.net/xterm/ctlseqs/ctlseqs.html>.</span></span>

## <a name="span-idoutput_sequencesspanspan-idoutput_sequencesspanspan-idoutput_sequencesspanoutput-sequences"></a><span data-ttu-id="32be2-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>輸出序列</span><span class="sxs-lookup"><span data-stu-id="32be2-111"><span id="Output_Sequences"></span><span id="output_sequences"></span><span id="OUTPUT_SEQUENCES"></span>Output Sequences</span></span>


<span data-ttu-id="32be2-112">寫入至輸出資料流時，如果使用 [**SetConsoleMode**](setconsolemode.md) 函式在畫面緩衝區控制代碼上設定 ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING 旗標，則主控台主機會攔截下列終端機序列。</span><span class="sxs-lookup"><span data-stu-id="32be2-112">The following terminal sequences are intercepted by the console host when written into the output stream, if the ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING flag is set on the screen buffer handle using the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="32be2-113">請注意，針對寫入任何資料列中最後一個資料行的字元，使用 DISABLE\_NEWLINE\_AUTO\_RETURN 旗標有助於模擬其他終端機模擬器的游標定位和捲動行為。</span><span class="sxs-lookup"><span data-stu-id="32be2-113">Note that the DISABLE\_NEWLINE\_AUTO\_RETURN flag may also be useful in emulating the cursor positioning and scrolling behavior of other terminal emulators in relation to characters written to the final column in any row.</span></span>

## <a name="span-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspanspan-idsimple_cursor_positioningspansimple-cursor-positioning"></a><span data-ttu-id="32be2-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>簡單的游標定位</span><span class="sxs-lookup"><span data-stu-id="32be2-114"><span id="Simple_Cursor_Positioning"></span><span id="simple_cursor_positioning"></span><span id="SIMPLE_CURSOR_POSITIONING"></span>Simple Cursor Positioning</span></span>


<span data-ttu-id="32be2-115">在下列所有描述中，ESC 一律是十六進位值 0x1B。</span><span class="sxs-lookup"><span data-stu-id="32be2-115">In all of the following descriptions, ESC is always the hexadecimal value 0x1B.</span></span> <span data-ttu-id="32be2-116">終端機序列中不會包含任何空格。</span><span class="sxs-lookup"><span data-stu-id="32be2-116">No spaces are to be included in terminal sequences.</span></span> <span data-ttu-id="32be2-117">如需如何在實務中使用這些序列的範例，請參閱本主題結尾處的[範例](#example)。</span><span class="sxs-lookup"><span data-stu-id="32be2-117">For an example of how these sequences are used in practice, please see the [example](#example) at the end of this topic.</span></span>

<span data-ttu-id="32be2-118">下表描述直接在 ESC 字元之後使用單一動作命令的簡單逸出序列，並。</span><span class="sxs-lookup"><span data-stu-id="32be2-118">The following table describes simple escape sequences with a single action command directly after the ESC character.</span></span> <span data-ttu-id="32be2-119">這些序列沒有參數，而且會立即生效。</span><span class="sxs-lookup"><span data-stu-id="32be2-119">These sequences have no parameters and take effect immediately.</span></span>

<span data-ttu-id="32be2-120">此資料表中的所有命令通常等同於呼叫 [**SetConsoleCursorPosition**](setconsolecursorposition.md) 主控台 API 來放置游標。</span><span class="sxs-lookup"><span data-stu-id="32be2-120">All commands in this table are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API to place the cursor.</span></span>

<span data-ttu-id="32be2-121">游標移動會由目前的檢視區繫結至緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="32be2-121">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="32be2-122">將不會發生捲動 (如果適用)。</span><span class="sxs-lookup"><span data-stu-id="32be2-122">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="32be2-123">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-123">Sequence</span></span> | <span data-ttu-id="32be2-124">速記法</span><span class="sxs-lookup"><span data-stu-id="32be2-124">Shorthand</span></span> | <span data-ttu-id="32be2-125">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-125">Behavior</span></span> |
|----------|-----------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="32be2-126">ESC A</span><span class="sxs-lookup"><span data-stu-id="32be2-126">ESC A</span></span> | <span data-ttu-id="32be2-127">CUU</span><span class="sxs-lookup"><span data-stu-id="32be2-127">CUU</span></span> | <span data-ttu-id="32be2-128">游標向上移 1 個位置</span><span class="sxs-lookup"><span data-stu-id="32be2-128">Cursor Up by 1</span></span> |
| <span data-ttu-id="32be2-129">ESC B</span><span class="sxs-lookup"><span data-stu-id="32be2-129">ESC B</span></span> | <span data-ttu-id="32be2-130">CUD</span><span class="sxs-lookup"><span data-stu-id="32be2-130">CUD</span></span> | <span data-ttu-id="32be2-131">游標向下移 1 個位置</span><span class="sxs-lookup"><span data-stu-id="32be2-131">Cursor Down by 1</span></span> |
| <span data-ttu-id="32be2-132">ESC C</span><span class="sxs-lookup"><span data-stu-id="32be2-132">ESC C</span></span> | <span data-ttu-id="32be2-133">CUF</span><span class="sxs-lookup"><span data-stu-id="32be2-133">CUF</span></span> | <span data-ttu-id="32be2-134">游標向前 (右) 移 1 個位置</span><span class="sxs-lookup"><span data-stu-id="32be2-134">Cursor Forward (Right) by 1</span></span> |
| <span data-ttu-id="32be2-135">ESC D</span><span class="sxs-lookup"><span data-stu-id="32be2-135">ESC D</span></span> | <span data-ttu-id="32be2-136">CUB</span><span class="sxs-lookup"><span data-stu-id="32be2-136">CUB</span></span> | <span data-ttu-id="32be2-137">游標向後 (左) 移 1 個位置</span><span class="sxs-lookup"><span data-stu-id="32be2-137">Cursor Backward (Left) by 1</span></span> |
| <span data-ttu-id="32be2-138">ESC M</span><span class="sxs-lookup"><span data-stu-id="32be2-138">ESC M</span></span> | <span data-ttu-id="32be2-139">RI</span><span class="sxs-lookup"><span data-stu-id="32be2-139">RI</span></span> | <span data-ttu-id="32be2-140">反向索引 – 執行 \\n 的反向作業，將游標向上移動一行並維持水準位置，可視需要捲動緩衝區\*</span><span class="sxs-lookup"><span data-stu-id="32be2-140">Reverse Index – Performs the reverse operation of \\n, moves cursor up one line, maintains horizontal position, scrolls buffer if necessary\*</span></span> |
| <span data-ttu-id="32be2-141">ESC 7</span><span class="sxs-lookup"><span data-stu-id="32be2-141">ESC 7</span></span> | <span data-ttu-id="32be2-142">DECSC</span><span class="sxs-lookup"><span data-stu-id="32be2-142">DECSC</span></span> | <span data-ttu-id="32be2-143">將游標位置儲存在記憶體中\*\*</span><span class="sxs-lookup"><span data-stu-id="32be2-143">Save Cursor Position in Memory\*\*</span></span> |
| <span data-ttu-id="32be2-144">ESC 8</span><span class="sxs-lookup"><span data-stu-id="32be2-144">ESC 8</span></span> | <span data-ttu-id="32be2-145">DECSR</span><span class="sxs-lookup"><span data-stu-id="32be2-145">DECSR</span></span> | <span data-ttu-id="32be2-146">從記憶體還原游標位置\*\*</span><span class="sxs-lookup"><span data-stu-id="32be2-146">Restore Cursor Position from Memory\*\*</span></span> |



> [!NOTE]
><span data-ttu-id="32be2-147">\* 如果有設定捲動邊界，邊界內的 RI 只會捲動邊界的內容，並讓檢視區保持不變。</span><span class="sxs-lookup"><span data-stu-id="32be2-147">\* If there are scroll margins set, RI inside the margins will scroll only the contents of the margins, and leave the viewport unchanged.</span></span> <span data-ttu-id="32be2-148">(請參閱捲動邊界)</span><span class="sxs-lookup"><span data-stu-id="32be2-148">(See Scrolling Margins)</span></span>
>
><span data-ttu-id="32be2-149">\*\*在第一次使用儲存命令之前，記憶體中不會儲存任何值。</span><span class="sxs-lookup"><span data-stu-id="32be2-149">\*\*There will be no value saved in memory until the first use of the save command.</span></span> <span data-ttu-id="32be2-150">存取儲存值的唯一方法是使用還原命令。</span><span class="sxs-lookup"><span data-stu-id="32be2-150">The only way to access the saved value is with the restore command.</span></span>

## <a name="span-idcursor_positioningspanspan-idcursor_positioningspanspan-idcursor_positioningspancursor-positioning"></a><span data-ttu-id="32be2-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>游標定位</span><span class="sxs-lookup"><span data-stu-id="32be2-151"><span id="Cursor_Positioning"></span><span id="cursor_positioning"></span><span id="CURSOR_POSITIONING"></span>Cursor Positioning</span></span>


<span data-ttu-id="32be2-152">下表包含控制序列引導器 (Control Sequence Introducer，CSI) 類型的序列。</span><span class="sxs-lookup"><span data-stu-id="32be2-152">The following tables encompass Control Sequence Introducer (CSI) type sequences.</span></span> <span data-ttu-id="32be2-153">所有 CSI 序列都是以 ESC (0x1B) 開頭，後面接著 \[ (左括弧 (0x5B))，而且可能包含可變長度的參數來指定每項作業的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="32be2-153">All CSI sequences start with ESC (0x1B) followed by \[ (left bracket, 0x5B) and may contain parameters of variable length to specify more information for each operation.</span></span> <span data-ttu-id="32be2-154">這會以速記法 &lt;n&gt; 表示。</span><span class="sxs-lookup"><span data-stu-id="32be2-154">This will be represented by the shorthand &lt;n&gt;.</span></span> <span data-ttu-id="32be2-155">下列每個資料表都會依功能分組，並在每個資料表下方說明群組的運作方式。</span><span class="sxs-lookup"><span data-stu-id="32be2-155">Each table below is grouped by functionality with notes below each table explaining how the group works.</span></span>

<span data-ttu-id="32be2-156">除非另有註明，否則所有參數皆適用下列規則：</span><span class="sxs-lookup"><span data-stu-id="32be2-156">For all parameters, the following rules apply unless otherwise noted:</span></span>

- <span data-ttu-id="32be2-157">&lt;n&gt; 代表要移動的距離，而且屬於選擇性參數</span><span class="sxs-lookup"><span data-stu-id="32be2-157">&lt;n&gt; represents the distance to move and is an optional parameter</span></span>
- <span data-ttu-id="32be2-158">如果 &lt;n&gt; 省略或等於 0，則會將其視為 1</span><span class="sxs-lookup"><span data-stu-id="32be2-158">If &lt;n&gt; is omitted or equals 0, it will be treated as a 1</span></span>
- <span data-ttu-id="32be2-159">&lt;n&gt; 不能大於 32,767 (最大 short 值)</span><span class="sxs-lookup"><span data-stu-id="32be2-159">&lt;n&gt; cannot be larger than 32,767 (maximum short value)</span></span>
- <span data-ttu-id="32be2-160">&lt;n&gt; 不可以是負數</span><span class="sxs-lookup"><span data-stu-id="32be2-160">&lt;n&gt; cannot be negative</span></span>

<span data-ttu-id="32be2-161">本節中的所有命令通常等同於呼叫 [**SetConsoleCursorPosition**](setconsolecursorposition.md)主控台 API。</span><span class="sxs-lookup"><span data-stu-id="32be2-161">All commands in this section are generally equivalent to calling the [**SetConsoleCursorPosition**](setconsolecursorposition.md) console API.</span></span>

<span data-ttu-id="32be2-162">游標移動會由目前的檢視區繫結至緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="32be2-162">Cursor movement will be bounded by the current viewport into the buffer.</span></span> <span data-ttu-id="32be2-163">將不會發生捲動 (如果適用)。</span><span class="sxs-lookup"><span data-stu-id="32be2-163">Scrolling (if available) will not occur.</span></span>


| <span data-ttu-id="32be2-164">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-164">Sequence</span></span> | <span data-ttu-id="32be2-165">程式碼</span><span class="sxs-lookup"><span data-stu-id="32be2-165">Code</span></span> | <span data-ttu-id="32be2-166">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-166">Description</span></span> | <span data-ttu-id="32be2-167">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-167">Behavior</span></span> |
|--------------------------------|-----------|-------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="32be2-168">ESC \[ &lt;n&gt; A</span><span class="sxs-lookup"><span data-stu-id="32be2-168">ESC \[ &lt;n&gt; A</span></span> | <span data-ttu-id="32be2-169">CUU</span><span class="sxs-lookup"><span data-stu-id="32be2-169">CUU</span></span> | <span data-ttu-id="32be2-170">游標向上移</span><span class="sxs-lookup"><span data-stu-id="32be2-170">Cursor Up</span></span> | <span data-ttu-id="32be2-171">游標向上移 &lt;n&gt; 個位置</span><span class="sxs-lookup"><span data-stu-id="32be2-171">Cursor up by &lt;n&gt;</span></span> |
| <span data-ttu-id="32be2-172">ESC \[ &lt;n&gt; B</span><span class="sxs-lookup"><span data-stu-id="32be2-172">ESC \[ &lt;n&gt; B</span></span> | <span data-ttu-id="32be2-173">CUD</span><span class="sxs-lookup"><span data-stu-id="32be2-173">CUD</span></span> | <span data-ttu-id="32be2-174">游標向下移</span><span class="sxs-lookup"><span data-stu-id="32be2-174">Cursor Down</span></span> | <span data-ttu-id="32be2-175">游標向下移 &lt;n&gt; 個位置</span><span class="sxs-lookup"><span data-stu-id="32be2-175">Cursor down by &lt;n&gt;</span></span> |
| <span data-ttu-id="32be2-176">ESC \[ &lt;n&gt; C</span><span class="sxs-lookup"><span data-stu-id="32be2-176">ESC \[ &lt;n&gt; C</span></span> | <span data-ttu-id="32be2-177">CUF</span><span class="sxs-lookup"><span data-stu-id="32be2-177">CUF</span></span> | <span data-ttu-id="32be2-178">游標向前移</span><span class="sxs-lookup"><span data-stu-id="32be2-178">Cursor Forward</span></span> | <span data-ttu-id="32be2-179">游標向前 (右) 移 &lt;n&gt; 個位置</span><span class="sxs-lookup"><span data-stu-id="32be2-179">Cursor forward (Right) by &lt;n&gt;</span></span> |
| <span data-ttu-id="32be2-180">ESC \[ &lt;n&gt; D</span><span class="sxs-lookup"><span data-stu-id="32be2-180">ESC \[ &lt;n&gt; D</span></span> | <span data-ttu-id="32be2-181">CUB</span><span class="sxs-lookup"><span data-stu-id="32be2-181">CUB</span></span> | <span data-ttu-id="32be2-182">游標向後移</span><span class="sxs-lookup"><span data-stu-id="32be2-182">Cursor Backward</span></span> | <span data-ttu-id="32be2-183">游標向後 (左) 移 &lt;n&gt; 個位置</span><span class="sxs-lookup"><span data-stu-id="32be2-183">Cursor backward (Left) by &lt;n&gt;</span></span> |
| <span data-ttu-id="32be2-184">ESC \[ &lt;n&gt; E</span><span class="sxs-lookup"><span data-stu-id="32be2-184">ESC \[ &lt;n&gt; E</span></span> | <span data-ttu-id="32be2-185">CNL</span><span class="sxs-lookup"><span data-stu-id="32be2-185">CNL</span></span> | <span data-ttu-id="32be2-186">游標移到下一行</span><span class="sxs-lookup"><span data-stu-id="32be2-186">Cursor Next Line</span></span> | <span data-ttu-id="32be2-187">游標從目前位置向下移動 &lt;n&gt; 行</span><span class="sxs-lookup"><span data-stu-id="32be2-187">Cursor down &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="32be2-188">ESC \[ &lt;n&gt; F</span><span class="sxs-lookup"><span data-stu-id="32be2-188">ESC \[ &lt;n&gt; F</span></span> | <span data-ttu-id="32be2-189">CPL</span><span class="sxs-lookup"><span data-stu-id="32be2-189">CPL</span></span> | <span data-ttu-id="32be2-190">游標移到上一行</span><span class="sxs-lookup"><span data-stu-id="32be2-190">Cursor Previous Line</span></span> | <span data-ttu-id="32be2-191">游標從目前位置向上移動 &lt;n&gt; 行</span><span class="sxs-lookup"><span data-stu-id="32be2-191">Cursor up &lt;n&gt; lines from current position</span></span> |
| <span data-ttu-id="32be2-192">ESC \[ &lt;n&gt; G</span><span class="sxs-lookup"><span data-stu-id="32be2-192">ESC \[ &lt;n&gt; G</span></span> | <span data-ttu-id="32be2-193">CHA</span><span class="sxs-lookup"><span data-stu-id="32be2-193">CHA</span></span> | <span data-ttu-id="32be2-194">游標水平移到絕對位置</span><span class="sxs-lookup"><span data-stu-id="32be2-194">Cursor Horizontal Absolute</span></span> | <span data-ttu-id="32be2-195">游標水平移至目前這一行中的第 &lt;n&gt; 個位置</span><span class="sxs-lookup"><span data-stu-id="32be2-195">Cursor moves to &lt;n&gt;th position horizontally in the current line</span></span> |
| <span data-ttu-id="32be2-196">ESC \[ &lt;n&gt; d</span><span class="sxs-lookup"><span data-stu-id="32be2-196">ESC \[ &lt;n&gt; d</span></span> | <span data-ttu-id="32be2-197">VPA</span><span class="sxs-lookup"><span data-stu-id="32be2-197">VPA</span></span> | <span data-ttu-id="32be2-198">游標垂直移動到行的絕對位置</span><span class="sxs-lookup"><span data-stu-id="32be2-198">Vertical Line Position Absolute</span></span> | <span data-ttu-id="32be2-199">游標垂直移至目前資料行中的第 &lt;n&gt; 個位置</span><span class="sxs-lookup"><span data-stu-id="32be2-199">Cursor moves to the &lt;n&gt;th position vertically in the current column</span></span> |
| <span data-ttu-id="32be2-200">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span><span class="sxs-lookup"><span data-stu-id="32be2-200">ESC \[ &lt;y&gt; ; &lt;x&gt; H</span></span> | <span data-ttu-id="32be2-201">CUP</span><span class="sxs-lookup"><span data-stu-id="32be2-201">CUP</span></span> | <span data-ttu-id="32be2-202">游標位置</span><span class="sxs-lookup"><span data-stu-id="32be2-202">Cursor Position</span></span> | <span data-ttu-id="32be2-203">\*游標移到檢視區中的 &lt;x&gt;; &lt;y&gt; 座標，其中 &lt;x&gt; 是 &lt;y&gt; 行的資料行</span><span class="sxs-lookup"><span data-stu-id="32be2-203">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="32be2-204">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span><span class="sxs-lookup"><span data-stu-id="32be2-204">ESC \[ &lt;y&gt; ; &lt;x&gt; f</span></span> | <span data-ttu-id="32be2-205">HVP</span><span class="sxs-lookup"><span data-stu-id="32be2-205">HVP</span></span> | <span data-ttu-id="32be2-206">水平垂直位置</span><span class="sxs-lookup"><span data-stu-id="32be2-206">Horizontal Vertical Position</span></span> | <span data-ttu-id="32be2-207">\*游標移到檢視區中的 &lt;x&gt;; &lt;y&gt; 座標，其中 &lt;x&gt; 是 &lt;y&gt; 行的資料行</span><span class="sxs-lookup"><span data-stu-id="32be2-207">\*Cursor moves to &lt;x&gt;; &lt;y&gt; coordinate within the viewport, where &lt;x&gt; is the column of the &lt;y&gt; line</span></span> |
| <span data-ttu-id="32be2-208">ESC \[ s</span><span class="sxs-lookup"><span data-stu-id="32be2-208">ESC \[ s</span></span> | <span data-ttu-id="32be2-209">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="32be2-209">ANSISYSSC</span></span> | <span data-ttu-id="32be2-210">儲存游標 – Ansi.sys 模擬</span><span class="sxs-lookup"><span data-stu-id="32be2-210">Save Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="32be2-211">\*\*在沒有參數的情況下，執行儲存游標作業 (如同 DECSC)</span><span class="sxs-lookup"><span data-stu-id="32be2-211">\*\*With no parameters, performs a save cursor operation like DECSC</span></span> |
| <span data-ttu-id="32be2-212">ESC \[ u</span><span class="sxs-lookup"><span data-stu-id="32be2-212">ESC \[ u</span></span> | <span data-ttu-id="32be2-213">ANSISYSSC</span><span class="sxs-lookup"><span data-stu-id="32be2-213">ANSISYSSC</span></span> | <span data-ttu-id="32be2-214">還原游標 – Ansi.sys 模擬</span><span class="sxs-lookup"><span data-stu-id="32be2-214">Restore Cursor – Ansi.sys emulation</span></span> | <span data-ttu-id="32be2-215">\*\*在沒有參數的情況下，執行還原游標作業 (如同 DECRC)</span><span class="sxs-lookup"><span data-stu-id="32be2-215">\*\*With no parameters, performs a restore cursor operation like DECRC</span></span> |



> [!NOTE]
><span data-ttu-id="32be2-216">\*&lt;x&gt; 和 &lt;y&gt; 參數與上述的 &lt;n&gt; 具有相同限制。</span><span class="sxs-lookup"><span data-stu-id="32be2-216">\*&lt;x&gt; and &lt;y&gt; parameters have the same limitations as &lt;n&gt; above.</span></span> <span data-ttu-id="32be2-217">如果省略 &lt;x&gt; 和 &lt;y&gt;，則會設為 1;1。</span><span class="sxs-lookup"><span data-stu-id="32be2-217">If &lt;x&gt; and &lt;y&gt; are omitted, they will be set to 1;1.</span></span>
>
><span data-ttu-id="32be2-218">\*\*您可以在 <https://msdn.microsoft.com/library/cc722862.aspx> 上找到 ANSI.sys 的歷程記錄文件，並針對便利性/相容性需求來加以實作。</span><span class="sxs-lookup"><span data-stu-id="32be2-218">\*\*ANSI.sys historical documentation can be found at <https://msdn.microsoft.com/library/cc722862.aspx> and is implemented for convenience/compatibility.</span></span>



## <a name="span-idcursor_visibilityspanspan-idcursor_visibilityspanspan-idcursor_visibilityspancursor-visibility"></a><span data-ttu-id="32be2-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>游標可見度</span><span class="sxs-lookup"><span data-stu-id="32be2-219"><span id="Cursor_Visibility"></span><span id="cursor_visibility"></span><span id="CURSOR_VISIBILITY"></span>Cursor Visibility</span></span>


<span data-ttu-id="32be2-220">下列命令會控制游標的可見度和其閃爍狀態。</span><span class="sxs-lookup"><span data-stu-id="32be2-220">The following commands control the visibility of the cursor and its blinking state.</span></span> <span data-ttu-id="32be2-221">DECTCEM 序列通常等同於呼叫 [**SetConsoleCursorInfo**](setconsolecursorinfo.md) 主控台 API 來切換游標可見度。</span><span class="sxs-lookup"><span data-stu-id="32be2-221">The DECTCEM sequences are generally equivalent to calling [**SetConsoleCursorInfo**](setconsolecursorinfo.md) console API to toggle cursor visibility.</span></span>


| <span data-ttu-id="32be2-222">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-222">Sequence</span></span> | <span data-ttu-id="32be2-223">程式碼</span><span class="sxs-lookup"><span data-stu-id="32be2-223">Code</span></span> | <span data-ttu-id="32be2-224">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-224">Description</span></span> | <span data-ttu-id="32be2-225">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-225">Behavior</span></span> |
|---------------|---------|------------------------------|---------------------------|
| <span data-ttu-id="32be2-226">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="32be2-226">ESC \[ ?</span></span> <span data-ttu-id="32be2-227">12 h</span><span class="sxs-lookup"><span data-stu-id="32be2-227">12 h</span></span> | <span data-ttu-id="32be2-228">ATT160</span><span class="sxs-lookup"><span data-stu-id="32be2-228">ATT160</span></span> | <span data-ttu-id="32be2-229">文字游標啟用閃爍</span><span class="sxs-lookup"><span data-stu-id="32be2-229">Text Cursor Enable Blinking</span></span> | <span data-ttu-id="32be2-230">啟動游標閃爍</span><span class="sxs-lookup"><span data-stu-id="32be2-230">Start the cursor blinking</span></span> |
| <span data-ttu-id="32be2-231">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="32be2-231">ESC \[ ?</span></span> <span data-ttu-id="32be2-232">12 l</span><span class="sxs-lookup"><span data-stu-id="32be2-232">12 l</span></span> | <span data-ttu-id="32be2-233">ATT160</span><span class="sxs-lookup"><span data-stu-id="32be2-233">ATT160</span></span> | <span data-ttu-id="32be2-234">文字游標停用閃爍</span><span class="sxs-lookup"><span data-stu-id="32be2-234">Text Cursor Disable Blinking</span></span> | <span data-ttu-id="32be2-235">停止游標閃爍</span><span class="sxs-lookup"><span data-stu-id="32be2-235">Stop blinking the cursor</span></span> |
| <span data-ttu-id="32be2-236">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="32be2-236">ESC \[ ?</span></span> <span data-ttu-id="32be2-237">25 h</span><span class="sxs-lookup"><span data-stu-id="32be2-237">25 h</span></span> | <span data-ttu-id="32be2-238">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="32be2-238">DECTCEM</span></span> | <span data-ttu-id="32be2-239">文字游標啟用模式顯示</span><span class="sxs-lookup"><span data-stu-id="32be2-239">Text Cursor Enable Mode Show</span></span> | <span data-ttu-id="32be2-240">顯示游標</span><span class="sxs-lookup"><span data-stu-id="32be2-240">Show the cursor</span></span> |
| <span data-ttu-id="32be2-241">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="32be2-241">ESC \[ ?</span></span> <span data-ttu-id="32be2-242">25 l</span><span class="sxs-lookup"><span data-stu-id="32be2-242">25 l</span></span> | <span data-ttu-id="32be2-243">DECTCEM</span><span class="sxs-lookup"><span data-stu-id="32be2-243">DECTCEM</span></span> | <span data-ttu-id="32be2-244">文字游標啟用模式隱藏</span><span class="sxs-lookup"><span data-stu-id="32be2-244">Text Cursor Enable Mode Hide</span></span> | <span data-ttu-id="32be2-245">隱藏游標</span><span class="sxs-lookup"><span data-stu-id="32be2-245">Hide the cursor</span></span> |

> [!TIP]
> <span data-ttu-id="32be2-246">啟用序列的結尾是小寫 H 字元 (`h`)，而停用序列的結尾則是小寫 L 字元 (`l`)。</span><span class="sxs-lookup"><span data-stu-id="32be2-246">The enable sequences end in a lowercase H character (`h`) and the disable sequences end in a lowercase L character (`l`).</span></span>

## <a name="span-idviewport_positioningspanspan-idviewport_positioningspanspan-idviewport_positioningspanviewport-positioning"></a><span data-ttu-id="32be2-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>檢視區定位</span><span class="sxs-lookup"><span data-stu-id="32be2-247"><span id="Viewport_Positioning"></span><span id="viewport_positioning"></span><span id="VIEWPORT_POSITIONING"></span>Viewport Positioning</span></span>


<span data-ttu-id="32be2-248">本節中的所有命令通常等同於呼叫 [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 主控台 API 來移動主控台緩衝區的內容。</span><span class="sxs-lookup"><span data-stu-id="32be2-248">All commands in this section are generally equivalent to calling [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console API to move the contents of the console buffer.</span></span>

<span data-ttu-id="32be2-249">**注意** 命令名稱會造成誤導。</span><span class="sxs-lookup"><span data-stu-id="32be2-249">**Caution** The command names are misleading.</span></span> <span data-ttu-id="32be2-250">捲動 (Scroll) 是指文字在作業期間移動的方向，而不是檢視區要移動的方式。</span><span class="sxs-lookup"><span data-stu-id="32be2-250">Scroll refers to which direction the text moves during the operation, not which way the viewport would seem to move.</span></span>




| <span data-ttu-id="32be2-251">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-251">Sequence</span></span> | <span data-ttu-id="32be2-252">程式碼</span><span class="sxs-lookup"><span data-stu-id="32be2-252">Code</span></span> | <span data-ttu-id="32be2-253">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-253">Description</span></span> | <span data-ttu-id="32be2-254">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-254">Behavior</span></span> |
|--------------------|------|-------------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="32be2-255">ESC \[ &lt;n&gt; S</span><span class="sxs-lookup"><span data-stu-id="32be2-255">ESC \[ &lt;n&gt; S</span></span> | <span data-ttu-id="32be2-256">SU</span><span class="sxs-lookup"><span data-stu-id="32be2-256">SU</span></span> | <span data-ttu-id="32be2-257">向上捲動</span><span class="sxs-lookup"><span data-stu-id="32be2-257">Scroll Up</span></span> | <span data-ttu-id="32be2-258">文字向上捲動 &lt;n&gt; 個位置。</span><span class="sxs-lookup"><span data-stu-id="32be2-258">Scroll text up by &lt;n&gt;.</span></span> <span data-ttu-id="32be2-259">也稱為「向下平移」，新行會從畫面底部填入</span><span class="sxs-lookup"><span data-stu-id="32be2-259">Also known as pan down, new lines fill in from the bottom of the screen</span></span> |
| <span data-ttu-id="32be2-260">ESC \[ &lt;n&gt; T</span><span class="sxs-lookup"><span data-stu-id="32be2-260">ESC \[ &lt;n&gt; T</span></span> | <span data-ttu-id="32be2-261">SD</span><span class="sxs-lookup"><span data-stu-id="32be2-261">SD</span></span> | <span data-ttu-id="32be2-262">向下捲動</span><span class="sxs-lookup"><span data-stu-id="32be2-262">Scroll Down</span></span> | <span data-ttu-id="32be2-263">向下捲動 &lt;n&gt; 個位置。</span><span class="sxs-lookup"><span data-stu-id="32be2-263">Scroll down by &lt;n&gt;.</span></span> <span data-ttu-id="32be2-264">也稱為「向上平移」，新行會從畫面頂端填入</span><span class="sxs-lookup"><span data-stu-id="32be2-264">Also known as pan up, new lines fill in from the top of the screen</span></span> |



<span data-ttu-id="32be2-265">文字會從游標所在的那一行開始移動。</span><span class="sxs-lookup"><span data-stu-id="32be2-265">The text is moved starting with the line the cursor is on.</span></span> <span data-ttu-id="32be2-266">如果游標位於檢視區的中間資料列上，則向上捲動會移動此檢視區的下半部，並在底部插入空白行。</span><span class="sxs-lookup"><span data-stu-id="32be2-266">If the cursor is on the middle row of the viewport, then scroll up would move the bottom half of the viewport, and insert blank lines at the bottom.</span></span> <span data-ttu-id="32be2-267">向下捲動會移動檢視區資料列的上半部，並在頂端插入新行。</span><span class="sxs-lookup"><span data-stu-id="32be2-267">Scroll down would move the top half of the viewport’s rows, and insert new lines at the top.</span></span>

<span data-ttu-id="32be2-268">另外，要注意的是，向上和向下捲動也會受到捲動邊界的影響。</span><span class="sxs-lookup"><span data-stu-id="32be2-268">Also important to note is scroll up and down are also affected by the scrolling margins.</span></span> <span data-ttu-id="32be2-269">向上和向下捲動不會影響捲動邊界以外的任何行。</span><span class="sxs-lookup"><span data-stu-id="32be2-269">Scroll up and down won’t affect any lines outside the scrolling margins.</span></span>

<span data-ttu-id="32be2-270">&lt;n&gt; 的預設值是 1，而且可以選擇性地省略此值。</span><span class="sxs-lookup"><span data-stu-id="32be2-270">The default value for &lt;n&gt; is 1, and the value can be optionally omitted.</span></span>

## <a name="span-idtext_modificationspanspan-idtext_modificationspanspan-idtext_modificationspantext-modification"></a><span data-ttu-id="32be2-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>文字修改</span><span class="sxs-lookup"><span data-stu-id="32be2-271"><span id="Text_Modification"></span><span id="text_modification"></span><span id="TEXT_MODIFICATION"></span>Text Modification</span></span>


<span data-ttu-id="32be2-272">本節中的所有命令通常等同於呼叫 [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md)、[**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) 和 [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 主控台 API 來修改文字緩衝區內容。</span><span class="sxs-lookup"><span data-stu-id="32be2-272">All commands in this section are generally equivalent to calling [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md), [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md), and [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) console APIs to modify the text buffer contents.</span></span>


| <span data-ttu-id="32be2-273">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-273">Sequence</span></span> | <span data-ttu-id="32be2-274">程式碼</span><span class="sxs-lookup"><span data-stu-id="32be2-274">Code</span></span> | <span data-ttu-id="32be2-275">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-275">Description</span></span> | <span data-ttu-id="32be2-276">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-276">Behavior</span></span> |
|--------------------|------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="32be2-277">ESC \[ &lt;n&gt; @</span><span class="sxs-lookup"><span data-stu-id="32be2-277">ESC \[ &lt;n&gt; @</span></span> | <span data-ttu-id="32be2-278">ICH</span><span class="sxs-lookup"><span data-stu-id="32be2-278">ICH</span></span> | <span data-ttu-id="32be2-279">插入字元</span><span class="sxs-lookup"><span data-stu-id="32be2-279">Insert Character</span></span> | <span data-ttu-id="32be2-280">在目前的游標位置上插入 &lt;n&gt; 個空格，並將所有現有的文字移至右方。</span><span class="sxs-lookup"><span data-stu-id="32be2-280">Insert &lt;n&gt; spaces at the current cursor position, shifting all existing text to the right.</span></span> <span data-ttu-id="32be2-281">移至畫面右側的現有文字會移除。</span><span class="sxs-lookup"><span data-stu-id="32be2-281">Text exiting the screen to the right is removed.</span></span> |
| <span data-ttu-id="32be2-282">ESC \[ &lt;n&gt; P</span><span class="sxs-lookup"><span data-stu-id="32be2-282">ESC \[ &lt;n&gt; P</span></span> | <span data-ttu-id="32be2-283">DCH</span><span class="sxs-lookup"><span data-stu-id="32be2-283">DCH</span></span> | <span data-ttu-id="32be2-284">刪除字元</span><span class="sxs-lookup"><span data-stu-id="32be2-284">Delete Character</span></span> | <span data-ttu-id="32be2-285">刪除目前游標位置上的 &lt;n&gt; 個字元，從畫面右側邊緣移入空白字元。</span><span class="sxs-lookup"><span data-stu-id="32be2-285">Delete &lt;n&gt; characters at the current cursor position, shifting in space characters from the right edge of the screen.</span></span> |
| <span data-ttu-id="32be2-286">ESC \[ &lt;n&gt; X</span><span class="sxs-lookup"><span data-stu-id="32be2-286">ESC \[ &lt;n&gt; X</span></span> | <span data-ttu-id="32be2-287">ECH</span><span class="sxs-lookup"><span data-stu-id="32be2-287">ECH</span></span> | <span data-ttu-id="32be2-288">清除字元</span><span class="sxs-lookup"><span data-stu-id="32be2-288">Erase Character</span></span> | <span data-ttu-id="32be2-289">藉由以空白字元覆寫的方式，從目前的游標位置清除 &lt;n&gt; 個字元。</span><span class="sxs-lookup"><span data-stu-id="32be2-289">Erase &lt;n&gt; characters from the current cursor position by overwriting them with a space character.</span></span> |
| <span data-ttu-id="32be2-290">ESC \[ &lt;n&gt; L</span><span class="sxs-lookup"><span data-stu-id="32be2-290">ESC \[ &lt;n&gt; L</span></span> | <span data-ttu-id="32be2-291">IL</span><span class="sxs-lookup"><span data-stu-id="32be2-291">IL</span></span> | <span data-ttu-id="32be2-292">插入行</span><span class="sxs-lookup"><span data-stu-id="32be2-292">Insert Line</span></span> | <span data-ttu-id="32be2-293">將 &lt;n&gt; 行插入游標位置上的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="32be2-293">Inserts &lt;n&gt; lines into the buffer at the cursor position.</span></span> <span data-ttu-id="32be2-294">游標所在的行和其下方的行將會向下移動。</span><span class="sxs-lookup"><span data-stu-id="32be2-294">The line the cursor is on, and lines below it, will be shifted downwards.</span></span> |
| <span data-ttu-id="32be2-295">ESC \[ &lt;n&gt; M</span><span class="sxs-lookup"><span data-stu-id="32be2-295">ESC \[ &lt;n&gt; M</span></span> | <span data-ttu-id="32be2-296">DL</span><span class="sxs-lookup"><span data-stu-id="32be2-296">DL</span></span> | <span data-ttu-id="32be2-297">刪除行</span><span class="sxs-lookup"><span data-stu-id="32be2-297">Delete Line</span></span> | <span data-ttu-id="32be2-298">從緩衝區中刪除 &lt;n&gt; 行，從游標所在的資料列開始。</span><span class="sxs-lookup"><span data-stu-id="32be2-298">Deletes &lt;n&gt; lines from the buffer, starting with the row the cursor is on.</span></span> |



> [!NOTE]
><span data-ttu-id="32be2-299">針對 IL 和 DL，只有捲動邊界 (請參閱捲動邊界) 中的行會受到影響。</span><span class="sxs-lookup"><span data-stu-id="32be2-299">For IL and DL, only the lines in the scrolling margins (see Scrolling Margins) are affected.</span></span> <span data-ttu-id="32be2-300">如果未設定邊界，則預設的邊界框線為目前的檢視區。</span><span class="sxs-lookup"><span data-stu-id="32be2-300">If no margins are set, the default margin borders are the current viewport.</span></span> <span data-ttu-id="32be2-301">如果行會在邊界下方移動，則會遭到捨棄。</span><span class="sxs-lookup"><span data-stu-id="32be2-301">If lines would be shifted below the margins, they are discarded.</span></span> <span data-ttu-id="32be2-302">刪除行時，邊界底部會插入空白行，而檢視區外的行則不會受到影響。</span><span class="sxs-lookup"><span data-stu-id="32be2-302">When lines are deleted, blank lines are inserted at the bottom of the margins, lines from outside the viewport are never affected.</span></span>

<span data-ttu-id="32be2-303">針對每個序列，如果省略 &lt;n&gt;，則預設值為0。</span><span class="sxs-lookup"><span data-stu-id="32be2-303">For each of the sequences, the default value for &lt;n&gt; if it is omitted is 0.</span></span>



<span data-ttu-id="32be2-304">在下列命令中，參數 &lt;n&gt; 具有 3 個有效值：</span><span class="sxs-lookup"><span data-stu-id="32be2-304">For the following commands, the parameter &lt;n&gt; has 3 valid values:</span></span>

- <span data-ttu-id="32be2-305">0 會從目前的游標位置 (包含該位置) 清除到行/顯示畫面的結尾</span><span class="sxs-lookup"><span data-stu-id="32be2-305">0 erases from the current cursor position (inclusive) to the end of the line/display</span></span>
- <span data-ttu-id="32be2-306">1 會從行/顯示畫面的開頭清除到目前的游標位置 (包含該位置)</span><span class="sxs-lookup"><span data-stu-id="32be2-306">1 erases from the beginning of the line/display up to and including the current cursor position</span></span>
- <span data-ttu-id="32be2-307">2 清除整行/整個顯示畫面</span><span class="sxs-lookup"><span data-stu-id="32be2-307">2 erases the entire line/display</span></span>


| <span data-ttu-id="32be2-308">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-308">Sequence</span></span> | <span data-ttu-id="32be2-309">程式碼</span><span class="sxs-lookup"><span data-stu-id="32be2-309">Code</span></span> | <span data-ttu-id="32be2-310">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-310">Description</span></span> | <span data-ttu-id="32be2-311">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-311">Behavior</span></span> |
|--------------------|------|------------------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="32be2-312">ESC \[ &lt;n&gt; J</span><span class="sxs-lookup"><span data-stu-id="32be2-312">ESC \[ &lt;n&gt; J</span></span> | <span data-ttu-id="32be2-313">ED</span><span class="sxs-lookup"><span data-stu-id="32be2-313">ED</span></span> | <span data-ttu-id="32be2-314">清除顯示畫面</span><span class="sxs-lookup"><span data-stu-id="32be2-314">Erase in Display</span></span> | <span data-ttu-id="32be2-315">以空白字元取代 &lt;n&gt; 所指定的目前檢視區/畫面中的所有文字</span><span class="sxs-lookup"><span data-stu-id="32be2-315">Replace all text in the current viewport/screen specified by &lt;n&gt; with space characters</span></span> |
| <span data-ttu-id="32be2-316">ESC \[ &lt;n&gt; K</span><span class="sxs-lookup"><span data-stu-id="32be2-316">ESC \[ &lt;n&gt; K</span></span> | <span data-ttu-id="32be2-317">EL</span><span class="sxs-lookup"><span data-stu-id="32be2-317">EL</span></span> | <span data-ttu-id="32be2-318">清除行</span><span class="sxs-lookup"><span data-stu-id="32be2-318">Erase in Line</span></span> | <span data-ttu-id="32be2-319">以空白字元取代 &lt;n&gt; 所指定游標所在行上的所有文字</span><span class="sxs-lookup"><span data-stu-id="32be2-319">Replace all text on the line with the cursor specified by &lt;n&gt; with space characters</span></span> |



## <a name="span-idtext_formattingspanspan-idtext_formattingspanspan-idtext_formattingspantext-formatting"></a><span data-ttu-id="32be2-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>文字格式</span><span class="sxs-lookup"><span data-stu-id="32be2-320"><span id="Text_Formatting"></span><span id="text_formatting"></span><span id="TEXT_FORMATTING"></span>Text Formatting</span></span>


<span data-ttu-id="32be2-321">本節中的所有命令通常等同於呼叫 [**SetConsoleTextAttribute**](setconsoletextattribute.md) 主控台 API，用於調整未來所有主控台輸出文字緩衝區的寫入格式。</span><span class="sxs-lookup"><span data-stu-id="32be2-321">All commands in this section are generally equivalent to calling [**SetConsoleTextAttribute**](setconsoletextattribute.md) console APIs to adjust the formatting of all future writes to the console output text buffer.</span></span>

<span data-ttu-id="32be2-322">此命令是特別的，因為下面的 &lt;n&gt; 位置可以接受 0 到 16 的參數 (以分號分隔)。</span><span class="sxs-lookup"><span data-stu-id="32be2-322">This command is special in that the &lt;n&gt; position below can accept between 0 and 16 parameters separated by semicolons.</span></span>

<span data-ttu-id="32be2-323">若未指定任何參數，則會將其視為等同於一個參數 0。</span><span class="sxs-lookup"><span data-stu-id="32be2-323">When no parameters are specified, it is treated the same as a single 0 parameter.</span></span>


| <span data-ttu-id="32be2-324">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-324">Sequence</span></span> | <span data-ttu-id="32be2-325">程式碼</span><span class="sxs-lookup"><span data-stu-id="32be2-325">Code</span></span> | <span data-ttu-id="32be2-326">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-326">Description</span></span> | <span data-ttu-id="32be2-327">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-327">Behavior</span></span> |
|--------------------|------|------------------------|-----------------------------------------------------------------|
| <span data-ttu-id="32be2-328">ESC \[ &lt;n&gt; m</span><span class="sxs-lookup"><span data-stu-id="32be2-328">ESC \[ &lt;n&gt; m</span></span> | <span data-ttu-id="32be2-329">SGR</span><span class="sxs-lookup"><span data-stu-id="32be2-329">SGR</span></span> | <span data-ttu-id="32be2-330">設定圖形轉譯</span><span class="sxs-lookup"><span data-stu-id="32be2-330">Set Graphics Rendition</span></span> | <span data-ttu-id="32be2-331">依據 &lt;n&gt; 所指定的內容設定畫面的格式和文字</span><span class="sxs-lookup"><span data-stu-id="32be2-331">Set the format of the screen and text as specified by &lt;n&gt;</span></span> |



<span data-ttu-id="32be2-332">下表的值可以在 &lt;n&gt; 中用來代表不同的格式化模式。</span><span class="sxs-lookup"><span data-stu-id="32be2-332">The following table of values can be used in &lt;n&gt; to represent different formatting modes.</span></span>

<span data-ttu-id="32be2-333">格式化模式會從左至右套用。</span><span class="sxs-lookup"><span data-stu-id="32be2-333">Formatting modes are applied from left to right.</span></span> <span data-ttu-id="32be2-334">套用競爭格式化選項會使最右邊的選項具有優先權。</span><span class="sxs-lookup"><span data-stu-id="32be2-334">Applying competing formatting options will result in the right-most option taking precedence.</span></span>

<span data-ttu-id="32be2-335">針對指定色彩的選項，這些色彩會依照主控台色彩表中的定義使用，您可以使用 [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API 加以修改。</span><span class="sxs-lookup"><span data-stu-id="32be2-335">For options that specify colors, the colors will be used as defined in the console color table which can be modified using the [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) API.</span></span> <span data-ttu-id="32be2-336">如果將資料表修改為讓資料表中的「藍色」位置顯示 RGB 色度的紅色，則對 **前景藍色** 發出的所有呼叫都會顯示該紅色色彩，直到另有變更為止。</span><span class="sxs-lookup"><span data-stu-id="32be2-336">If the table is modified to make the “blue” position in the table display an RGB shade of red, then all calls to **Foreground Blue** will display that red color until otherwise changed.</span></span>


| <span data-ttu-id="32be2-337">值</span><span class="sxs-lookup"><span data-stu-id="32be2-337">Value</span></span> | <span data-ttu-id="32be2-338">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-338">Description</span></span> | <span data-ttu-id="32be2-339">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-339">Behavior</span></span> |
|-------|---------------------------|--------------------------------------------------------------------|
| <span data-ttu-id="32be2-340">0</span><span class="sxs-lookup"><span data-stu-id="32be2-340">0</span></span> | <span data-ttu-id="32be2-341">預設</span><span class="sxs-lookup"><span data-stu-id="32be2-341">Default</span></span> | <span data-ttu-id="32be2-342">在修改前將所有屬性都設回為預設狀態</span><span class="sxs-lookup"><span data-stu-id="32be2-342">Returns all attributes to the default state prior to modification</span></span> |
| <span data-ttu-id="32be2-343">1</span><span class="sxs-lookup"><span data-stu-id="32be2-343">1</span></span> | <span data-ttu-id="32be2-344">濃厚/明亮</span><span class="sxs-lookup"><span data-stu-id="32be2-344">Bold/Bright</span></span> | <span data-ttu-id="32be2-345">將亮度/飽和度旗標套用至前景色彩</span><span class="sxs-lookup"><span data-stu-id="32be2-345">Applies brightness/intensity flag to foreground color</span></span> |
| <span data-ttu-id="32be2-346">22</span><span class="sxs-lookup"><span data-stu-id="32be2-346">22</span></span> | <span data-ttu-id="32be2-347">無粗體/亮色</span><span class="sxs-lookup"><span data-stu-id="32be2-347">No bold/bright</span></span> | <span data-ttu-id="32be2-348">移除前景色彩的亮度/濃度旗標</span><span class="sxs-lookup"><span data-stu-id="32be2-348">Removes brightness/intensity flag from foreground color</span></span> |
| <span data-ttu-id="32be2-349">4</span><span class="sxs-lookup"><span data-stu-id="32be2-349">4</span></span> | <span data-ttu-id="32be2-350">Underline</span><span class="sxs-lookup"><span data-stu-id="32be2-350">Underline</span></span> | <span data-ttu-id="32be2-351">加底線</span><span class="sxs-lookup"><span data-stu-id="32be2-351">Adds underline</span></span> |
| <span data-ttu-id="32be2-352">24</span><span class="sxs-lookup"><span data-stu-id="32be2-352">24</span></span> | <span data-ttu-id="32be2-353">沒有底線</span><span class="sxs-lookup"><span data-stu-id="32be2-353">No underline</span></span> | <span data-ttu-id="32be2-354">移除底線</span><span class="sxs-lookup"><span data-stu-id="32be2-354">Removes underline</span></span> |
| <span data-ttu-id="32be2-355">7</span><span class="sxs-lookup"><span data-stu-id="32be2-355">7</span></span> | <span data-ttu-id="32be2-356">負</span><span class="sxs-lookup"><span data-stu-id="32be2-356">Negative</span></span> | <span data-ttu-id="32be2-357">交換前景和背景色彩</span><span class="sxs-lookup"><span data-stu-id="32be2-357">Swaps foreground and background colors</span></span> |
| <span data-ttu-id="32be2-358">27</span><span class="sxs-lookup"><span data-stu-id="32be2-358">27</span></span> | <span data-ttu-id="32be2-359">正面 (非負面)</span><span class="sxs-lookup"><span data-stu-id="32be2-359">Positive (No negative)</span></span> | <span data-ttu-id="32be2-360">讓前景/背景回到一般狀態</span><span class="sxs-lookup"><span data-stu-id="32be2-360">Returns foreground/background to normal</span></span> |
| <span data-ttu-id="32be2-361">30</span><span class="sxs-lookup"><span data-stu-id="32be2-361">30</span></span> | <span data-ttu-id="32be2-362">前景黑色</span><span class="sxs-lookup"><span data-stu-id="32be2-362">Foreground Black</span></span> | <span data-ttu-id="32be2-363">將非濃厚/明亮的黑色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-363">Applies non-bold/bright black to foreground</span></span> |
| <span data-ttu-id="32be2-364">31</span><span class="sxs-lookup"><span data-stu-id="32be2-364">31</span></span> | <span data-ttu-id="32be2-365">前景紅色</span><span class="sxs-lookup"><span data-stu-id="32be2-365">Foreground Red</span></span> | <span data-ttu-id="32be2-366">將非濃厚/明亮的紅色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-366">Applies non-bold/bright red to foreground</span></span> |
| <span data-ttu-id="32be2-367">32</span><span class="sxs-lookup"><span data-stu-id="32be2-367">32</span></span> | <span data-ttu-id="32be2-368">前景綠色</span><span class="sxs-lookup"><span data-stu-id="32be2-368">Foreground Green</span></span> | <span data-ttu-id="32be2-369">將非濃厚/明亮的綠色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-369">Applies non-bold/bright green to foreground</span></span> |
| <span data-ttu-id="32be2-370">33</span><span class="sxs-lookup"><span data-stu-id="32be2-370">33</span></span> | <span data-ttu-id="32be2-371">前景黃色</span><span class="sxs-lookup"><span data-stu-id="32be2-371">Foreground Yellow</span></span> | <span data-ttu-id="32be2-372">將非濃厚/明亮的黃色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-372">Applies non-bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="32be2-373">34</span><span class="sxs-lookup"><span data-stu-id="32be2-373">34</span></span> | <span data-ttu-id="32be2-374">前景藍色</span><span class="sxs-lookup"><span data-stu-id="32be2-374">Foreground Blue</span></span> | <span data-ttu-id="32be2-375">將非濃厚/明亮的藍色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-375">Applies non-bold/bright blue to foreground</span></span> |
| <span data-ttu-id="32be2-376">35</span><span class="sxs-lookup"><span data-stu-id="32be2-376">35</span></span> | <span data-ttu-id="32be2-377">前景洋紅色</span><span class="sxs-lookup"><span data-stu-id="32be2-377">Foreground Magenta</span></span> | <span data-ttu-id="32be2-378">將非濃厚/明亮的洋紅色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-378">Applies non-bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="32be2-379">36</span><span class="sxs-lookup"><span data-stu-id="32be2-379">36</span></span> | <span data-ttu-id="32be2-380">前景青色</span><span class="sxs-lookup"><span data-stu-id="32be2-380">Foreground Cyan</span></span> | <span data-ttu-id="32be2-381">將非濃厚/明亮的青色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-381">Applies non-bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="32be2-382">37</span><span class="sxs-lookup"><span data-stu-id="32be2-382">37</span></span> | <span data-ttu-id="32be2-383">前景白色</span><span class="sxs-lookup"><span data-stu-id="32be2-383">Foreground White</span></span> | <span data-ttu-id="32be2-384">將非濃厚/明亮的白色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-384">Applies non-bold/bright white to foreground</span></span> |
| <span data-ttu-id="32be2-385">38</span><span class="sxs-lookup"><span data-stu-id="32be2-385">38</span></span> | <span data-ttu-id="32be2-386">前景擴充</span><span class="sxs-lookup"><span data-stu-id="32be2-386">Foreground Extended</span></span> | <span data-ttu-id="32be2-387">將擴充的色彩值套用至前景 (請參閱下列詳細資料)</span><span class="sxs-lookup"><span data-stu-id="32be2-387">Applies extended color value to the foreground (see details below)</span></span> |
| <span data-ttu-id="32be2-388">39</span><span class="sxs-lookup"><span data-stu-id="32be2-388">39</span></span> | <span data-ttu-id="32be2-389">前景預設值</span><span class="sxs-lookup"><span data-stu-id="32be2-389">Foreground Default</span></span> | <span data-ttu-id="32be2-390">僅套用預設的前景部分 (請參閱 0)</span><span class="sxs-lookup"><span data-stu-id="32be2-390">Applies only the foreground portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="32be2-391">40</span><span class="sxs-lookup"><span data-stu-id="32be2-391">40</span></span> | <span data-ttu-id="32be2-392">背景黑色</span><span class="sxs-lookup"><span data-stu-id="32be2-392">Background Black</span></span> | <span data-ttu-id="32be2-393">將非濃厚/明亮的黑色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-393">Applies non-bold/bright black to background</span></span> |
| <span data-ttu-id="32be2-394">41</span><span class="sxs-lookup"><span data-stu-id="32be2-394">41</span></span> | <span data-ttu-id="32be2-395">背景紅色</span><span class="sxs-lookup"><span data-stu-id="32be2-395">Background Red</span></span> | <span data-ttu-id="32be2-396">將非濃厚/明亮的紅色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-396">Applies non-bold/bright red to background</span></span> |
| <span data-ttu-id="32be2-397">42</span><span class="sxs-lookup"><span data-stu-id="32be2-397">42</span></span> | <span data-ttu-id="32be2-398">背景綠色</span><span class="sxs-lookup"><span data-stu-id="32be2-398">Background Green</span></span> | <span data-ttu-id="32be2-399">將非濃厚/明亮的綠色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-399">Applies non-bold/bright green to background</span></span> |
| <span data-ttu-id="32be2-400">43</span><span class="sxs-lookup"><span data-stu-id="32be2-400">43</span></span> | <span data-ttu-id="32be2-401">背景黃色</span><span class="sxs-lookup"><span data-stu-id="32be2-401">Background Yellow</span></span> | <span data-ttu-id="32be2-402">將非濃厚/明亮的黃色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-402">Applies non-bold/bright yellow to background</span></span> |
| <span data-ttu-id="32be2-403">44</span><span class="sxs-lookup"><span data-stu-id="32be2-403">44</span></span> | <span data-ttu-id="32be2-404">背景藍色</span><span class="sxs-lookup"><span data-stu-id="32be2-404">Background Blue</span></span> | <span data-ttu-id="32be2-405">將非濃厚/明亮的藍色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-405">Applies non-bold/bright blue to background</span></span> |
| <span data-ttu-id="32be2-406">45</span><span class="sxs-lookup"><span data-stu-id="32be2-406">45</span></span> | <span data-ttu-id="32be2-407">背景洋紅色</span><span class="sxs-lookup"><span data-stu-id="32be2-407">Background Magenta</span></span> | <span data-ttu-id="32be2-408">將非濃厚/明亮的洋紅色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-408">Applies non-bold/bright magenta to background</span></span> |
| <span data-ttu-id="32be2-409">46</span><span class="sxs-lookup"><span data-stu-id="32be2-409">46</span></span> | <span data-ttu-id="32be2-410">背景青色</span><span class="sxs-lookup"><span data-stu-id="32be2-410">Background Cyan</span></span> | <span data-ttu-id="32be2-411">將非濃厚/明亮的青色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-411">Applies non-bold/bright cyan to background</span></span> |
| <span data-ttu-id="32be2-412">47</span><span class="sxs-lookup"><span data-stu-id="32be2-412">47</span></span> | <span data-ttu-id="32be2-413">背景白色</span><span class="sxs-lookup"><span data-stu-id="32be2-413">Background White</span></span> | <span data-ttu-id="32be2-414">將非濃厚/明亮的白色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-414">Applies non-bold/bright white to background</span></span> |
| <span data-ttu-id="32be2-415">48</span><span class="sxs-lookup"><span data-stu-id="32be2-415">48</span></span> | <span data-ttu-id="32be2-416">背景擴充</span><span class="sxs-lookup"><span data-stu-id="32be2-416">Background Extended</span></span> | <span data-ttu-id="32be2-417">將擴充的色彩值套用至背景 (請參閱下列詳細資料)</span><span class="sxs-lookup"><span data-stu-id="32be2-417">Applies extended color value to the background (see details below)</span></span> |
| <span data-ttu-id="32be2-418">49</span><span class="sxs-lookup"><span data-stu-id="32be2-418">49</span></span> | <span data-ttu-id="32be2-419">背景預設值</span><span class="sxs-lookup"><span data-stu-id="32be2-419">Background Default</span></span> | <span data-ttu-id="32be2-420">僅套用預設的背景部分 (請參閱0)</span><span class="sxs-lookup"><span data-stu-id="32be2-420">Applies only the background portion of the defaults (see 0)</span></span> |
| <span data-ttu-id="32be2-421">90</span><span class="sxs-lookup"><span data-stu-id="32be2-421">90</span></span> | <span data-ttu-id="32be2-422">明亮前景黑色</span><span class="sxs-lookup"><span data-stu-id="32be2-422">Bright Foreground Black</span></span> | <span data-ttu-id="32be2-423">將濃厚/明亮的亮黑色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-423">Applies bold/bright black to foreground</span></span> |
| <span data-ttu-id="32be2-424">91</span><span class="sxs-lookup"><span data-stu-id="32be2-424">91</span></span> | <span data-ttu-id="32be2-425">明亮前景紅色</span><span class="sxs-lookup"><span data-stu-id="32be2-425">Bright Foreground Red</span></span> | <span data-ttu-id="32be2-426">將濃厚/明亮的紅色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-426">Applies bold/bright red to foreground</span></span> |
| <span data-ttu-id="32be2-427">92</span><span class="sxs-lookup"><span data-stu-id="32be2-427">92</span></span> | <span data-ttu-id="32be2-428">明亮前景綠色</span><span class="sxs-lookup"><span data-stu-id="32be2-428">Bright Foreground Green</span></span> | <span data-ttu-id="32be2-429">將濃厚/明亮的綠色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-429">Applies bold/bright green to foreground</span></span> |
| <span data-ttu-id="32be2-430">93</span><span class="sxs-lookup"><span data-stu-id="32be2-430">93</span></span> | <span data-ttu-id="32be2-431">明亮前景黃色</span><span class="sxs-lookup"><span data-stu-id="32be2-431">Bright Foreground Yellow</span></span> | <span data-ttu-id="32be2-432">將濃厚/明亮的黃色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-432">Applies bold/bright yellow to foreground</span></span> |
| <span data-ttu-id="32be2-433">94</span><span class="sxs-lookup"><span data-stu-id="32be2-433">94</span></span> | <span data-ttu-id="32be2-434">明亮前景藍色</span><span class="sxs-lookup"><span data-stu-id="32be2-434">Bright Foreground Blue</span></span> | <span data-ttu-id="32be2-435">將濃厚/明亮的藍色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-435">Applies bold/bright blue to foreground</span></span> |
| <span data-ttu-id="32be2-436">95</span><span class="sxs-lookup"><span data-stu-id="32be2-436">95</span></span> | <span data-ttu-id="32be2-437">明亮前景洋紅色</span><span class="sxs-lookup"><span data-stu-id="32be2-437">Bright Foreground Magenta</span></span> | <span data-ttu-id="32be2-438">將濃厚/明亮的洋紅色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-438">Applies bold/bright magenta to foreground</span></span> |
| <span data-ttu-id="32be2-439">96</span><span class="sxs-lookup"><span data-stu-id="32be2-439">96</span></span> | <span data-ttu-id="32be2-440">明亮前景青色</span><span class="sxs-lookup"><span data-stu-id="32be2-440">Bright Foreground Cyan</span></span> | <span data-ttu-id="32be2-441">將濃厚/明亮的青色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-441">Applies bold/bright cyan to foreground</span></span> |
| <span data-ttu-id="32be2-442">97</span><span class="sxs-lookup"><span data-stu-id="32be2-442">97</span></span> | <span data-ttu-id="32be2-443">明亮前景白色</span><span class="sxs-lookup"><span data-stu-id="32be2-443">Bright Foreground White</span></span> | <span data-ttu-id="32be2-444">將濃厚/明亮的白色套用至前景</span><span class="sxs-lookup"><span data-stu-id="32be2-444">Applies bold/bright white to foreground</span></span> |
| <span data-ttu-id="32be2-445">100</span><span class="sxs-lookup"><span data-stu-id="32be2-445">100</span></span> | <span data-ttu-id="32be2-446">明亮的背景黑色</span><span class="sxs-lookup"><span data-stu-id="32be2-446">Bright Background Black</span></span> | <span data-ttu-id="32be2-447">將濃厚/明亮的黑色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-447">Applies bold/bright black to background</span></span> |
| <span data-ttu-id="32be2-448">101</span><span class="sxs-lookup"><span data-stu-id="32be2-448">101</span></span> | <span data-ttu-id="32be2-449">明亮背景紅色</span><span class="sxs-lookup"><span data-stu-id="32be2-449">Bright Background Red</span></span> | <span data-ttu-id="32be2-450">將濃厚/明亮的紅色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-450">Applies bold/bright red to background</span></span> |
| <span data-ttu-id="32be2-451">102</span><span class="sxs-lookup"><span data-stu-id="32be2-451">102</span></span> | <span data-ttu-id="32be2-452">明亮背景綠色</span><span class="sxs-lookup"><span data-stu-id="32be2-452">Bright Background Green</span></span> | <span data-ttu-id="32be2-453">將濃厚/明亮的綠色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-453">Applies bold/bright green to background</span></span> |
| <span data-ttu-id="32be2-454">103</span><span class="sxs-lookup"><span data-stu-id="32be2-454">103</span></span> | <span data-ttu-id="32be2-455">明亮的背景黃色</span><span class="sxs-lookup"><span data-stu-id="32be2-455">Bright Background Yellow</span></span> | <span data-ttu-id="32be2-456">將濃厚/明亮的黃色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-456">Applies bold/bright yellow to background</span></span> |
| <span data-ttu-id="32be2-457">104</span><span class="sxs-lookup"><span data-stu-id="32be2-457">104</span></span> | <span data-ttu-id="32be2-458">明亮背景藍色</span><span class="sxs-lookup"><span data-stu-id="32be2-458">Bright Background Blue</span></span> | <span data-ttu-id="32be2-459">將濃厚/明亮的藍色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-459">Applies bold/bright blue to background</span></span> |
| <span data-ttu-id="32be2-460">105</span><span class="sxs-lookup"><span data-stu-id="32be2-460">105</span></span> | <span data-ttu-id="32be2-461">明亮背景洋紅色</span><span class="sxs-lookup"><span data-stu-id="32be2-461">Bright Background Magenta</span></span> | <span data-ttu-id="32be2-462">將濃厚/明亮的洋紅色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-462">Applies bold/bright magenta to background</span></span> |
| <span data-ttu-id="32be2-463">106</span><span class="sxs-lookup"><span data-stu-id="32be2-463">106</span></span> | <span data-ttu-id="32be2-464">明亮背景青色</span><span class="sxs-lookup"><span data-stu-id="32be2-464">Bright Background Cyan</span></span> | <span data-ttu-id="32be2-465">將濃厚/明亮的青色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-465">Applies bold/bright cyan to background</span></span> |
| <span data-ttu-id="32be2-466">107</span><span class="sxs-lookup"><span data-stu-id="32be2-466">107</span></span> | <span data-ttu-id="32be2-467">明亮背景白色</span><span class="sxs-lookup"><span data-stu-id="32be2-467">Bright Background White</span></span> | <span data-ttu-id="32be2-468">將濃厚/明亮的白色套用至背景</span><span class="sxs-lookup"><span data-stu-id="32be2-468">Applies bold/bright white to background</span></span> |



### <a name="span-idextended_colorsspanspan-idextended_colorsspanspan-idextended_colorsspanextended-colors"></a><span data-ttu-id="32be2-469"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>擴充的色彩</span><span class="sxs-lookup"><span data-stu-id="32be2-469"><span id="Extended_Colors"></span><span id="extended_colors"></span><span id="EXTENDED_COLORS"></span>Extended Colors</span></span>

<span data-ttu-id="32be2-470">某些虛擬終端機模擬器支援的色彩調色板多於 Windows 主控台所提供的 16 種色彩。</span><span class="sxs-lookup"><span data-stu-id="32be2-470">Some virtual terminal emulators support a palette of colors greater than the 16 colors provided by the Windows Console.</span></span> <span data-ttu-id="32be2-471">針對這些擴充的色彩，Windows 主控台會從現有的 16 色表格中選擇最接近的色彩來顯示。</span><span class="sxs-lookup"><span data-stu-id="32be2-471">For these extended colors, the Windows Console will choose the nearest appropriate color from the existing 16 color table for display.</span></span> <span data-ttu-id="32be2-472">不同於上述的一般 SGR 值，擴充的值會根據下表，在使用最初的指示器之後取用額外的參數。</span><span class="sxs-lookup"><span data-stu-id="32be2-472">Unlike typical SGR values above, the extended values will consume additional parameters after the initial indicator according to the table below.</span></span>


| <span data-ttu-id="32be2-473">SGR 子序列</span><span class="sxs-lookup"><span data-stu-id="32be2-473">SGR Subsequence</span></span> | <span data-ttu-id="32be2-474">說明</span><span class="sxs-lookup"><span data-stu-id="32be2-474">Description</span></span> |
|--------------------------------------------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="32be2-475">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="32be2-475">38 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="32be2-476">將前景色彩設為 &lt;r&gt;、&lt;g&gt;、&lt;b&gt; 參數中指定的 RGB 值\*</span><span class="sxs-lookup"><span data-stu-id="32be2-476">Set foreground color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="32be2-477">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span><span class="sxs-lookup"><span data-stu-id="32be2-477">48 ; 2 ; &lt;r&gt; ; &lt;g&gt; ; &lt;b&gt;</span></span> | <span data-ttu-id="32be2-478">將背景色彩設為以 &lt;r&gt;、&lt;g&gt;、&lt;b&gt; 參數指定的 RGB 值\*</span><span class="sxs-lookup"><span data-stu-id="32be2-478">Set background color to RGB value specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt; parameters\*</span></span> |
| <span data-ttu-id="32be2-479">38 ; 5 ; &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="32be2-479">38 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="32be2-480">將前景色彩設為 88 或 256 色彩表中的 &lt;s&gt; 索引\*</span><span class="sxs-lookup"><span data-stu-id="32be2-480">Set foreground color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |
| <span data-ttu-id="32be2-481">48 ; 5 ; &lt;s&gt;</span><span class="sxs-lookup"><span data-stu-id="32be2-481">48 ; 5 ; &lt;s&gt;</span></span> | <span data-ttu-id="32be2-482">將背景色彩設為 88 或 256 色彩表中的 &lt;s&gt; 索引\*</span><span class="sxs-lookup"><span data-stu-id="32be2-482">Set background color to &lt;s&gt; index in 88 or 256 color table\*</span></span> |



<span data-ttu-id="32be2-483">\*在內部維護以進行比較的 88 和 256 色調色盤，是以 xterm 終端機模擬器為基礎。</span><span class="sxs-lookup"><span data-stu-id="32be2-483">\*The 88 and 256 color palettes maintained internally for comparison are based from the xterm terminal emulator.</span></span> <span data-ttu-id="32be2-484">目前無法修改比較/進位表。</span><span class="sxs-lookup"><span data-stu-id="32be2-484">The comparison/rounding tables cannot be modified at this time.</span></span>


## <a name="span-idscreen_colorsspanspan-idscreen_colorsspanspan-idscreen_colorsspanscreen-colors"></a><span data-ttu-id="32be2-485"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>畫面色彩</span><span class="sxs-lookup"><span data-stu-id="32be2-485"><span id="Screen_Colors"></span><span id="screen_colors"></span><span id="SCREEN_COLORS"></span>Screen Colors</span></span>


<span data-ttu-id="32be2-486">下列命令可讓應用程式將畫面色彩調色盤值設定為任何 RGB 值。</span><span class="sxs-lookup"><span data-stu-id="32be2-486">The following command allows the application to set the screen colors palette values to any RGB value.</span></span>

<span data-ttu-id="32be2-487">RGB 值應該是 `0` 和 `ff` 之間的十六進位值，並以正斜線字元 (例如 `rgb:1/24/86`) 分隔。</span><span class="sxs-lookup"><span data-stu-id="32be2-487">The RGB values should be hexadecimal values between `0` and `ff`, and separated by the forward-slash character (e.g. `rgb:1/24/86`).</span></span>

<span data-ttu-id="32be2-488">請注意，此序列是一個 OSC (作業系統命令) 序列，而不是類似於列出許多其他序列的 CSI，因此開頭為 "\\x1b\]"，而不是 "\\x1b\["。</span><span class="sxs-lookup"><span data-stu-id="32be2-488">Note that this sequence is an OSC “Operating system command” sequence, and not a CSI like many of the other sequences listed, and as such start with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="32be2-489">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-489">Sequence</span></span> | <span data-ttu-id="32be2-490">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-490">Description</span></span> | <span data-ttu-id="32be2-491">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-491">Behavior</span></span> |
|--------------------------------------------------------------------|----------------------|--------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="32be2-492">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span><span class="sxs-lookup"><span data-stu-id="32be2-492">ESC \] 4 ; &lt;i&gt; ; rgb : &lt;r&gt; / &lt;g&gt; / &lt;b&gt; ESC</span></span> | <span data-ttu-id="32be2-493">修改畫面色彩</span><span class="sxs-lookup"><span data-stu-id="32be2-493">Modify Screen Colors</span></span> | <span data-ttu-id="32be2-494">將畫面色彩調色盤索引 &lt;i&gt; 設定為 &lt;r&gt;、&lt;g&gt;、&lt;b&gt; 中指定的 RGB 值</span><span class="sxs-lookup"><span data-stu-id="32be2-494">Sets the screen color palette index &lt;i&gt; to the RGB values specified in &lt;r&gt;, &lt;g&gt;, &lt;b&gt;</span></span> |



## <a name="span-idmode_changes__spanspan-idmode_changes__spanspan-idmode_changes__spanmode-changes"></a><span data-ttu-id="32be2-495"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>模式變更</span><span class="sxs-lookup"><span data-stu-id="32be2-495"><span id="Mode_Changes__"></span><span id="mode_changes__"></span><span id="MODE_CHANGES__"></span>Mode Changes</span></span>


<span data-ttu-id="32be2-496">這些是控制輸入模式的序列。</span><span class="sxs-lookup"><span data-stu-id="32be2-496">These are sequences that control the input modes.</span></span> <span data-ttu-id="32be2-497">有兩組不同的輸入模式：游標按鍵模式和鍵盤按鍵模式。</span><span class="sxs-lookup"><span data-stu-id="32be2-497">There are two different sets of input modes, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="32be2-498">游標按鍵模式會控制由方向鍵及 Home 與 End 所發出的序列，而鍵盤按鍵模式會控制主要由 Numpad 上按鍵及功能鍵所發出的序列。</span><span class="sxs-lookup"><span data-stu-id="32be2-498">The Cursor Keys Mode controls the sequences that are emitted by the arrow keys as well as Home and End, while the Keypad Keys Mode controls the sequences emitted by the keys on the numpad primarily, as well as the function keys.</span></span>

<span data-ttu-id="32be2-499">這些模式中的每一個都是簡單的布林值設定 – 游標按鍵模式是標準 (預設) 或應用程式，而鍵盤按鍵模式則是數字 (預設值) 或應用程式。</span><span class="sxs-lookup"><span data-stu-id="32be2-499">Each of these modes are simple boolean settings – the Cursor Keys Mode is either Normal (default) or Application, and the Keypad Keys Mode is either Numeric (default) or Application.</span></span>

<span data-ttu-id="32be2-500">請參閱 [游標按鍵] 和 [Numpad 與功能鍵] 區段，以了解在這些模式中發出的序列。</span><span class="sxs-lookup"><span data-stu-id="32be2-500">See the Cursor Keys and Numpad & Function Keys sections for the sequences emitted in these modes.</span></span>


| <span data-ttu-id="32be2-501">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-501">Sequence</span></span> | <span data-ttu-id="32be2-502">程式碼</span><span class="sxs-lookup"><span data-stu-id="32be2-502">Code</span></span> | <span data-ttu-id="32be2-503">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-503">Description</span></span> | <span data-ttu-id="32be2-504">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-504">Behavior</span></span> |
|--------------|---------|--------------------------------------------------------|---------------------------------------------------------|
| <span data-ttu-id="32be2-505">ESC =</span><span class="sxs-lookup"><span data-stu-id="32be2-505">ESC =</span></span> | <span data-ttu-id="32be2-506">DECKPAM</span><span class="sxs-lookup"><span data-stu-id="32be2-506">DECKPAM</span></span> | <span data-ttu-id="32be2-507">啟用鍵盤應用程式模式</span><span class="sxs-lookup"><span data-stu-id="32be2-507">Enable Keypad Application Mode</span></span> | <span data-ttu-id="32be2-508">鍵盤按鍵會發出其應用程式模式序列。</span><span class="sxs-lookup"><span data-stu-id="32be2-508">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="32be2-509">ESC &gt;</span><span class="sxs-lookup"><span data-stu-id="32be2-509">ESC &gt;</span></span> | <span data-ttu-id="32be2-510">DECKPNM</span><span class="sxs-lookup"><span data-stu-id="32be2-510">DECKPNM</span></span> | <span data-ttu-id="32be2-511">啟用鍵盤數字模式</span><span class="sxs-lookup"><span data-stu-id="32be2-511">Enable Keypad Numeric Mode</span></span> | <span data-ttu-id="32be2-512">鍵盤按鍵會發出其數字模式序列。</span><span class="sxs-lookup"><span data-stu-id="32be2-512">Keypad keys will emit their Numeric Mode sequences.</span></span> |
| <span data-ttu-id="32be2-513">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="32be2-513">ESC \[ ?</span></span> <span data-ttu-id="32be2-514">1 小時</span><span class="sxs-lookup"><span data-stu-id="32be2-514">1 h</span></span> | <span data-ttu-id="32be2-515">DECCKM</span><span class="sxs-lookup"><span data-stu-id="32be2-515">DECCKM</span></span> | <span data-ttu-id="32be2-516">啟用游標按鍵應用程式模式</span><span class="sxs-lookup"><span data-stu-id="32be2-516">Enable Cursor Keys Application Mode</span></span> | <span data-ttu-id="32be2-517">鍵盤按鍵會發出其應用程式模式序列。</span><span class="sxs-lookup"><span data-stu-id="32be2-517">Keypad keys will emit their Application Mode sequences.</span></span> |
| <span data-ttu-id="32be2-518">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="32be2-518">ESC \[ ?</span></span> <span data-ttu-id="32be2-519">1 l</span><span class="sxs-lookup"><span data-stu-id="32be2-519">1 l</span></span> | <span data-ttu-id="32be2-520">DECCKM</span><span class="sxs-lookup"><span data-stu-id="32be2-520">DECCKM</span></span> | <span data-ttu-id="32be2-521">停用游標按鍵應用程式模式 (使用標準模式)</span><span class="sxs-lookup"><span data-stu-id="32be2-521">Disable Cursor Keys Application Mode (use Normal Mode)</span></span> | <span data-ttu-id="32be2-522">鍵盤按鍵會發出其數字模式序列。</span><span class="sxs-lookup"><span data-stu-id="32be2-522">Keypad keys will emit their Numeric Mode sequences.</span></span> |



## <a name="span-idquery_statespanspan-idquery_statespanspan-idquery_statespanquery-state"></a><span data-ttu-id="32be2-523"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>查詢狀態</span><span class="sxs-lookup"><span data-stu-id="32be2-523"><span id="Query_State"></span><span id="query_state"></span><span id="QUERY_STATE"></span>Query State</span></span>


<span data-ttu-id="32be2-524">本節中的所有命令通常等同於呼叫 Get\* 主控台 API，用於取得目前主控台緩衝區狀態的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="32be2-524">All commands in this section are generally equivalent to calling Get\* console APIs to retrieve status information about the current console buffer state.</span></span>

> [!NOTE]
><span data-ttu-id="32be2-525">若已設定 ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING，當這些查詢在輸出資料流上完成辨識後，就會立即將其回應發出至主控台輸入資料流。</span><span class="sxs-lookup"><span data-stu-id="32be2-525">These queries will emit their responses into the console input stream immediately after being recognized on the output stream while ENABLE\_VIRTUAL\_TERMINAL\_PROCESSING is set.</span></span> <span data-ttu-id="32be2-526">ENABLE\_VIRTUAL\_TERMINAL\_INPUT 旗標不會套用至查詢命令，因為已假設執行查詢的應用程式一律要收到回覆。</span><span class="sxs-lookup"><span data-stu-id="32be2-526">The ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag does not apply to query commands as it is assumed that an application making the query will always want to receive the reply.</span></span>




| <span data-ttu-id="32be2-527">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-527">Sequence</span></span> | <span data-ttu-id="32be2-528">程式碼</span><span class="sxs-lookup"><span data-stu-id="32be2-528">Code</span></span> | <span data-ttu-id="32be2-529">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-529">Description</span></span> | <span data-ttu-id="32be2-530">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-530">Behavior</span></span> |
|------------|---------|------------------------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="32be2-531">ESC \[ 6 n</span><span class="sxs-lookup"><span data-stu-id="32be2-531">ESC \[ 6 n</span></span> | <span data-ttu-id="32be2-532">DECXCPR</span><span class="sxs-lookup"><span data-stu-id="32be2-532">DECXCPR</span></span> | <span data-ttu-id="32be2-533">回報游標位置</span><span class="sxs-lookup"><span data-stu-id="32be2-533">Report Cursor Position</span></span> | <span data-ttu-id="32be2-534">將游標位置發出為：ESC \[ &lt;r&gt; ; &lt;c&gt; R，其中 &lt;R&gt; = 游標資料列，而 &lt;c&gt; = 游標資料行</span><span class="sxs-lookup"><span data-stu-id="32be2-534">Emit the cursor position as: ESC \[ &lt;r&gt; ; &lt;c&gt; R Where &lt;r&gt; = cursor row and &lt;c&gt; = cursor column</span></span> |
| <span data-ttu-id="32be2-535">ESC \[ 0 c</span><span class="sxs-lookup"><span data-stu-id="32be2-535">ESC \[ 0 c</span></span> | <span data-ttu-id="32be2-536">DA</span><span class="sxs-lookup"><span data-stu-id="32be2-536">DA</span></span> | <span data-ttu-id="32be2-537">裝置屬性</span><span class="sxs-lookup"><span data-stu-id="32be2-537">Device Attributes</span></span> | <span data-ttu-id="32be2-538">回報終端機身分識別。</span><span class="sxs-lookup"><span data-stu-id="32be2-538">Report the terminal identity.</span></span> <span data-ttu-id="32be2-539">將會發出 “\\x1b\[?1;0c”，指出「沒有選項的 VT101」。</span><span class="sxs-lookup"><span data-stu-id="32be2-539">Will emit “\\x1b\[?1;0c”, indicating "VT101 with No Options".</span></span> |



## <a name="span-idtabsspanspan-idtabsspanspan-idtabsspantabs"></a><span data-ttu-id="32be2-540"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tab</span><span class="sxs-lookup"><span data-stu-id="32be2-540"><span id="Tabs"></span><span id="tabs"></span><span id="TABS"></span>Tabs</span></span>


<span data-ttu-id="32be2-541">雖然視窗主控台在傳統上預期 Tab 會是專屬的八個字元寬，但使用特定序列的 \*nix 應用程式可以操控主控台視窗中 Tab 停止的位置，以最佳化應用程式的游標移動。</span><span class="sxs-lookup"><span data-stu-id="32be2-541">While the windows console traditionally expects tabs to be exclusively eight characters wide, \*nix applications utilizing certain sequences can manipulate where the tab stops are within the console windows to optimize cursor movement by the application.</span></span>

<span data-ttu-id="32be2-542">下列序列可讓應用程式設定主控台視窗中 Tab 的停止位置、將這些位置移除，以及在這些位置之間瀏覽。</span><span class="sxs-lookup"><span data-stu-id="32be2-542">The following sequences allow an application to set the tab stop locations within the console window, remove them, and navigate between them.</span></span>


| <span data-ttu-id="32be2-543">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-543">Sequence</span></span> | <span data-ttu-id="32be2-544">程式碼</span><span class="sxs-lookup"><span data-stu-id="32be2-544">Code</span></span> | <span data-ttu-id="32be2-545">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-545">Description</span></span> | <span data-ttu-id="32be2-546">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-546">Behavior</span></span> |
|--------------------|------|---------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="32be2-547">ESC H</span><span class="sxs-lookup"><span data-stu-id="32be2-547">ESC H</span></span> | <span data-ttu-id="32be2-548">HTS</span><span class="sxs-lookup"><span data-stu-id="32be2-548">HTS</span></span> | <span data-ttu-id="32be2-549">水平 Tab 設定</span><span class="sxs-lookup"><span data-stu-id="32be2-549">Horizontal Tab Set</span></span> | <span data-ttu-id="32be2-550">在游標所在的目前資料行中設定 Tab 停止點。</span><span class="sxs-lookup"><span data-stu-id="32be2-550">Sets a tab stop in the current column the cursor is in.</span></span> |
| <span data-ttu-id="32be2-551">ESC \[ &lt;n&gt; I</span><span class="sxs-lookup"><span data-stu-id="32be2-551">ESC \[ &lt;n&gt; I</span></span> | <span data-ttu-id="32be2-552">CHT</span><span class="sxs-lookup"><span data-stu-id="32be2-552">CHT</span></span> | <span data-ttu-id="32be2-553">游標水平 (向前) Tab</span><span class="sxs-lookup"><span data-stu-id="32be2-553">Cursor Horizontal (Forward) Tab</span></span> | <span data-ttu-id="32be2-554">使游標前進至下一個資料行 (在相同的資料列中)，並使用 Tab 停止點。</span><span class="sxs-lookup"><span data-stu-id="32be2-554">Advance the cursor to the next column (in the same row) with a tab stop.</span></span> <span data-ttu-id="32be2-555">如果不再有 Tab 停止點，則移至資料列中的最後一個資料行。</span><span class="sxs-lookup"><span data-stu-id="32be2-555">If there are no more tab stops, move to the last column in the row.</span></span> <span data-ttu-id="32be2-556">如果游標在最後一個資料行中，則移至下一個資料列的第一個資料行。</span><span class="sxs-lookup"><span data-stu-id="32be2-556">If the cursor is in the last column, move to the first column of the next row.</span></span> |
| <span data-ttu-id="32be2-557">ESC \[ &lt;n&gt; Z</span><span class="sxs-lookup"><span data-stu-id="32be2-557">ESC \[ &lt;n&gt; Z</span></span> | <span data-ttu-id="32be2-558">CBT</span><span class="sxs-lookup"><span data-stu-id="32be2-558">CBT</span></span> | <span data-ttu-id="32be2-559">游標向後 Tab</span><span class="sxs-lookup"><span data-stu-id="32be2-559">Cursor Backwards Tab</span></span> | <span data-ttu-id="32be2-560">使游標移至上一個資料行 (在相同的資料列中)，並使用 Tab 停止點。</span><span class="sxs-lookup"><span data-stu-id="32be2-560">Move the cursor to the previous column (in the same row) with a tab stop.</span></span> <span data-ttu-id="32be2-561">如果不再有 Tab 停止點，則將游標移至第一個資料行。</span><span class="sxs-lookup"><span data-stu-id="32be2-561">If there are no more tab stops, moves the cursor to the first column.</span></span> <span data-ttu-id="32be2-562">如果游標在第一個資料行中，則不移動游標。</span><span class="sxs-lookup"><span data-stu-id="32be2-562">If the cursor is in the first column, doesn’t move the cursor.</span></span> |
| <span data-ttu-id="32be2-563">ESC \[ 0 g</span><span class="sxs-lookup"><span data-stu-id="32be2-563">ESC \[ 0 g</span></span> | <span data-ttu-id="32be2-564">TBC</span><span class="sxs-lookup"><span data-stu-id="32be2-564">TBC</span></span> | <span data-ttu-id="32be2-565">Tab 清除 (目前的資料行)</span><span class="sxs-lookup"><span data-stu-id="32be2-565">Tab Clear (current column)</span></span> | <span data-ttu-id="32be2-566">清除目前資料行中的 Tab 停止點 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="32be2-566">Clears the tab stop in the current column, if there is one.</span></span> <span data-ttu-id="32be2-567">沒有的話，則不會執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="32be2-567">Otherwise does nothing.</span></span> |
| <span data-ttu-id="32be2-568">ESC \[ 3 g</span><span class="sxs-lookup"><span data-stu-id="32be2-568">ESC \[ 3 g</span></span> | <span data-ttu-id="32be2-569">TBC</span><span class="sxs-lookup"><span data-stu-id="32be2-569">TBC</span></span> | <span data-ttu-id="32be2-570">Tab 清除 (所有資料行)</span><span class="sxs-lookup"><span data-stu-id="32be2-570">Tab Clear (all columns)</span></span> | <span data-ttu-id="32be2-571">清除所有目前設定的 Tab 停止點。</span><span class="sxs-lookup"><span data-stu-id="32be2-571">Clears all currently set tab stops.</span></span> |



- <span data-ttu-id="32be2-572">對於 CHT 和 CBT，&lt;n&gt; 是選擇性參數 (預設值 = 1)，表示要讓游標在指定的方向前進多少次。</span><span class="sxs-lookup"><span data-stu-id="32be2-572">For both CHT and CBT, &lt;n&gt; is an optional parameter that (default=1) indicating how many times to advance the cursor in the specified direction.</span></span>
- <span data-ttu-id="32be2-573">如果沒有透過 HTS 設定的 Tab 停止點，CHT 和 CBT 會將視窗的第一個和最後一個資料行視為唯一的兩個 Tab 停止點。</span><span class="sxs-lookup"><span data-stu-id="32be2-573">If there are no tab stops set via HTS, CHT and CBT will treat the first and last columns of the window as the only two tab stops.</span></span>
- <span data-ttu-id="32be2-574">使用 HTS 設定 Tab 停止點也會讓主控台瀏覽至 TAB (0x09, ‘\\t’) 字元輸出上的下一個 Tab 停止點，其方式與 CHT 相同。</span><span class="sxs-lookup"><span data-stu-id="32be2-574">Using HTS to set a tab stop will also cause the console to navigate to the next tab stop on the output of a TAB (0x09, ‘\\t’) character, in the same manner as CHT.</span></span>

## <a name="span-iddesignate_character_setspanspan-iddesignate_character_setspanspan-iddesignate_character_setspandesignate-character-set"></a><span data-ttu-id="32be2-575"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>指定字元集</span><span class="sxs-lookup"><span data-stu-id="32be2-575"><span id="Designate_Character_Set"></span><span id="designate_character_set"></span><span id="DESIGNATE_CHARACTER_SET"></span>Designate Character Set</span></span>


<span data-ttu-id="32be2-576">下列序列可讓程式變更作用中字元集的對應。</span><span class="sxs-lookup"><span data-stu-id="32be2-576">The following sequences allow a program to change the active character set mapping.</span></span> <span data-ttu-id="32be2-577">這可讓程式發出 7 位元的 ASCII 字元，但會在終端機畫面本身將其顯示為其他字符。</span><span class="sxs-lookup"><span data-stu-id="32be2-577">This allows a program to emit 7-bit ASCII characters, but have them displayed as other glyphs on the terminal screen itself.</span></span> <span data-ttu-id="32be2-578">目前唯一支援的兩個字元集是 ASCII (預設值) 和 DEC 特殊圖形字元集。</span><span class="sxs-lookup"><span data-stu-id="32be2-578">Currently, the only two supported character sets are ASCII (default) and the DEC Special Graphics Character Set.</span></span> <span data-ttu-id="32be2-579">如需 DEC 特殊圖形字元集所代表的所有字元清單，請參閱 <http://vt100.net/docs/vt220-rm/table2-4.html>。</span><span class="sxs-lookup"><span data-stu-id="32be2-579">See <http://vt100.net/docs/vt220-rm/table2-4.html> for a listing of all of the characters represented by the DEC Special Graphics Character Set.</span></span>


| <span data-ttu-id="32be2-580">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-580">Sequence</span></span> | <span data-ttu-id="32be2-581">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-581">Description</span></span> | <span data-ttu-id="32be2-582">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-582">Behavior</span></span> |
|----------|--------------------------------------------|-------------------------------|
| <span data-ttu-id="32be2-583">ESC ( 0</span><span class="sxs-lookup"><span data-stu-id="32be2-583">ESC ( 0</span></span> | <span data-ttu-id="32be2-584">指定字元集 – DEC 線條繪圖</span><span class="sxs-lookup"><span data-stu-id="32be2-584">Designate Character Set – DEC Line Drawing</span></span> | <span data-ttu-id="32be2-585">啟用 DEC 線條繪圖模式</span><span class="sxs-lookup"><span data-stu-id="32be2-585">Enables DEC Line Drawing Mode</span></span> |
| <span data-ttu-id="32be2-586">ESC ( B</span><span class="sxs-lookup"><span data-stu-id="32be2-586">ESC ( B</span></span> | <span data-ttu-id="32be2-587">指定字元集 – US ASCII</span><span class="sxs-lookup"><span data-stu-id="32be2-587">Designate Character Set – US ASCII</span></span> | <span data-ttu-id="32be2-588">啟用 ASCII 模式 (預設值)</span><span class="sxs-lookup"><span data-stu-id="32be2-588">Enables ASCII Mode (Default)</span></span> |



<span data-ttu-id="32be2-589">值得注意的是，DEC 線條繪圖模式會用來在主控台應用程式中繪製框線。</span><span class="sxs-lookup"><span data-stu-id="32be2-589">Notably, the DEC Line Drawing mode is used for drawing borders in console applications.</span></span> <span data-ttu-id="32be2-590">下表顯示 ASCII 字元與線條繪圖字元的對應。</span><span class="sxs-lookup"><span data-stu-id="32be2-590">The following table shows what ASCII character maps to which line drawing character.</span></span>


| <span data-ttu-id="32be2-591">Hex</span><span class="sxs-lookup"><span data-stu-id="32be2-591">Hex</span></span> | <span data-ttu-id="32be2-592">ASCII</span><span class="sxs-lookup"><span data-stu-id="32be2-592">ASCII</span></span> | <span data-ttu-id="32be2-593">DEC 線條繪圖</span><span class="sxs-lookup"><span data-stu-id="32be2-593">DEC Line Drawing</span></span> |
|------|-------|------------------|
| <span data-ttu-id="32be2-594">0x6a</span><span class="sxs-lookup"><span data-stu-id="32be2-594">0x6a</span></span> | <span data-ttu-id="32be2-595">j</span><span class="sxs-lookup"><span data-stu-id="32be2-595">j</span></span> | <span data-ttu-id="32be2-596">┘</span><span class="sxs-lookup"><span data-stu-id="32be2-596">┘</span></span> |
| <span data-ttu-id="32be2-597">0x6b</span><span class="sxs-lookup"><span data-stu-id="32be2-597">0x6b</span></span> | <span data-ttu-id="32be2-598">k</span><span class="sxs-lookup"><span data-stu-id="32be2-598">k</span></span> | <span data-ttu-id="32be2-599">┐</span><span class="sxs-lookup"><span data-stu-id="32be2-599">┐</span></span> |
| <span data-ttu-id="32be2-600">0x6c</span><span class="sxs-lookup"><span data-stu-id="32be2-600">0x6c</span></span> | <span data-ttu-id="32be2-601">l</span><span class="sxs-lookup"><span data-stu-id="32be2-601">l</span></span> | <span data-ttu-id="32be2-602">┌</span><span class="sxs-lookup"><span data-stu-id="32be2-602">┌</span></span> |
| <span data-ttu-id="32be2-603">0x6d</span><span class="sxs-lookup"><span data-stu-id="32be2-603">0x6d</span></span> | <span data-ttu-id="32be2-604">m</span><span class="sxs-lookup"><span data-stu-id="32be2-604">m</span></span> | <span data-ttu-id="32be2-605">└</span><span class="sxs-lookup"><span data-stu-id="32be2-605">└</span></span> |
| <span data-ttu-id="32be2-606">0x6e</span><span class="sxs-lookup"><span data-stu-id="32be2-606">0x6e</span></span> | <span data-ttu-id="32be2-607">n</span><span class="sxs-lookup"><span data-stu-id="32be2-607">n</span></span> | <span data-ttu-id="32be2-608">┼</span><span class="sxs-lookup"><span data-stu-id="32be2-608">┼</span></span> |
| <span data-ttu-id="32be2-609">0x71</span><span class="sxs-lookup"><span data-stu-id="32be2-609">0x71</span></span> | <span data-ttu-id="32be2-610">q</span><span class="sxs-lookup"><span data-stu-id="32be2-610">q</span></span> | <span data-ttu-id="32be2-611">─</span><span class="sxs-lookup"><span data-stu-id="32be2-611">─</span></span> |
| <span data-ttu-id="32be2-612">0x74</span><span class="sxs-lookup"><span data-stu-id="32be2-612">0x74</span></span> | <span data-ttu-id="32be2-613">t</span><span class="sxs-lookup"><span data-stu-id="32be2-613">t</span></span> | <span data-ttu-id="32be2-614">├</span><span class="sxs-lookup"><span data-stu-id="32be2-614">├</span></span> |
| <span data-ttu-id="32be2-615">0x75</span><span class="sxs-lookup"><span data-stu-id="32be2-615">0x75</span></span> | <span data-ttu-id="32be2-616">u</span><span class="sxs-lookup"><span data-stu-id="32be2-616">u</span></span> | <span data-ttu-id="32be2-617">┤</span><span class="sxs-lookup"><span data-stu-id="32be2-617">┤</span></span> |
| <span data-ttu-id="32be2-618">0x76</span><span class="sxs-lookup"><span data-stu-id="32be2-618">0x76</span></span> | <span data-ttu-id="32be2-619">v</span><span class="sxs-lookup"><span data-stu-id="32be2-619">v</span></span> | <span data-ttu-id="32be2-620">┴</span><span class="sxs-lookup"><span data-stu-id="32be2-620">┴</span></span> |
| <span data-ttu-id="32be2-621">0x77</span><span class="sxs-lookup"><span data-stu-id="32be2-621">0x77</span></span> | <span data-ttu-id="32be2-622">w</span><span class="sxs-lookup"><span data-stu-id="32be2-622">w</span></span> | <span data-ttu-id="32be2-623">┬</span><span class="sxs-lookup"><span data-stu-id="32be2-623">┬</span></span> |
| <span data-ttu-id="32be2-624">0x78</span><span class="sxs-lookup"><span data-stu-id="32be2-624">0x78</span></span> | <span data-ttu-id="32be2-625">x</span><span class="sxs-lookup"><span data-stu-id="32be2-625">x</span></span> | <span data-ttu-id="32be2-626">│</span><span class="sxs-lookup"><span data-stu-id="32be2-626">│</span></span> |




## <a name="span-idscrolling_marginsspanspan-idscrolling_marginsspanspan-idscrolling_marginsspanscrolling-margins"></a><span data-ttu-id="32be2-627"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>捲動邊界</span><span class="sxs-lookup"><span data-stu-id="32be2-627"><span id="Scrolling_Margins"></span><span id="scrolling_margins"></span><span id="SCROLLING_MARGINS"></span>Scrolling Margins</span></span>


<span data-ttu-id="32be2-628">下列序列可讓程式設定受到捲動作業影響的畫面「捲動區域」。</span><span class="sxs-lookup"><span data-stu-id="32be2-628">The following sequences allow a program to configure the “scrolling region” of the screen that is affected by scrolling operations.</span></span> <span data-ttu-id="32be2-629">這是資料列的子集，會在畫面以其他方式捲動 (例如 ‘\\n’ 或 RI) 時進行調整。</span><span class="sxs-lookup"><span data-stu-id="32be2-629">This is a subset of the rows that are adjusted when the screen would otherwise scroll, for example, on a ‘\\n’ or RI.</span></span> <span data-ttu-id="32be2-630">這些邊界也會影響插入行 (IL) 和刪除行 (DL) 及向上捲動 (SU) 和向下捲動 (SD) 所修改的資料列。</span><span class="sxs-lookup"><span data-stu-id="32be2-630">These margins also affect the rows modified by Insert Line (IL) and Delete Line (DL), Scroll Up (SU) and Scroll Down (SD).</span></span>

<span data-ttu-id="32be2-631">如果畫面有個部分不會在畫面其餘部分填滿時捲動，例如應用程式頂端有標題列或底部有狀態列，則特別適用捲動邊界。</span><span class="sxs-lookup"><span data-stu-id="32be2-631">The scrolling margins can be especially useful for having a portion of the screen that doesn’t scroll when the rest of the screen is filled, such as having a title bar at the top or a status bar at the bottom of your application.</span></span>

<span data-ttu-id="32be2-632">DECSTBM 有兩個選擇性參數：&lt;t&gt; 和 &lt;b&gt;，可用來指定代表捲動區域頂端和底部幾行的資料列 (含)。</span><span class="sxs-lookup"><span data-stu-id="32be2-632">For DECSTBM, there are two optional parameters, &lt;t&gt; and &lt;b&gt;, which are used to specify the rows that represent the top and bottom lines of the scroll region, inclusive.</span></span> <span data-ttu-id="32be2-633">如果省略參數，&lt;t&gt; 會預設為1，而 &lt;b&gt; 會預設為目前檢視區的高度。</span><span class="sxs-lookup"><span data-stu-id="32be2-633">If the parameters are omitted, &lt;t&gt; defaults to 1 and &lt;b&gt; defaults to the current viewport height.</span></span>

<span data-ttu-id="32be2-634">捲動邊界是為每個緩衝區設定的，所以很重要的是，替代緩衝區和主要緩衝區會維持不同的捲動邊界設定 (因此，替代緩衝區中的全畫面應用程式不會妨礙到主要緩衝區的邊界)。</span><span class="sxs-lookup"><span data-stu-id="32be2-634">Scrolling margins are per-buffer, so importantly, the Alternate Buffer and Main Buffer maintain separate scrolling margins settings (so a full screen application in the alternate buffer will not poison the main buffer’s margins).</span></span>


| <span data-ttu-id="32be2-635">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-635">Sequence</span></span> | <span data-ttu-id="32be2-636">程式碼</span><span class="sxs-lookup"><span data-stu-id="32be2-636">Code</span></span> | <span data-ttu-id="32be2-637">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-637">Description</span></span> | <span data-ttu-id="32be2-638">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-638">Behavior</span></span> |
|--------------------------------|---------|----------------------|------------------------------------------------|
| <span data-ttu-id="32be2-639">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span><span class="sxs-lookup"><span data-stu-id="32be2-639">ESC \[ &lt;t&gt; ; &lt;b&gt; r</span></span> | <span data-ttu-id="32be2-640">DECSTBM</span><span class="sxs-lookup"><span data-stu-id="32be2-640">DECSTBM</span></span> | <span data-ttu-id="32be2-641">設定捲動區域</span><span class="sxs-lookup"><span data-stu-id="32be2-641">Set Scrolling Region</span></span> | <span data-ttu-id="32be2-642">設定檢視區的 VT 捲動邊界。</span><span class="sxs-lookup"><span data-stu-id="32be2-642">Sets the VT scrolling margins of the viewport.</span></span> |



## <a name="span-idwindow_titlespanspan-idwindow_titlespanspan-idwindow_titlespanwindow-title"></a><span data-ttu-id="32be2-643"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>視窗標題</span><span class="sxs-lookup"><span data-stu-id="32be2-643"><span id="Window_Title"></span><span id="window_title"></span><span id="WINDOW_TITLE"></span>Window Title</span></span>


<span data-ttu-id="32be2-644">下列命令可讓應用程式將主控台視窗的標題設定為指定的 &lt;字串&gt; 參數。</span><span class="sxs-lookup"><span data-stu-id="32be2-644">The following commands allows the application to set the title of the console window to the given &lt;string&gt; parameter.</span></span> <span data-ttu-id="32be2-645">字串必須小於 255 個字元才能被接受。</span><span class="sxs-lookup"><span data-stu-id="32be2-645">The string must be less than 255 characters to be accepted.</span></span> <span data-ttu-id="32be2-646">這相當於以指定字串呼叫 SetConsoleTitle。</span><span class="sxs-lookup"><span data-stu-id="32be2-646">This is equivalent to calling SetConsoleTitle with the given string.</span></span>

<span data-ttu-id="32be2-647">請注意，這些序列是 OSC (作業系統命令) 序列，而不是類似於列出許多其他序列的 CSI，因此開頭為 "\\x1b\]"，而不是 "\\x1b\["。</span><span class="sxs-lookup"><span data-stu-id="32be2-647">Note that these sequences are OSC “Operating system command” sequences, and not a CSI like many of the other sequences listed, and as such starts with “\\x1b\]”, not “\\x1b\[”.</span></span>


| <span data-ttu-id="32be2-648">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-648">Sequence</span></span> | <span data-ttu-id="32be2-649">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-649">Description</span></span> | <span data-ttu-id="32be2-650">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-650">Behavior</span></span> |
|-------------------------------|---------------------------|----------------------------------------------------|
| <span data-ttu-id="32be2-651">ESC \] 0 ; &lt;字串&gt; BEL</span><span class="sxs-lookup"><span data-stu-id="32be2-651">ESC \] 0 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="32be2-652">設定圖示和視窗標題</span><span class="sxs-lookup"><span data-stu-id="32be2-652">Set Icon and Window Title</span></span> | <span data-ttu-id="32be2-653">將主控台視窗的標題設定為 &lt;字串&gt;。</span><span class="sxs-lookup"><span data-stu-id="32be2-653">Sets the console window’s title to &lt;string&gt;.</span></span> |
| <span data-ttu-id="32be2-654">ESC \] 2 ; &lt;字串&gt; BEL</span><span class="sxs-lookup"><span data-stu-id="32be2-654">ESC \] 2 ; &lt;string&gt; BEL</span></span> | <span data-ttu-id="32be2-655">設定 Window 標題</span><span class="sxs-lookup"><span data-stu-id="32be2-655">Set Window Title</span></span> | <span data-ttu-id="32be2-656">將主控台視窗的標題設定為 &lt;字串&gt;。</span><span class="sxs-lookup"><span data-stu-id="32be2-656">Sets the console window’s title to &lt;string&gt;.</span></span> |



<span data-ttu-id="32be2-657">此處的終止字元是 “Bell” 字元：‘\\x07’</span><span class="sxs-lookup"><span data-stu-id="32be2-657">The terminating character here is the “Bell” character, ‘\\x07’</span></span>

## <a name="span-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanspan-idalternate_screen_buffer__spanalternate-screen-buffer"></a><span data-ttu-id="32be2-658"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>替代畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="32be2-658"><span id="Alternate_Screen_Buffer__"></span><span id="alternate_screen_buffer__"></span><span id="ALTERNATE_SCREEN_BUFFER__"></span>Alternate Screen Buffer</span></span>


<span data-ttu-id="32be2-659">\*Nix 樣式應用程式通常會使用替代畫面緩衝區，讓其可修改緩衝區的完整內容，而不會影響到將其啟動的應用程式。</span><span class="sxs-lookup"><span data-stu-id="32be2-659">\*Nix style applications often utilize an alternate screen buffer, so that they can modify the entire contents of the buffer, without affecting the application that started them.</span></span> <span data-ttu-id="32be2-660">替代緩衝區完全是視窗的維度，沒有任何回捲區域。</span><span class="sxs-lookup"><span data-stu-id="32be2-660">The alternate buffer is exactly the dimensions of the window, without any scrollback region.</span></span>

<span data-ttu-id="32be2-661">如需此行為的範例，請考慮從 bash 啟動 Vim 的時機。</span><span class="sxs-lookup"><span data-stu-id="32be2-661">For an example of this behavior, consider when vim is launched from bash.</span></span> <span data-ttu-id="32be2-662">Vim 會使用整個畫面來編輯檔案，然後返回 bash 會讓原始緩衝區保持不變。</span><span class="sxs-lookup"><span data-stu-id="32be2-662">Vim uses the entirety of the screen to edit the file, then returning to bash leaves the original buffer unchanged.</span></span>


| <span data-ttu-id="32be2-663">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-663">Sequence</span></span> | <span data-ttu-id="32be2-664">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-664">Description</span></span> | <span data-ttu-id="32be2-665">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-665">Behavior</span></span> |
|--------------------|-----------------------------|--------------------------------------------|
| <span data-ttu-id="32be2-666">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="32be2-666">ESC \[ ?</span></span> <span data-ttu-id="32be2-667">1 0 4 9 h</span><span class="sxs-lookup"><span data-stu-id="32be2-667">1 0 4 9 h</span></span> | <span data-ttu-id="32be2-668">使用替代畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="32be2-668">Use Alternate Screen Buffer</span></span> | <span data-ttu-id="32be2-669">切換至新的替代畫面緩衝區。</span><span class="sxs-lookup"><span data-stu-id="32be2-669">Switches to a new alternate screen buffer.</span></span> |
| <span data-ttu-id="32be2-670">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="32be2-670">ESC \[ ?</span></span> <span data-ttu-id="32be2-671">1 0 4 9 l</span><span class="sxs-lookup"><span data-stu-id="32be2-671">1 0 4 9 l</span></span> | <span data-ttu-id="32be2-672">使用主要畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="32be2-672">Use Main Screen Buffer</span></span> | <span data-ttu-id="32be2-673">切換至主要緩衝區。</span><span class="sxs-lookup"><span data-stu-id="32be2-673">Switches to the main buffer.</span></span> |



## <a name="span-idwindow_widthspanspan-idwindow_widthspanspan-idwindow_widthspanwindow-width"></a><span data-ttu-id="32be2-674"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>視窗寬度</span><span class="sxs-lookup"><span data-stu-id="32be2-674"><span id="Window_Width"></span><span id="window_width"></span><span id="WINDOW_WIDTH"></span>Window Width</span></span>


<span data-ttu-id="32be2-675">您可以使用下列序列來控制主控台視窗的寬度。</span><span class="sxs-lookup"><span data-stu-id="32be2-675">The following sequences can be used to control the width of the console window.</span></span> <span data-ttu-id="32be2-676">這些序列大致等同於呼叫 SetConsoleScreenBufferInfoEx 主控台 API 來設定視窗寬度。</span><span class="sxs-lookup"><span data-stu-id="32be2-676">They are roughly equivalent to the calling the SetConsoleScreenBufferInfoEx console API to set the window width.</span></span>


| <span data-ttu-id="32be2-677">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-677">Sequence</span></span> | <span data-ttu-id="32be2-678">程式碼</span><span class="sxs-lookup"><span data-stu-id="32be2-678">Code</span></span> | <span data-ttu-id="32be2-679">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-679">Description</span></span> | <span data-ttu-id="32be2-680">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-680">Behavior</span></span> |
|--------------|---------|------------------------------|---------------------------------------------|
| <span data-ttu-id="32be2-681">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="32be2-681">ESC \[ ?</span></span> <span data-ttu-id="32be2-682">3 h</span><span class="sxs-lookup"><span data-stu-id="32be2-682">3 h</span></span> | <span data-ttu-id="32be2-683">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="32be2-683">DECCOLM</span></span> | <span data-ttu-id="32be2-684">將資料行數目設定為 132</span><span class="sxs-lookup"><span data-stu-id="32be2-684">Set Number of Columns to 132</span></span> | <span data-ttu-id="32be2-685">將主控台寬度設定為 132 個資料行寬。</span><span class="sxs-lookup"><span data-stu-id="32be2-685">Sets the console width to 132 columns wide.</span></span> |
| <span data-ttu-id="32be2-686">ESC \[ ?</span><span class="sxs-lookup"><span data-stu-id="32be2-686">ESC \[ ?</span></span> <span data-ttu-id="32be2-687">3 l</span><span class="sxs-lookup"><span data-stu-id="32be2-687">3 l</span></span> | <span data-ttu-id="32be2-688">DECCOLM</span><span class="sxs-lookup"><span data-stu-id="32be2-688">DECCOLM</span></span> | <span data-ttu-id="32be2-689">將資料行數目設定為 80</span><span class="sxs-lookup"><span data-stu-id="32be2-689">Set Number of Columns to 80</span></span> | <span data-ttu-id="32be2-690">將主控台寬度設定為 80 個資料行寬。</span><span class="sxs-lookup"><span data-stu-id="32be2-690">Sets the console width to 80 columns wide.</span></span> |



## <a name="span-idsoft_resetspanspan-idsoft_resetspanspan-idsoft_resetspansoft-reset"></a><span data-ttu-id="32be2-691"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>軟重設</span><span class="sxs-lookup"><span data-stu-id="32be2-691"><span id="Soft_Reset"></span><span id="soft_reset"></span><span id="SOFT_RESET"></span>Soft Reset</span></span>


<span data-ttu-id="32be2-692">您可以使用下列序列將某些屬性重設為預設值。下列屬性會重設為下列預設值 (也會列出控制這些屬性的序列)：</span><span class="sxs-lookup"><span data-stu-id="32be2-692">The following sequence can be used to reset certain properties to their default values.The following properties are reset to the following default values (also listed are the sequences that control those properties):</span></span>

- <span data-ttu-id="32be2-693">游標可見度：可見 (DECTEM)</span><span class="sxs-lookup"><span data-stu-id="32be2-693">Cursor visibility: visible (DECTEM)</span></span>
- <span data-ttu-id="32be2-694">數字鍵盤：數字模式 (DECNKM)</span><span class="sxs-lookup"><span data-stu-id="32be2-694">Numeric Keypad: Numeric Mode (DECNKM)</span></span>
- <span data-ttu-id="32be2-695">游標按鍵模式：標準模式 (DECCKM)</span><span class="sxs-lookup"><span data-stu-id="32be2-695">Cursor Keys Mode: Normal Mode (DECCKM)</span></span>
- <span data-ttu-id="32be2-696">頂端和底部邊界：頂端 = 1、底端 = 主控台高度 (DECSTBM)</span><span class="sxs-lookup"><span data-stu-id="32be2-696">Top and Bottom Margins: Top=1, Bottom=Console height (DECSTBM)</span></span>
- <span data-ttu-id="32be2-697">字元集：US ASCII</span><span class="sxs-lookup"><span data-stu-id="32be2-697">Character Set: US ASCII</span></span>
- <span data-ttu-id="32be2-698">圖形轉譯：預設/關閉 (SGR)</span><span class="sxs-lookup"><span data-stu-id="32be2-698">Graphics Rendition: Default/Off (SGR)</span></span>
- <span data-ttu-id="32be2-699">儲存游標狀態：首頁位置 (0,0) (DECSC)</span><span class="sxs-lookup"><span data-stu-id="32be2-699">Save cursor state: Home position (0,0) (DECSC)</span></span>


| <span data-ttu-id="32be2-700">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-700">Sequence</span></span> | <span data-ttu-id="32be2-701">程式碼</span><span class="sxs-lookup"><span data-stu-id="32be2-701">Code</span></span> | <span data-ttu-id="32be2-702">描述</span><span class="sxs-lookup"><span data-stu-id="32be2-702">Description</span></span> | <span data-ttu-id="32be2-703">行為</span><span class="sxs-lookup"><span data-stu-id="32be2-703">Behavior</span></span> |
|------------|--------|-------------|----------------------------------------------------|
| <span data-ttu-id="32be2-704">ESC \[ !</span><span class="sxs-lookup"><span data-stu-id="32be2-704">ESC \[ !</span></span> <span data-ttu-id="32be2-705">p</span><span class="sxs-lookup"><span data-stu-id="32be2-705">p</span></span> | <span data-ttu-id="32be2-706">DECSTR</span><span class="sxs-lookup"><span data-stu-id="32be2-706">DECSTR</span></span> | <span data-ttu-id="32be2-707">軟重設</span><span class="sxs-lookup"><span data-stu-id="32be2-707">Soft Reset</span></span> | <span data-ttu-id="32be2-708">將特定的終端機設定重設為預設值。</span><span class="sxs-lookup"><span data-stu-id="32be2-708">Reset certain terminal settings to their defaults.</span></span> |



## <a name="span-idinput_sequencesspanspan-idinput_sequencesspanspan-idinput_sequencesspaninput-sequences"></a><span data-ttu-id="32be2-709"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>輸入序列</span><span class="sxs-lookup"><span data-stu-id="32be2-709"><span id="Input_Sequences"></span><span id="input_sequences"></span><span id="INPUT_SEQUENCES"></span>Input Sequences</span></span>


<span data-ttu-id="32be2-710">如果使用 SetConsoleMode 旗標在輸入緩衝區控制代碼上設定 ENABLE\_VIRTUAL\_TERMINAL\_INPUT 旗標，則主控台主機會在輸入資料流上發出下列終端機序列。</span><span class="sxs-lookup"><span data-stu-id="32be2-710">The following terminal sequences are emitted by the console host on the input stream if the ENABLE\_VIRTUAL\_TERMINAL\_INPUT flag is set on the input buffer handle using the SetConsoleMode flag.</span></span>

<span data-ttu-id="32be2-711">有兩種內部模式可控制針對指定輸入鍵發出的序列：游標按鍵模式和鍵盤按鍵模式。</span><span class="sxs-lookup"><span data-stu-id="32be2-711">There are two internal modes that control which sequences are emitted for the given input keys, the Cursor Keys Mode and the Keypad Keys Mode.</span></span> <span data-ttu-id="32be2-712">這會在 [模式變更] 區段中加以說明。</span><span class="sxs-lookup"><span data-stu-id="32be2-712">These are described in the Mode Changes section.</span></span>

### <a name="span-idcursor_keys__spanspan-idcursor_keys__spanspan-idcursor_keys__spancursor-keys"></a><span data-ttu-id="32be2-713"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>游標按鍵</span><span class="sxs-lookup"><span data-stu-id="32be2-713"><span id="Cursor_Keys__"></span><span id="cursor_keys__"></span><span id="CURSOR_KEYS__"></span>Cursor Keys</span></span>


| <span data-ttu-id="32be2-714">答案</span><span class="sxs-lookup"><span data-stu-id="32be2-714">Key</span></span> | <span data-ttu-id="32be2-715">正常模式</span><span class="sxs-lookup"><span data-stu-id="32be2-715">Normal Mode</span></span> | <span data-ttu-id="32be2-716">應用程式模式</span><span class="sxs-lookup"><span data-stu-id="32be2-716">Application Mode</span></span> |
|-------------|-------------|------------------|
| <span data-ttu-id="32be2-717">向上箭號</span><span class="sxs-lookup"><span data-stu-id="32be2-717">Up Arrow</span></span> | <span data-ttu-id="32be2-718">ESC \[ A</span><span class="sxs-lookup"><span data-stu-id="32be2-718">ESC \[ A</span></span> | <span data-ttu-id="32be2-719">ESC O A</span><span class="sxs-lookup"><span data-stu-id="32be2-719">ESC O A</span></span> |
| <span data-ttu-id="32be2-720">向下箭號</span><span class="sxs-lookup"><span data-stu-id="32be2-720">Down Arrow</span></span> | <span data-ttu-id="32be2-721">ESC \[ B</span><span class="sxs-lookup"><span data-stu-id="32be2-721">ESC \[ B</span></span> | <span data-ttu-id="32be2-722">ESC O B</span><span class="sxs-lookup"><span data-stu-id="32be2-722">ESC O B</span></span> |
| <span data-ttu-id="32be2-723">向右鍵</span><span class="sxs-lookup"><span data-stu-id="32be2-723">Right Arrow</span></span> | <span data-ttu-id="32be2-724">ESC \[ C</span><span class="sxs-lookup"><span data-stu-id="32be2-724">ESC \[ C</span></span> | <span data-ttu-id="32be2-725">ESC O C</span><span class="sxs-lookup"><span data-stu-id="32be2-725">ESC O C</span></span> |
| <span data-ttu-id="32be2-726">向左鍵</span><span class="sxs-lookup"><span data-stu-id="32be2-726">Left Arrow</span></span> | <span data-ttu-id="32be2-727">ESC \[ D</span><span class="sxs-lookup"><span data-stu-id="32be2-727">ESC \[ D</span></span> | <span data-ttu-id="32be2-728">ESC O D</span><span class="sxs-lookup"><span data-stu-id="32be2-728">ESC O D</span></span> |
| <span data-ttu-id="32be2-729">家庭</span><span class="sxs-lookup"><span data-stu-id="32be2-729">Home</span></span> | <span data-ttu-id="32be2-730">ESC \[ H</span><span class="sxs-lookup"><span data-stu-id="32be2-730">ESC \[ H</span></span> | <span data-ttu-id="32be2-731">ESC O H</span><span class="sxs-lookup"><span data-stu-id="32be2-731">ESC O H</span></span> |
| <span data-ttu-id="32be2-732">結束</span><span class="sxs-lookup"><span data-stu-id="32be2-732">End</span></span> | <span data-ttu-id="32be2-733">ESC \[ F</span><span class="sxs-lookup"><span data-stu-id="32be2-733">ESC \[ F</span></span> | <span data-ttu-id="32be2-734">ESC O F</span><span class="sxs-lookup"><span data-stu-id="32be2-734">ESC O F</span></span> |



<span data-ttu-id="32be2-735">此外，如果按下 Ctrl 鍵和這其中任何一個鍵，則會改為發出下列序列 (不論游標按鍵模式為何)：</span><span class="sxs-lookup"><span data-stu-id="32be2-735">Additionally, if Ctrl is pressed with any of these keys, the following sequences are emitted instead, regardless of the Cursor Keys Mode:</span></span>


| <span data-ttu-id="32be2-736">答案</span><span class="sxs-lookup"><span data-stu-id="32be2-736">Key</span></span> | <span data-ttu-id="32be2-737">任何模式</span><span class="sxs-lookup"><span data-stu-id="32be2-737">Any Mode</span></span> |
|--------------------|----------------|
| <span data-ttu-id="32be2-738">Ctrl + 向上鍵</span><span class="sxs-lookup"><span data-stu-id="32be2-738">Ctrl + Up Arrow</span></span> | <span data-ttu-id="32be2-739">ESC \[ 1 ; 5 A</span><span class="sxs-lookup"><span data-stu-id="32be2-739">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="32be2-740">Ctrl + 向下鍵</span><span class="sxs-lookup"><span data-stu-id="32be2-740">Ctrl + Down Arrow</span></span> | <span data-ttu-id="32be2-741">ESC \[ 1 ; 5 B</span><span class="sxs-lookup"><span data-stu-id="32be2-741">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="32be2-742">Ctrl + 向右鍵</span><span class="sxs-lookup"><span data-stu-id="32be2-742">Ctrl + Right Arrow</span></span> | <span data-ttu-id="32be2-743">ESC \[ 1 ; 5 C</span><span class="sxs-lookup"><span data-stu-id="32be2-743">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="32be2-744">Ctrl + 向左鍵</span><span class="sxs-lookup"><span data-stu-id="32be2-744">Ctrl + Left Arrow</span></span> | <span data-ttu-id="32be2-745">ESC \[ 1 ; 5 D</span><span class="sxs-lookup"><span data-stu-id="32be2-745">ESC \[ 1 ; 5 D</span></span> |



### <a name="span-idnumpad___function_keys__spanspan-idnumpad___function_keys__spanspan-idnumpad___function_keys__spannumpad--function-keys"></a><span data-ttu-id="32be2-746"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad 與功能鍵</span><span class="sxs-lookup"><span data-stu-id="32be2-746"><span id="Numpad___Function_Keys__"></span><span id="numpad___function_keys__"></span><span id="NUMPAD___FUNCTION_KEYS__"></span>Numpad & Function Keys</span></span>


| <span data-ttu-id="32be2-747">答案</span><span class="sxs-lookup"><span data-stu-id="32be2-747">Key</span></span> | <span data-ttu-id="32be2-748">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-748">Sequence</span></span> |
|-----------|--------------|
| <span data-ttu-id="32be2-749">退格鍵</span><span class="sxs-lookup"><span data-stu-id="32be2-749">Backspace</span></span> | <span data-ttu-id="32be2-750">0x7f (DEL)</span><span class="sxs-lookup"><span data-stu-id="32be2-750">0x7f (DEL)</span></span> |
| <span data-ttu-id="32be2-751">暫停</span><span class="sxs-lookup"><span data-stu-id="32be2-751">Pause</span></span> | <span data-ttu-id="32be2-752">0x1a (SUB)</span><span class="sxs-lookup"><span data-stu-id="32be2-752">0x1a (SUB)</span></span> |
| <span data-ttu-id="32be2-753">逸出</span><span class="sxs-lookup"><span data-stu-id="32be2-753">Escape</span></span> | <span data-ttu-id="32be2-754">0x1b (ESC)</span><span class="sxs-lookup"><span data-stu-id="32be2-754">0x1b (ESC)</span></span> |
| <span data-ttu-id="32be2-755">插入</span><span class="sxs-lookup"><span data-stu-id="32be2-755">Insert</span></span> | <span data-ttu-id="32be2-756">ESC \[ 2 ~</span><span class="sxs-lookup"><span data-stu-id="32be2-756">ESC \[ 2 ~</span></span> |
| <span data-ttu-id="32be2-757">刪除</span><span class="sxs-lookup"><span data-stu-id="32be2-757">Delete</span></span> | <span data-ttu-id="32be2-758">ESC \[ 3 ~</span><span class="sxs-lookup"><span data-stu-id="32be2-758">ESC \[ 3 ~</span></span> |
| <span data-ttu-id="32be2-759">Page Up</span><span class="sxs-lookup"><span data-stu-id="32be2-759">Page Up</span></span> | <span data-ttu-id="32be2-760">ESC \[ 5 ~</span><span class="sxs-lookup"><span data-stu-id="32be2-760">ESC \[ 5 ~</span></span> |
| <span data-ttu-id="32be2-761">Page Down</span><span class="sxs-lookup"><span data-stu-id="32be2-761">Page Down</span></span> | <span data-ttu-id="32be2-762">ESC \[ 6 ~</span><span class="sxs-lookup"><span data-stu-id="32be2-762">ESC \[ 6 ~</span></span> |
| <span data-ttu-id="32be2-763">F1</span><span class="sxs-lookup"><span data-stu-id="32be2-763">F1</span></span> | <span data-ttu-id="32be2-764">ESC O P</span><span class="sxs-lookup"><span data-stu-id="32be2-764">ESC O P</span></span> |
| <span data-ttu-id="32be2-765">F2</span><span class="sxs-lookup"><span data-stu-id="32be2-765">F2</span></span> | <span data-ttu-id="32be2-766">ESC O Q</span><span class="sxs-lookup"><span data-stu-id="32be2-766">ESC O Q</span></span> |
| <span data-ttu-id="32be2-767">F3</span><span class="sxs-lookup"><span data-stu-id="32be2-767">F3</span></span> | <span data-ttu-id="32be2-768">ESC O R</span><span class="sxs-lookup"><span data-stu-id="32be2-768">ESC O R</span></span> |
| <span data-ttu-id="32be2-769">F4</span><span class="sxs-lookup"><span data-stu-id="32be2-769">F4</span></span> | <span data-ttu-id="32be2-770">ESC O S</span><span class="sxs-lookup"><span data-stu-id="32be2-770">ESC O S</span></span> |
| <span data-ttu-id="32be2-771">F5</span><span class="sxs-lookup"><span data-stu-id="32be2-771">F5</span></span> | <span data-ttu-id="32be2-772">ESC \[ 1 5 ~</span><span class="sxs-lookup"><span data-stu-id="32be2-772">ESC \[ 1 5 ~</span></span> |
| <span data-ttu-id="32be2-773">F6</span><span class="sxs-lookup"><span data-stu-id="32be2-773">F6</span></span> | <span data-ttu-id="32be2-774">ESC \[ 1 7 ~</span><span class="sxs-lookup"><span data-stu-id="32be2-774">ESC \[ 1 7 ~</span></span> |
| <span data-ttu-id="32be2-775">F7</span><span class="sxs-lookup"><span data-stu-id="32be2-775">F7</span></span> | <span data-ttu-id="32be2-776">ESC \[ 1 8 ~</span><span class="sxs-lookup"><span data-stu-id="32be2-776">ESC \[ 1 8 ~</span></span> |
| <span data-ttu-id="32be2-777">F8</span><span class="sxs-lookup"><span data-stu-id="32be2-777">F8</span></span> | <span data-ttu-id="32be2-778">ESC \[ 1 9 ~</span><span class="sxs-lookup"><span data-stu-id="32be2-778">ESC \[ 1 9 ~</span></span> |
| <span data-ttu-id="32be2-779">F9</span><span class="sxs-lookup"><span data-stu-id="32be2-779">F9</span></span> | <span data-ttu-id="32be2-780">ESC \[ 2 0 ~</span><span class="sxs-lookup"><span data-stu-id="32be2-780">ESC \[ 2 0 ~</span></span> |
| <span data-ttu-id="32be2-781">F10</span><span class="sxs-lookup"><span data-stu-id="32be2-781">F10</span></span> | <span data-ttu-id="32be2-782">ESC \[ 2 1 ~</span><span class="sxs-lookup"><span data-stu-id="32be2-782">ESC \[ 2 1 ~</span></span> |
| <span data-ttu-id="32be2-783">F11</span><span class="sxs-lookup"><span data-stu-id="32be2-783">F11</span></span> | <span data-ttu-id="32be2-784">ESC \[ 2 3 ~</span><span class="sxs-lookup"><span data-stu-id="32be2-784">ESC \[ 2 3 ~</span></span> |
| <span data-ttu-id="32be2-785">F12</span><span class="sxs-lookup"><span data-stu-id="32be2-785">F12</span></span> | <span data-ttu-id="32be2-786">ESC \[ 2 4 ~</span><span class="sxs-lookup"><span data-stu-id="32be2-786">ESC \[ 2 4 ~</span></span> |



### <a name="span-idmodifiers__spanspan-idmodifiers__spanspan-idmodifiers__spanmodifiers"></a><span data-ttu-id="32be2-787"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>輔助按鍵</span><span class="sxs-lookup"><span data-stu-id="32be2-787"><span id="Modifiers__"></span><span id="modifiers__"></span><span id="MODIFIERS__"></span>Modifiers</span></span>

<span data-ttu-id="32be2-788">Alt 的處理方式是在序列前方加上 escape：ESC &lt;c&gt;，其中 &lt;c&gt; 是作業系統所傳遞的字元。</span><span class="sxs-lookup"><span data-stu-id="32be2-788">Alt is treated by prefixing the sequence with an escape: ESC &lt;c&gt; where &lt;c&gt; is the character passed by the operating system.</span></span> <span data-ttu-id="32be2-789">Alt+Ctrl 的處理方式相同，不同之處在於作業系統會將 &lt;c&gt; 鍵預先轉移至適當的控制字元，以轉送至應用程式。</span><span class="sxs-lookup"><span data-stu-id="32be2-789">Alt+Ctrl is handled the same way except that the operating system will have pre-shifted the &lt;c&gt; key to the appropriate control character which will be relayed to the application.</span></span>

<span data-ttu-id="32be2-790">傳遞的 Ctrl 通常會與從系統中收到的完全相同。</span><span class="sxs-lookup"><span data-stu-id="32be2-790">Ctrl is generally passed through exactly as received from the system.</span></span> <span data-ttu-id="32be2-791">這通常是移到控制字元保留空間 (0x0-0x1f) 中的單一字元。</span><span class="sxs-lookup"><span data-stu-id="32be2-791">This is typically a single character shifted down into the control character reserved space (0x0-0x1f).</span></span> <span data-ttu-id="32be2-792">例如，Ctrl+@ (0x40) 變成 NUL (0x00)，Ctrl+\[ (0x5b) 變成 ESC (0x1b) 等等。有幾個 Ctrl 鍵組合會根據下表來特別處理：</span><span class="sxs-lookup"><span data-stu-id="32be2-792">For example, Ctrl+@ (0x40) becomes NUL (0x00), Ctrl+\[ (0x5b) becomes ESC (0x1b), etc. A few Ctrl key combinations are treated specially according to the following table:</span></span>


| <span data-ttu-id="32be2-793">答案</span><span class="sxs-lookup"><span data-stu-id="32be2-793">Key</span></span> | <span data-ttu-id="32be2-794">順序</span><span class="sxs-lookup"><span data-stu-id="32be2-794">Sequence</span></span> |
|--------------------|----------------|
| <span data-ttu-id="32be2-795">Ctrl + 空格鍵</span><span class="sxs-lookup"><span data-stu-id="32be2-795">Ctrl + Space</span></span> | <span data-ttu-id="32be2-796">0x00 (NUL)</span><span class="sxs-lookup"><span data-stu-id="32be2-796">0x00 (NUL)</span></span> |
| <span data-ttu-id="32be2-797">Ctrl + 向上鍵</span><span class="sxs-lookup"><span data-stu-id="32be2-797">Ctrl + Up Arrow</span></span> | <span data-ttu-id="32be2-798">ESC \[ 1 ; 5 A</span><span class="sxs-lookup"><span data-stu-id="32be2-798">ESC \[ 1 ; 5 A</span></span> |
| <span data-ttu-id="32be2-799">Ctrl + 向下鍵</span><span class="sxs-lookup"><span data-stu-id="32be2-799">Ctrl + Down Arrow</span></span> | <span data-ttu-id="32be2-800">ESC \[ 1 ; 5 B</span><span class="sxs-lookup"><span data-stu-id="32be2-800">ESC \[ 1 ; 5 B</span></span> |
| <span data-ttu-id="32be2-801">Ctrl + 向右鍵</span><span class="sxs-lookup"><span data-stu-id="32be2-801">Ctrl + Right Arrow</span></span> | <span data-ttu-id="32be2-802">ESC \[ 1 ; 5 C</span><span class="sxs-lookup"><span data-stu-id="32be2-802">ESC \[ 1 ; 5 C</span></span> |
| <span data-ttu-id="32be2-803">Ctrl + 向左鍵</span><span class="sxs-lookup"><span data-stu-id="32be2-803">Ctrl + Left Arrow</span></span> | <span data-ttu-id="32be2-804">ESC \[ 1 ; 5 D</span><span class="sxs-lookup"><span data-stu-id="32be2-804">ESC \[ 1 ; 5 D</span></span> |



> [!NOTE]
><span data-ttu-id="32be2-805">左側 <kbd>Ctrl</kbd> + 右側 <kbd>Alt</kbd> 會視為 AltGr。</span><span class="sxs-lookup"><span data-stu-id="32be2-805">Left <kbd>Ctrl</kbd> + Right <kbd>Alt</kbd> is treated as AltGr.</span></span> <span data-ttu-id="32be2-806">兩者同時出現時，則會將這兩者移除，並將系統所呈現的字元 Unicode 值傳遞到目標。</span><span class="sxs-lookup"><span data-stu-id="32be2-806">When both are seen together, they will be stripped and the Unicode value of the character presented by the system will be passed into the target.</span></span> <span data-ttu-id="32be2-807">系統會根據目前的系統輸入設定，預先轉譯 AltGr 值。</span><span class="sxs-lookup"><span data-stu-id="32be2-807">The system will pre-translate AltGr values according to the current system input settings.</span></span>



## <a name="span-idsamplesspanspan-idsamplesspanspan-idsamplesspansamples"></a><span data-ttu-id="32be2-808"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>範例</span><span class="sxs-lookup"><span data-stu-id="32be2-808"><span id="Samples"></span><span id="samples"></span><span id="SAMPLES"></span>Samples</span></span>


### <a name="span-idexamplespanspan-idexamplespanexample-of-sgr-terminal-sequences"></a><span data-ttu-id="32be2-809"><span id="example"></span><span id="EXAMPLE"></span>SGR 終端機序列的範例</span><span class="sxs-lookup"><span data-stu-id="32be2-809"><span id="example"></span><span id="EXAMPLE"></span>Example of SGR terminal sequences</span></span>

<span data-ttu-id="32be2-810">下列程式碼提供幾個文字格式化的範例。</span><span class="sxs-lookup"><span data-stu-id="32be2-810">The following code provides several examples of text formatting.</span></span>

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
><span data-ttu-id="32be2-811">在上述範例中，字串 '`\x1b[31m`' 是 **ESC \[ &lt;n&gt; m** 的實作，&lt;n&gt; 為 31。</span><span class="sxs-lookup"><span data-stu-id="32be2-811">In the previous example, the string '`\x1b[31m`' is the implementation of **ESC \[ &lt;n&gt; m** with &lt;n&gt; being 31.</span></span>



<span data-ttu-id="32be2-812">下圖顯示先前程式碼範例的輸出。</span><span class="sxs-lookup"><span data-stu-id="32be2-812">The following graphic shows the output of the previous code example.</span></span>

![使用 sgr 命令的主控台輸出](images/sgr.png)

### <a name="span-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanspan-idexample_of_enabling_virtual_terminal_processingspanexample-of-enabling-virtual-terminal-processing"></a><span data-ttu-id="32be2-814"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>啟用虛擬終端處理的範例</span><span class="sxs-lookup"><span data-stu-id="32be2-814"><span id="Example_of_Enabling_Virtual_Terminal_Processing"></span><span id="example_of_enabling_virtual_terminal_processing"></span><span id="EXAMPLE_OF_ENABLING_VIRTUAL_TERMINAL_PROCESSING"></span>Example of Enabling Virtual Terminal Processing</span></span>

<span data-ttu-id="32be2-815">下列程式碼提供為應用程式啟用虛擬終端處理的建議方式範例。</span><span class="sxs-lookup"><span data-stu-id="32be2-815">The following code provides an example of the recommended way to enable virtual terminal processing for an application.</span></span> <span data-ttu-id="32be2-816">範例的目的是要示範：</span><span class="sxs-lookup"><span data-stu-id="32be2-816">The intent of the sample is to demonstrate:</span></span>

1. <span data-ttu-id="32be2-817">現有模式應一律透過 GetConsoleMode 取得，並在使用 SetConsoleMode 設定之前進行分析。</span><span class="sxs-lookup"><span data-stu-id="32be2-817">The existing mode should always be retrieved via GetConsoleMode and analyzed before being set with SetConsoleMode.</span></span>

2. <span data-ttu-id="32be2-818">檢查 SetConsoleMode 是否傳回 `0` 及 GetLastError 是否傳回 STATUS\_INVALID\_PARAMETER 是目前在下層系統上執行時所要判斷的機制。</span><span class="sxs-lookup"><span data-stu-id="32be2-818">Checking whether SetConsoleMode returns `0` and GetLastError returns STATUS\_INVALID\_PARAMETER is the current mechanism to determine when running on a down-level system.</span></span> <span data-ttu-id="32be2-819">應用程式若收到 STATUS\_INVALID\_PARAMETER 且在位元欄位中有一個較新的主控台模式旗標，則應以適當方式降低行為層級，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="32be2-819">An application receiving STATUS\_INVALID\_PARAMETER with one of the newer console mode flags in the bit field should gracefully degrade behavior and try again.</span></span>

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

### <a name="span-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanspan-idexample_of_select_anniversary_update_featuresspanexample-of-select-anniversary-update-features"></a><span data-ttu-id="32be2-820"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>選取年度更新功能的範例</span><span class="sxs-lookup"><span data-stu-id="32be2-820"><span id="Example_of_Select_Anniversary_Update_Features"></span><span id="example_of_select_anniversary_update_features"></span><span id="EXAMPLE_OF_SELECT_ANNIVERSARY_UPDATE_FEATURES"></span>Example of Select Anniversary Update Features</span></span>

<span data-ttu-id="32be2-821">下列範例是使用各種逸出序列來操作緩衝區且更健全的程式碼範例，並且會強調 Windows 10 年度更新版中新增的功能。</span><span class="sxs-lookup"><span data-stu-id="32be2-821">The following example is intended to be a more robust example of code using a variety of escape sequences to manipulate the buffer, with an emphasis on the features added in the Anniversary Update for Windows 10.</span></span>

<span data-ttu-id="32be2-822">此範例會使用替代畫面緩衝區、操控 Tab 停止點、設定捲動邊界及變更字元集。</span><span class="sxs-lookup"><span data-stu-id="32be2-822">This example makes use of the alternate screen buffer, manipulating tab stops, setting scrolling margins, and changing the character set.</span></span>

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

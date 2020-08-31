---
title: 高層級主控台模式
description: 高層級主控台功能的行為會受到主控台輸入和輸出模式的影響。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_high\_level\_console\_modes'
- base.high\_level\_console\_modes
- consoles.high\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3ec915eb-333d-484d-a14d-46377b503ecc
ms.openlocfilehash: b5b24056a1283d46cbfe21737bd930318042c039
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059083"
---
# <a name="high-level-console-modes"></a><span data-ttu-id="06095-104">高層級主控台模式</span><span class="sxs-lookup"><span data-stu-id="06095-104">High-Level Console Modes</span></span>


<span data-ttu-id="06095-105">高層級主控台功能的行為會受到主控台輸入和輸出模式的影響。</span><span class="sxs-lookup"><span data-stu-id="06095-105">The behavior of the high-level console functions is affected by the console input and output modes.</span></span> <span data-ttu-id="06095-106">主控台建立時，主控台的輸入緩衝區會啟用下列所有的主控台輸入模式：</span><span class="sxs-lookup"><span data-stu-id="06095-106">All of the following console input modes are enabled for a console's input buffer when a console is created:</span></span>

- <span data-ttu-id="06095-107">行輸入模式</span><span class="sxs-lookup"><span data-stu-id="06095-107">Line input mode</span></span>
- <span data-ttu-id="06095-108">已處理的輸入模式</span><span class="sxs-lookup"><span data-stu-id="06095-108">Processed input mode</span></span>
- <span data-ttu-id="06095-109">Echo 輸入模式</span><span class="sxs-lookup"><span data-stu-id="06095-109">Echo input mode</span></span>

<span data-ttu-id="06095-110">主控台螢幕緩衝區在建立時，會啟用下列兩個主控台輸出模式：</span><span class="sxs-lookup"><span data-stu-id="06095-110">Both of the following console output modes are enabled for a console screen buffer when it is created:</span></span>

- <span data-ttu-id="06095-111">處理的輸出模式</span><span class="sxs-lookup"><span data-stu-id="06095-111">Processed output mode</span></span>
- <span data-ttu-id="06095-112">以 EOL 輸出模式換行</span><span class="sxs-lookup"><span data-stu-id="06095-112">Wrapping at EOL output mode</span></span>

<span data-ttu-id="06095-113">所有三種輸入模式以及已處理的輸出模式都是設計來一起使用。</span><span class="sxs-lookup"><span data-stu-id="06095-113">All three input modes, along with processed output mode, are designed to work together.</span></span> <span data-ttu-id="06095-114">最好是以群組方式啟用或停用這些模式。</span><span class="sxs-lookup"><span data-stu-id="06095-114">It is best to either enable or disable all of these modes as a group.</span></span> <span data-ttu-id="06095-115">當所有都啟用時，應用程式就會被視為「處理後」模式，這表示大部分的處理都是針對應用程式進行處理。</span><span class="sxs-lookup"><span data-stu-id="06095-115">When all are enabled, the application is said to be in "cooked" mode, which means that most of the processing is handled for the application.</span></span> <span data-ttu-id="06095-116">當全部停用時，應用程式會處於「未經處理」模式，這表示未篩選輸入，而且會對應用程式留下任何處理。</span><span class="sxs-lookup"><span data-stu-id="06095-116">When all are disabled, the application is in "raw" mode, which means that input is unfiltered and any processing is left to the application.</span></span>

<span data-ttu-id="06095-117">應用程式可以使用 [**GetConsoleMode**](getconsolemode.md) 函式來判斷主控台之輸入緩衝區或螢幕緩衝區的目前模式。</span><span class="sxs-lookup"><span data-stu-id="06095-117">An application can use the [**GetConsoleMode**](getconsolemode.md) function to determine the current mode of a console's input buffer or screen buffer.</span></span> <span data-ttu-id="06095-118">您可以使用 [**SetConsoleMode**](setconsolemode.md) 函式中的下列值，來啟用或停用這些模式中的任何一種。</span><span class="sxs-lookup"><span data-stu-id="06095-118">You can enable or disable any of these modes by using the following values in the [**SetConsoleMode**](setconsolemode.md) function.</span></span> <span data-ttu-id="06095-119">請注意，設定一個螢幕緩衝區的輸出模式不會影響其他螢幕緩衝區的輸出模式。</span><span class="sxs-lookup"><span data-stu-id="06095-119">Note that setting the output mode of one screen buffer does not affect the output mode of other screen buffers.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="06095-120">[模式]</span><span class="sxs-lookup"><span data-stu-id="06095-120">Mode</span></span></th>
<th><span data-ttu-id="06095-121">描述</span><span class="sxs-lookup"><span data-stu-id="06095-121">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="06095-122"><strong>ENABLE_PROCESSED_INPUT</strong></span><span class="sxs-lookup"><span data-stu-id="06095-122"><strong>ENABLE_PROCESSED_INPUT</strong></span></span></td>
<td><span data-ttu-id="06095-123">搭配主控台輸入控制碼使用，可讓系統處理任何系統編輯或控制索引鍵輸入，而不是在讀取作業&#39;s 緩衝區中傳回做為輸入。</span><span class="sxs-lookup"><span data-stu-id="06095-123">Used with a console input handle to cause the system to process any system editing or control key input rather than returning it as input in the read operation&#39;s buffer.</span></span> <span data-ttu-id="06095-124">如果也啟用行輸入，則會正確處理 backspaces 和回車。</span><span class="sxs-lookup"><span data-stu-id="06095-124">If line input is also enabled, backspaces and carriage returns are handled correctly.</span></span> <span data-ttu-id="06095-125">倒退鍵會導致游標移回一個空間，而不會影響游標位置的字元。</span><span class="sxs-lookup"><span data-stu-id="06095-125">A backspace causes the cursor to move back one space without affecting the character at the cursor position.</span></span> <span data-ttu-id="06095-126">換行字元會轉換成換行字元（換行字元組合）。</span><span class="sxs-lookup"><span data-stu-id="06095-126">A carriage return is converted to carriage return – line feed character combination.</span></span> <span data-ttu-id="06095-127">如果已啟用 echo 輸入模式且輸出應該會反映系統編輯，則必須針對使用中的螢幕緩衝區啟用已處理的輸出。</span><span class="sxs-lookup"><span data-stu-id="06095-127">If echo input mode is enabled and the output should reflect system editing, processed output must be enabled for the active screen buffer.</span></span> <span data-ttu-id="06095-128">如果已啟用已處理的輸入，則不論是否啟用行輸入，CTRL + C 按鍵組合都會傳遞至適當的處理常式。</span><span class="sxs-lookup"><span data-stu-id="06095-128">If processed input is enabled, the CTRL+C key combination is passed on to the appropriate handler regardless of whether line input is enabled.</span></span> <span data-ttu-id="06095-129">如需控制處理常式的詳細資訊，請參閱 <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">主控台控制項處理常式</a>。</span><span class="sxs-lookup"><span data-stu-id="06095-129">For more information about control handlers, see <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">Console Control Handlers</a>.</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="06095-130"><strong>ENABLE_LINE_INPUT</strong></span><span class="sxs-lookup"><span data-stu-id="06095-130"><strong>ENABLE_LINE_INPUT</strong></span></span></td>
<td><span data-ttu-id="06095-131">搭配主控台輸入控制碼使用，可在按下 ENTER 鍵時，讓 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> 和 <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> 函數傳回。</span><span class="sxs-lookup"><span data-stu-id="06095-131">Used with a console input handle to cause the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> and <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> functions to return when the ENTER key is pressed.</span></span> <span data-ttu-id="06095-132">如果已停用行輸入模式，當輸入緩衝區中有一或多個字元可用時，函式就會傳回。</span><span class="sxs-lookup"><span data-stu-id="06095-132">If line input mode is disabled, the functions return when one or more characters are available in the input buffer.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="06095-133"><strong>ENABLE_ECHO_INPUT</strong></span><span class="sxs-lookup"><span data-stu-id="06095-133"><strong>ENABLE_ECHO_INPUT</strong></span></span></td>
<td><span data-ttu-id="06095-134">搭配主控台輸入控制碼使用，可讓 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> 或 <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> 函式讀取的鍵盤輸入回應至使用中的螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="06095-134">Used with a console input handle to cause keyboard input read by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function to be echoed to the active screen buffer.</span></span> <span data-ttu-id="06095-135">只有呼叫 <strong>ReadFile</strong> 或 <strong>ReadConsole</strong> 的進程具有主動螢幕緩衝區的開啟控制碼時，才會回顯字元。</span><span class="sxs-lookup"><span data-stu-id="06095-135">Characters are echoed only if the process that calls <strong>ReadFile</strong> or <strong>ReadConsole</strong> has an open handle to the active screen buffer.</span></span> <span data-ttu-id="06095-136">除非也啟用了行輸入，否則無法啟用 Echo 模式。</span><span class="sxs-lookup"><span data-stu-id="06095-136">Echo mode cannot be enabled unless line input is also enabled.</span></span> <span data-ttu-id="06095-137">現用螢幕緩衝區的輸出模式會影響回應輸入的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="06095-137">The output mode of the active screen buffer affects the way echoed input is displayed.</span></span></td>
</tr>
<tr class="even">
<td><span data-ttu-id="06095-138"><strong>ENABLE_PROCESSED_OUTPUT</strong></span><span class="sxs-lookup"><span data-stu-id="06095-138"><strong>ENABLE_PROCESSED_OUTPUT</strong></span></span></td>
<td><span data-ttu-id="06095-139">搭配主控台畫面緩衝區控制碼使用，讓系統針對寫入螢幕緩衝區的 ANSI 控制字元執行適當的動作。</span><span class="sxs-lookup"><span data-stu-id="06095-139">Used with a console screen buffer handle to cause the system to perform the appropriate action for ANSI control characters that are written to a screen buffer.</span></span> <span data-ttu-id="06095-140">會處理倒退鍵、定位字元、鐘、換行字元和換行字元。</span><span class="sxs-lookup"><span data-stu-id="06095-140">The backspace, tab, bell, carriage return, and line feed characters are processed.</span></span> <span data-ttu-id="06095-141">Tab 字元會將游標移至下一個索引標籤，這會在每8個字元發生。</span><span class="sxs-lookup"><span data-stu-id="06095-141">A tab character moves the cursor to the next tab stop, which occurs every eight characters.</span></span> <span data-ttu-id="06095-142">鐘字元聽起來很簡單。</span><span class="sxs-lookup"><span data-stu-id="06095-142">A bell character sounds a short tone.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="06095-143"><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></span><span class="sxs-lookup"><span data-stu-id="06095-143"><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></span></span></td>
<td><span data-ttu-id="06095-144">搭配主控台畫面緩衝區控制碼使用，可讓目前的輸出位置 (資料指標位置，) 在到達目前資料列的結尾時，) 下一個資料列中的第一個資料 (行。</span><span class="sxs-lookup"><span data-stu-id="06095-144">Used with a console screen buffer handle to cause the current output position (cursor position) to move to the first column in the next row (line) when the end of the current row is reached.</span></span> <span data-ttu-id="06095-145">如果到達視窗區域的底部，視窗原點會向下移動一個資料列。</span><span class="sxs-lookup"><span data-stu-id="06095-145">If the bottom of the window region is reached, the window origin is moved down one row.</span></span> <span data-ttu-id="06095-146">這項移動的效果是將視窗的內容向上滾動一個資料列。</span><span class="sxs-lookup"><span data-stu-id="06095-146">This movement has the effect of scrolling the contents of the window up one row.</span></span> <span data-ttu-id="06095-147">如果到達主控台螢幕緩衝區的底部，主控台畫面緩衝區的內容會向上滾動一個資料列，並捨棄主控台螢幕緩衝區的頂端列。</span><span class="sxs-lookup"><span data-stu-id="06095-147">If the bottom of the console screen buffer is reached, the contents of the console screen buffer are scrolled up one row, and the top row of the console screen buffer is discarded.</span></span>
<p><span data-ttu-id="06095-148">如果停用此模式，則會以任何後續字元覆寫資料列中的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="06095-148">If this mode is disabled, the last character in the row is overwritten with any subsequent characters.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

 

 





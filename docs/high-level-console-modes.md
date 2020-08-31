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
# <a name="high-level-console-modes"></a>高層級主控台模式


高層級主控台功能的行為會受到主控台輸入和輸出模式的影響。 主控台建立時，主控台的輸入緩衝區會啟用下列所有的主控台輸入模式：

- 行輸入模式
- 已處理的輸入模式
- Echo 輸入模式

主控台螢幕緩衝區在建立時，會啟用下列兩個主控台輸出模式：

- 處理的輸出模式
- 以 EOL 輸出模式換行

所有三種輸入模式以及已處理的輸出模式都是設計來一起使用。 最好是以群組方式啟用或停用這些模式。 當所有都啟用時，應用程式就會被視為「處理後」模式，這表示大部分的處理都是針對應用程式進行處理。 當全部停用時，應用程式會處於「未經處理」模式，這表示未篩選輸入，而且會對應用程式留下任何處理。

應用程式可以使用 [**GetConsoleMode**](getconsolemode.md) 函式來判斷主控台之輸入緩衝區或螢幕緩衝區的目前模式。 您可以使用 [**SetConsoleMode**](setconsolemode.md) 函式中的下列值，來啟用或停用這些模式中的任何一種。 請注意，設定一個螢幕緩衝區的輸出模式不會影響其他螢幕緩衝區的輸出模式。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>[模式]</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>ENABLE_PROCESSED_INPUT</strong></td>
<td>搭配主控台輸入控制碼使用，可讓系統處理任何系統編輯或控制索引鍵輸入，而不是在讀取作業&#39;s 緩衝區中傳回做為輸入。 如果也啟用行輸入，則會正確處理 backspaces 和回車。 倒退鍵會導致游標移回一個空間，而不會影響游標位置的字元。 換行字元會轉換成換行字元（換行字元組合）。 如果已啟用 echo 輸入模式且輸出應該會反映系統編輯，則必須針對使用中的螢幕緩衝區啟用已處理的輸出。 如果已啟用已處理的輸入，則不論是否啟用行輸入，CTRL + C 按鍵組合都會傳遞至適當的處理常式。 如需控制處理常式的詳細資訊，請參閱 <a href="console-control-handlers.md" data-raw-source="[Console Control Handlers](console-control-handlers.md)">主控台控制項處理常式</a>。</td>
</tr>
<tr class="even">
<td><strong>ENABLE_LINE_INPUT</strong></td>
<td>搭配主控台輸入控制碼使用，可在按下 ENTER 鍵時，讓 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> 和 <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> 函數傳回。 如果已停用行輸入模式，當輸入緩衝區中有一或多個字元可用時，函式就會傳回。</td>
</tr>
<tr class="odd">
<td><strong>ENABLE_ECHO_INPUT</strong></td>
<td>搭配主控台輸入控制碼使用，可讓 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> 或 <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> 函式讀取的鍵盤輸入回應至使用中的螢幕緩衝區。 只有呼叫 <strong>ReadFile</strong> 或 <strong>ReadConsole</strong> 的進程具有主動螢幕緩衝區的開啟控制碼時，才會回顯字元。 除非也啟用了行輸入，否則無法啟用 Echo 模式。 現用螢幕緩衝區的輸出模式會影響回應輸入的顯示方式。</td>
</tr>
<tr class="even">
<td><strong>ENABLE_PROCESSED_OUTPUT</strong></td>
<td>搭配主控台畫面緩衝區控制碼使用，讓系統針對寫入螢幕緩衝區的 ANSI 控制字元執行適當的動作。 會處理倒退鍵、定位字元、鐘、換行字元和換行字元。 Tab 字元會將游標移至下一個索引標籤，這會在每8個字元發生。 鐘字元聽起來很簡單。</td>
</tr>
<tr class="odd">
<td><strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong></td>
<td>搭配主控台畫面緩衝區控制碼使用，可讓目前的輸出位置 (資料指標位置，) 在到達目前資料列的結尾時，) 下一個資料列中的第一個資料 (行。 如果到達視窗區域的底部，視窗原點會向下移動一個資料列。 這項移動的效果是將視窗的內容向上滾動一個資料列。 如果到達主控台螢幕緩衝區的底部，主控台畫面緩衝區的內容會向上滾動一個資料列，並捨棄主控台螢幕緩衝區的頂端列。
<p>如果停用此模式，則會以任何後續字元覆寫資料列中的最後一個字元。</p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

 

 





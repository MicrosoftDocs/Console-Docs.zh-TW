---
title: 主控台 WinEvents
description: 下列事件常數用於 WinEventProc 回呼函數的事件參數。 如需詳細資訊，請參閱 WinEvents。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- winuser/EVENT_CONSOLE_CARET
- winuser/EVENT_CONSOLE_END_APPLICATION
- winuser/EVENT_CONSOLE_LAYOUT
- winuser/EVENT_CONSOLE_START_APPLICATION
- winuser/EVENT_CONSOLE_UPDATE_REGION
- winuser/EVENT_CONSOLE_UPDATE_SCROLL
- winuser/EVENT_CONSOLE_UPDATE_SIMPLE
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
MS-HAID:
- '\_win32\_console\_winevents'
- base.console\_winevents
- consoles.console\_winevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b7078b2d-5508-4e42-bac2-34b70f1856e2
topic_type:
- apiref
api_name:
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
api_location:
- Winuser.h
api_type:
- HeaderDef
ms.openlocfilehash: ab58df01b3fb29e6efea3ecd0aab145fe2f298c2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059243"
---
# <a name="console-winevents"></a>主控台 WinEvents


下列事件常數用於[*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx)回呼函數的*事件*參數。 如需詳細資訊，請參閱 [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889)。

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>常數/值</th>
<th>描述</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span id="EVENT_CONSOLE_CARET"></span><span id="event_console_caret"></span>
<strong>EVENT_CONSOLE_CARET</strong> 0x4001</td>
<td><p>主控台插入號已移動。 <em>IdObject</em>參數是下列其中一個或多個值： <strong>CONSOLE_CARET_SELECTION</strong>或<strong>CONSOLE_CARET_VISIBLE</strong>。</p>
<p><em>IdChild</em>參數是一種<strong><a href="https://docs.microsoft.com/windows/console/coord-str">COORD</a></strong>結構，可指定資料指標的目前位置。</p></td>
</tr>
<tr class="even">
<td><span id="EVENT_CONSOLE_END_APPLICATION"></span><span id="event_console_end_application"></span>
<strong>EVENT_CONSOLE_END_APPLICATION</strong> 0x4007</td>
<td><p>主控台進程已結束。 <em>IdObject</em>參數包含終止進程的處理序識別碼。</p></td>
</tr>
<tr class="odd">
<td><span id="EVENT_CONSOLE_LAYOUT"></span><span id="event_console_layout"></span>
<strong>EVENT_CONSOLE_LAYOUT</strong> 0x4005</td>
<td><p>主控台版面配置已變更。</p></td>
</tr>
<tr class="even">
<td><span id="EVENT_CONSOLE_START_APPLICATION"></span><span id="event_console_start_application"></span>
<strong>EVENT_CONSOLE_START_APPLICATION</strong> 0x4006</td>
<td><p>新的主控台進程已啟動。 <em>IdObject</em>參數包含新建立之進程的處理序識別碼。 如果應用程式是16位的應用程式，則會<strong>CONSOLE_APPLICATION_16BIT</strong> <em>idChild</em>參數，而<em>idObject</em>是與主控台相關聯之 NTVDM 會話的處理序識別碼。</p></td>
</tr>
<tr class="odd">
<td><span id="EVENT_CONSOLE_UPDATE_REGION"></span><span id="event_console_update_region"></span>
<strong>EVENT_CONSOLE_UPDATE_REGION</strong> 0x4002</td>
<td><p>有一個以上的字元已經變更。 <em>IdObject</em>參數是指定變更區域開頭的<a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>COORD</strong></a>結構。 <em>IdChild</em>參數是指定已變更區域結尾的<strong>COORD</strong>結構。</p></td>
</tr>
<tr class="even">
<td><span id="EVENT_CONSOLE_UPDATE_SCROLL"></span><span id="event_console_update_scroll"></span>
<strong>EVENT_CONSOLE_UPDATE_SCROLL</strong> 0x4004</td>
<td><p>主控台已滾動。 <em>IdObject</em>參數是主控台滾動的水準距離。 <em>IdChild</em>參數是主控台滾動的垂直距離。</p></td>
</tr>
<tr class="odd">
<td><span id="EVENT_CONSOLE_UPDATE_SIMPLE"></span><span id="event_console_update_simple"></span>
<strong>EVENT_CONSOLE_UPDATE_SIMPLE</strong> 0x4003</td>
<td><p>單一字元已經變更。 <em>IdObject</em>參數是指定已變更之字元的<a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>COORD</strong></a>結構。 <em>IdChild</em>參數會指定低字組中的字元和高位字中的<a href="console-screen-buffers.md#_win32_font_attributes" data-raw-source="[character attributes](console-screen-buffers.md#_win32_font_attributes)">字元屬性</a>。</p></td>
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
<td>Winuser。h</td>
</tr>
</tbody>
</table>

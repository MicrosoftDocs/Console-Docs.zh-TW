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
# <a name="console-winevents"></a><span data-ttu-id="6c32a-105">主控台 WinEvents</span><span class="sxs-lookup"><span data-stu-id="6c32a-105">Console WinEvents</span></span>


<span data-ttu-id="6c32a-106">下列事件常數用於[*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx)回呼函數的*事件*參數。</span><span class="sxs-lookup"><span data-stu-id="6c32a-106">The following event constants are used in the *event* parameter of the [*WinEventProc*](https://msdn.microsoft.com/library/windows/desktop/dd373885(v=vs.85).aspx) callback function.</span></span> <span data-ttu-id="6c32a-107">如需詳細資訊，請參閱 [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889)。</span><span class="sxs-lookup"><span data-stu-id="6c32a-107">For more information, see [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="6c32a-108">常數/值</span><span class="sxs-lookup"><span data-stu-id="6c32a-108">Constant/value</span></span></th>
<th><span data-ttu-id="6c32a-109">描述</span><span class="sxs-lookup"><span data-stu-id="6c32a-109">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="6c32a-110"><span id="EVENT_CONSOLE_CARET"></span><span id="event_console_caret"></span>
<strong>EVENT_CONSOLE_CARET</strong> 0x4001</span><span class="sxs-lookup"><span data-stu-id="6c32a-110"><span id="EVENT_CONSOLE_CARET"></span><span id="event_console_caret"></span>
<strong>EVENT_CONSOLE_CARET</strong> 0x4001</span></span></td>
<td><p><span data-ttu-id="6c32a-111">主控台插入號已移動。</span><span class="sxs-lookup"><span data-stu-id="6c32a-111">The console caret has moved.</span></span> <span data-ttu-id="6c32a-112"><em>IdObject</em>參數是下列其中一個或多個值： <strong>CONSOLE_CARET_SELECTION</strong>或<strong>CONSOLE_CARET_VISIBLE</strong>。</span><span class="sxs-lookup"><span data-stu-id="6c32a-112">The <em>idObject</em> parameter is one or more of the following values: <strong>CONSOLE_CARET_SELECTION</strong> or <strong>CONSOLE_CARET_VISIBLE</strong>.</span></span></p>
<p><span data-ttu-id="6c32a-113"><em>IdChild</em>參數是一種<strong><a href="https://docs.microsoft.com/windows/console/coord-str">COORD</a></strong>結構，可指定資料指標的目前位置。</span><span class="sxs-lookup"><span data-stu-id="6c32a-113">The <em>idChild</em> parameter is a <strong><a href="https://docs.microsoft.com/windows/console/coord-str">COORD</a></strong> structure that specifies the cursor's current position.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="6c32a-114"><span id="EVENT_CONSOLE_END_APPLICATION"></span><span id="event_console_end_application"></span>
<strong>EVENT_CONSOLE_END_APPLICATION</strong> 0x4007</span><span class="sxs-lookup"><span data-stu-id="6c32a-114"><span id="EVENT_CONSOLE_END_APPLICATION"></span><span id="event_console_end_application"></span>
<strong>EVENT_CONSOLE_END_APPLICATION</strong> 0x4007</span></span></td>
<td><p><span data-ttu-id="6c32a-115">主控台進程已結束。</span><span class="sxs-lookup"><span data-stu-id="6c32a-115">A console process has exited.</span></span> <span data-ttu-id="6c32a-116"><em>IdObject</em>參數包含終止進程的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="6c32a-116">The <em>idObject</em> parameter contains the process identifier of the terminated process.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="6c32a-117"><span id="EVENT_CONSOLE_LAYOUT"></span><span id="event_console_layout"></span>
<strong>EVENT_CONSOLE_LAYOUT</strong> 0x4005</span><span class="sxs-lookup"><span data-stu-id="6c32a-117"><span id="EVENT_CONSOLE_LAYOUT"></span><span id="event_console_layout"></span>
<strong>EVENT_CONSOLE_LAYOUT</strong> 0x4005</span></span></td>
<td><p><span data-ttu-id="6c32a-118">主控台版面配置已變更。</span><span class="sxs-lookup"><span data-stu-id="6c32a-118">The console layout has changed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="6c32a-119"><span id="EVENT_CONSOLE_START_APPLICATION"></span><span id="event_console_start_application"></span>
<strong>EVENT_CONSOLE_START_APPLICATION</strong> 0x4006</span><span class="sxs-lookup"><span data-stu-id="6c32a-119"><span id="EVENT_CONSOLE_START_APPLICATION"></span><span id="event_console_start_application"></span>
<strong>EVENT_CONSOLE_START_APPLICATION</strong> 0x4006</span></span></td>
<td><p><span data-ttu-id="6c32a-120">新的主控台進程已啟動。</span><span class="sxs-lookup"><span data-stu-id="6c32a-120">A new console process has started.</span></span> <span data-ttu-id="6c32a-121"><em>IdObject</em>參數包含新建立之進程的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="6c32a-121">The <em>idObject</em> parameter contains the process identifier of the newly created process.</span></span> <span data-ttu-id="6c32a-122">如果應用程式是16位的應用程式，則會<strong>CONSOLE_APPLICATION_16BIT</strong> <em>idChild</em>參數，而<em>idObject</em>是與主控台相關聯之 NTVDM 會話的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="6c32a-122">If the application is a 16-bit application, the <em>idChild</em> parameter is <strong>CONSOLE_APPLICATION_16BIT</strong> and <em>idObject</em> is the process identifier of the NTVDM session associated with the console.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="6c32a-123"><span id="EVENT_CONSOLE_UPDATE_REGION"></span><span id="event_console_update_region"></span>
<strong>EVENT_CONSOLE_UPDATE_REGION</strong> 0x4002</span><span class="sxs-lookup"><span data-stu-id="6c32a-123"><span id="EVENT_CONSOLE_UPDATE_REGION"></span><span id="event_console_update_region"></span>
<strong>EVENT_CONSOLE_UPDATE_REGION</strong> 0x4002</span></span></td>
<td><p><span data-ttu-id="6c32a-124">有一個以上的字元已經變更。</span><span class="sxs-lookup"><span data-stu-id="6c32a-124">More than one character has changed.</span></span> <span data-ttu-id="6c32a-125"><em>IdObject</em>參數是指定變更區域開頭的<a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>COORD</strong></a>結構。</span><span class="sxs-lookup"><span data-stu-id="6c32a-125">The <em>idObject</em> parameter is a <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>COORD</strong></a> structure that specifies the start of the changed region.</span></span> <span data-ttu-id="6c32a-126"><em>IdChild</em>參數是指定已變更區域結尾的<strong>COORD</strong>結構。</span><span class="sxs-lookup"><span data-stu-id="6c32a-126">The <em>idChild</em> parameter is a <strong>COORD</strong> structure that specifies the end of the changed region.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="6c32a-127"><span id="EVENT_CONSOLE_UPDATE_SCROLL"></span><span id="event_console_update_scroll"></span>
<strong>EVENT_CONSOLE_UPDATE_SCROLL</strong> 0x4004</span><span class="sxs-lookup"><span data-stu-id="6c32a-127"><span id="EVENT_CONSOLE_UPDATE_SCROLL"></span><span id="event_console_update_scroll"></span>
<strong>EVENT_CONSOLE_UPDATE_SCROLL</strong> 0x4004</span></span></td>
<td><p><span data-ttu-id="6c32a-128">主控台已滾動。</span><span class="sxs-lookup"><span data-stu-id="6c32a-128">The console has scrolled.</span></span> <span data-ttu-id="6c32a-129"><em>IdObject</em>參數是主控台滾動的水準距離。</span><span class="sxs-lookup"><span data-stu-id="6c32a-129">The <em>idObject</em> parameter is the horizontal distance the console has scrolled.</span></span> <span data-ttu-id="6c32a-130"><em>IdChild</em>參數是主控台滾動的垂直距離。</span><span class="sxs-lookup"><span data-stu-id="6c32a-130">The <em>idChild</em> parameter is the vertical distance the console has scrolled.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="6c32a-131"><span id="EVENT_CONSOLE_UPDATE_SIMPLE"></span><span id="event_console_update_simple"></span>
<strong>EVENT_CONSOLE_UPDATE_SIMPLE</strong> 0x4003</span><span class="sxs-lookup"><span data-stu-id="6c32a-131"><span id="EVENT_CONSOLE_UPDATE_SIMPLE"></span><span id="event_console_update_simple"></span>
<strong>EVENT_CONSOLE_UPDATE_SIMPLE</strong> 0x4003</span></span></td>
<td><p><span data-ttu-id="6c32a-132">單一字元已經變更。</span><span class="sxs-lookup"><span data-stu-id="6c32a-132">A single character has changed.</span></span> <span data-ttu-id="6c32a-133"><em>IdObject</em>參數是指定已變更之字元的<a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>COORD</strong></a>結構。</span><span class="sxs-lookup"><span data-stu-id="6c32a-133">The <em>idObject</em> parameter is a <a href="coord-str.md" data-raw-source="[&lt;strong&gt;COORD&lt;/strong&gt;](coord-str.md)"><strong>COORD</strong></a> structure that specifies the character that has changed.</span></span> <span data-ttu-id="6c32a-134"><em>IdChild</em>參數會指定低字組中的字元和高位字中的<a href="console-screen-buffers.md#_win32_font_attributes" data-raw-source="[character attributes](console-screen-buffers.md#_win32_font_attributes)">字元屬性</a>。</span><span class="sxs-lookup"><span data-stu-id="6c32a-134">The <em>idChild</em> parameter specifies the character in the low word and the <a href="console-screen-buffers.md#_win32_font_attributes" data-raw-source="[character attributes](console-screen-buffers.md#_win32_font_attributes)">character attributes</a> in the high word.</span></span></p></td>
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

<a name="requirements"></a><span data-ttu-id="6c32a-135">規格需求</span><span class="sxs-lookup"><span data-stu-id="6c32a-135">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="6c32a-136">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="6c32a-136">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="6c32a-137">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="6c32a-137">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6c32a-138">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="6c32a-138">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="6c32a-139">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="6c32a-139">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6c32a-140">標頭</span><span class="sxs-lookup"><span data-stu-id="6c32a-140">Header</span></span></p></td>
<td><span data-ttu-id="6c32a-141">Winuser。h</span><span class="sxs-lookup"><span data-stu-id="6c32a-141">Winuser.h</span></span></td>
</tr>
</tbody>
</table>

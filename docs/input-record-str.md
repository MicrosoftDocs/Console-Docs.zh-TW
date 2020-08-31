---
title: INPUT_RECORD 結構
description: 請參閱在主控台輸入緩衝區中描述輸入事件的 INPUT_RECORD 結構相關參考資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- wincontypes/INPUT_RECORD
- wincon/INPUT_RECORD
- INPUT_RECORD
- wincontypes/PINPUT_RECORD
- wincon/PINPUT_RECORD
- PINPUT_RECORD
MS-HAID:
- '\_win32\_input\_record\_str'
- base.input\_record\_str
- consoles.input\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a46ba7fd-097a-455d-96ac-13aa01e11dc1
topic_type:
- apiref
api_name:
- INPUT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 5d532b5a009681e650991fd083f7d6ab932a05da
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059486"
---
# <a name="input_record-structure"></a><span data-ttu-id="748cf-104">輸入 \_ 記錄結構</span><span class="sxs-lookup"><span data-stu-id="748cf-104">INPUT\_RECORD structure</span></span>


<span data-ttu-id="748cf-105">描述主控台輸入緩衝區中的輸入事件。</span><span class="sxs-lookup"><span data-stu-id="748cf-105">Describes an input event in the console input buffer.</span></span> <span data-ttu-id="748cf-106">您可以使用 [**ReadConsoleInput**](readconsoleinput.md) 或 [**PeekConsoleInput**](peekconsoleinput.md) 函數從輸入緩衝區讀取這些記錄，或使用 [**WriteConsoleInput**](writeconsoleinput.md) 函式將它們寫入至輸入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="748cf-106">These records can be read from the input buffer by using the [**ReadConsoleInput**](readconsoleinput.md) or [**PeekConsoleInput**](peekconsoleinput.md) function, or written to the input buffer by using the [**WriteConsoleInput**](writeconsoleinput.md) function.</span></span>

<a name="syntax"></a><span data-ttu-id="748cf-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="748cf-107">Syntax</span></span>
------

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

<a name="members"></a><span data-ttu-id="748cf-108">成員</span><span class="sxs-lookup"><span data-stu-id="748cf-108">Members</span></span>
-------

<span data-ttu-id="748cf-109">**EventType**</span><span class="sxs-lookup"><span data-stu-id="748cf-109">**EventType**</span></span>  
<span data-ttu-id="748cf-110">輸入事件種類的控制碼和儲存在 **事件** 成員中的事件記錄。</span><span class="sxs-lookup"><span data-stu-id="748cf-110">A handle to the type of input event and the event record stored in the **Event** member.</span></span>

<span data-ttu-id="748cf-111">這個成員可以是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="748cf-111">This member can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="748cf-112">值</span><span class="sxs-lookup"><span data-stu-id="748cf-112">Value</span></span></th>
<th><span data-ttu-id="748cf-113">意義</span><span class="sxs-lookup"><span data-stu-id="748cf-113">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="748cf-114"><span id="FOCUS_EVENT"></span><span id="focus_event"></span>
<strong>FOCUS_EVENT</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="748cf-114"><span id="FOCUS_EVENT"></span><span id="focus_event"></span>
<strong>FOCUS_EVENT</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="748cf-115"><strong>事件</strong>成員包含<a href="focus-event-record-str.md" data-raw-source="[&lt;strong&gt;FOCUS_EVENT_RECORD&lt;/strong&gt;](focus-event-record-str.md)"><strong>FOCUS_EVENT_RECORD</strong></a>結構。</span><span class="sxs-lookup"><span data-stu-id="748cf-115">The <strong>Event</strong> member contains a <a href="focus-event-record-str.md" data-raw-source="[&lt;strong&gt;FOCUS_EVENT_RECORD&lt;/strong&gt;](focus-event-record-str.md)"><strong>FOCUS_EVENT_RECORD</strong></a> structure.</span></span> <span data-ttu-id="748cf-116">這些事件會在內部使用，應該予以忽略。</span><span class="sxs-lookup"><span data-stu-id="748cf-116">These events are used internally and should be ignored.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="748cf-117"><span id="KEY_EVENT"></span><span id="key_event"></span>
<strong>KEY_EVENT</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="748cf-117"><span id="KEY_EVENT"></span><span id="key_event"></span>
<strong>KEY_EVENT</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="748cf-118"><strong>事件</strong>成員包含具有鍵盤事件相關資訊的<a href="key-event-record-str.md" data-raw-source="[&lt;strong&gt;KEY_EVENT_RECORD&lt;/strong&gt;](key-event-record-str.md)"><strong>KEY_EVENT_RECORD</strong></a>結構。</span><span class="sxs-lookup"><span data-stu-id="748cf-118">The <strong>Event</strong> member contains a <a href="key-event-record-str.md" data-raw-source="[&lt;strong&gt;KEY_EVENT_RECORD&lt;/strong&gt;](key-event-record-str.md)"><strong>KEY_EVENT_RECORD</strong></a> structure with information about a keyboard event.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="748cf-119"><span id="MENU_EVENT"></span><span id="menu_event"></span>
<strong>MENU_EVENT</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="748cf-119"><span id="MENU_EVENT"></span><span id="menu_event"></span>
<strong>MENU_EVENT</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="748cf-120"><strong>事件</strong>成員包含<a href="menu-event-record-str.md" data-raw-source="[&lt;strong&gt;MENU_EVENT_RECORD&lt;/strong&gt;](menu-event-record-str.md)"><strong>MENU_EVENT_RECORD</strong></a>結構。</span><span class="sxs-lookup"><span data-stu-id="748cf-120">The <strong>Event</strong> member contains a <a href="menu-event-record-str.md" data-raw-source="[&lt;strong&gt;MENU_EVENT_RECORD&lt;/strong&gt;](menu-event-record-str.md)"><strong>MENU_EVENT_RECORD</strong></a> structure.</span></span> <span data-ttu-id="748cf-121">這些事件會在內部使用，應該予以忽略。</span><span class="sxs-lookup"><span data-stu-id="748cf-121">These events are used internally and should be ignored.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="748cf-122"><span id="MOUSE_EVENT"></span><span id="mouse_event"></span>
<strong>MOUSE_EVENT</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="748cf-122"><span id="MOUSE_EVENT"></span><span id="mouse_event"></span>
<strong>MOUSE_EVENT</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="748cf-123"><strong>事件</strong>成員包含<a href="mouse-event-record-str.md" data-raw-source="[&lt;strong&gt;MOUSE_EVENT_RECORD&lt;/strong&gt;](mouse-event-record-str.md)"><strong>MOUSE_EVENT_RECORD</strong></a>結構，其中包含滑鼠移動或按鈕按下事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="748cf-123">The <strong>Event</strong> member contains a <a href="mouse-event-record-str.md" data-raw-source="[&lt;strong&gt;MOUSE_EVENT_RECORD&lt;/strong&gt;](mouse-event-record-str.md)"><strong>MOUSE_EVENT_RECORD</strong></a> structure with information about a mouse movement or button press event.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="748cf-124"><span id="WINDOW_BUFFER_SIZE_EVENT"></span><span id="window_buffer_size_event"></span>
<strong>WINDOW_BUFFER_SIZE_EVENT</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="748cf-124"><span id="WINDOW_BUFFER_SIZE_EVENT"></span><span id="window_buffer_size_event"></span>
<strong>WINDOW_BUFFER_SIZE_EVENT</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="748cf-125"><strong>事件</strong>成員包含<a href="window-buffer-size-record-str.md" data-raw-source="[&lt;strong&gt;WINDOW_BUFFER_SIZE_RECORD&lt;/strong&gt;](window-buffer-size-record-str.md)"><strong>WINDOW_BUFFER_SIZE_RECORD</strong></a>結構，以及主控台螢幕緩衝區新大小的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="748cf-125">The <strong>Event</strong> member contains a <a href="window-buffer-size-record-str.md" data-raw-source="[&lt;strong&gt;WINDOW_BUFFER_SIZE_RECORD&lt;/strong&gt;](window-buffer-size-record-str.md)"><strong>WINDOW_BUFFER_SIZE_RECORD</strong></a> structure with information about the new size of the console screen buffer.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="748cf-126">**事件**</span><span class="sxs-lookup"><span data-stu-id="748cf-126">**Event**</span></span>  
<span data-ttu-id="748cf-127">事件資訊。</span><span class="sxs-lookup"><span data-stu-id="748cf-127">The event information.</span></span> <span data-ttu-id="748cf-128">此成員的格式取決 **于事件種類成員所** 指定的事件種類。</span><span class="sxs-lookup"><span data-stu-id="748cf-128">The format of this member depends on the event type specified by the **EventType** member.</span></span>

<a name="examples"></a><span data-ttu-id="748cf-129">範例</span><span class="sxs-lookup"><span data-stu-id="748cf-129">Examples</span></span>
--------

<span data-ttu-id="748cf-130">如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。</span><span class="sxs-lookup"><span data-stu-id="748cf-130">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="748cf-131">規格需求</span><span class="sxs-lookup"><span data-stu-id="748cf-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="748cf-132">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="748cf-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="748cf-133">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="748cf-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="748cf-134">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="748cf-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="748cf-135">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="748cf-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="748cf-136">標頭</span><span class="sxs-lookup"><span data-stu-id="748cf-136">Header</span></span></p></td>
<td><span data-ttu-id="748cf-137">WinConTypes .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="748cf-137">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="748cf-138"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="748cf-138"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="748cf-139">**焦點 \_ 事件 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="748cf-139">**FOCUS\_EVENT\_RECORD**</span></span>](focus-event-record-str.md)

[<span data-ttu-id="748cf-140">**關鍵 \_ 事件 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="748cf-140">**KEY\_EVENT\_RECORD**</span></span>](key-event-record-str.md)

[<span data-ttu-id="748cf-141">**功能表 \_ 事件 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="748cf-141">**MENU\_EVENT\_RECORD**</span></span>](menu-event-record-str.md)

[<span data-ttu-id="748cf-142">**滑鼠 \_ 事件 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="748cf-142">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="748cf-143">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="748cf-143">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="748cf-144">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="748cf-144">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="748cf-145">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="748cf-145">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 





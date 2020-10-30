---
title: INPUT_RECORD 結構
description: 請參閱在主控台輸入緩衝區中描述輸入事件的 INPUT_RECORD 結構相關參考資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4ad86de170c1fef74f133a5d5c51d8de2dea497f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038536"
---
# <a name="input_record-structure"></a><span data-ttu-id="9de7a-104">輸入 \_ 記錄結構</span><span class="sxs-lookup"><span data-stu-id="9de7a-104">INPUT\_RECORD structure</span></span>

<span data-ttu-id="9de7a-105">描述主控台輸入緩衝區中的輸入事件。</span><span class="sxs-lookup"><span data-stu-id="9de7a-105">Describes an input event in the console input buffer.</span></span> <span data-ttu-id="9de7a-106">您可以使用 [**ReadConsoleInput**](readconsoleinput.md) 或 [**PeekConsoleInput**](peekconsoleinput.md) 函數從輸入緩衝區讀取這些記錄，或使用 [**WriteConsoleInput**](writeconsoleinput.md) 函式將它們寫入至輸入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9de7a-106">These records can be read from the input buffer by using the [**ReadConsoleInput**](readconsoleinput.md) or [**PeekConsoleInput**](peekconsoleinput.md) function, or written to the input buffer by using the [**WriteConsoleInput**](writeconsoleinput.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="9de7a-107">語法</span><span class="sxs-lookup"><span data-stu-id="9de7a-107">Syntax</span></span>

```C
typedef struct _INPUT_RECORD {
  WORD  EventType;
  union {
    KEY_EVENT_RECORD          KeyEvent;
    MOUSE_EVENT_RECORD        MouseEvent;
    WINDOW_BUFFER_SIZE_RECORD WindowBufferSizeEvent;
    MENU_EVENT_RECORD         MenuEvent;
    FOCUS_EVENT_RECORD        FocusEvent;
  } Event;
} INPUT_RECORD;
```

## <a name="members"></a><span data-ttu-id="9de7a-108">成員</span><span class="sxs-lookup"><span data-stu-id="9de7a-108">Members</span></span>

<span data-ttu-id="9de7a-109">**EventType**</span><span class="sxs-lookup"><span data-stu-id="9de7a-109">**EventType**</span></span>  
<span data-ttu-id="9de7a-110">輸入事件種類的控制碼和儲存在 **事件** 成員中的事件記錄。</span><span class="sxs-lookup"><span data-stu-id="9de7a-110">A handle to the type of input event and the event record stored in the **Event** member.</span></span>

<span data-ttu-id="9de7a-111">這個成員可以是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="9de7a-111">This member can be one of the following values.</span></span>

| <span data-ttu-id="9de7a-112">值</span><span class="sxs-lookup"><span data-stu-id="9de7a-112">Value</span></span> | <span data-ttu-id="9de7a-113">意義</span><span class="sxs-lookup"><span data-stu-id="9de7a-113">Meaning</span></span> |
|-|-|
| <span data-ttu-id="9de7a-114">**FOCUS_EVENT** 0x0010</span><span class="sxs-lookup"><span data-stu-id="9de7a-114">**FOCUS_EVENT** 0x0010</span></span> | <span data-ttu-id="9de7a-115">**事件** 成員包含 **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** 結構。</span><span class="sxs-lookup"><span data-stu-id="9de7a-115">The **Event** member contains a **[FOCUS_EVENT_RECORD](focus-event-record-str.md)** structure.</span></span> <span data-ttu-id="9de7a-116">這些事件會在內部使用，應該予以忽略。</span><span class="sxs-lookup"><span data-stu-id="9de7a-116">These events are used internally and should be ignored.</span></span> |
| <span data-ttu-id="9de7a-117">**KEY_EVENT** 0x0001</span><span class="sxs-lookup"><span data-stu-id="9de7a-117">**KEY_EVENT** 0x0001</span></span> | <span data-ttu-id="9de7a-118">**事件** 成員包含具有鍵盤事件相關資訊的 **[KEY_EVENT_RECORD](key-event-record-str.md)** 結構。</span><span class="sxs-lookup"><span data-stu-id="9de7a-118">The **Event** member contains a **[KEY_EVENT_RECORD](key-event-record-str.md)** structure with information about a keyboard event.</span></span> |
| <span data-ttu-id="9de7a-119">**MENU_EVENT** 0x0008</span><span class="sxs-lookup"><span data-stu-id="9de7a-119">**MENU_EVENT** 0x0008</span></span> | <span data-ttu-id="9de7a-120">**事件** 成員包含 **[MENU_EVENT_RECORD](menu-event-record-str.md)** 結構。</span><span class="sxs-lookup"><span data-stu-id="9de7a-120">The **Event** member contains a **[MENU_EVENT_RECORD](menu-event-record-str.md)** structure.</span></span> <span data-ttu-id="9de7a-121">這些事件會在內部使用，應該予以忽略。</span><span class="sxs-lookup"><span data-stu-id="9de7a-121">These events are used internally and should be ignored.</span></span> |
| <span data-ttu-id="9de7a-122">**MOUSE_EVENT** 0x0002</span><span class="sxs-lookup"><span data-stu-id="9de7a-122">**MOUSE_EVENT** 0x0002</span></span> | <span data-ttu-id="9de7a-123">**事件** 成員包含 **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** 結構，其中包含滑鼠移動或按鈕按下事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9de7a-123">The **Event** member contains a **[MOUSE_EVENT_RECORD](mouse-event-record-str.md)** structure with information about a mouse movement or button press event.</span></span> |
| <span data-ttu-id="9de7a-124">**WINDOW_BUFFER_SIZE_EVENT** 0x0004</span><span class="sxs-lookup"><span data-stu-id="9de7a-124">**WINDOW_BUFFER_SIZE_EVENT** 0x0004</span></span> | <span data-ttu-id="9de7a-125">**事件** 成員包含 **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** 結構，以及主控台螢幕緩衝區新大小的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9de7a-125">The **Event** member contains a **[WINDOW_BUFFER_SIZE_RECORD](window-buffer-size-record-str.md)** structure with information about the new size of the console screen buffer.</span></span> |

<span data-ttu-id="9de7a-126">**事件**</span><span class="sxs-lookup"><span data-stu-id="9de7a-126">**Event**</span></span>  
<span data-ttu-id="9de7a-127">事件資訊。</span><span class="sxs-lookup"><span data-stu-id="9de7a-127">The event information.</span></span> <span data-ttu-id="9de7a-128">此成員的格式取決 **于事件種類成員所** 指定的事件種類。</span><span class="sxs-lookup"><span data-stu-id="9de7a-128">The format of this member depends on the event type specified by the **EventType** member.</span></span>

## <a name="examples"></a><span data-ttu-id="9de7a-129">範例</span><span class="sxs-lookup"><span data-stu-id="9de7a-129">Examples</span></span>

<span data-ttu-id="9de7a-130">如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。</span><span class="sxs-lookup"><span data-stu-id="9de7a-130">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="9de7a-131">規格需求</span><span class="sxs-lookup"><span data-stu-id="9de7a-131">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9de7a-132">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="9de7a-132">Minimum supported client</span></span> | <span data-ttu-id="9de7a-133">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="9de7a-133">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="9de7a-134">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="9de7a-134">Minimum supported server</span></span> | <span data-ttu-id="9de7a-135">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="9de7a-135">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="9de7a-136">標頭</span><span class="sxs-lookup"><span data-stu-id="9de7a-136">Header</span></span> | <span data-ttu-id="9de7a-137">WinConTypes .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="9de7a-137">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="9de7a-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="9de7a-138">See also</span></span>

[<span data-ttu-id="9de7a-139">**焦點 \_ 事件 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="9de7a-139">**FOCUS\_EVENT\_RECORD**</span></span>](focus-event-record-str.md)

[<span data-ttu-id="9de7a-140">**關鍵 \_ 事件 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="9de7a-140">**KEY\_EVENT\_RECORD**</span></span>](key-event-record-str.md)

[<span data-ttu-id="9de7a-141">**功能表 \_ 事件 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="9de7a-141">**MENU\_EVENT\_RECORD**</span></span>](menu-event-record-str.md)

[<span data-ttu-id="9de7a-142">**滑鼠 \_ 事件 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="9de7a-142">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="9de7a-143">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="9de7a-143">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="9de7a-144">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="9de7a-144">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="9de7a-145">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="9de7a-145">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

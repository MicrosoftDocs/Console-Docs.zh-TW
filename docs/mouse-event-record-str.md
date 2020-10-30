---
title: MOUSE_EVENT_RECORD 結構
description: 請參閱 MOUSE_EVENT_RECORD 結構的參考資訊，其描述主控台 INPUT_RECORD 結構中的滑鼠輸入事件。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- wincontypes/MOUSE_EVENT_RECORD
- wincon/MOUSE_EVENT_RECORD
- MOUSE_EVENT_RECORD
- wincontypes/PMOUSE_EVENT_RECORD
- wincon/PMOUSE_EVENT_RECORD
- PMOUSE_EVENT_RECORD
MS-HAID:
- '\_win32\_mouse\_event\_record\_str'
- base.mouse\_event\_record\_str
- consoles.mouse\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ea54c6-8872-4111-8d72-1377409b9247
topic_type:
- apiref
api_name:
- MOUSE_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: c10047d1386f3bce1546ee21bacdc81b8fb7bb55
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038516"
---
# <a name="mouse_event_record-structure"></a><span data-ttu-id="c82d2-104">滑鼠 \_ 事件 \_ 記錄結構</span><span class="sxs-lookup"><span data-stu-id="c82d2-104">MOUSE\_EVENT\_RECORD structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="c82d2-105">描述主控台 [**輸入 \_ 記錄**](input-record-str.md) 結構中的滑鼠輸入事件。</span><span class="sxs-lookup"><span data-stu-id="c82d2-105">Describes a mouse input event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="c82d2-106">語法</span><span class="sxs-lookup"><span data-stu-id="c82d2-106">Syntax</span></span>

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

## <a name="members"></a><span data-ttu-id="c82d2-107">成員</span><span class="sxs-lookup"><span data-stu-id="c82d2-107">Members</span></span>

<span data-ttu-id="c82d2-108">**dwMousePosition**</span><span class="sxs-lookup"><span data-stu-id="c82d2-108">**dwMousePosition**</span></span>  
<span data-ttu-id="c82d2-109">[**COORD**](coord-str.md)結構，其中包含游標的位置，以主控台螢幕緩衝區的字元儲存格座標為單位。</span><span class="sxs-lookup"><span data-stu-id="c82d2-109">A [**COORD**](coord-str.md) structure that contains the location of the cursor, in terms of the console screen buffer's character-cell coordinates.</span></span>

<span data-ttu-id="c82d2-110">**dwButtonState**</span><span class="sxs-lookup"><span data-stu-id="c82d2-110">**dwButtonState**</span></span>  
<span data-ttu-id="c82d2-111">滑鼠按鍵的狀態。</span><span class="sxs-lookup"><span data-stu-id="c82d2-111">The status of the mouse buttons.</span></span> <span data-ttu-id="c82d2-112">最不重要的位會對應到最左邊的滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="c82d2-112">The least significant bit corresponds to the leftmost mouse button.</span></span> <span data-ttu-id="c82d2-113">下一個最小的位會對應至最右邊的滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="c82d2-113">The next least significant bit corresponds to the rightmost mouse button.</span></span> <span data-ttu-id="c82d2-114">下個位表示從下到左的滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="c82d2-114">The next bit indicates the next-to-leftmost mouse button.</span></span> <span data-ttu-id="c82d2-115">然後，位會從左至右對應至滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="c82d2-115">The bits then correspond left to right to the mouse buttons.</span></span> <span data-ttu-id="c82d2-116">如果已按下按鈕，則位為1。</span><span class="sxs-lookup"><span data-stu-id="c82d2-116">A bit is 1 if the button was pressed.</span></span>

<span data-ttu-id="c82d2-117">以下是前五個滑鼠按鍵的定義常數。</span><span class="sxs-lookup"><span data-stu-id="c82d2-117">The following constants are defined for the first five mouse buttons.</span></span>

| <span data-ttu-id="c82d2-118">值</span><span class="sxs-lookup"><span data-stu-id="c82d2-118">Value</span></span> | <span data-ttu-id="c82d2-119">意義</span><span class="sxs-lookup"><span data-stu-id="c82d2-119">Meaning</span></span> |
|-|-|
| <span data-ttu-id="c82d2-120">**FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="c82d2-120">**FROM_LEFT_1ST_BUTTON_PRESSED** 0x0001</span></span> | <span data-ttu-id="c82d2-121">最左邊的滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="c82d2-121">The leftmost mouse button.</span></span> |
| <span data-ttu-id="c82d2-122">**FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="c82d2-122">**FROM_LEFT_2ND_BUTTON_PRESSED** 0x0004</span></span> | <span data-ttu-id="c82d2-123">第二個按鈕從左邊。</span><span class="sxs-lookup"><span data-stu-id="c82d2-123">The second button fom the left.</span></span> |
| <span data-ttu-id="c82d2-124">**FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="c82d2-124">**FROM_LEFT_3RD_BUTTON_PRESSED** 0x0008</span></span> | <span data-ttu-id="c82d2-125">左邊的第三個按鈕。</span><span class="sxs-lookup"><span data-stu-id="c82d2-125">The third button from the left.</span></span> |
| <span data-ttu-id="c82d2-126">**FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010</span><span class="sxs-lookup"><span data-stu-id="c82d2-126">**FROM_LEFT_4TH_BUTTON_PRESSED** 0x0010</span></span> | <span data-ttu-id="c82d2-127">左邊的第四個按鈕。</span><span class="sxs-lookup"><span data-stu-id="c82d2-127">The fourth button from the left.</span></span> |
| <span data-ttu-id="c82d2-128">**RIGHTMOST_BUTTON_PRESSED** 0x0002</span><span class="sxs-lookup"><span data-stu-id="c82d2-128">**RIGHTMOST_BUTTON_PRESSED** 0x0002</span></span> | <span data-ttu-id="c82d2-129">最右邊的滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="c82d2-129">The rightmost mouse button.</span></span> |

<span data-ttu-id="c82d2-130">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="c82d2-130">**dwControlKeyState**</span></span>  
<span data-ttu-id="c82d2-131">控制項索引鍵的狀態。</span><span class="sxs-lookup"><span data-stu-id="c82d2-131">The state of the control keys.</span></span> <span data-ttu-id="c82d2-132">這個成員可以是下列一或多個值。</span><span class="sxs-lookup"><span data-stu-id="c82d2-132">This member can be one or more of the following values.</span></span>

| <span data-ttu-id="c82d2-133">值</span><span class="sxs-lookup"><span data-stu-id="c82d2-133">Value</span></span> | <span data-ttu-id="c82d2-134">意義</span><span class="sxs-lookup"><span data-stu-id="c82d2-134">Meaning</span></span> |
|-|-|
| <span data-ttu-id="c82d2-135">**CAPSLOCK_ON** 0x0080</span><span class="sxs-lookup"><span data-stu-id="c82d2-135">**CAPSLOCK_ON** 0x0080</span></span> | <span data-ttu-id="c82d2-136">CAPS LOCK 燈開啟。</span><span class="sxs-lookup"><span data-stu-id="c82d2-136">The CAPS LOCK light is on.</span></span> |
| <span data-ttu-id="c82d2-137">**ENHANCED_KEY** 0x0100</span><span class="sxs-lookup"><span data-stu-id="c82d2-137">**ENHANCED_KEY** 0x0100</span></span> | <span data-ttu-id="c82d2-138">金鑰已增強。</span><span class="sxs-lookup"><span data-stu-id="c82d2-138">The key is enhanced.</span></span> <span data-ttu-id="c82d2-139">請參閱 [備註](key-event-record-str.md#remarks)。</span><span class="sxs-lookup"><span data-stu-id="c82d2-139">See [remarks](key-event-record-str.md#remarks).</span></span> |
| <span data-ttu-id="c82d2-140">**LEFT_ALT_PRESSED** 0x0002</span><span class="sxs-lookup"><span data-stu-id="c82d2-140">**LEFT_ALT_PRESSED** 0x0002</span></span> | <span data-ttu-id="c82d2-141">左 ALT 鍵已按下。</span><span class="sxs-lookup"><span data-stu-id="c82d2-141">The left ALT key is pressed.</span></span> |
| <span data-ttu-id="c82d2-142">**LEFT_CTRL_PRESSED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="c82d2-142">**LEFT_CTRL_PRESSED** 0x0008</span></span> | <span data-ttu-id="c82d2-143">按下 CTRL 鍵。</span><span class="sxs-lookup"><span data-stu-id="c82d2-143">The left CTRL key is pressed.</span></span> |
| <span data-ttu-id="c82d2-144">**NUMLOCK_ON** 0x0020</span><span class="sxs-lookup"><span data-stu-id="c82d2-144">**NUMLOCK_ON** 0x0020</span></span> | <span data-ttu-id="c82d2-145">NUM LOCK 燈開啟。</span><span class="sxs-lookup"><span data-stu-id="c82d2-145">The NUM LOCK light is on.</span></span> |
| <span data-ttu-id="c82d2-146">**RIGHT_ALT_PRESSED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="c82d2-146">**RIGHT_ALT_PRESSED** 0x0001</span></span> | <span data-ttu-id="c82d2-147">按下右邊的 ALT 鍵。</span><span class="sxs-lookup"><span data-stu-id="c82d2-147">The right ALT key is pressed.</span></span> |
| <span data-ttu-id="c82d2-148">**RIGHT_CTRL_PRESSED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="c82d2-148">**RIGHT_CTRL_PRESSED** 0x0004</span></span> | <span data-ttu-id="c82d2-149">按下 CTRL 鍵。</span><span class="sxs-lookup"><span data-stu-id="c82d2-149">The right CTRL key is pressed.</span></span> |
| <span data-ttu-id="c82d2-150">**SCROLLLOCK_ON** 0x0040</span><span class="sxs-lookup"><span data-stu-id="c82d2-150">**SCROLLLOCK_ON** 0x0040</span></span> | <span data-ttu-id="c82d2-151">捲軸鎖定燈開啟。</span><span class="sxs-lookup"><span data-stu-id="c82d2-151">The SCROLL LOCK light is on.</span></span> |
| <span data-ttu-id="c82d2-152">**SHIFT_PRESSED** 0x0010</span><span class="sxs-lookup"><span data-stu-id="c82d2-152">**SHIFT_PRESSED** 0x0010</span></span> | <span data-ttu-id="c82d2-153">按下 SHIFT 鍵。</span><span class="sxs-lookup"><span data-stu-id="c82d2-153">The SHIFT key is pressed.</span></span> |

<span data-ttu-id="c82d2-154">**dwEventFlags**</span><span class="sxs-lookup"><span data-stu-id="c82d2-154">**dwEventFlags**</span></span>  
<span data-ttu-id="c82d2-155">滑鼠事件的類型。</span><span class="sxs-lookup"><span data-stu-id="c82d2-155">The type of mouse event.</span></span> <span data-ttu-id="c82d2-156">如果這個值為零，表示已按下或放開滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="c82d2-156">If this value is zero, it indicates a mouse button being pressed or released.</span></span> <span data-ttu-id="c82d2-157">否則，此成員會是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="c82d2-157">Otherwise, this member is one of the following values.</span></span>

| <span data-ttu-id="c82d2-158">值</span><span class="sxs-lookup"><span data-stu-id="c82d2-158">Value</span></span> | <span data-ttu-id="c82d2-159">意義</span><span class="sxs-lookup"><span data-stu-id="c82d2-159">Meaning</span></span> |
|-|-|
| <span data-ttu-id="c82d2-160">**DOUBLE_CLICK** 0x0002</span><span class="sxs-lookup"><span data-stu-id="c82d2-160">**DOUBLE_CLICK** 0x0002</span></span> | <span data-ttu-id="c82d2-161">第二次按一下 (按鈕時，請按下滑鼠按鍵) 。</span><span class="sxs-lookup"><span data-stu-id="c82d2-161">The second click (button press) of a double-click occurred.</span></span> <span data-ttu-id="c82d2-162">第一次按一下會以一般按鈕按下事件的方式傳回。</span><span class="sxs-lookup"><span data-stu-id="c82d2-162">The first click is returned as a regular button-press event.</span></span> |
| <span data-ttu-id="c82d2-163">**MOUSE_HWHEELED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="c82d2-163">**MOUSE_HWHEELED** 0x0008</span></span> | <span data-ttu-id="c82d2-164">移動了水準滑鼠滾輪。</span><span class="sxs-lookup"><span data-stu-id="c82d2-164">The horizontal mouse wheel was moved.</span></span><br /><br /><span data-ttu-id="c82d2-165">如果 **dwButtonState** 成員的最大文字包含正值，滾輪就會向右旋轉。</span><span class="sxs-lookup"><span data-stu-id="c82d2-165">If the high word of the **dwButtonState** member contains a positive value, the wheel was rotated to the right.</span></span> <span data-ttu-id="c82d2-166">否則，滾輪會旋轉至左方。</span><span class="sxs-lookup"><span data-stu-id="c82d2-166">Otherwise, the wheel was rotated to the left.</span></span> |
| <span data-ttu-id="c82d2-167">**MOUSE_MOVED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="c82d2-167">**MOUSE_MOVED** 0x0001</span></span> | <span data-ttu-id="c82d2-168">發生滑鼠位置變更。</span><span class="sxs-lookup"><span data-stu-id="c82d2-168">A change in mouse position occurred.</span></span> |
| <span data-ttu-id="c82d2-169">**MOUSE_WHEELED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="c82d2-169">**MOUSE_WHEELED** 0x0004</span></span> | <span data-ttu-id="c82d2-170">移動了垂直滑鼠滾輪。</span><span class="sxs-lookup"><span data-stu-id="c82d2-170">The vertical mouse wheel was moved.</span></span><br /><br /><span data-ttu-id="c82d2-171">如果 **dwButtonState** 成員的高單字包含正值，則滾輪會向前旋轉，而不是使用者。</span><span class="sxs-lookup"><span data-stu-id="c82d2-171">If the high word of the **dwButtonState** member contains a positive value, the wheel was rotated forward, away from the user.</span></span> <span data-ttu-id="c82d2-172">否則，滾輪會向使用者旋轉。</span><span class="sxs-lookup"><span data-stu-id="c82d2-172">Otherwise, the wheel was rotated backward, toward the user.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c82d2-173">備註</span><span class="sxs-lookup"><span data-stu-id="c82d2-173">Remarks</span></span>

<span data-ttu-id="c82d2-174">當主控台處於滑鼠模式時，滑鼠事件會放置在輸入緩衝區中 ( **啟用 \_ 滑鼠 \_ 輸入** ) 。</span><span class="sxs-lookup"><span data-stu-id="c82d2-174">Mouse events are placed in the input buffer when the console is in mouse mode ( **ENABLE\_MOUSE\_INPUT** ).</span></span>

<span data-ttu-id="c82d2-175">每當使用者移動滑鼠或按下或放開其中一個滑鼠按鍵時，就會產生滑鼠事件。</span><span class="sxs-lookup"><span data-stu-id="c82d2-175">Mouse events are generated whenever the user moves the mouse, or presses or releases one of the mouse buttons.</span></span> <span data-ttu-id="c82d2-176">只有當主控台群組具有鍵盤焦點，且游標位於主控台視窗的框線內時，滑鼠事件才會放在主控台的輸入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="c82d2-176">Mouse events are placed in a console's input buffer only when the console group has the keyboard focus and the cursor is within the borders of the console's window.</span></span>

## <a name="examples"></a><span data-ttu-id="c82d2-177">範例</span><span class="sxs-lookup"><span data-stu-id="c82d2-177">Examples</span></span>

<span data-ttu-id="c82d2-178">如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。</span><span class="sxs-lookup"><span data-stu-id="c82d2-178">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="c82d2-179">規格需求</span><span class="sxs-lookup"><span data-stu-id="c82d2-179">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c82d2-180">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="c82d2-180">Minimum supported client</span></span> | <span data-ttu-id="c82d2-181">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="c82d2-181">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="c82d2-182">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="c82d2-182">Minimum supported server</span></span> | <span data-ttu-id="c82d2-183">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="c82d2-183">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="c82d2-184">標頭</span><span class="sxs-lookup"><span data-stu-id="c82d2-184">Header</span></span> | <span data-ttu-id="c82d2-185">WinConTypes .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="c82d2-185">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="c82d2-186">請參閱</span><span class="sxs-lookup"><span data-stu-id="c82d2-186">See also</span></span>

[<span data-ttu-id="c82d2-187">**COORD**</span><span class="sxs-lookup"><span data-stu-id="c82d2-187">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="c82d2-188">**輸入 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="c82d2-188">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="c82d2-189">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="c82d2-189">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="c82d2-190">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="c82d2-190">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="c82d2-191">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="c82d2-191">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

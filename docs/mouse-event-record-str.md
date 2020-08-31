---
title: MOUSE_EVENT_RECORD 結構
description: 請參閱 MOUSE_EVENT_RECORD 結構的參考資訊，其描述主控台 INPUT_RECORD 結構中的滑鼠輸入事件。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: a3e95e9d35cdf2af2ec6836021dd8819323a4790
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059062"
---
# <a name="mouse_event_record-structure"></a><span data-ttu-id="e98b6-104">滑鼠 \_ 事件 \_ 記錄結構</span><span class="sxs-lookup"><span data-stu-id="e98b6-104">MOUSE\_EVENT\_RECORD structure</span></span>


<span data-ttu-id="e98b6-105">描述主控台 [**輸入 \_ 記錄**](input-record-str.md) 結構中的滑鼠輸入事件。</span><span class="sxs-lookup"><span data-stu-id="e98b6-105">Describes a mouse input event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span>

<a name="syntax"></a><span data-ttu-id="e98b6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e98b6-106">Syntax</span></span>
------

```C
typedef struct _MOUSE_EVENT_RECORD {
  COORD dwMousePosition;
  DWORD dwButtonState;
  DWORD dwControlKeyState;
  DWORD dwEventFlags;
} MOUSE_EVENT_RECORD;
```

<a name="members"></a><span data-ttu-id="e98b6-107">成員</span><span class="sxs-lookup"><span data-stu-id="e98b6-107">Members</span></span>
-------

<span data-ttu-id="e98b6-108">**dwMousePosition**</span><span class="sxs-lookup"><span data-stu-id="e98b6-108">**dwMousePosition**</span></span>  
<span data-ttu-id="e98b6-109">[**COORD**](coord-str.md)結構，其中包含游標的位置，以主控台螢幕緩衝區的字元儲存格座標為單位。</span><span class="sxs-lookup"><span data-stu-id="e98b6-109">A [**COORD**](coord-str.md) structure that contains the location of the cursor, in terms of the console screen buffer's character-cell coordinates.</span></span>

<span data-ttu-id="e98b6-110">**dwButtonState**</span><span class="sxs-lookup"><span data-stu-id="e98b6-110">**dwButtonState**</span></span>  
<span data-ttu-id="e98b6-111">滑鼠按鍵的狀態。</span><span class="sxs-lookup"><span data-stu-id="e98b6-111">The status of the mouse buttons.</span></span> <span data-ttu-id="e98b6-112">最不重要的位會對應到最左邊的滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="e98b6-112">The least significant bit corresponds to the leftmost mouse button.</span></span> <span data-ttu-id="e98b6-113">下一個最小的位會對應至最右邊的滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="e98b6-113">The next least significant bit corresponds to the rightmost mouse button.</span></span> <span data-ttu-id="e98b6-114">下個位表示從下到左的滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="e98b6-114">The next bit indicates the next-to-leftmost mouse button.</span></span> <span data-ttu-id="e98b6-115">然後，位會從左至右對應至滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="e98b6-115">The bits then correspond left to right to the mouse buttons.</span></span> <span data-ttu-id="e98b6-116">如果已按下按鈕，則位為1。</span><span class="sxs-lookup"><span data-stu-id="e98b6-116">A bit is 1 if the button was pressed.</span></span>

<span data-ttu-id="e98b6-117">以下是前五個滑鼠按鍵的定義常數。</span><span class="sxs-lookup"><span data-stu-id="e98b6-117">The following constants are defined for the first five mouse buttons.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="e98b6-118">值</span><span class="sxs-lookup"><span data-stu-id="e98b6-118">Value</span></span></th>
<th><span data-ttu-id="e98b6-119">意義</span><span class="sxs-lookup"><span data-stu-id="e98b6-119">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="e98b6-120"><span id="FROM_LEFT_1ST_BUTTON_PRESSED"></span><span id="from_left_1st_button_pressed"></span>
<strong>FROM_LEFT_1ST_BUTTON_PRESSED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="e98b6-120"><span id="FROM_LEFT_1ST_BUTTON_PRESSED"></span><span id="from_left_1st_button_pressed"></span>
<strong>FROM_LEFT_1ST_BUTTON_PRESSED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="e98b6-121">最左邊的滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="e98b6-121">The leftmost mouse button.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e98b6-122"><span id="FROM_LEFT_2ND_BUTTON_PRESSED"></span><span id="from_left_2nd_button_pressed"></span>
<strong>FROM_LEFT_2ND_BUTTON_PRESSED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="e98b6-122"><span id="FROM_LEFT_2ND_BUTTON_PRESSED"></span><span id="from_left_2nd_button_pressed"></span>
<strong>FROM_LEFT_2ND_BUTTON_PRESSED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="e98b6-123">左邊的第二個按鈕。</span><span class="sxs-lookup"><span data-stu-id="e98b6-123">The second button from the left.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e98b6-124"><span id="FROM_LEFT_3RD_BUTTON_PRESSED"></span><span id="from_left_3rd_button_pressed"></span>
<strong>FROM_LEFT_3RD_BUTTON_PRESSED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="e98b6-124"><span id="FROM_LEFT_3RD_BUTTON_PRESSED"></span><span id="from_left_3rd_button_pressed"></span>
<strong>FROM_LEFT_3RD_BUTTON_PRESSED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="e98b6-125">左邊的第三個按鈕。</span><span class="sxs-lookup"><span data-stu-id="e98b6-125">The third button from the left.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e98b6-126"><span id="FROM_LEFT_4TH_BUTTON_PRESSED"></span><span id="from_left_4th_button_pressed"></span>
<strong>FROM_LEFT_4TH_BUTTON_PRESSED</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="e98b6-126"><span id="FROM_LEFT_4TH_BUTTON_PRESSED"></span><span id="from_left_4th_button_pressed"></span>
<strong>FROM_LEFT_4TH_BUTTON_PRESSED</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="e98b6-127">左邊的第四個按鈕。</span><span class="sxs-lookup"><span data-stu-id="e98b6-127">The fourth button from the left.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e98b6-128"><span id="RIGHTMOST_BUTTON_PRESSED"></span><span id="rightmost_button_pressed"></span>
<strong>RIGHTMOST_BUTTON_PRESSED</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="e98b6-128"><span id="RIGHTMOST_BUTTON_PRESSED"></span><span id="rightmost_button_pressed"></span>
<strong>RIGHTMOST_BUTTON_PRESSED</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="e98b6-129">最右邊的滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="e98b6-129">The rightmost mouse button.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="e98b6-130">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="e98b6-130">**dwControlKeyState**</span></span>  
<span data-ttu-id="e98b6-131">控制項索引鍵的狀態。</span><span class="sxs-lookup"><span data-stu-id="e98b6-131">The state of the control keys.</span></span> <span data-ttu-id="e98b6-132">這個成員可以是下列一或多個值。</span><span class="sxs-lookup"><span data-stu-id="e98b6-132">This member can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="e98b6-133">值</span><span class="sxs-lookup"><span data-stu-id="e98b6-133">Value</span></span></th>
<th><span data-ttu-id="e98b6-134">意義</span><span class="sxs-lookup"><span data-stu-id="e98b6-134">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="e98b6-135"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="e98b6-135"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="e98b6-136">CAPS LOCK 燈開啟。</span><span class="sxs-lookup"><span data-stu-id="e98b6-136">The CAPS LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e98b6-137"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span><span class="sxs-lookup"><span data-stu-id="e98b6-137"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span></span></td>
<td><p><span data-ttu-id="e98b6-138">金鑰已增強。</span><span class="sxs-lookup"><span data-stu-id="e98b6-138">The key is enhanced.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e98b6-139"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="e98b6-139"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="e98b6-140">左 ALT 鍵已按下。</span><span class="sxs-lookup"><span data-stu-id="e98b6-140">The left ALT key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e98b6-141"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="e98b6-141"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="e98b6-142">按下 CTRL 鍵。</span><span class="sxs-lookup"><span data-stu-id="e98b6-142">The left CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e98b6-143"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="e98b6-143"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="e98b6-144">NUM LOCK 燈開啟。</span><span class="sxs-lookup"><span data-stu-id="e98b6-144">The NUM LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e98b6-145"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="e98b6-145"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="e98b6-146">按下右邊的 ALT 鍵。</span><span class="sxs-lookup"><span data-stu-id="e98b6-146">The right ALT key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e98b6-147"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="e98b6-147"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="e98b6-148">按下 CTRL 鍵。</span><span class="sxs-lookup"><span data-stu-id="e98b6-148">The right CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e98b6-149"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="e98b6-149"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="e98b6-150">捲軸鎖定燈開啟。</span><span class="sxs-lookup"><span data-stu-id="e98b6-150">The SCROLL LOCK light is on.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e98b6-151"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="e98b6-151"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="e98b6-152">按下 SHIFT 鍵。</span><span class="sxs-lookup"><span data-stu-id="e98b6-152">The SHIFT key is pressed.</span></span></p></td>
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
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="e98b6-153">**dwEventFlags**</span><span class="sxs-lookup"><span data-stu-id="e98b6-153">**dwEventFlags**</span></span>  
<span data-ttu-id="e98b6-154">滑鼠事件的類型。</span><span class="sxs-lookup"><span data-stu-id="e98b6-154">The type of mouse event.</span></span> <span data-ttu-id="e98b6-155">如果這個值為零，表示已按下或放開滑鼠按鍵。</span><span class="sxs-lookup"><span data-stu-id="e98b6-155">If this value is zero, it indicates a mouse button being pressed or released.</span></span> <span data-ttu-id="e98b6-156">否則，此成員會是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="e98b6-156">Otherwise, this member is one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="e98b6-157">值</span><span class="sxs-lookup"><span data-stu-id="e98b6-157">Value</span></span></th>
<th><span data-ttu-id="e98b6-158">意義</span><span class="sxs-lookup"><span data-stu-id="e98b6-158">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="e98b6-159"><span id="DOUBLE_CLICK"></span><span id="double_click"></span>
<strong>DOUBLE_CLICK</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="e98b6-159"><span id="DOUBLE_CLICK"></span><span id="double_click"></span>
<strong>DOUBLE_CLICK</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="e98b6-160">第二次按一下 (按鈕時，請按下滑鼠按鍵) 。</span><span class="sxs-lookup"><span data-stu-id="e98b6-160">The second click (button press) of a double-click occurred.</span></span> <span data-ttu-id="e98b6-161">第一次按一下會以一般按鈕按下事件的方式傳回。</span><span class="sxs-lookup"><span data-stu-id="e98b6-161">The first click is returned as a regular button-press event.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e98b6-162"><span id="MOUSE_HWHEELED"></span><span id="mouse_hwheeled"></span>
<strong>MOUSE_HWHEELED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="e98b6-162"><span id="MOUSE_HWHEELED"></span><span id="mouse_hwheeled"></span>
<strong>MOUSE_HWHEELED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="e98b6-163">移動了水準滑鼠滾輪。</span><span class="sxs-lookup"><span data-stu-id="e98b6-163">The horizontal mouse wheel was moved.</span></span></p>
<p><span data-ttu-id="e98b6-164">如果 <strong>dwButtonState</strong> 成員的最大文字包含正值，滾輪就會向右旋轉。</span><span class="sxs-lookup"><span data-stu-id="e98b6-164">If the high word of the <strong>dwButtonState</strong> member contains a positive value, the wheel was rotated to the right.</span></span> <span data-ttu-id="e98b6-165">否則，滾輪會旋轉至左方。</span><span class="sxs-lookup"><span data-stu-id="e98b6-165">Otherwise, the wheel was rotated to the left.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e98b6-166"><span id="MOUSE_MOVED"></span><span id="mouse_moved"></span>
<strong>MOUSE_MOVED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="e98b6-166"><span id="MOUSE_MOVED"></span><span id="mouse_moved"></span>
<strong>MOUSE_MOVED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="e98b6-167">發生滑鼠位置變更。</span><span class="sxs-lookup"><span data-stu-id="e98b6-167">A change in mouse position occurred.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e98b6-168"><span id="MOUSE_WHEELED"></span><span id="mouse_wheeled"></span>
<strong>MOUSE_WHEELED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="e98b6-168"><span id="MOUSE_WHEELED"></span><span id="mouse_wheeled"></span>
<strong>MOUSE_WHEELED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="e98b6-169">移動了垂直滑鼠滾輪。</span><span class="sxs-lookup"><span data-stu-id="e98b6-169">The vertical mouse wheel was moved.</span></span></p>
<p><span data-ttu-id="e98b6-170">如果 <strong>dwButtonState</strong> 成員的高單字包含正值，則滾輪會向前旋轉，而不是使用者。</span><span class="sxs-lookup"><span data-stu-id="e98b6-170">If the high word of the <strong>dwButtonState</strong> member contains a positive value, the wheel was rotated forward, away from the user.</span></span> <span data-ttu-id="e98b6-171">否則，滾輪會向使用者旋轉。</span><span class="sxs-lookup"><span data-stu-id="e98b6-171">Otherwise, the wheel was rotated backward, toward the user.</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="remarks"></a><span data-ttu-id="e98b6-172">備註</span><span class="sxs-lookup"><span data-stu-id="e98b6-172">Remarks</span></span>
-------

<span data-ttu-id="e98b6-173">當主控台處於滑鼠模式時，滑鼠事件會放置在輸入緩衝區中 (**啟用 \_ 滑鼠 \_ 輸入**) 。</span><span class="sxs-lookup"><span data-stu-id="e98b6-173">Mouse events are placed in the input buffer when the console is in mouse mode (**ENABLE\_MOUSE\_INPUT**).</span></span>

<span data-ttu-id="e98b6-174">每當使用者移動滑鼠或按下或放開其中一個滑鼠按鍵時，就會產生滑鼠事件。</span><span class="sxs-lookup"><span data-stu-id="e98b6-174">Mouse events are generated whenever the user moves the mouse, or presses or releases one of the mouse buttons.</span></span> <span data-ttu-id="e98b6-175">只有當主控台群組具有鍵盤焦點，且游標位於主控台視窗的框線內時，滑鼠事件才會放在主控台的輸入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="e98b6-175">Mouse events are placed in a console's input buffer only when the console group has the keyboard focus and the cursor is within the borders of the console's window.</span></span>

<a name="examples"></a><span data-ttu-id="e98b6-176">範例</span><span class="sxs-lookup"><span data-stu-id="e98b6-176">Examples</span></span>
--------

<span data-ttu-id="e98b6-177">如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。</span><span class="sxs-lookup"><span data-stu-id="e98b6-177">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="e98b6-178">規格需求</span><span class="sxs-lookup"><span data-stu-id="e98b6-178">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e98b6-179">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="e98b6-179">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e98b6-180">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="e98b6-180">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e98b6-181">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="e98b6-181">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e98b6-182">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="e98b6-182">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e98b6-183">標頭</span><span class="sxs-lookup"><span data-stu-id="e98b6-183">Header</span></span></p></td>
<td><span data-ttu-id="e98b6-184">WinConTypes .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="e98b6-184">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e98b6-185"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="e98b6-185"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e98b6-186">**COORD**</span><span class="sxs-lookup"><span data-stu-id="e98b6-186">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="e98b6-187">**輸入 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="e98b6-187">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="e98b6-188">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="e98b6-188">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="e98b6-189">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="e98b6-189">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="e98b6-190">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="e98b6-190">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 





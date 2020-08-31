---
title: CONSOLE_READCONSOLE_CONTROL 結構
description: 請參閱 CONSOLE_READCONSOLE_CONTROL 結構的參考資訊，其中包含主控台讀取操作的資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi/CONSOLE_READCONSOLE_CONTROL
- wincon/CONSOLE_READCONSOLE_CONTROL
- CONSOLE_READCONSOLE_CONTROL
- consoleapi/PCONSOLE_READCONSOLE_CONTROL
- wincon/PCONSOLE_READCONSOLE_CONTROL
- PCONSOLE_READCONSOLE_CONTROL
MS-HAID:
- base.console\_readconsole\_control
- consoles.console\_readconsole\_control
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a8451a6-d692-43af-88c4-972c4dc5e07c
topic_type:
- apiref
api_name:
- CONSOLE_READCONSOLE_CONTROL
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4fc6af26cd540a7af207af252963c21ba216cdee
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059307"
---
# <a name="console_readconsole_control-structure"></a><span data-ttu-id="e7bbc-104">主控台 \_ READCONSOLE \_ 控制結構</span><span class="sxs-lookup"><span data-stu-id="e7bbc-104">CONSOLE\_READCONSOLE\_CONTROL structure</span></span>


<span data-ttu-id="e7bbc-105">包含主控台讀取操作的資訊。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-105">Contains information for a console read operation.</span></span>

<a name="syntax"></a><span data-ttu-id="e7bbc-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e7bbc-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

<a name="members"></a><span data-ttu-id="e7bbc-107">成員</span><span class="sxs-lookup"><span data-stu-id="e7bbc-107">Members</span></span>
-------

<span data-ttu-id="e7bbc-108">**nLength**</span><span class="sxs-lookup"><span data-stu-id="e7bbc-108">**nLength**</span></span>  
<span data-ttu-id="e7bbc-109">結構的大小。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-109">The size of the structure.</span></span> <span data-ttu-id="e7bbc-110">將這個成員設定為 `sizeof(CONSOLE_READCONSOLE_CONTROL)` 。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-110">Set this member to `sizeof(CONSOLE_READCONSOLE_CONTROL)`.</span></span>

<span data-ttu-id="e7bbc-111">**nInitialChars**</span><span class="sxs-lookup"><span data-stu-id="e7bbc-111">**nInitialChars**</span></span>  
<span data-ttu-id="e7bbc-112">要略過的字元數 (，因此在傳遞至 [**ReadConsole**](readconsole.md) 函式的緩衝區中寫入新的讀取輸入之前，會保留) 。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-112">The number of characters to skip (and thus preserve) before writing newly read input in the buffer passed to the [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="e7bbc-113">這個值必須小於**ReadConsole**函數的*nNumberOfCharsToRead*參數。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-113">This value must be less than the *nNumberOfCharsToRead* parameter of the **ReadConsole** function.</span></span>

<span data-ttu-id="e7bbc-114">**dwCtrlWakeupMask**</span><span class="sxs-lookup"><span data-stu-id="e7bbc-114">**dwCtrlWakeupMask**</span></span>  
<span data-ttu-id="e7bbc-115">使用者定義的控制字元，用來表示讀取已完成。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-115">A user-defined control character used to signal that the read is complete.</span></span>

<span data-ttu-id="e7bbc-116">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="e7bbc-116">**dwControlKeyState**</span></span>  
<span data-ttu-id="e7bbc-117">控制項索引鍵的狀態。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-117">The state of the control keys.</span></span> <span data-ttu-id="e7bbc-118">這個成員可以是下列一或多個值。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-118">This member can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="e7bbc-119">值</span><span class="sxs-lookup"><span data-stu-id="e7bbc-119">Value</span></span></th>
<th><span data-ttu-id="e7bbc-120">意義</span><span class="sxs-lookup"><span data-stu-id="e7bbc-120">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="e7bbc-121"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="e7bbc-121"><span id="CAPSLOCK_ON"></span><span id="capslock_on"></span>
<strong>CAPSLOCK_ON</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="e7bbc-122">CAPS LOCK 燈開啟。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-122">The CAPS LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e7bbc-123"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span><span class="sxs-lookup"><span data-stu-id="e7bbc-123"><span id="ENHANCED_KEY"></span><span id="enhanced_key"></span>
<strong>ENHANCED_KEY</strong> 0x0100</span></span></td>
<td><p><span data-ttu-id="e7bbc-124">金鑰已增強。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-124">The key is enhanced.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e7bbc-125"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="e7bbc-125"><span id="LEFT_ALT_PRESSED"></span><span id="left_alt_pressed"></span>
<strong>LEFT_ALT_PRESSED</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="e7bbc-126">左 ALT 鍵已按下。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-126">The left ALT key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e7bbc-127"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="e7bbc-127"><span id="LEFT_CTRL_PRESSED"></span><span id="left_ctrl_pressed"></span>
<strong>LEFT_CTRL_PRESSED</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="e7bbc-128">按下 CTRL 鍵。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-128">The left CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e7bbc-129"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="e7bbc-129"><span id="NUMLOCK_ON"></span><span id="numlock_on"></span>
<strong>NUMLOCK_ON</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="e7bbc-130">NUM LOCK 燈開啟。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-130">The NUM LOCK light is on.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e7bbc-131"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="e7bbc-131"><span id="RIGHT_ALT_PRESSED"></span><span id="right_alt_pressed"></span>
<strong>RIGHT_ALT_PRESSED</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="e7bbc-132">按下右邊的 ALT 鍵。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-132">The right ALT key is pressed.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e7bbc-133"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="e7bbc-133"><span id="RIGHT_CTRL_PRESSED"></span><span id="right_ctrl_pressed"></span>
<strong>RIGHT_CTRL_PRESSED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="e7bbc-134">按下 CTRL 鍵。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-134">The right CTRL key is pressed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e7bbc-135"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="e7bbc-135"><span id="SCROLLLOCK_ON"></span><span id="scrolllock_on"></span>
<strong>SCROLLLOCK_ON</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="e7bbc-136">捲軸鎖定燈開啟。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-136">The SCROLL LOCK light is on.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e7bbc-137"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="e7bbc-137"><span id="SHIFT_PRESSED"></span><span id="shift_pressed"></span>
<strong>SHIFT_PRESSED</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="e7bbc-138">按下 SHIFT 鍵。</span><span class="sxs-lookup"><span data-stu-id="e7bbc-138">The SHIFT key is pressed.</span></span></p></td>
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

 

<a name="requirements"></a><span data-ttu-id="e7bbc-139">規格需求</span><span class="sxs-lookup"><span data-stu-id="e7bbc-139">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e7bbc-140">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="e7bbc-140">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e7bbc-141">Windows Vista [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="e7bbc-141">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e7bbc-142">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="e7bbc-142">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e7bbc-143">Windows Server 2008 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="e7bbc-143">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e7bbc-144">標頭</span><span class="sxs-lookup"><span data-stu-id="e7bbc-144">Header</span></span></p></td>
<td><span data-ttu-id="e7bbc-145">ConsoleApi .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="e7bbc-145">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e7bbc-146"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7bbc-146"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e7bbc-147">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="e7bbc-147">**ReadConsole**</span></span>](readconsole.md)

 

 





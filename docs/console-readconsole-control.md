---
title: CONSOLE_READCONSOLE_CONTROL 結構
description: 請參閱 CONSOLE_READCONSOLE_CONTROL 結構的參考資訊，其中包含主控台讀取操作的資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8a703a1eaa370e16095e1b10eb146a0718f332e9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039186"
---
# <a name="console_readconsole_control-structure"></a><span data-ttu-id="79c5e-104">主控台 \_ READCONSOLE \_ 控制結構</span><span class="sxs-lookup"><span data-stu-id="79c5e-104">CONSOLE\_READCONSOLE\_CONTROL structure</span></span>

<span data-ttu-id="79c5e-105">包含主控台讀取操作的資訊。</span><span class="sxs-lookup"><span data-stu-id="79c5e-105">Contains information for a console read operation.</span></span>

## <a name="syntax"></a><span data-ttu-id="79c5e-106">語法</span><span class="sxs-lookup"><span data-stu-id="79c5e-106">Syntax</span></span>

```C
typedef struct _CONSOLE_READCONSOLE_CONTROL {
  ULONG nLength;
  ULONG nInitialChars;
  ULONG dwCtrlWakeupMask;
  ULONG dwControlKeyState;
} CONSOLE_READCONSOLE_CONTROL, *PCONSOLE_READCONSOLE_CONTROL;
```

## <a name="members"></a><span data-ttu-id="79c5e-107">成員</span><span class="sxs-lookup"><span data-stu-id="79c5e-107">Members</span></span>

<span data-ttu-id="79c5e-108">**nLength**</span><span class="sxs-lookup"><span data-stu-id="79c5e-108">**nLength**</span></span>  
<span data-ttu-id="79c5e-109">結構的大小。</span><span class="sxs-lookup"><span data-stu-id="79c5e-109">The size of the structure.</span></span> <span data-ttu-id="79c5e-110">將這個成員設定為 `sizeof(CONSOLE_READCONSOLE_CONTROL)` 。</span><span class="sxs-lookup"><span data-stu-id="79c5e-110">Set this member to `sizeof(CONSOLE_READCONSOLE_CONTROL)`.</span></span>

<span data-ttu-id="79c5e-111">**nInitialChars**</span><span class="sxs-lookup"><span data-stu-id="79c5e-111">**nInitialChars**</span></span>  
<span data-ttu-id="79c5e-112">要略過的字元數 (，因此在傳遞至 [**ReadConsole**](readconsole.md) 函式的緩衝區中寫入新的讀取輸入之前，會保留) 。</span><span class="sxs-lookup"><span data-stu-id="79c5e-112">The number of characters to skip (and thus preserve) before writing newly read input in the buffer passed to the [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="79c5e-113">這個值必須小於 **ReadConsole** 函數的 *nNumberOfCharsToRead* 參數。</span><span class="sxs-lookup"><span data-stu-id="79c5e-113">This value must be less than the *nNumberOfCharsToRead* parameter of the **ReadConsole** function.</span></span>

<span data-ttu-id="79c5e-114">**dwCtrlWakeupMask**</span><span class="sxs-lookup"><span data-stu-id="79c5e-114">**dwCtrlWakeupMask**</span></span>  
<span data-ttu-id="79c5e-115">遮罩，指定應該使用和之間的控制字元 `0x00` `0x1F` 來表示讀取已完成。</span><span class="sxs-lookup"><span data-stu-id="79c5e-115">A mask specifying which control characters between `0x00` and `0x1F` should be used to signal that the read is complete.</span></span> <span data-ttu-id="79c5e-116">每個位都對應到一個字元，且該字元的最小位對應于或 `0x00` `NUL` 以及與或相對應的最高有效位 `0x1F` `US` 。</span><span class="sxs-lookup"><span data-stu-id="79c5e-116">Each bit corresponds to a character with the least significant bit corresponding to `0x00` or `NUL` and the most significant bit corresponding to `0x1F` or `US`.</span></span> <span data-ttu-id="79c5e-117">您可以指定多個位 (控制字元) 。</span><span class="sxs-lookup"><span data-stu-id="79c5e-117">Multiple bits (control characters) can be specified.</span></span>

<span data-ttu-id="79c5e-118">**dwControlKeyState**</span><span class="sxs-lookup"><span data-stu-id="79c5e-118">**dwControlKeyState**</span></span>  
<span data-ttu-id="79c5e-119">控制項索引鍵的狀態。</span><span class="sxs-lookup"><span data-stu-id="79c5e-119">The state of the control keys.</span></span> <span data-ttu-id="79c5e-120">這個成員可以是下列一或多個值。</span><span class="sxs-lookup"><span data-stu-id="79c5e-120">This member can be one or more of the following values.</span></span>

| <span data-ttu-id="79c5e-121">值</span><span class="sxs-lookup"><span data-stu-id="79c5e-121">Value</span></span> | <span data-ttu-id="79c5e-122">意義</span><span class="sxs-lookup"><span data-stu-id="79c5e-122">Meaning</span></span> |
|-|-|
| <span data-ttu-id="79c5e-123">**CAPSLOCK_ON** 0x0080</span><span class="sxs-lookup"><span data-stu-id="79c5e-123">**CAPSLOCK_ON** 0x0080</span></span> | <span data-ttu-id="79c5e-124">CAPS LOCK 燈開啟。</span><span class="sxs-lookup"><span data-stu-id="79c5e-124">The CAPS LOCK light is on.</span></span> |
| <span data-ttu-id="79c5e-125">**ENHANCED_KEY** 0x0100</span><span class="sxs-lookup"><span data-stu-id="79c5e-125">**ENHANCED_KEY** 0x0100</span></span> | <span data-ttu-id="79c5e-126">金鑰已增強。</span><span class="sxs-lookup"><span data-stu-id="79c5e-126">The key is enhanced.</span></span> <span data-ttu-id="79c5e-127">請參閱 [備註](key-event-record-str.md#remarks)。</span><span class="sxs-lookup"><span data-stu-id="79c5e-127">See [remarks](key-event-record-str.md#remarks).</span></span> |
| <span data-ttu-id="79c5e-128">**LEFT_ALT_PRESSED** 0x0002</span><span class="sxs-lookup"><span data-stu-id="79c5e-128">**LEFT_ALT_PRESSED** 0x0002</span></span> | <span data-ttu-id="79c5e-129">左 ALT 鍵已按下。</span><span class="sxs-lookup"><span data-stu-id="79c5e-129">The left ALT key is pressed.</span></span> |
| <span data-ttu-id="79c5e-130">**LEFT_CTRL_PRESSED** 0x0008</span><span class="sxs-lookup"><span data-stu-id="79c5e-130">**LEFT_CTRL_PRESSED** 0x0008</span></span> | <span data-ttu-id="79c5e-131">按下 CTRL 鍵。</span><span class="sxs-lookup"><span data-stu-id="79c5e-131">The left CTRL key is pressed.</span></span> |
| <span data-ttu-id="79c5e-132">**NUMLOCK_ON** 0x0020</span><span class="sxs-lookup"><span data-stu-id="79c5e-132">**NUMLOCK_ON** 0x0020</span></span> | <span data-ttu-id="79c5e-133">NUM LOCK 燈開啟。</span><span class="sxs-lookup"><span data-stu-id="79c5e-133">The NUM LOCK light is on.</span></span> |
| <span data-ttu-id="79c5e-134">**RIGHT_ALT_PRESSED** 0x0001</span><span class="sxs-lookup"><span data-stu-id="79c5e-134">**RIGHT_ALT_PRESSED** 0x0001</span></span> | <span data-ttu-id="79c5e-135">按下右邊的 ALT 鍵。</span><span class="sxs-lookup"><span data-stu-id="79c5e-135">The right ALT key is pressed.</span></span> |
| <span data-ttu-id="79c5e-136">**RIGHT_CTRL_PRESSED** 0x0004</span><span class="sxs-lookup"><span data-stu-id="79c5e-136">**RIGHT_CTRL_PRESSED** 0x0004</span></span> | <span data-ttu-id="79c5e-137">按下 CTRL 鍵。</span><span class="sxs-lookup"><span data-stu-id="79c5e-137">The right CTRL key is pressed.</span></span> |
| <span data-ttu-id="79c5e-138">**SCROLLLOCK_ON** 0x0040</span><span class="sxs-lookup"><span data-stu-id="79c5e-138">**SCROLLLOCK_ON** 0x0040</span></span> | <span data-ttu-id="79c5e-139">捲軸鎖定燈開啟。</span><span class="sxs-lookup"><span data-stu-id="79c5e-139">The SCROLL LOCK light is on.</span></span> |
| <span data-ttu-id="79c5e-140">**SHIFT_PRESSED** 0x0010</span><span class="sxs-lookup"><span data-stu-id="79c5e-140">**SHIFT_PRESSED** 0x0010</span></span> | <span data-ttu-id="79c5e-141">按下 SHIFT 鍵。</span><span class="sxs-lookup"><span data-stu-id="79c5e-141">The SHIFT key is pressed.</span></span> |

## <a name="requirements"></a><span data-ttu-id="79c5e-142">規格需求</span><span class="sxs-lookup"><span data-stu-id="79c5e-142">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="79c5e-143">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="79c5e-143">Minimum supported client</span></span> | <span data-ttu-id="79c5e-144">\[僅限 Windows Vista 桌面應用程式\]</span><span class="sxs-lookup"><span data-stu-id="79c5e-144">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="79c5e-145">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="79c5e-145">Minimum supported server</span></span> | <span data-ttu-id="79c5e-146">僅限 Windows Server 2008 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="79c5e-146">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="79c5e-147">標頭</span><span class="sxs-lookup"><span data-stu-id="79c5e-147">Header</span></span> | <span data-ttu-id="79c5e-148">ConsoleApi .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="79c5e-148">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="79c5e-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="79c5e-149">See also</span></span>

[<span data-ttu-id="79c5e-150">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="79c5e-150">**ReadConsole**</span></span>](readconsole.md)

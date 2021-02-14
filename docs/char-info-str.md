---
title: CHAR_INFO 結構
description: 指定 Unicode 或 ANSI 字元及其屬性。 主控台函式會使用此結構讀取和寫入主控台螢幕緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- wincontypes/CHAR_INFO
- wincon/CHAR_INFO
- CHAR_INFO
- wincontypes/PCHAR_INFO
- wincon/PCHAR_INFO
- PCHAR_INFO
MS-HAID:
- '\_win32\_char\_info\_str'
- base.char\_info\_str
- consoles.char\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5574a862-b262-41af-8862-e9837c5c7b5f
topic_type:
- apiref
api_name:
- CHAR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: a16fb23d148f75480437211204a0fd7c1f161bfe
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357848"
---
# `CHAR\_INFO structure`

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="adc35-105">指定 Unicode 或 ANSI 字元及其屬性。</span><span class="sxs-lookup"><span data-stu-id="adc35-105">Specifies a Unicode or ANSI character and its attributes.</span></span> <span data-ttu-id="adc35-106">主控台函式會使用此結構讀取和寫入主控台螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="adc35-106">This structure is used by console functions to read from and write to a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="adc35-107">語法</span><span class="sxs-lookup"><span data-stu-id="adc35-107">Syntax</span></span>

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## <a name="members"></a><span data-ttu-id="adc35-108">成員</span><span class="sxs-lookup"><span data-stu-id="adc35-108">Members</span></span>

<span data-ttu-id="adc35-109">**Char**</span><span class="sxs-lookup"><span data-stu-id="adc35-109">**Char**</span></span>  
<span data-ttu-id="adc35-110">下列成員的聯集。</span><span class="sxs-lookup"><span data-stu-id="adc35-110">A union of the following members.</span></span>

<span data-ttu-id="adc35-111">**UnicodeChar**</span><span class="sxs-lookup"><span data-stu-id="adc35-111">**UnicodeChar**</span></span>  
<span data-ttu-id="adc35-112">螢幕緩衝區字元資料格的 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="adc35-112">Unicode character of a screen buffer character cell.</span></span>

<span data-ttu-id="adc35-113">**AsciiChar**</span><span class="sxs-lookup"><span data-stu-id="adc35-113">**AsciiChar**</span></span>  
<span data-ttu-id="adc35-114">螢幕緩衝區字元資料格的 ANSI 字元。</span><span class="sxs-lookup"><span data-stu-id="adc35-114">ANSI character of a screen buffer character cell.</span></span>

<span data-ttu-id="adc35-115">**屬性**</span><span class="sxs-lookup"><span data-stu-id="adc35-115">**Attributes**</span></span>  
<span data-ttu-id="adc35-116">字元屬性。</span><span class="sxs-lookup"><span data-stu-id="adc35-116">The character attributes.</span></span> <span data-ttu-id="adc35-117">這個成員可以是零或下列值的任何組合。</span><span class="sxs-lookup"><span data-stu-id="adc35-117">This member can be zero or any combination of the following values.</span></span>

| <span data-ttu-id="adc35-118">值</span><span class="sxs-lookup"><span data-stu-id="adc35-118">Value</span></span> | <span data-ttu-id="adc35-119">意義</span><span class="sxs-lookup"><span data-stu-id="adc35-119">Meaning</span></span> |
|-|-|
| <span data-ttu-id="adc35-120">**FOREGROUND_BLUE**`0x0001`</span><span class="sxs-lookup"><span data-stu-id="adc35-120">**FOREGROUND_BLUE** `0x0001`</span></span> | <span data-ttu-id="adc35-121">文字色彩包含藍色。</span><span class="sxs-lookup"><span data-stu-id="adc35-121">Text color contains blue.</span></span> |
| <span data-ttu-id="adc35-122">**FOREGROUND_GREEN**`0x0002`</span><span class="sxs-lookup"><span data-stu-id="adc35-122">**FOREGROUND_GREEN** `0x0002`</span></span> | <span data-ttu-id="adc35-123">文字色彩包含綠色。</span><span class="sxs-lookup"><span data-stu-id="adc35-123">Text color contains green.</span></span> |
| <span data-ttu-id="adc35-124">**FOREGROUND_RED**`0x0004`</span><span class="sxs-lookup"><span data-stu-id="adc35-124">**FOREGROUND_RED** `0x0004`</span></span> | <span data-ttu-id="adc35-125">文字色彩包含紅色。</span><span class="sxs-lookup"><span data-stu-id="adc35-125">Text color contains red.</span></span> |
| <span data-ttu-id="adc35-126">**FOREGROUND_INTENSITY**`0x0008`</span><span class="sxs-lookup"><span data-stu-id="adc35-126">**FOREGROUND_INTENSITY** `0x0008`</span></span> | <span data-ttu-id="adc35-127">加深文字色彩。</span><span class="sxs-lookup"><span data-stu-id="adc35-127">Text color is intensified.</span></span> |
| <span data-ttu-id="adc35-128">**BACKGROUND_BLUE**`0x0010`</span><span class="sxs-lookup"><span data-stu-id="adc35-128">**BACKGROUND_BLUE** `0x0010`</span></span> | <span data-ttu-id="adc35-129">背景色彩包含藍色。</span><span class="sxs-lookup"><span data-stu-id="adc35-129">Background color contains blue.</span></span> |
| <span data-ttu-id="adc35-130">**BACKGROUND_GREEN**`0x0020`</span><span class="sxs-lookup"><span data-stu-id="adc35-130">**BACKGROUND_GREEN** `0x0020`</span></span> | <span data-ttu-id="adc35-131">背景色彩包含綠色。</span><span class="sxs-lookup"><span data-stu-id="adc35-131">Background color contains green.</span></span> |
| <span data-ttu-id="adc35-132">**BACKGROUND_RED**`0x0040`</span><span class="sxs-lookup"><span data-stu-id="adc35-132">**BACKGROUND_RED** `0x0040`</span></span> | <span data-ttu-id="adc35-133">背景色彩包含紅色。</span><span class="sxs-lookup"><span data-stu-id="adc35-133">Background color contains red.</span></span> |
| <span data-ttu-id="adc35-134">**BACKGROUND_INTENSITY**`0x0080`</span><span class="sxs-lookup"><span data-stu-id="adc35-134">**BACKGROUND_INTENSITY** `0x0080`</span></span> | <span data-ttu-id="adc35-135">加深背景色彩。</span><span class="sxs-lookup"><span data-stu-id="adc35-135">Background color is intensified.</span></span> |
| <span data-ttu-id="adc35-136">**COMMON_LVB_LEADING_BYTE**`0x0100`</span><span class="sxs-lookup"><span data-stu-id="adc35-136">**COMMON_LVB_LEADING_BYTE** `0x0100`</span></span> | <span data-ttu-id="adc35-137">前置位元組。</span><span class="sxs-lookup"><span data-stu-id="adc35-137">Leading byte.</span></span> |
| <span data-ttu-id="adc35-138">**COMMON_LVB_TRAILING_BYTE**`0x0200`</span><span class="sxs-lookup"><span data-stu-id="adc35-138">**COMMON_LVB_TRAILING_BYTE** `0x0200`</span></span> | <span data-ttu-id="adc35-139">尾端位元組。</span><span class="sxs-lookup"><span data-stu-id="adc35-139">Trailing byte.</span></span> |
| <span data-ttu-id="adc35-140">**COMMON_LVB_GRID_HORIZONTAL**`0x0400`</span><span class="sxs-lookup"><span data-stu-id="adc35-140">**COMMON_LVB_GRID_HORIZONTAL** `0x0400`</span></span> | <span data-ttu-id="adc35-141">水平置頂。</span><span class="sxs-lookup"><span data-stu-id="adc35-141">Top horizontal.</span></span> |
| <span data-ttu-id="adc35-142">**COMMON_LVB_GRID_LVERTICAL**`0x0800`</span><span class="sxs-lookup"><span data-stu-id="adc35-142">**COMMON_LVB_GRID_LVERTICAL** `0x0800`</span></span> | <span data-ttu-id="adc35-143">垂直靠左。</span><span class="sxs-lookup"><span data-stu-id="adc35-143">Left vertical.</span></span> |
| <span data-ttu-id="adc35-144">**COMMON_LVB_GRID_RVERTICAL**`0x1000`</span><span class="sxs-lookup"><span data-stu-id="adc35-144">**COMMON_LVB_GRID_RVERTICAL** `0x1000`</span></span> | <span data-ttu-id="adc35-145">垂直靠右。</span><span class="sxs-lookup"><span data-stu-id="adc35-145">Right vertical.</span></span> |
| <span data-ttu-id="adc35-146">**COMMON_LVB_REVERSE_VIDEO**`0x4000`</span><span class="sxs-lookup"><span data-stu-id="adc35-146">**COMMON_LVB_REVERSE_VIDEO** `0x4000`</span></span> | <span data-ttu-id="adc35-147">反向前景和背景屬性。</span><span class="sxs-lookup"><span data-stu-id="adc35-147">Reverse foreground and background attribute.</span></span> |
| <span data-ttu-id="adc35-148">**COMMON_LVB_UNDERSCORE**`0x8000`</span><span class="sxs-lookup"><span data-stu-id="adc35-148">**COMMON_LVB_UNDERSCORE** `0x8000`</span></span> | <span data-ttu-id="adc35-149">底線。</span><span class="sxs-lookup"><span data-stu-id="adc35-149">Underscore.</span></span> |

## <a name="examples"></a><span data-ttu-id="adc35-150">範例</span><span class="sxs-lookup"><span data-stu-id="adc35-150">Examples</span></span>

<span data-ttu-id="adc35-151">如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="adc35-151">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="adc35-152">規格需求</span><span class="sxs-lookup"><span data-stu-id="adc35-152">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="adc35-153">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="adc35-153">Minimum supported client</span></span> | <span data-ttu-id="adc35-154">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="adc35-154">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="adc35-155">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="adc35-155">Minimum supported server</span></span> | <span data-ttu-id="adc35-156">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="adc35-156">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="adc35-157">標頭</span><span class="sxs-lookup"><span data-stu-id="adc35-157">Header</span></span> | <span data-ttu-id="adc35-158">WinCon (包含) 的 Windows。h</span><span class="sxs-lookup"><span data-stu-id="adc35-158">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="adc35-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adc35-159">See also</span></span>

[<span data-ttu-id="adc35-160">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="adc35-160">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="adc35-161">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="adc35-161">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="adc35-162">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="adc35-162">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

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
ms.openlocfilehash: b07938d6ac58744533711c91a04b1a0188f7daf6
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037376"
---
# <a name="char_info-structure"></a><span data-ttu-id="ea778-105">CHAR \_ 資訊結構</span><span class="sxs-lookup"><span data-stu-id="ea778-105">CHAR\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="ea778-106">指定 Unicode 或 ANSI 字元及其屬性。</span><span class="sxs-lookup"><span data-stu-id="ea778-106">Specifies a Unicode or ANSI character and its attributes.</span></span> <span data-ttu-id="ea778-107">主控台函式會使用此結構讀取和寫入主控台螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ea778-107">This structure is used by console functions to read from and write to a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="ea778-108">語法</span><span class="sxs-lookup"><span data-stu-id="ea778-108">Syntax</span></span>

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

## <a name="members"></a><span data-ttu-id="ea778-109">成員</span><span class="sxs-lookup"><span data-stu-id="ea778-109">Members</span></span>

<span data-ttu-id="ea778-110">**字元**</span><span class="sxs-lookup"><span data-stu-id="ea778-110">**Char**</span></span>  
<span data-ttu-id="ea778-111">下列成員的聯集。</span><span class="sxs-lookup"><span data-stu-id="ea778-111">A union of the following members.</span></span>

<span data-ttu-id="ea778-112">**UnicodeChar**</span><span class="sxs-lookup"><span data-stu-id="ea778-112">**UnicodeChar**</span></span>  
<span data-ttu-id="ea778-113">螢幕緩衝區字元資料格的 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="ea778-113">Unicode character of a screen buffer character cell.</span></span>

<span data-ttu-id="ea778-114">**AsciiChar**</span><span class="sxs-lookup"><span data-stu-id="ea778-114">**AsciiChar**</span></span>  
<span data-ttu-id="ea778-115">螢幕緩衝區字元資料格的 ANSI 字元。</span><span class="sxs-lookup"><span data-stu-id="ea778-115">ANSI character of a screen buffer character cell.</span></span>

<span data-ttu-id="ea778-116">**屬性**</span><span class="sxs-lookup"><span data-stu-id="ea778-116">**Attributes**</span></span>  
<span data-ttu-id="ea778-117">字元屬性。</span><span class="sxs-lookup"><span data-stu-id="ea778-117">The character attributes.</span></span> <span data-ttu-id="ea778-118">這個成員可以是零或下列值的任何組合。</span><span class="sxs-lookup"><span data-stu-id="ea778-118">This member can be zero or any combination of the following values.</span></span>

| <span data-ttu-id="ea778-119">值</span><span class="sxs-lookup"><span data-stu-id="ea778-119">Value</span></span> | <span data-ttu-id="ea778-120">意義</span><span class="sxs-lookup"><span data-stu-id="ea778-120">Meaning</span></span> |
|-|-|
| <span data-ttu-id="ea778-121">**FOREGROUND_BLUE**`0x0001`</span><span class="sxs-lookup"><span data-stu-id="ea778-121">**FOREGROUND_BLUE** `0x0001`</span></span> | <span data-ttu-id="ea778-122">文字色彩包含藍色。</span><span class="sxs-lookup"><span data-stu-id="ea778-122">Text color contains blue.</span></span> |
| <span data-ttu-id="ea778-123">**FOREGROUND_GREEN**`0x0002`</span><span class="sxs-lookup"><span data-stu-id="ea778-123">**FOREGROUND_GREEN** `0x0002`</span></span> | <span data-ttu-id="ea778-124">文字色彩包含綠色。</span><span class="sxs-lookup"><span data-stu-id="ea778-124">Text color contains green.</span></span> |
| <span data-ttu-id="ea778-125">**FOREGROUND_RED**`0x0004`</span><span class="sxs-lookup"><span data-stu-id="ea778-125">**FOREGROUND_RED** `0x0004`</span></span> | <span data-ttu-id="ea778-126">文字色彩包含紅色。</span><span class="sxs-lookup"><span data-stu-id="ea778-126">Text color contains red.</span></span> |
| <span data-ttu-id="ea778-127">**FOREGROUND_INTENSITY**`0x0008`</span><span class="sxs-lookup"><span data-stu-id="ea778-127">**FOREGROUND_INTENSITY** `0x0008`</span></span> | <span data-ttu-id="ea778-128">文字色彩為更。</span><span class="sxs-lookup"><span data-stu-id="ea778-128">Text color is intensified.</span></span> |
| <span data-ttu-id="ea778-129">**BACKGROUND_BLUE**`0x0010`</span><span class="sxs-lookup"><span data-stu-id="ea778-129">**BACKGROUND_BLUE** `0x0010`</span></span> | <span data-ttu-id="ea778-130">背景色彩包含藍色。</span><span class="sxs-lookup"><span data-stu-id="ea778-130">Background color contains blue.</span></span> |
| <span data-ttu-id="ea778-131">**BACKGROUND_GREEN**`0x0020`</span><span class="sxs-lookup"><span data-stu-id="ea778-131">**BACKGROUND_GREEN** `0x0020`</span></span> | <span data-ttu-id="ea778-132">背景色彩包含綠色。</span><span class="sxs-lookup"><span data-stu-id="ea778-132">Background color contains green.</span></span> |
| <span data-ttu-id="ea778-133">**BACKGROUND_RED**`0x0040`</span><span class="sxs-lookup"><span data-stu-id="ea778-133">**BACKGROUND_RED** `0x0040`</span></span> | <span data-ttu-id="ea778-134">背景色彩包含紅色。</span><span class="sxs-lookup"><span data-stu-id="ea778-134">Background color contains red.</span></span> |
| <span data-ttu-id="ea778-135">**BACKGROUND_INTENSITY**`0x0080`</span><span class="sxs-lookup"><span data-stu-id="ea778-135">**BACKGROUND_INTENSITY** `0x0080`</span></span> | <span data-ttu-id="ea778-136">背景色彩為更。</span><span class="sxs-lookup"><span data-stu-id="ea778-136">Background color is intensified.</span></span> |
| <span data-ttu-id="ea778-137">**COMMON_LVB_LEADING_BYTE**`0x0100`</span><span class="sxs-lookup"><span data-stu-id="ea778-137">**COMMON_LVB_LEADING_BYTE** `0x0100`</span></span> | <span data-ttu-id="ea778-138">前置位元組。</span><span class="sxs-lookup"><span data-stu-id="ea778-138">Leading byte.</span></span> |
| <span data-ttu-id="ea778-139">**COMMON_LVB_TRAILING_BYTE**`0x0200`</span><span class="sxs-lookup"><span data-stu-id="ea778-139">**COMMON_LVB_TRAILING_BYTE** `0x0200`</span></span> | <span data-ttu-id="ea778-140">尾端位元組。</span><span class="sxs-lookup"><span data-stu-id="ea778-140">Trailing byte.</span></span> |
| <span data-ttu-id="ea778-141">**COMMON_LVB_GRID_HORIZONTAL**`0x0400`</span><span class="sxs-lookup"><span data-stu-id="ea778-141">**COMMON_LVB_GRID_HORIZONTAL** `0x0400`</span></span> | <span data-ttu-id="ea778-142">上水準。</span><span class="sxs-lookup"><span data-stu-id="ea778-142">Top horizontal.</span></span> |
| <span data-ttu-id="ea778-143">**COMMON_LVB_GRID_LVERTICAL**`0x0800`</span><span class="sxs-lookup"><span data-stu-id="ea778-143">**COMMON_LVB_GRID_LVERTICAL** `0x0800`</span></span> | <span data-ttu-id="ea778-144">左方垂直。</span><span class="sxs-lookup"><span data-stu-id="ea778-144">Left vertical.</span></span> |
| <span data-ttu-id="ea778-145">**COMMON_LVB_GRID_RVERTICAL**`0x1000`</span><span class="sxs-lookup"><span data-stu-id="ea778-145">**COMMON_LVB_GRID_RVERTICAL** `0x1000`</span></span> | <span data-ttu-id="ea778-146">右垂直。</span><span class="sxs-lookup"><span data-stu-id="ea778-146">Right vertical.</span></span> |
| <span data-ttu-id="ea778-147">**COMMON_LVB_REVERSE_VIDEO**`0x4000`</span><span class="sxs-lookup"><span data-stu-id="ea778-147">**COMMON_LVB_REVERSE_VIDEO** `0x4000`</span></span> | <span data-ttu-id="ea778-148">反向前景和背景屬性。</span><span class="sxs-lookup"><span data-stu-id="ea778-148">Reverse foreground and background attribute.</span></span> |
| <span data-ttu-id="ea778-149">**COMMON_LVB_UNDERSCORE**`0x8000`</span><span class="sxs-lookup"><span data-stu-id="ea778-149">**COMMON_LVB_UNDERSCORE** `0x8000`</span></span> | <span data-ttu-id="ea778-150">強調。</span><span class="sxs-lookup"><span data-stu-id="ea778-150">Underscore.</span></span> |

## <a name="examples"></a><span data-ttu-id="ea778-151">範例</span><span class="sxs-lookup"><span data-stu-id="ea778-151">Examples</span></span>

<span data-ttu-id="ea778-152">如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="ea778-152">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="ea778-153">規格需求</span><span class="sxs-lookup"><span data-stu-id="ea778-153">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ea778-154">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="ea778-154">Minimum supported client</span></span> | <span data-ttu-id="ea778-155">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="ea778-155">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="ea778-156">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="ea778-156">Minimum supported server</span></span> | <span data-ttu-id="ea778-157">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="ea778-157">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="ea778-158">標頭</span><span class="sxs-lookup"><span data-stu-id="ea778-158">Header</span></span> | <span data-ttu-id="ea778-159">WinCon (包含) 的 Windows。h</span><span class="sxs-lookup"><span data-stu-id="ea778-159">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="ea778-160">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea778-160">See also</span></span>

[<span data-ttu-id="ea778-161">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="ea778-161">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="ea778-162">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="ea778-162">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="ea778-163">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="ea778-163">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

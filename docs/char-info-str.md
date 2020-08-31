---
title: CHAR_INFO 結構
description: 指定 Unicode 或 ANSI 字元及其屬性。 主控台函式會使用此結構讀取和寫入主控台螢幕緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6244edaa06b6dd69f8ab3962cf42cb893d08f699
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059374"
---
# <a name="char_info-structure"></a><span data-ttu-id="21987-105">CHAR \_ 資訊結構</span><span class="sxs-lookup"><span data-stu-id="21987-105">CHAR\_INFO structure</span></span>


<span data-ttu-id="21987-106">指定 Unicode 或 ANSI 字元及其屬性。</span><span class="sxs-lookup"><span data-stu-id="21987-106">Specifies a Unicode or ANSI character and its attributes.</span></span> <span data-ttu-id="21987-107">主控台函式會使用此結構讀取和寫入主控台螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="21987-107">This structure is used by console functions to read from and write to a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="21987-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="21987-108">Syntax</span></span>
------

```C
typedef struct _CHAR_INFO {
  union {
    WCHAR UnicodeChar;
    CHAR  AsciiChar;
  } Char;
  WORD  Attributes;
} CHAR_INFO, *PCHAR_INFO;
```

<a name="members"></a><span data-ttu-id="21987-109">成員</span><span class="sxs-lookup"><span data-stu-id="21987-109">Members</span></span>
-------

<span data-ttu-id="21987-110">**字元**</span><span class="sxs-lookup"><span data-stu-id="21987-110">**Char**</span></span>  
<span data-ttu-id="21987-111">下列成員的聯集。</span><span class="sxs-lookup"><span data-stu-id="21987-111">A union of the following members.</span></span>

<span data-ttu-id="21987-112">**UnicodeChar**</span><span class="sxs-lookup"><span data-stu-id="21987-112">**UnicodeChar**</span></span>  
<span data-ttu-id="21987-113">螢幕緩衝區字元資料格的 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="21987-113">Unicode character of a screen buffer character cell.</span></span>

<span data-ttu-id="21987-114">**AsciiChar**</span><span class="sxs-lookup"><span data-stu-id="21987-114">**AsciiChar**</span></span>  
<span data-ttu-id="21987-115">螢幕緩衝區字元資料格的 ANSI 字元。</span><span class="sxs-lookup"><span data-stu-id="21987-115">ANSI character of a screen buffer character cell.</span></span>

<span data-ttu-id="21987-116">**屬性**</span><span class="sxs-lookup"><span data-stu-id="21987-116">**Attributes**</span></span>  
<span data-ttu-id="21987-117">字元屬性。</span><span class="sxs-lookup"><span data-stu-id="21987-117">The character attributes.</span></span> <span data-ttu-id="21987-118">這個成員可以是零或下列值的任何組合。</span><span class="sxs-lookup"><span data-stu-id="21987-118">This member can be zero or any combination of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="21987-119">值</span><span class="sxs-lookup"><span data-stu-id="21987-119">Value</span></span></th>
<th><span data-ttu-id="21987-120">意義</span><span class="sxs-lookup"><span data-stu-id="21987-120">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="21987-121"><span id="FOREGROUND_BLUE"></span><span id="foreground_blue"></span>
<strong>FOREGROUND_BLUE</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="21987-121"><span id="FOREGROUND_BLUE"></span><span id="foreground_blue"></span>
<strong>FOREGROUND_BLUE</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="21987-122">文字色彩包含藍色。</span><span class="sxs-lookup"><span data-stu-id="21987-122">Text color contains blue.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="21987-123"><span id="FOREGROUND_GREEN"></span><span id="foreground_green"></span>
<strong>FOREGROUND_GREEN</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="21987-123"><span id="FOREGROUND_GREEN"></span><span id="foreground_green"></span>
<strong>FOREGROUND_GREEN</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="21987-124">文字色彩包含綠色。</span><span class="sxs-lookup"><span data-stu-id="21987-124">Text color contains green.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="21987-125"><span id="FOREGROUND_RED"></span><span id="foreground_red"></span>
<strong>FOREGROUND_RED</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="21987-125"><span id="FOREGROUND_RED"></span><span id="foreground_red"></span>
<strong>FOREGROUND_RED</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="21987-126">文字色彩包含紅色。</span><span class="sxs-lookup"><span data-stu-id="21987-126">Text color contains red.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="21987-127"><span id="FOREGROUND_INTENSITY"></span><span id="foreground_intensity"></span>
<strong>FOREGROUND_INTENSITY</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="21987-127"><span id="FOREGROUND_INTENSITY"></span><span id="foreground_intensity"></span>
<strong>FOREGROUND_INTENSITY</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="21987-128">文字色彩為更。</span><span class="sxs-lookup"><span data-stu-id="21987-128">Text color is intensified.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="21987-129"><span id="BACKGROUND_BLUE"></span><span id="background_blue"></span>
<strong>BACKGROUND_BLUE</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="21987-129"><span id="BACKGROUND_BLUE"></span><span id="background_blue"></span>
<strong>BACKGROUND_BLUE</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="21987-130">背景色彩包含藍色。</span><span class="sxs-lookup"><span data-stu-id="21987-130">Background color contains blue.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="21987-131"><span id="BACKGROUND_GREEN"></span><span id="background_green"></span>
<strong>BACKGROUND_GREEN</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="21987-131"><span id="BACKGROUND_GREEN"></span><span id="background_green"></span>
<strong>BACKGROUND_GREEN</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="21987-132">背景色彩包含綠色。</span><span class="sxs-lookup"><span data-stu-id="21987-132">Background color contains green.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="21987-133"><span id="BACKGROUND_RED"></span><span id="background_red"></span>
<strong>BACKGROUND_RED</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="21987-133"><span id="BACKGROUND_RED"></span><span id="background_red"></span>
<strong>BACKGROUND_RED</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="21987-134">背景色彩包含紅色。</span><span class="sxs-lookup"><span data-stu-id="21987-134">Background color contains red.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="21987-135"><span id="BACKGROUND_INTENSITY"></span><span id="background_intensity"></span>
<strong>BACKGROUND_INTENSITY</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="21987-135"><span id="BACKGROUND_INTENSITY"></span><span id="background_intensity"></span>
<strong>BACKGROUND_INTENSITY</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="21987-136">背景色彩為更。</span><span class="sxs-lookup"><span data-stu-id="21987-136">Background color is intensified.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="21987-137"><span id="COMMON_LVB_LEADING_BYTE"></span><span id="common_lvb_leading_byte"></span>
<strong>COMMON_LVB_LEADING_BYTE</strong> 0x0100</span><span class="sxs-lookup"><span data-stu-id="21987-137"><span id="COMMON_LVB_LEADING_BYTE"></span><span id="common_lvb_leading_byte"></span>
<strong>COMMON_LVB_LEADING_BYTE</strong> 0x0100</span></span></td>
<td><p><span data-ttu-id="21987-138">前置位元組。</span><span class="sxs-lookup"><span data-stu-id="21987-138">Leading byte.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="21987-139"><span id="COMMON_LVB_TRAILING_BYTE"></span><span id="common_lvb_trailing_byte"></span>
<strong>COMMON_LVB_TRAILING_BYTE</strong> 0x0200</span><span class="sxs-lookup"><span data-stu-id="21987-139"><span id="COMMON_LVB_TRAILING_BYTE"></span><span id="common_lvb_trailing_byte"></span>
<strong>COMMON_LVB_TRAILING_BYTE</strong> 0x0200</span></span></td>
<td><p><span data-ttu-id="21987-140">尾端位元組。</span><span class="sxs-lookup"><span data-stu-id="21987-140">Trailing byte.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="21987-141"><span id="COMMON_LVB_GRID_HORIZONTAL"></span><span id="common_lvb_grid_horizontal"></span>
<strong>COMMON_LVB_GRID_HORIZONTAL</strong> 0x0400</span><span class="sxs-lookup"><span data-stu-id="21987-141"><span id="COMMON_LVB_GRID_HORIZONTAL"></span><span id="common_lvb_grid_horizontal"></span>
<strong>COMMON_LVB_GRID_HORIZONTAL</strong> 0x0400</span></span></td>
<td><p><span data-ttu-id="21987-142">上水準</span><span class="sxs-lookup"><span data-stu-id="21987-142">Top horizontal</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="21987-143"><span id="COMMON_LVB_GRID_LVERTICAL"></span><span id="common_lvb_grid_lvertical"></span>
<strong>COMMON_LVB_GRID_LVERTICAL</strong> 0x0800</span><span class="sxs-lookup"><span data-stu-id="21987-143"><span id="COMMON_LVB_GRID_LVERTICAL"></span><span id="common_lvb_grid_lvertical"></span>
<strong>COMMON_LVB_GRID_LVERTICAL</strong> 0x0800</span></span></td>
<td><p><span data-ttu-id="21987-144">左方垂直。</span><span class="sxs-lookup"><span data-stu-id="21987-144">Left vertical.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="21987-145"><span id="COMMON_LVB_GRID_RVERTICAL"></span><span id="common_lvb_grid_rvertical"></span>
<strong>COMMON_LVB_GRID_RVERTICAL</strong> 0x1000</span><span class="sxs-lookup"><span data-stu-id="21987-145"><span id="COMMON_LVB_GRID_RVERTICAL"></span><span id="common_lvb_grid_rvertical"></span>
<strong>COMMON_LVB_GRID_RVERTICAL</strong> 0x1000</span></span></td>
<td><p><span data-ttu-id="21987-146">右垂直。</span><span class="sxs-lookup"><span data-stu-id="21987-146">Right vertical.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="21987-147"><span id="COMMON_LVB_REVERSE_VIDEO"></span><span id="common_lvb_reverse_video"></span>
<strong>COMMON_LVB_REVERSE_VIDEO</strong> 0x4000</span><span class="sxs-lookup"><span data-stu-id="21987-147"><span id="COMMON_LVB_REVERSE_VIDEO"></span><span id="common_lvb_reverse_video"></span>
<strong>COMMON_LVB_REVERSE_VIDEO</strong> 0x4000</span></span></td>
<td><p><span data-ttu-id="21987-148">反向前景和背景屬性。</span><span class="sxs-lookup"><span data-stu-id="21987-148">Reverse foreground and background attribute.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="21987-149"><span id="COMMON_LVB_UNDERSCORE"></span><span id="common_lvb_underscore"></span>
<strong>COMMON_LVB_UNDERSCORE</strong> 0x8000</span><span class="sxs-lookup"><span data-stu-id="21987-149"><span id="COMMON_LVB_UNDERSCORE"></span><span id="common_lvb_underscore"></span>
<strong>COMMON_LVB_UNDERSCORE</strong> 0x8000</span></span></td>
<td><p><span data-ttu-id="21987-150">強調。</span><span class="sxs-lookup"><span data-stu-id="21987-150">Underscore.</span></span></p></td>
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

 

<a name="examples"></a><span data-ttu-id="21987-151">範例</span><span class="sxs-lookup"><span data-stu-id="21987-151">Examples</span></span>
--------

<span data-ttu-id="21987-152">如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="21987-152">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="21987-153">規格需求</span><span class="sxs-lookup"><span data-stu-id="21987-153">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="21987-154">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="21987-154">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="21987-155">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="21987-155">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="21987-156">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="21987-156">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="21987-157">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="21987-157">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="21987-158">標頭</span><span class="sxs-lookup"><span data-stu-id="21987-158">Header</span></span></p></td>
<td><span data-ttu-id="21987-159">Wincon (包含) 的 Windows。h</span><span class="sxs-lookup"><span data-stu-id="21987-159">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="21987-160"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="21987-160"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="21987-161">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="21987-161">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="21987-162">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="21987-162">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="21987-163">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="21987-163">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

 

 





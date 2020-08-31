---
title: CONSOLE_FONT_INFOEX 結構
description: 請參閱有關 CONSOLE_FONT_INFOEX 結構的參考資訊，其中包含主控台字型的延伸資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi3/CONSOLE_FONT_INFOEX
- wincon/CONSOLE_FONT_INFOEX
- CONSOLE_FONT_INFOEX
- consoleapi3/PCONSOLE_FONT_INFOEX
- wincon/PCONSOLE_FONT_INFOEX
- PCONSOLE_FONT_INFOEX
MS-HAID:
- base.console\_font\_infoex
- consoles.console\_font\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e9a087e1-264d-4d48-8adb-771a0e35b511
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFOEX
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 12977e288a63397c581143683047239e4d410eec
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059319"
---
# <a name="console_font_infoex-structure"></a><span data-ttu-id="21ac9-104">主控台 \_ 字型 \_ INFOEX 結構</span><span class="sxs-lookup"><span data-stu-id="21ac9-104">CONSOLE\_FONT\_INFOEX structure</span></span>


<span data-ttu-id="21ac9-105">包含主控台字型的延伸資訊。</span><span class="sxs-lookup"><span data-stu-id="21ac9-105">Contains extended information for a console font.</span></span>

<a name="syntax"></a><span data-ttu-id="21ac9-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="21ac9-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

<a name="members"></a><span data-ttu-id="21ac9-107">成員</span><span class="sxs-lookup"><span data-stu-id="21ac9-107">Members</span></span>
-------

<span data-ttu-id="21ac9-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="21ac9-108">**cbSize**</span></span>  
<span data-ttu-id="21ac9-109">此結構的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="21ac9-109">The size of this structure, in bytes.</span></span> <span data-ttu-id="21ac9-110">這個成員必須在 `sizeof(CONSOLE_FONT_INFOEX)` 呼叫 [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) 之前設定為，否則它將會失敗。</span><span class="sxs-lookup"><span data-stu-id="21ac9-110">This member must be set to `sizeof(CONSOLE_FONT_INFOEX)` before calling [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) or it will fail.</span></span>

<span data-ttu-id="21ac9-111">**nFont**</span><span class="sxs-lookup"><span data-stu-id="21ac9-111">**nFont**</span></span>  
<span data-ttu-id="21ac9-112">系統的主控台字型表中的字型索引。</span><span class="sxs-lookup"><span data-stu-id="21ac9-112">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="21ac9-113">**dwFontSize**</span><span class="sxs-lookup"><span data-stu-id="21ac9-113">**dwFontSize**</span></span>  
<span data-ttu-id="21ac9-114">[**COORD**](coord-str.md)結構，其中包含字型中每個字元的寬度和高度（以邏輯單位表示）。</span><span class="sxs-lookup"><span data-stu-id="21ac9-114">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="21ac9-115">**X**成員包含寬度，而**Y**成員包含高度。</span><span class="sxs-lookup"><span data-stu-id="21ac9-115">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="21ac9-116">**FontFamily**</span><span class="sxs-lookup"><span data-stu-id="21ac9-116">**FontFamily**</span></span>  
<span data-ttu-id="21ac9-117">字型音調和系列。</span><span class="sxs-lookup"><span data-stu-id="21ac9-117">The font pitch and family.</span></span> <span data-ttu-id="21ac9-118">如需此成員可能值的詳細資訊，請參閱[**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132)結構之**tmPitchAndFamily**成員的描述。</span><span class="sxs-lookup"><span data-stu-id="21ac9-118">For information about the possible values for this member, see the description of the **tmPitchAndFamily** member of the [**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132) structure.</span></span>

<span data-ttu-id="21ac9-119">**FontWeight**</span><span class="sxs-lookup"><span data-stu-id="21ac9-119">**FontWeight**</span></span>  
<span data-ttu-id="21ac9-120">字型粗細。</span><span class="sxs-lookup"><span data-stu-id="21ac9-120">The font weight.</span></span> <span data-ttu-id="21ac9-121">權數的範圍可以從100到1000，以100的倍數為限。</span><span class="sxs-lookup"><span data-stu-id="21ac9-121">The weight can range from 100 to 1000, in multiples of 100.</span></span> <span data-ttu-id="21ac9-122">例如，標準權數為400，而700為粗體。</span><span class="sxs-lookup"><span data-stu-id="21ac9-122">For example, the normal weight is 400, while 700 is bold.</span></span>

<span data-ttu-id="21ac9-123">**FaceName**</span><span class="sxs-lookup"><span data-stu-id="21ac9-123">**FaceName**</span></span>  
<span data-ttu-id="21ac9-124">字型 (的名稱，例如 [中] 或 [Arial]) 。</span><span class="sxs-lookup"><span data-stu-id="21ac9-124">The name of the typeface (such as Courier or Arial).</span></span>

<a name="remarks"></a><span data-ttu-id="21ac9-125">備註</span><span class="sxs-lookup"><span data-stu-id="21ac9-125">Remarks</span></span>
-------

<span data-ttu-id="21ac9-126">若要取得字型的大小，請將字型索引傳遞給 [**GetConsoleFontSize**](getconsolefontsize.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="21ac9-126">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

<a name="requirements"></a><span data-ttu-id="21ac9-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="21ac9-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="21ac9-128">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="21ac9-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="21ac9-129">Windows Vista [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="21ac9-129">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="21ac9-130">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="21ac9-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="21ac9-131">Windows Server 2008 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="21ac9-131">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="21ac9-132">標頭</span><span class="sxs-lookup"><span data-stu-id="21ac9-132">Header</span></span></p></td>
<td><span data-ttu-id="21ac9-133">Wincon (包含) 的 Windows。h</span><span class="sxs-lookup"><span data-stu-id="21ac9-133">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="21ac9-134"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="21ac9-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="21ac9-135">**GetCurrentConsoleFontEx**</span><span class="sxs-lookup"><span data-stu-id="21ac9-135">**GetCurrentConsoleFontEx**</span></span>](getcurrentconsolefontex.md)

 

 





---
title: CONSOLE_FONT_INFO 結構
description: 請參閱 CONSOLE_FONT_INFO 結構的參考資訊，其中包含主控台字型的索引和大小。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- wincontypes/CONSOLE_FONT_INFO
- wincon/CONSOLE_FONT_INFO
- CONSOLE_FONT_INFO
- wincontypes/PCONSOLE_FONT_INFO
- wincon/PCONSOLE_FONT_INFO
- PCONSOLE_FONT_INFO
MS-HAID:
- '\_win32\_console\_font\_info\_str'
- base.console\_font\_info\_str
- consoles.console\_font\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 380b8183-1964-46f2-a511-01f39f21f5c5
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: c4218c53eacd95d67f3dc9056f5a1024ac1a8ab0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059334"
---
# <a name="console_font_info-structure"></a><span data-ttu-id="35069-104">主控台 \_ 字型 \_ 資訊結構</span><span class="sxs-lookup"><span data-stu-id="35069-104">CONSOLE\_FONT\_INFO structure</span></span>


<span data-ttu-id="35069-105">包含主控台字型的資訊。</span><span class="sxs-lookup"><span data-stu-id="35069-105">Contains information for a console font.</span></span>

<a name="syntax"></a><span data-ttu-id="35069-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="35069-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

<a name="members"></a><span data-ttu-id="35069-107">成員</span><span class="sxs-lookup"><span data-stu-id="35069-107">Members</span></span>
-------

<span data-ttu-id="35069-108">**nFont**</span><span class="sxs-lookup"><span data-stu-id="35069-108">**nFont**</span></span>  
<span data-ttu-id="35069-109">系統的主控台字型表中的字型索引。</span><span class="sxs-lookup"><span data-stu-id="35069-109">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="35069-110">**dwFontSize**</span><span class="sxs-lookup"><span data-stu-id="35069-110">**dwFontSize**</span></span>  
<span data-ttu-id="35069-111">[**COORD**](coord-str.md)結構，其中包含字型中每個字元的寬度和高度（以邏輯單位表示）。</span><span class="sxs-lookup"><span data-stu-id="35069-111">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="35069-112">**X**成員包含寬度，而**Y**成員包含高度。</span><span class="sxs-lookup"><span data-stu-id="35069-112">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<a name="remarks"></a><span data-ttu-id="35069-113">備註</span><span class="sxs-lookup"><span data-stu-id="35069-113">Remarks</span></span>
-------

<span data-ttu-id="35069-114">若要取得字型的大小，請將字型索引傳遞給 [**GetConsoleFontSize**](getconsolefontsize.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="35069-114">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

<a name="requirements"></a><span data-ttu-id="35069-115">規格需求</span><span class="sxs-lookup"><span data-stu-id="35069-115">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="35069-116">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="35069-116">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="35069-117">Windows XP [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="35069-117">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="35069-118">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="35069-118">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="35069-119">Windows Server 2003 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="35069-119">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="35069-120">標頭</span><span class="sxs-lookup"><span data-stu-id="35069-120">Header</span></span></p></td>
<td><span data-ttu-id="35069-121">Wincon (包含) 的 Windows。h</span><span class="sxs-lookup"><span data-stu-id="35069-121">Wincon.h (include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="35069-122"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="35069-122"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="35069-123">**COORD**</span><span class="sxs-lookup"><span data-stu-id="35069-123">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="35069-124">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="35069-124">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)

 

 





---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- wincontypes/SMALL_RECT
- wincon/SMALL_RECT
- SMALL_RECT
title: SMALL_RECT 結構
description: 定義矩形左上角和右下角的座標。
MS-HAID:
- '\_win32\_small\_rect\_str'
- base.small\_rect\_str
- consoles.small\_rect\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 62639815-c7e9-4ae2-b152-61290f78422b
topic_type:
- apiref
api_name:
- SMALL_RECT
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: b0c0bfe93c85af89c5aaefeda032795de72ed627
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059547"
---
# <a name="small_rect-structure"></a><span data-ttu-id="f9a1b-104">SMALL \_ RECT 結構</span><span class="sxs-lookup"><span data-stu-id="f9a1b-104">SMALL\_RECT structure</span></span>


<span data-ttu-id="f9a1b-105">定義矩形左上角和右下角的座標。</span><span class="sxs-lookup"><span data-stu-id="f9a1b-105">Defines the coordinates of the upper left and lower right corners of a rectangle.</span></span>

<a name="syntax"></a><span data-ttu-id="f9a1b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f9a1b-106">Syntax</span></span>
------

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

<a name="members"></a><span data-ttu-id="f9a1b-107">成員</span><span class="sxs-lookup"><span data-stu-id="f9a1b-107">Members</span></span>
-------

<span data-ttu-id="f9a1b-108">**離開**</span><span class="sxs-lookup"><span data-stu-id="f9a1b-108">**Left**</span></span>  
<span data-ttu-id="f9a1b-109">矩形左上角的 x 座標。</span><span class="sxs-lookup"><span data-stu-id="f9a1b-109">The x-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="f9a1b-110">**前幾個**</span><span class="sxs-lookup"><span data-stu-id="f9a1b-110">**Top**</span></span>  
<span data-ttu-id="f9a1b-111">矩形左上角的 y 座標。</span><span class="sxs-lookup"><span data-stu-id="f9a1b-111">The y-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="f9a1b-112">**對**</span><span class="sxs-lookup"><span data-stu-id="f9a1b-112">**Right**</span></span>  
<span data-ttu-id="f9a1b-113">矩形右下角的 x 座標。</span><span class="sxs-lookup"><span data-stu-id="f9a1b-113">The x-coordinate of the lower right corner of the rectangle.</span></span>

<span data-ttu-id="f9a1b-114">**下層**</span><span class="sxs-lookup"><span data-stu-id="f9a1b-114">**Bottom**</span></span>  
<span data-ttu-id="f9a1b-115">矩形右下角的 y 座標。</span><span class="sxs-lookup"><span data-stu-id="f9a1b-115">The y-coordinate of the lower right corner of the rectangle.</span></span>

<a name="remarks"></a><span data-ttu-id="f9a1b-116">備註</span><span class="sxs-lookup"><span data-stu-id="f9a1b-116">Remarks</span></span>
-------

<span data-ttu-id="f9a1b-117">主控台函式會使用此結構來指定主控台螢幕緩衝區的矩形區域，其中的座標會指定螢幕緩衝區字元資料格的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="f9a1b-117">This structure is used by console functions to specify rectangular areas of console screen buffers, where the coordinates specify the rows and columns of screen-buffer character cells.</span></span>

<a name="examples"></a><span data-ttu-id="f9a1b-118">範例</span><span class="sxs-lookup"><span data-stu-id="f9a1b-118">Examples</span></span>
--------

<span data-ttu-id="f9a1b-119">如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="f9a1b-119">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="f9a1b-120">規格需求</span><span class="sxs-lookup"><span data-stu-id="f9a1b-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f9a1b-121">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="f9a1b-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="f9a1b-122">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="f9a1b-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f9a1b-123">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="f9a1b-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="f9a1b-124">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="f9a1b-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f9a1b-125">標頭</span><span class="sxs-lookup"><span data-stu-id="f9a1b-125">Header</span></span></p></td>
<td><span data-ttu-id="f9a1b-126">WinConTypes .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="f9a1b-126">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="f9a1b-127"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9a1b-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="f9a1b-128">**矩形**</span><span class="sxs-lookup"><span data-stu-id="f9a1b-128">**RECT**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162897)

[<span data-ttu-id="f9a1b-129">**RECTL**</span><span class="sxs-lookup"><span data-stu-id="f9a1b-129">**RECTL**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162907)

 

 





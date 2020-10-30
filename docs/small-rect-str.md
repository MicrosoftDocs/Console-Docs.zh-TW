---
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 93121864c8754b281b92051a5e4a174b2d5956a3
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037096"
---
# <a name="small_rect-structure"></a><span data-ttu-id="6c426-104">SMALL \_ RECT 結構</span><span class="sxs-lookup"><span data-stu-id="6c426-104">SMALL\_RECT structure</span></span>

<span data-ttu-id="6c426-105">定義矩形左上角和右下角的座標。</span><span class="sxs-lookup"><span data-stu-id="6c426-105">Defines the coordinates of the upper left and lower right corners of a rectangle.</span></span>

## <a name="syntax"></a><span data-ttu-id="6c426-106">語法</span><span class="sxs-lookup"><span data-stu-id="6c426-106">Syntax</span></span>

```C
typedef struct _SMALL_RECT {
  SHORT Left;
  SHORT Top;
  SHORT Right;
  SHORT Bottom;
} SMALL_RECT;
```

## <a name="members"></a><span data-ttu-id="6c426-107">成員</span><span class="sxs-lookup"><span data-stu-id="6c426-107">Members</span></span>

<span data-ttu-id="6c426-108">**離開**</span><span class="sxs-lookup"><span data-stu-id="6c426-108">**Left**</span></span>  
<span data-ttu-id="6c426-109">矩形左上角的 x 座標。</span><span class="sxs-lookup"><span data-stu-id="6c426-109">The x-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="6c426-110">**前幾個**</span><span class="sxs-lookup"><span data-stu-id="6c426-110">**Top**</span></span>  
<span data-ttu-id="6c426-111">矩形左上角的 y 座標。</span><span class="sxs-lookup"><span data-stu-id="6c426-111">The y-coordinate of the upper left corner of the rectangle.</span></span>

<span data-ttu-id="6c426-112">**對**</span><span class="sxs-lookup"><span data-stu-id="6c426-112">**Right**</span></span>  
<span data-ttu-id="6c426-113">矩形右下角的 x 座標。</span><span class="sxs-lookup"><span data-stu-id="6c426-113">The x-coordinate of the lower right corner of the rectangle.</span></span>

<span data-ttu-id="6c426-114">**底端**</span><span class="sxs-lookup"><span data-stu-id="6c426-114">**Bottom**</span></span>  
<span data-ttu-id="6c426-115">矩形右下角的 y 座標。</span><span class="sxs-lookup"><span data-stu-id="6c426-115">The y-coordinate of the lower right corner of the rectangle.</span></span>

## <a name="remarks"></a><span data-ttu-id="6c426-116">備註</span><span class="sxs-lookup"><span data-stu-id="6c426-116">Remarks</span></span>

<span data-ttu-id="6c426-117">主控台函式會使用此結構來指定主控台螢幕緩衝區的矩形區域，其中的座標會指定螢幕緩衝區字元資料格的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="6c426-117">This structure is used by console functions to specify rectangular areas of console screen buffers, where the coordinates specify the rows and columns of screen-buffer character cells.</span></span>

## <a name="examples"></a><span data-ttu-id="6c426-118">範例</span><span class="sxs-lookup"><span data-stu-id="6c426-118">Examples</span></span>

<span data-ttu-id="6c426-119">如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="6c426-119">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="6c426-120">規格需求</span><span class="sxs-lookup"><span data-stu-id="6c426-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="6c426-121">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="6c426-121">Minimum supported client</span></span> | <span data-ttu-id="6c426-122">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="6c426-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="6c426-123">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="6c426-123">Minimum supported server</span></span> | <span data-ttu-id="6c426-124">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="6c426-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="6c426-125">標頭</span><span class="sxs-lookup"><span data-stu-id="6c426-125">Header</span></span> | <span data-ttu-id="6c426-126">WinConTypes .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="6c426-126">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="6c426-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="6c426-127">See also</span></span>

[<span data-ttu-id="6c426-128">**矩形**</span><span class="sxs-lookup"><span data-stu-id="6c426-128">**RECT**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162897)

[<span data-ttu-id="6c426-129">**RECTL**</span><span class="sxs-lookup"><span data-stu-id="6c426-129">**RECTL**</span></span>](https://msdn.microsoft.com/library/windows/desktop/dd162907)

---
title: COORD 結構
description: 在主控台螢幕緩衝區中定義字元資料格的座標。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- wincontypes/COORD
- wincon/COORD
- COORD
- wincontypes/PCOORD
- wincon/PCOORD
- PCOORD
MS-HAID:
- '\_win32\_coord\_str'
- base.coord\_str
- consoles.coord\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d730c46e-ea17-475e-b956-8ee5f4f5c04e
topic_type:
- apiref
api_name:
- COORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: c8e6f87c3a2730a8af21b9bc064c71900fb82f5b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038306"
---
# <a name="coord-structure"></a><span data-ttu-id="4031d-104">COORD 結構</span><span class="sxs-lookup"><span data-stu-id="4031d-104">COORD structure</span></span>

<span data-ttu-id="4031d-105">在主控台螢幕緩衝區中定義字元資料格的座標。</span><span class="sxs-lookup"><span data-stu-id="4031d-105">Defines the coordinates of a character cell in a console screen buffer.</span></span> <span data-ttu-id="4031d-106">座標系統的原點 (0，0) 位於緩衝區的左上角儲存格。</span><span class="sxs-lookup"><span data-stu-id="4031d-106">The origin of the coordinate system (0,0) is at the top, left cell of the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="4031d-107">語法</span><span class="sxs-lookup"><span data-stu-id="4031d-107">Syntax</span></span>

```C
typedef struct _COORD {
  SHORT X;
  SHORT Y;
} COORD, *PCOORD;
```

## <a name="members"></a><span data-ttu-id="4031d-108">成員</span><span class="sxs-lookup"><span data-stu-id="4031d-108">Members</span></span>

<span data-ttu-id="4031d-109">**X**</span><span class="sxs-lookup"><span data-stu-id="4031d-109">**X**</span></span>  
<span data-ttu-id="4031d-110">水準座標或資料行值。</span><span class="sxs-lookup"><span data-stu-id="4031d-110">The horizontal coordinate or column value.</span></span> <span data-ttu-id="4031d-111">單位取決於函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="4031d-111">The units depend on the function call.</span></span>

<span data-ttu-id="4031d-112">**Y**</span><span class="sxs-lookup"><span data-stu-id="4031d-112">**Y**</span></span>  
<span data-ttu-id="4031d-113">垂直座標或資料行值。</span><span class="sxs-lookup"><span data-stu-id="4031d-113">The vertical coordinate or row value.</span></span> <span data-ttu-id="4031d-114">單位取決於函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="4031d-114">The units depend on the function call.</span></span>

## <a name="examples"></a><span data-ttu-id="4031d-115">範例</span><span class="sxs-lookup"><span data-stu-id="4031d-115">Examples</span></span>

<span data-ttu-id="4031d-116">如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="4031d-116">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="4031d-117">規格需求</span><span class="sxs-lookup"><span data-stu-id="4031d-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4031d-118">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="4031d-118">Minimum supported client</span></span> | <span data-ttu-id="4031d-119">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="4031d-119">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="4031d-120">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="4031d-120">Minimum supported server</span></span> | <span data-ttu-id="4031d-121">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="4031d-121">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="4031d-122">標頭</span><span class="sxs-lookup"><span data-stu-id="4031d-122">Header</span></span> | <span data-ttu-id="4031d-123">WinConTypes .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="4031d-123">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="4031d-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="4031d-124">See also</span></span>

[<span data-ttu-id="4031d-125">**主控台 \_ 字型 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="4031d-125">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="4031d-126">**主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="4031d-126">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="4031d-127">**主控台 \_ 選取 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="4031d-127">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)

[<span data-ttu-id="4031d-128">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="4031d-128">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="4031d-129">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="4031d-129">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="4031d-130">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="4031d-130">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)

[<span data-ttu-id="4031d-131">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="4031d-131">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="4031d-132">**滑鼠 \_ 事件 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="4031d-132">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="4031d-133">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="4031d-133">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="4031d-134">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="4031d-134">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="4031d-135">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="4031d-135">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="4031d-136">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="4031d-136">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="4031d-137">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="4031d-137">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="4031d-138">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="4031d-138">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)

[<span data-ttu-id="4031d-139">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="4031d-139">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="4031d-140">**視窗 \_ 緩衝區 \_ 大小 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="4031d-140">**WINDOW\_BUFFER\_SIZE\_RECORD**</span></span>](window-buffer-size-record-str.md)

[<span data-ttu-id="4031d-141">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="4031d-141">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="4031d-142">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="4031d-142">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="4031d-143">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="4031d-143">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

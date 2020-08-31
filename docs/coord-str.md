---
title: COORD 結構
description: 在主控台螢幕緩衝區中定義字元資料格的座標。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: c29594cbddd69ae8ca6d3f958acd0eeb3cb60e9b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059239"
---
# <a name="coord-structure"></a><span data-ttu-id="ce782-104">COORD 結構</span><span class="sxs-lookup"><span data-stu-id="ce782-104">COORD structure</span></span>


<span data-ttu-id="ce782-105">在主控台螢幕緩衝區中定義字元資料格的座標。</span><span class="sxs-lookup"><span data-stu-id="ce782-105">Defines the coordinates of a character cell in a console screen buffer.</span></span> <span data-ttu-id="ce782-106">座標系統的原點 (0，0) 位於緩衝區的左上角儲存格。</span><span class="sxs-lookup"><span data-stu-id="ce782-106">The origin of the coordinate system (0,0) is at the top, left cell of the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="ce782-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ce782-107">Syntax</span></span>
------

```C
typedef struct _COORD {
  SHORT X;
  SHORT Y;
} COORD, *PCOORD;
```

<a name="members"></a><span data-ttu-id="ce782-108">成員</span><span class="sxs-lookup"><span data-stu-id="ce782-108">Members</span></span>
-------

<span data-ttu-id="ce782-109">**X**</span><span class="sxs-lookup"><span data-stu-id="ce782-109">**X**</span></span>  
<span data-ttu-id="ce782-110">水準座標或資料行值。</span><span class="sxs-lookup"><span data-stu-id="ce782-110">The horizontal coordinate or column value.</span></span> <span data-ttu-id="ce782-111">單位取決於函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="ce782-111">The units depend on the function call.</span></span>

<span data-ttu-id="ce782-112">**Y**</span><span class="sxs-lookup"><span data-stu-id="ce782-112">**Y**</span></span>  
<span data-ttu-id="ce782-113">垂直座標或資料行值。</span><span class="sxs-lookup"><span data-stu-id="ce782-113">The vertical coordinate or row value.</span></span> <span data-ttu-id="ce782-114">單位取決於函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="ce782-114">The units depend on the function call.</span></span>

<a name="examples"></a><span data-ttu-id="ce782-115">範例</span><span class="sxs-lookup"><span data-stu-id="ce782-115">Examples</span></span>
--------

<span data-ttu-id="ce782-116">如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="ce782-116">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="ce782-117">規格需求</span><span class="sxs-lookup"><span data-stu-id="ce782-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="ce782-118">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="ce782-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="ce782-119">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="ce782-119">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ce782-120">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="ce782-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="ce782-121">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="ce782-121">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ce782-122">標頭</span><span class="sxs-lookup"><span data-stu-id="ce782-122">Header</span></span></p></td>
<td><span data-ttu-id="ce782-123">WinConTypes .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="ce782-123">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="ce782-124"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce782-124"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="ce782-125">**主控台 \_ 字型 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="ce782-125">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="ce782-126">**主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="ce782-126">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="ce782-127">**主控台 \_ 選取 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="ce782-127">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)

[<span data-ttu-id="ce782-128">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="ce782-128">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="ce782-129">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="ce782-129">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="ce782-130">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="ce782-130">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)

[<span data-ttu-id="ce782-131">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="ce782-131">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="ce782-132">**滑鼠 \_ 事件 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="ce782-132">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

[<span data-ttu-id="ce782-133">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="ce782-133">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="ce782-134">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="ce782-134">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="ce782-135">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="ce782-135">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="ce782-136">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="ce782-136">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="ce782-137">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="ce782-137">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="ce782-138">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="ce782-138">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)

[<span data-ttu-id="ce782-139">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="ce782-139">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="ce782-140">**視窗 \_ 緩衝區 \_ 大小 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="ce782-140">**WINDOW\_BUFFER\_SIZE\_RECORD**</span></span>](window-buffer-size-record-str.md)

[<span data-ttu-id="ce782-141">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="ce782-141">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="ce782-142">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="ce782-142">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="ce782-143">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="ce782-143">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 





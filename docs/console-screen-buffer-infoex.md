---
title: CONSOLE_SCREEN_BUFFER_INFOEX 結構
description: 請參閱有關 CONSOLE_SCREEN_BUFFER_INFOEX 結構的參考資訊，其中包含主控台螢幕緩衝區的延伸資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFOEX
- wincon/CONSOLE_SCREEN_BUFFER_INFOEX
- CONSOLE_SCREEN_BUFFER_INFOEX
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFOEX
- wincon/PCONSOLE_SCREEN_BUFFER_INFOEX
- PCONSOLE_SCREEN_BUFFER_INFOEX
MS-HAID:
- base.console\_screen\_buffer\_infoex
- consoles.console\_screen\_buffer\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6ed40df3-063d-41c9-8637-510c95104603
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFOEX
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 1e4e30601655190bc6f597bbd33dd99f14f8d488
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358079"
---
# <a name="console_screen_buffer_infoex-structure"></a><span data-ttu-id="ee2aa-104">主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX 結構</span><span class="sxs-lookup"><span data-stu-id="ee2aa-104">CONSOLE\_SCREEN\_BUFFER\_INFOEX structure</span></span>

<span data-ttu-id="ee2aa-105">包含有關主控台螢幕緩衝區的延伸資訊。</span><span class="sxs-lookup"><span data-stu-id="ee2aa-105">Contains extended information about a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="ee2aa-106">語法</span><span class="sxs-lookup"><span data-stu-id="ee2aa-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFOEX {
  ULONG      cbSize;
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
  WORD       wPopupAttributes;
  BOOL       bFullscreenSupported;
  COLORREF   ColorTable[16];
} CONSOLE_SCREEN_BUFFER_INFOEX, *PCONSOLE_SCREEN_BUFFER_INFOEX;
```

## <a name="members"></a><span data-ttu-id="ee2aa-107">成員</span><span class="sxs-lookup"><span data-stu-id="ee2aa-107">Members</span></span>

<span data-ttu-id="ee2aa-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="ee2aa-108">**cbSize**</span></span>  
<span data-ttu-id="ee2aa-109">此結構的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="ee2aa-109">The size of this structure, in bytes.</span></span>

<span data-ttu-id="ee2aa-110">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="ee2aa-110">**dwSize**</span></span>  
<span data-ttu-id="ee2aa-111">[**COORD**](coord-str.md)結構，其中包含主控台螢幕緩衝區的大小（以字元資料行和資料列為限）。</span><span class="sxs-lookup"><span data-stu-id="ee2aa-111">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="ee2aa-112">**dwCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="ee2aa-112">**dwCursorPosition**</span></span>  
<span data-ttu-id="ee2aa-113">[**COORD**](coord-str.md)結構，其中包含主控台螢幕緩衝區中資料指標的資料行和資料列座標。</span><span class="sxs-lookup"><span data-stu-id="ee2aa-113">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="ee2aa-114">**wAttributes**</span><span class="sxs-lookup"><span data-stu-id="ee2aa-114">**wAttributes**</span></span>  
<span data-ttu-id="ee2aa-115">[**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)和 [**WriteConsole**](writeconsole.md)函式寫入螢幕緩衝區的字元屬性，或 [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)和 [**ReadConsole**](readconsole.md)函式的螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ee2aa-115">The attributes of the characters written to a screen buffer by the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="ee2aa-116">如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#character-attributes)。</span><span class="sxs-lookup"><span data-stu-id="ee2aa-116">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="ee2aa-117">**srWindow**</span><span class="sxs-lookup"><span data-stu-id="ee2aa-117">**srWindow**</span></span>  
<span data-ttu-id="ee2aa-118">[**小型 \_ 矩形**](small-rect-str.md)結構，其中包含顯示視窗左上角和右下角的主控台螢幕緩衝區座標。</span><span class="sxs-lookup"><span data-stu-id="ee2aa-118">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="ee2aa-119">**dwMaximumWindowSize**</span><span class="sxs-lookup"><span data-stu-id="ee2aa-119">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="ee2aa-120">[**COORD**](coord-str.md)結構，其中包含主控台視窗的大小上限（以字元資料行和資料列為限），指定目前的螢幕緩衝區大小和字型和螢幕大小。</span><span class="sxs-lookup"><span data-stu-id="ee2aa-120">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

<span data-ttu-id="ee2aa-121">**wPopupAttributes**</span><span class="sxs-lookup"><span data-stu-id="ee2aa-121">**wPopupAttributes**</span></span>  
<span data-ttu-id="ee2aa-122">主控台快顯視窗的填滿屬性。</span><span class="sxs-lookup"><span data-stu-id="ee2aa-122">The fill attribute for console pop-ups.</span></span>

<span data-ttu-id="ee2aa-123">**bFullscreenSupported**</span><span class="sxs-lookup"><span data-stu-id="ee2aa-123">**bFullscreenSupported**</span></span>  
<span data-ttu-id="ee2aa-124">如果這個成員是 `TRUE` ，則支援全螢幕模式; 否則就不支援。</span><span class="sxs-lookup"><span data-stu-id="ee2aa-124">If this member is `TRUE`, full-screen mode is supported; otherwise, it is not.</span></span> <span data-ttu-id="ee2aa-125">這一律 `FALSE` 適用于 Windows Vista 含 [WDDM 驅動程式模型](/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) 的系統，因為它已不再提供對監視的直接 VGA 存取。</span><span class="sxs-lookup"><span data-stu-id="ee2aa-125">This will always be `FALSE` for systems after Windows Vista with the [WDDM driver model](/windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model) as true direct VGA access to the monitor is no longer available.</span></span>

<span data-ttu-id="ee2aa-126">**ColorTable**</span><span class="sxs-lookup"><span data-stu-id="ee2aa-126">**ColorTable**</span></span>  
<span data-ttu-id="ee2aa-127">描述主控台色彩設定的 [**COLORREF**](/windows/win32/gdi/colorref) 值陣列。</span><span class="sxs-lookup"><span data-stu-id="ee2aa-127">An array of [**COLORREF**](/windows/win32/gdi/colorref) values that describe the console's color settings.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee2aa-128">規格需求</span><span class="sxs-lookup"><span data-stu-id="ee2aa-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="ee2aa-129">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="ee2aa-129">Minimum supported client</span></span> | <span data-ttu-id="ee2aa-130">\[僅限 Windows Vista 桌面應用程式\]</span><span class="sxs-lookup"><span data-stu-id="ee2aa-130">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="ee2aa-131">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="ee2aa-131">Minimum supported server</span></span> | <span data-ttu-id="ee2aa-132">僅限 Windows Server 2008 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="ee2aa-132">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="ee2aa-133">標頭</span><span class="sxs-lookup"><span data-stu-id="ee2aa-133">Header</span></span> | <span data-ttu-id="ee2aa-134">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="ee2aa-134">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="ee2aa-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee2aa-135">See also</span></span>

[<span data-ttu-id="ee2aa-136">**COORD**</span><span class="sxs-lookup"><span data-stu-id="ee2aa-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="ee2aa-137">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="ee2aa-137">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)

[<span data-ttu-id="ee2aa-138">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="ee2aa-138">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)

[<span data-ttu-id="ee2aa-139">**小型 \_ 矩形**</span><span class="sxs-lookup"><span data-stu-id="ee2aa-139">**SMALL\_RECT**</span></span>](small-rect-str.md)
---
title: CONSOLE_SCREEN_BUFFER_INFO 結構
description: 請參閱有關 CONSOLE_SCREEN_BUFFER_INFO 結構的參考資訊，其中包含主控台螢幕緩衝區的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/CONSOLE_SCREEN_BUFFER_INFO
- wincon/CONSOLE_SCREEN_BUFFER_INFO
- CONSOLE_SCREEN_BUFFER_INFO
- consoleapi2/PCONSOLE_SCREEN_BUFFER_INFO
- wincon/PCONSOLE_SCREEN_BUFFER_INFO
- PCONSOLE_SCREEN_BUFFER_INFO
MS-HAID:
- '\_win32\_console\_screen\_buffer\_info\_str'
- base.console\_screen\_buffer\_info\_str
- consoles.console\_screen\_buffer\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 586b3e0f-2f6b-4a03-b8e4-602a892be56d
topic_type:
- apiref
api_name:
- CONSOLE_SCREEN_BUFFER_INFO
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 4089541ddac93f5be61b7a21d5aa88a88061b261
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059295"
---
# <a name="console_screen_buffer_info-structure"></a><span data-ttu-id="9e2f6-104">主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊結構</span><span class="sxs-lookup"><span data-stu-id="9e2f6-104">CONSOLE\_SCREEN\_BUFFER\_INFO structure</span></span>


<span data-ttu-id="9e2f6-105">包含主控台螢幕緩衝區的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-105">Contains information about a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="9e2f6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="9e2f6-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFO {
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
} CONSOLE_SCREEN_BUFFER_INFO;
```

<a name="members"></a><span data-ttu-id="9e2f6-107">成員</span><span class="sxs-lookup"><span data-stu-id="9e2f6-107">Members</span></span>
-------

<span data-ttu-id="9e2f6-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="9e2f6-108">**dwSize**</span></span>  
<span data-ttu-id="9e2f6-109">[**COORD**](coord-str.md)結構，其中包含主控台螢幕緩衝區的大小（以字元資料行和資料列為限）。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="9e2f6-110">**dwCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="9e2f6-110">**dwCursorPosition**</span></span>  
<span data-ttu-id="9e2f6-111">[**COORD**](coord-str.md)結構，其中包含主控台螢幕緩衝區中資料指標的資料行和資料列座標。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-111">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="9e2f6-112">**wAttributes**</span><span class="sxs-lookup"><span data-stu-id="9e2f6-112">**wAttributes**</span></span>  
<span data-ttu-id="9e2f6-113">[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)和[**WriteConsole**](writeconsole.md)函式寫入螢幕緩衝區的字元屬性，或[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)和[**ReadConsole**](readconsole.md)函式的螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-113">The attributes of the characters written to a screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="9e2f6-114">如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#_win32_font_attributes)。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-114">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="9e2f6-115">**srWindow**</span><span class="sxs-lookup"><span data-stu-id="9e2f6-115">**srWindow**</span></span>  
<span data-ttu-id="9e2f6-116">[**小型 \_ 矩形**](small-rect-str.md)結構，其中包含顯示視窗左上角和右下角的主控台螢幕緩衝區座標。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-116">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="9e2f6-117">**dwMaximumWindowSize**</span><span class="sxs-lookup"><span data-stu-id="9e2f6-117">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="9e2f6-118">[**COORD**](coord-str.md)結構，其中包含主控台視窗的大小上限（以字元資料行和資料列為限），指定目前的螢幕緩衝區大小和字型和螢幕大小。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-118">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

<a name="examples"></a><span data-ttu-id="9e2f6-119">範例</span><span class="sxs-lookup"><span data-stu-id="9e2f6-119">Examples</span></span>
--------

<span data-ttu-id="9e2f6-120">如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="9e2f6-120">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

<a name="requirements"></a><span data-ttu-id="9e2f6-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="9e2f6-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="9e2f6-122">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="9e2f6-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="9e2f6-123">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="9e2f6-123">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="9e2f6-124">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="9e2f6-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="9e2f6-125">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="9e2f6-125">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="9e2f6-126">標頭</span><span class="sxs-lookup"><span data-stu-id="9e2f6-126">Header</span></span></p></td>
<td><span data-ttu-id="9e2f6-127">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="9e2f6-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="9e2f6-128"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e2f6-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="9e2f6-129">**COORD**</span><span class="sxs-lookup"><span data-stu-id="9e2f6-129">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="9e2f6-130">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="9e2f6-130">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="9e2f6-131">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="9e2f6-131">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="9e2f6-132">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="9e2f6-132">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="9e2f6-133">**小型 \_ 矩形**</span><span class="sxs-lookup"><span data-stu-id="9e2f6-133">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="9e2f6-134">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="9e2f6-134">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="9e2f6-135">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="9e2f6-135">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 





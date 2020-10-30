---
title: CONSOLE_SCREEN_BUFFER_INFO 結構
description: 請參閱有關 CONSOLE_SCREEN_BUFFER_INFO 結構的參考資訊，其中包含主控台螢幕緩衝區的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8b3a739a9f66e25687b60a3450c9381822c16e53
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039176"
---
# <a name="console_screen_buffer_info-structure"></a><span data-ttu-id="4b22e-104">主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊結構</span><span class="sxs-lookup"><span data-stu-id="4b22e-104">CONSOLE\_SCREEN\_BUFFER\_INFO structure</span></span>

<span data-ttu-id="4b22e-105">包含主控台螢幕緩衝區的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4b22e-105">Contains information about a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="4b22e-106">語法</span><span class="sxs-lookup"><span data-stu-id="4b22e-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SCREEN_BUFFER_INFO {
  COORD      dwSize;
  COORD      dwCursorPosition;
  WORD       wAttributes;
  SMALL_RECT srWindow;
  COORD      dwMaximumWindowSize;
} CONSOLE_SCREEN_BUFFER_INFO;
```

## <a name="members"></a><span data-ttu-id="4b22e-107">成員</span><span class="sxs-lookup"><span data-stu-id="4b22e-107">Members</span></span>

<span data-ttu-id="4b22e-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="4b22e-108">**dwSize**</span></span>  
<span data-ttu-id="4b22e-109">[**COORD**](coord-str.md)結構，其中包含主控台螢幕緩衝區的大小（以字元資料行和資料列為限）。</span><span class="sxs-lookup"><span data-stu-id="4b22e-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character columns and rows.</span></span>

<span data-ttu-id="4b22e-110">**dwCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="4b22e-110">**dwCursorPosition**</span></span>  
<span data-ttu-id="4b22e-111">[**COORD**](coord-str.md)結構，其中包含主控台螢幕緩衝區中資料指標的資料行和資料列座標。</span><span class="sxs-lookup"><span data-stu-id="4b22e-111">A [**COORD**](coord-str.md) structure that contains the column and row coordinates of the cursor in the console screen buffer.</span></span>

<span data-ttu-id="4b22e-112">**wAttributes**</span><span class="sxs-lookup"><span data-stu-id="4b22e-112">**wAttributes**</span></span>  
<span data-ttu-id="4b22e-113">[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)和 [**WriteConsole**](writeconsole.md)函式寫入螢幕緩衝區的字元屬性，或 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)和 [**ReadConsole**](readconsole.md)函式的螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="4b22e-113">The attributes of the characters written to a screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) and [**WriteConsole**](writeconsole.md) functions, or echoed to a screen buffer by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md) functions.</span></span> <span data-ttu-id="4b22e-114">如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#character-attributes)。</span><span class="sxs-lookup"><span data-stu-id="4b22e-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="4b22e-115">**srWindow**</span><span class="sxs-lookup"><span data-stu-id="4b22e-115">**srWindow**</span></span>  
<span data-ttu-id="4b22e-116">[**小型 \_ 矩形**](small-rect-str.md)結構，其中包含顯示視窗左上角和右下角的主控台螢幕緩衝區座標。</span><span class="sxs-lookup"><span data-stu-id="4b22e-116">A [**SMALL\_RECT**](small-rect-str.md) structure that contains the console screen buffer coordinates of the upper-left and lower-right corners of the display window.</span></span>

<span data-ttu-id="4b22e-117">**dwMaximumWindowSize**</span><span class="sxs-lookup"><span data-stu-id="4b22e-117">**dwMaximumWindowSize**</span></span>  
<span data-ttu-id="4b22e-118">[**COORD**](coord-str.md)結構，其中包含主控台視窗的大小上限（以字元資料行和資料列為限），指定目前的螢幕緩衝區大小和字型和螢幕大小。</span><span class="sxs-lookup"><span data-stu-id="4b22e-118">A [**COORD**](coord-str.md) structure that contains the maximum size of the console window, in character columns and rows, given the current screen buffer size and font and the screen size.</span></span>

## <a name="examples"></a><span data-ttu-id="4b22e-119">範例</span><span class="sxs-lookup"><span data-stu-id="4b22e-119">Examples</span></span>

<span data-ttu-id="4b22e-120">如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="4b22e-120">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="4b22e-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="4b22e-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4b22e-122">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="4b22e-122">Minimum supported client</span></span> | <span data-ttu-id="4b22e-123">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="4b22e-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="4b22e-124">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="4b22e-124">Minimum supported server</span></span> | <span data-ttu-id="4b22e-125">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="4b22e-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="4b22e-126">標頭</span><span class="sxs-lookup"><span data-stu-id="4b22e-126">Header</span></span> | <span data-ttu-id="4b22e-127">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="4b22e-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="4b22e-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="4b22e-128">See also</span></span>

[<span data-ttu-id="4b22e-129">**COORD**</span><span class="sxs-lookup"><span data-stu-id="4b22e-129">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="4b22e-130">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="4b22e-130">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="4b22e-131">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="4b22e-131">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="4b22e-132">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="4b22e-132">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="4b22e-133">**小型 \_ 矩形**</span><span class="sxs-lookup"><span data-stu-id="4b22e-133">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="4b22e-134">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="4b22e-134">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="4b22e-135">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="4b22e-135">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

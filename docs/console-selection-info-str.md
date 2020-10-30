---
title: CONSOLE_SELECTION_INFO 結構
description: 請參閱 CONSOLE_SELECTION_INFO 結構的參考資訊，其中包含主控台選取專案的資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/CONSOLE_SELECTION_INFO
- wincon/CONSOLE_SELECTION_INFO
- CONSOLE_SELECTION_INFO
- consoleapi3/PCONSOLE_SELECTION_INFO
- wincon/PCONSOLE_SELECTION_INFO
- PCONSOLE_SELECTION_INFO
MS-HAID:
- '\_win32\_console\_selection\_info\_str'
- base.console\_selection\_info\_str
- consoles.console\_selection\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9530b249-8db4-4516-9cc8-2b452c6751f9
topic_type:
- apiref
api_name:
- CONSOLE_SELECTION_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: aaf1cfaea2a8822c142aab87f6dcf1b022b7160c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038366"
---
# <a name="console_selection_info-structure"></a><span data-ttu-id="591c1-104">主控台 \_ 選取 \_ 資訊結構</span><span class="sxs-lookup"><span data-stu-id="591c1-104">CONSOLE\_SELECTION\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="591c1-105">包含主控台選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="591c1-105">Contains information for a console selection.</span></span>

## <a name="syntax"></a><span data-ttu-id="591c1-106">語法</span><span class="sxs-lookup"><span data-stu-id="591c1-106">Syntax</span></span>

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

## <a name="members"></a><span data-ttu-id="591c1-107">成員</span><span class="sxs-lookup"><span data-stu-id="591c1-107">Members</span></span>

<span data-ttu-id="591c1-108">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="591c1-108">**dwFlags**</span></span>  
<span data-ttu-id="591c1-109">選取指標。</span><span class="sxs-lookup"><span data-stu-id="591c1-109">The selection indicator.</span></span> <span data-ttu-id="591c1-110">這個成員可以是下列一或多個值。</span><span class="sxs-lookup"><span data-stu-id="591c1-110">This member can be one or more of the following values.</span></span>

| <span data-ttu-id="591c1-111">值</span><span class="sxs-lookup"><span data-stu-id="591c1-111">Value</span></span> | <span data-ttu-id="591c1-112">意義</span><span class="sxs-lookup"><span data-stu-id="591c1-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="591c1-113">**CONSOLE_MOUSE_DOWN** 0x0008</span><span class="sxs-lookup"><span data-stu-id="591c1-113">**CONSOLE_MOUSE_DOWN** 0x0008</span></span> | <span data-ttu-id="591c1-114">滑鼠已關閉。</span><span class="sxs-lookup"><span data-stu-id="591c1-114">Mouse is down.</span></span> <span data-ttu-id="591c1-115">使用者正在使用滑鼠主動調整選取矩形。</span><span class="sxs-lookup"><span data-stu-id="591c1-115">The user is actively adjusting the selection rectangle with a mouse.</span></span> |
| <span data-ttu-id="591c1-116">**CONSOLE_MOUSE_SELECTION** 0x0004</span><span class="sxs-lookup"><span data-stu-id="591c1-116">**CONSOLE_MOUSE_SELECTION** 0x0004</span></span> | <span data-ttu-id="591c1-117">使用滑鼠選取。</span><span class="sxs-lookup"><span data-stu-id="591c1-117">Selecting with the mouse.</span></span> <span data-ttu-id="591c1-118">如果是 off，則使用者會 `conhost.exe` 以鍵盤選取操作標示模式。</span><span class="sxs-lookup"><span data-stu-id="591c1-118">If off, the user is operating `conhost.exe` mark mode selection with the keyboard.</span></span> |
| <span data-ttu-id="591c1-119">**CONSOLE_NO_SELECTION** 0x0000</span><span class="sxs-lookup"><span data-stu-id="591c1-119">**CONSOLE_NO_SELECTION** 0x0000</span></span> | <span data-ttu-id="591c1-120">沒有選取專案。</span><span class="sxs-lookup"><span data-stu-id="591c1-120">No selection.</span></span> |
| <span data-ttu-id="591c1-121">**CONSOLE_SELECTION_IN_PROGRESS** 0x0001</span><span class="sxs-lookup"><span data-stu-id="591c1-121">**CONSOLE_SELECTION_IN_PROGRESS** 0x0001</span></span> | <span data-ttu-id="591c1-122">選取範圍已開始。</span><span class="sxs-lookup"><span data-stu-id="591c1-122">Selection has begun.</span></span> <span data-ttu-id="591c1-123">如果選取滑鼠，通常不會發生此 `CONSOLE_SELECTION_NOT_EMPTY` 旗標。</span><span class="sxs-lookup"><span data-stu-id="591c1-123">If a mouse selection, this will typically not occur without the `CONSOLE_SELECTION_NOT_EMPTY` flag.</span></span> <span data-ttu-id="591c1-124">如果選擇鍵盤，則在輸入標記模式，但使用者仍在流覽至初始位置時，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="591c1-124">If a keyboard selection, this may occur when mark mode has been entered but the user is still navigating to the initial position.</span></span> |
| <span data-ttu-id="591c1-125">**CONSOLE_SELECTION_NOT_EMPTY** 0x0002</span><span class="sxs-lookup"><span data-stu-id="591c1-125">**CONSOLE_SELECTION_NOT_EMPTY** 0x0002</span></span> | <span data-ttu-id="591c1-126">選取範圍矩形不是空的。</span><span class="sxs-lookup"><span data-stu-id="591c1-126">Selection rectangle not empty.</span></span> <span data-ttu-id="591c1-127">*DwSelectionAnchor* 和 *srSelection* 的承載有效。</span><span class="sxs-lookup"><span data-stu-id="591c1-127">The payload of *dwSelectionAnchor* and *srSelection* are valid.</span></span>  |

<span data-ttu-id="591c1-128">**dwSelectionAnchor**</span><span class="sxs-lookup"><span data-stu-id="591c1-128">**dwSelectionAnchor**</span></span>  
<span data-ttu-id="591c1-129">指定選取範圍錨點的 [**COORD**](coord-str.md) 結構（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="591c1-129">A [**COORD**](coord-str.md) structure that specifies the selection anchor, in characters.</span></span>

<span data-ttu-id="591c1-130">**srSelection**</span><span class="sxs-lookup"><span data-stu-id="591c1-130">**srSelection**</span></span>  
<span data-ttu-id="591c1-131">指定選取矩形的 [**小型 \_ 矩形**](small-rect-str.md) 結構。</span><span class="sxs-lookup"><span data-stu-id="591c1-131">A [**SMALL\_RECT**](small-rect-str.md) structure that specifies the selection rectangle.</span></span>

## <a name="requirements"></a><span data-ttu-id="591c1-132">規格需求</span><span class="sxs-lookup"><span data-stu-id="591c1-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="591c1-133">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="591c1-133">Minimum supported client</span></span> | <span data-ttu-id="591c1-134">\[僅限 WINDOWS XP desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="591c1-134">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="591c1-135">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="591c1-135">Minimum supported server</span></span> | <span data-ttu-id="591c1-136">僅限 Windows Server 2003 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="591c1-136">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="591c1-137">標頭</span><span class="sxs-lookup"><span data-stu-id="591c1-137">Header</span></span> | <span data-ttu-id="591c1-138">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="591c1-138">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="591c1-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="591c1-139">See also</span></span>

[<span data-ttu-id="591c1-140">**COORD**</span><span class="sxs-lookup"><span data-stu-id="591c1-140">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="591c1-141">**GetConsoleSelectionInfo**</span><span class="sxs-lookup"><span data-stu-id="591c1-141">**GetConsoleSelectionInfo**</span></span>](getconsoleselectioninfo.md)

[<span data-ttu-id="591c1-142">**小型 \_ 矩形**</span><span class="sxs-lookup"><span data-stu-id="591c1-142">**SMALL\_RECT**</span></span>](small-rect-str.md)

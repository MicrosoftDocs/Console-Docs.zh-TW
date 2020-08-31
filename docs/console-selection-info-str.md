---
title: CONSOLE_SELECTION_INFO 結構
description: 請參閱 CONSOLE_SELECTION_INFO 結構的參考資訊，其中包含主控台選取專案的資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: a16fe43e7b7cc4b5890284921823aee7b79217b2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059270"
---
# <a name="console_selection_info-structure"></a><span data-ttu-id="8cf21-104">主控台 \_ 選取 \_ 資訊結構</span><span class="sxs-lookup"><span data-stu-id="8cf21-104">CONSOLE\_SELECTION\_INFO structure</span></span>


<span data-ttu-id="8cf21-105">包含主控台選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="8cf21-105">Contains information for a console selection.</span></span>

<a name="syntax"></a><span data-ttu-id="8cf21-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8cf21-106">Syntax</span></span>
------

```C
typedef struct _CONSOLE_SELECTION_INFO {
  DWORD      dwFlags;
  COORD      dwSelectionAnchor;
  SMALL_RECT srSelection;
} CONSOLE_SELECTION_INFO, *PCONSOLE_SELECTION_INFO;
```

<a name="members"></a><span data-ttu-id="8cf21-107">成員</span><span class="sxs-lookup"><span data-stu-id="8cf21-107">Members</span></span>
-------

<span data-ttu-id="8cf21-108">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="8cf21-108">**dwFlags**</span></span>  
<span data-ttu-id="8cf21-109">選取指標。</span><span class="sxs-lookup"><span data-stu-id="8cf21-109">The selection indicator.</span></span> <span data-ttu-id="8cf21-110">這個成員可以是下列一或多個值。</span><span class="sxs-lookup"><span data-stu-id="8cf21-110">This member can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="8cf21-111">值</span><span class="sxs-lookup"><span data-stu-id="8cf21-111">Value</span></span></th>
<th><span data-ttu-id="8cf21-112">意義</span><span class="sxs-lookup"><span data-stu-id="8cf21-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="8cf21-113"><span id="CONSOLE_MOUSE_DOWN"></span><span id="console_mouse_down"></span>
<strong>CONSOLE_MOUSE_DOWN</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="8cf21-113"><span id="CONSOLE_MOUSE_DOWN"></span><span id="console_mouse_down"></span>
<strong>CONSOLE_MOUSE_DOWN</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="8cf21-114">滑鼠已關閉</span><span class="sxs-lookup"><span data-stu-id="8cf21-114">Mouse is down</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="8cf21-115"><span id="CONSOLE_MOUSE_SELECTION"></span><span id="console_mouse_selection"></span>
<strong>CONSOLE_MOUSE_SELECTION</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="8cf21-115"><span id="CONSOLE_MOUSE_SELECTION"></span><span id="console_mouse_selection"></span>
<strong>CONSOLE_MOUSE_SELECTION</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="8cf21-116">使用滑鼠選取</span><span class="sxs-lookup"><span data-stu-id="8cf21-116">Selecting with the mouse</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="8cf21-117"><span id="CONSOLE_NO_SELECTION"></span><span id="console_no_selection"></span>
<strong>CONSOLE_NO_SELECTION</strong> 0x0000</span><span class="sxs-lookup"><span data-stu-id="8cf21-117"><span id="CONSOLE_NO_SELECTION"></span><span id="console_no_selection"></span>
<strong>CONSOLE_NO_SELECTION</strong> 0x0000</span></span></td>
<td><p><span data-ttu-id="8cf21-118">沒有選取項目</span><span class="sxs-lookup"><span data-stu-id="8cf21-118">No selection</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="8cf21-119"><span id="CONSOLE_SELECTION_IN_PROGRESS"></span><span id="console_selection_in_progress"></span>
<strong>CONSOLE_SELECTION_IN_PROGRESS</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="8cf21-119"><span id="CONSOLE_SELECTION_IN_PROGRESS"></span><span id="console_selection_in_progress"></span>
<strong>CONSOLE_SELECTION_IN_PROGRESS</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="8cf21-120">選取範圍已開始</span><span class="sxs-lookup"><span data-stu-id="8cf21-120">Selection has begun</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="8cf21-121"><span id="CONSOLE_SELECTION_NOT_EMPTY"></span><span id="console_selection_not_empty"></span>
<strong>CONSOLE_SELECTION_NOT_EMPTY</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="8cf21-121"><span id="CONSOLE_SELECTION_NOT_EMPTY"></span><span id="console_selection_not_empty"></span>
<strong>CONSOLE_SELECTION_NOT_EMPTY</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="8cf21-122">選取範圍矩形不是空的</span><span class="sxs-lookup"><span data-stu-id="8cf21-122">Selection rectangle is not empty</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<span data-ttu-id="8cf21-123">**dwSelectionAnchor**</span><span class="sxs-lookup"><span data-stu-id="8cf21-123">**dwSelectionAnchor**</span></span>  
<span data-ttu-id="8cf21-124">指定選取範圍錨點的 [**COORD**](coord-str.md) 結構（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="8cf21-124">A [**COORD**](coord-str.md) structure that specifies the selection anchor, in characters.</span></span>

<span data-ttu-id="8cf21-125">**srSelection**</span><span class="sxs-lookup"><span data-stu-id="8cf21-125">**srSelection**</span></span>  
<span data-ttu-id="8cf21-126">指定選取矩形的 [**小型 \_ 矩形**](small-rect-str.md) 結構。</span><span class="sxs-lookup"><span data-stu-id="8cf21-126">A [**SMALL\_RECT**](small-rect-str.md) structure that specifies the selection rectangle.</span></span>

<a name="requirements"></a><span data-ttu-id="8cf21-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="8cf21-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="8cf21-128">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="8cf21-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="8cf21-129">Windows XP [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="8cf21-129">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="8cf21-130">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="8cf21-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="8cf21-131">Windows Server 2003 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="8cf21-131">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="8cf21-132">標頭</span><span class="sxs-lookup"><span data-stu-id="8cf21-132">Header</span></span></p></td>
<td><span data-ttu-id="8cf21-133">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="8cf21-133">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="8cf21-134"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cf21-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="8cf21-135">**COORD**</span><span class="sxs-lookup"><span data-stu-id="8cf21-135">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="8cf21-136">**GetConsoleSelectionInfo**</span><span class="sxs-lookup"><span data-stu-id="8cf21-136">**GetConsoleSelectionInfo**</span></span>](getconsoleselectioninfo.md)

[<span data-ttu-id="8cf21-137">**小型 \_ 矩形**</span><span class="sxs-lookup"><span data-stu-id="8cf21-137">**SMALL\_RECT**</span></span>](small-rect-str.md)

 

 





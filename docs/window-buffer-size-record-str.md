---
title: WINDOW_BUFFER_SIZE_RECORD 結構
description: 請參閱 WINDOW_BUFFER_SIZE_RECORD 結構的參考資訊，其中描述主控台螢幕緩衝區大小的變更。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- wincontypes/WINDOW_BUFFER_SIZE_RECORD
- wincon/WINDOW_BUFFER_SIZE_RECORD
- WINDOW_BUFFER_SIZE_RECORD
- wincontypes/PWINDOW_BUFFER_SIZE_RECORD
- wincon/PWINDOW_BUFFER_SIZE_RECORD
- PWINDOW_BUFFER_SIZE_RECORD
MS-HAID:
- '\_win32\_window\_buffer\_size\_record\_str'
- base.window\_buffer\_size\_record\_str
- consoles.window\_buffer\_size\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f2875e8-aa09-455b-a923-7cc388525b98
topic_type:
- apiref
api_name:
- WINDOW_BUFFER_SIZE_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 0041c4390fe331302df458965faec0ace2d1888f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059542"
---
# <a name="window_buffer_size_record-structure"></a><span data-ttu-id="4e335-104">視窗 \_ 緩衝區 \_ 大小 \_ 記錄結構</span><span class="sxs-lookup"><span data-stu-id="4e335-104">WINDOW\_BUFFER\_SIZE\_RECORD structure</span></span>


<span data-ttu-id="4e335-105">描述主控台螢幕緩衝區大小的變更。</span><span class="sxs-lookup"><span data-stu-id="4e335-105">Describes a change in the size of the console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="4e335-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4e335-106">Syntax</span></span>
------

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

<a name="members"></a><span data-ttu-id="4e335-107">成員</span><span class="sxs-lookup"><span data-stu-id="4e335-107">Members</span></span>
-------

<span data-ttu-id="4e335-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="4e335-108">**dwSize**</span></span>  
<span data-ttu-id="4e335-109">[**COORD**](coord-str.md)結構，其中包含主控台螢幕緩衝區的大小、字元資料格資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="4e335-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character cell columns and rows.</span></span>

<a name="remarks"></a><span data-ttu-id="4e335-110">備註</span><span class="sxs-lookup"><span data-stu-id="4e335-110">Remarks</span></span>
-------

<span data-ttu-id="4e335-111">當主控台處於視窗感知模式時，緩衝區大小事件就會放在輸入緩衝區中 (**啟用 \_ 視窗 \_ 輸入**) 。</span><span class="sxs-lookup"><span data-stu-id="4e335-111">Buffer size events are placed in the input buffer when the console is in window-aware mode (**ENABLE\_WINDOW\_INPUT**).</span></span>

<a name="examples"></a><span data-ttu-id="4e335-112">範例</span><span class="sxs-lookup"><span data-stu-id="4e335-112">Examples</span></span>
--------

<span data-ttu-id="4e335-113">如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。</span><span class="sxs-lookup"><span data-stu-id="4e335-113">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="4e335-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="4e335-114">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="4e335-115">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="4e335-115">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="4e335-116">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="4e335-116">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4e335-117">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="4e335-117">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="4e335-118">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="4e335-118">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4e335-119">標頭</span><span class="sxs-lookup"><span data-stu-id="4e335-119">Header</span></span></p></td>
<td><span data-ttu-id="4e335-120">WinConTypes .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="4e335-120">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="4e335-121"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e335-121"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="4e335-122">**COORD**</span><span class="sxs-lookup"><span data-stu-id="4e335-122">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="4e335-123">**輸入 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="4e335-123">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="4e335-124">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="4e335-124">**ReadConsoleInput**</span></span>](readconsoleinput.md)

 

 





---
title: WINDOW_BUFFER_SIZE_RECORD 結構
description: 請參閱 WINDOW_BUFFER_SIZE_RECORD 結構的參考資訊，其中描述主控台螢幕緩衝區大小的變更。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 355482dfd162e2c29944d53e5b17b0315ea15950
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039266"
---
# <a name="window_buffer_size_record-structure"></a><span data-ttu-id="1a3f8-104">視窗 \_ 緩衝區 \_ 大小 \_ 記錄結構</span><span class="sxs-lookup"><span data-stu-id="1a3f8-104">WINDOW\_BUFFER\_SIZE\_RECORD structure</span></span>

<span data-ttu-id="1a3f8-105">描述主控台螢幕緩衝區大小的變更。</span><span class="sxs-lookup"><span data-stu-id="1a3f8-105">Describes a change in the size of the console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="1a3f8-106">語法</span><span class="sxs-lookup"><span data-stu-id="1a3f8-106">Syntax</span></span>

```C
typedef struct _WINDOW_BUFFER_SIZE_RECORD {
  COORD dwSize;
} WINDOW_BUFFER_SIZE_RECORD;
```

## <a name="members"></a><span data-ttu-id="1a3f8-107">成員</span><span class="sxs-lookup"><span data-stu-id="1a3f8-107">Members</span></span>

<span data-ttu-id="1a3f8-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="1a3f8-108">**dwSize**</span></span>  
<span data-ttu-id="1a3f8-109">[**COORD**](coord-str.md)結構，其中包含主控台螢幕緩衝區的大小、字元資料格資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="1a3f8-109">A [**COORD**](coord-str.md) structure that contains the size of the console screen buffer, in character cell columns and rows.</span></span>

## <a name="remarks"></a><span data-ttu-id="1a3f8-110">備註</span><span class="sxs-lookup"><span data-stu-id="1a3f8-110">Remarks</span></span>

<span data-ttu-id="1a3f8-111">當主控台處於視窗感知模式時，緩衝區大小事件就會放在輸入緩衝區中 ( **啟用 \_ 視窗 \_ 輸入** ) 。</span><span class="sxs-lookup"><span data-stu-id="1a3f8-111">Buffer size events are placed in the input buffer when the console is in window-aware mode ( **ENABLE\_WINDOW\_INPUT** ).</span></span>

## <a name="examples"></a><span data-ttu-id="1a3f8-112">範例</span><span class="sxs-lookup"><span data-stu-id="1a3f8-112">Examples</span></span>

<span data-ttu-id="1a3f8-113">如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。</span><span class="sxs-lookup"><span data-stu-id="1a3f8-113">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="1a3f8-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="1a3f8-114">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1a3f8-115">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="1a3f8-115">Minimum supported client</span></span> | <span data-ttu-id="1a3f8-116">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="1a3f8-116">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1a3f8-117">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="1a3f8-117">Minimum supported server</span></span> | <span data-ttu-id="1a3f8-118">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="1a3f8-118">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1a3f8-119">標頭</span><span class="sxs-lookup"><span data-stu-id="1a3f8-119">Header</span></span> | <span data-ttu-id="1a3f8-120">WinConTypes .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="1a3f8-120">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="1a3f8-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="1a3f8-121">See also</span></span>

[<span data-ttu-id="1a3f8-122">**COORD**</span><span class="sxs-lookup"><span data-stu-id="1a3f8-122">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="1a3f8-123">**輸入 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="1a3f8-123">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="1a3f8-124">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="1a3f8-124">**ReadConsoleInput**</span></span>](readconsoleinput.md)

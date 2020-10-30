---
title: FOCUS_EVENT_RECORD 結構
description: 描述主控台輸入記錄結構中的焦點事件 \_ 。 這些事件會在內部使用，應該予以忽略。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- wincontypes/FOCUS_EVENT_RECORD
- wincon/FOCUS_EVENT_RECORD
- FOCUS_EVENT_RECORD
- wincontypes/PFOCUS_EVENT_RECORD
- wincon/PFOCUS_EVENT_RECORD
- PFOCUS_EVENT_RECORD
MS-HAID:
- '\_win32\_focus\_event\_record\_str'
- base.focus\_event\_record\_str
- consoles.focus\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4db0ae89-8446-4f0a-98e2-ba0b11ef7efe
topic_type:
- apiref
api_name:
- FOCUS_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: dc86c1b5b1c42a9d905673da4ea368de76a5fae9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038166"
---
# <a name="focus_event_record-structure"></a><span data-ttu-id="aa69b-105">焦點 \_ 事件 \_ 記錄結構</span><span class="sxs-lookup"><span data-stu-id="aa69b-105">FOCUS\_EVENT\_RECORD structure</span></span>

<span data-ttu-id="aa69b-106">描述主控台 [**輸入 \_ 記錄**](input-record-str.md) 結構中的焦點事件。</span><span class="sxs-lookup"><span data-stu-id="aa69b-106">Describes a focus event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="aa69b-107">這些事件會在內部使用，應該予以忽略。</span><span class="sxs-lookup"><span data-stu-id="aa69b-107">These events are used internally and should be ignored.</span></span>

## <a name="syntax"></a><span data-ttu-id="aa69b-108">語法</span><span class="sxs-lookup"><span data-stu-id="aa69b-108">Syntax</span></span>

```C
typedef struct _FOCUS_EVENT_RECORD {
  BOOL bSetFocus;
} FOCUS_EVENT_RECORD;
```

## <a name="members"></a><span data-ttu-id="aa69b-109">成員</span><span class="sxs-lookup"><span data-stu-id="aa69b-109">Members</span></span>

<span data-ttu-id="aa69b-110">**bSetFocus**</span><span class="sxs-lookup"><span data-stu-id="aa69b-110">**bSetFocus**</span></span>  
<span data-ttu-id="aa69b-111">保留的。</span><span class="sxs-lookup"><span data-stu-id="aa69b-111">Reserved.</span></span>

## <a name="requirements"></a><span data-ttu-id="aa69b-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="aa69b-112">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="aa69b-113">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="aa69b-113">Minimum supported client</span></span> | <span data-ttu-id="aa69b-114">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="aa69b-114">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="aa69b-115">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="aa69b-115">Minimum supported server</span></span> | <span data-ttu-id="aa69b-116">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="aa69b-116">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="aa69b-117">標頭</span><span class="sxs-lookup"><span data-stu-id="aa69b-117">Header</span></span> | <span data-ttu-id="aa69b-118">WinConTypes .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="aa69b-118">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="aa69b-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="aa69b-119">See also</span></span>

[<span data-ttu-id="aa69b-120">**輸入 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="aa69b-120">**INPUT\_RECORD**</span></span>](input-record-str.md)

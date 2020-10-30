---
title: MENU_EVENT_RECORD 結構
description: 描述主控台輸入記錄結構中的功能表事件 \_ 。 這些事件會在內部使用，應該予以忽略。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- wincontypes/MENU_EVENT_RECORD
- wincon/MENU_EVENT_RECORD
- MENU_EVENT_RECORD
- wincontypes/PMENU_EVENT_RECORD
- wincon/PMENU_EVENT_RECORD
- PMENU_EVENT_RECORD
MS-HAID:
- '\_win32\_menu\_event\_record\_str'
- base.menu\_event\_record\_str
- consoles.menu\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7efef0e0-01ba-44ba-a972-25c6b3aed2bd
topic_type:
- apiref
api_name:
- MENU_EVENT_RECORD
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: dfca825c03dbf0e63041e68adc5e43f2ca0ef669
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039516"
---
# <a name="menu_event_record-structure"></a><span data-ttu-id="2662e-105">功能表 \_ 事件 \_ 記錄結構</span><span class="sxs-lookup"><span data-stu-id="2662e-105">MENU\_EVENT\_RECORD structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="2662e-106">描述主控台 [**輸入 \_ 記錄**](input-record-str.md) 結構中的功能表事件。</span><span class="sxs-lookup"><span data-stu-id="2662e-106">Describes a menu event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="2662e-107">這些事件會在內部使用，應該予以忽略。</span><span class="sxs-lookup"><span data-stu-id="2662e-107">These events are used internally and should be ignored.</span></span>

## <a name="syntax"></a><span data-ttu-id="2662e-108">語法</span><span class="sxs-lookup"><span data-stu-id="2662e-108">Syntax</span></span>

```C
typedef struct _MENU_EVENT_RECORD {
  UINT dwCommandId;
} MENU_EVENT_RECORD, *PMENU_EVENT_RECORD;
```

## <a name="members"></a><span data-ttu-id="2662e-109">成員</span><span class="sxs-lookup"><span data-stu-id="2662e-109">Members</span></span>

<span data-ttu-id="2662e-110">**dwCommandId**</span><span class="sxs-lookup"><span data-stu-id="2662e-110">**dwCommandId**</span></span>  
<span data-ttu-id="2662e-111">保留的。</span><span class="sxs-lookup"><span data-stu-id="2662e-111">Reserved.</span></span>

## <a name="requirements"></a><span data-ttu-id="2662e-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="2662e-112">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="2662e-113">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="2662e-113">Minimum supported client</span></span> | <span data-ttu-id="2662e-114">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="2662e-114">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="2662e-115">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="2662e-115">Minimum supported server</span></span> | <span data-ttu-id="2662e-116">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="2662e-116">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="2662e-117">標頭</span><span class="sxs-lookup"><span data-stu-id="2662e-117">Header</span></span> | <span data-ttu-id="2662e-118">WinConTypes .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="2662e-118">WinConTypes.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="2662e-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="2662e-119">See also</span></span>

[<span data-ttu-id="2662e-120">**輸入 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="2662e-120">**INPUT\_RECORD**</span></span>](input-record-str.md)

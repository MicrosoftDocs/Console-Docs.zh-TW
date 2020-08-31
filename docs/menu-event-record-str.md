---
title: MENU_EVENT_RECORD 結構
description: 描述主控台輸入記錄結構中的功能表事件 \_ 。 這些事件會在內部使用，應該予以忽略。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 8bbfbf6ad8bd885d69ce08e94dfced93b0bd3257
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059078"
---
# <a name="menu_event_record-structure"></a><span data-ttu-id="5ce9c-105">功能表 \_ 事件 \_ 記錄結構</span><span class="sxs-lookup"><span data-stu-id="5ce9c-105">MENU\_EVENT\_RECORD structure</span></span>


<span data-ttu-id="5ce9c-106">描述主控台 [**輸入 \_ 記錄**](input-record-str.md) 結構中的功能表事件。</span><span class="sxs-lookup"><span data-stu-id="5ce9c-106">Describes a menu event in a console [**INPUT\_RECORD**](input-record-str.md) structure.</span></span> <span data-ttu-id="5ce9c-107">這些事件會在內部使用，應該予以忽略。</span><span class="sxs-lookup"><span data-stu-id="5ce9c-107">These events are used internally and should be ignored.</span></span>

<a name="syntax"></a><span data-ttu-id="5ce9c-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="5ce9c-108">Syntax</span></span>
------

```C
typedef struct _MENU_EVENT_RECORD {
  UINT dwCommandId;
} MENU_EVENT_RECORD, *PMENU_EVENT_RECORD;
```

<a name="members"></a><span data-ttu-id="5ce9c-109">成員</span><span class="sxs-lookup"><span data-stu-id="5ce9c-109">Members</span></span>
-------

<span data-ttu-id="5ce9c-110">**dwCommandId**</span><span class="sxs-lookup"><span data-stu-id="5ce9c-110">**dwCommandId**</span></span>  
<span data-ttu-id="5ce9c-111">保留的。</span><span class="sxs-lookup"><span data-stu-id="5ce9c-111">Reserved.</span></span>

<a name="requirements"></a><span data-ttu-id="5ce9c-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="5ce9c-112">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="5ce9c-113">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="5ce9c-113">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="5ce9c-114">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="5ce9c-114">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5ce9c-115">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="5ce9c-115">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="5ce9c-116">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="5ce9c-116">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5ce9c-117">標頭</span><span class="sxs-lookup"><span data-stu-id="5ce9c-117">Header</span></span></p></td>
<td><span data-ttu-id="5ce9c-118">WinConTypes .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="5ce9c-118">WinConTypes.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="5ce9c-119"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ce9c-119"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="5ce9c-120">**輸入 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="5ce9c-120">**INPUT\_RECORD**</span></span>](input-record-str.md)

 

 





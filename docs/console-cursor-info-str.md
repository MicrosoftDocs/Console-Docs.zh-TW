---
title: CONSOLE_CURSOR_INFO 結構
description: 包含有關主控台資料指標的大小和可見度資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- wincontypes/CONSOLE_CURSOR_INFO
- wincon/CONSOLE_CURSOR_INFO
- CONSOLE_CURSOR_INFO
- wincontypes/PCONSOLE_CURSOR_INFO
- wincon/PCONSOLE_CURSOR_INFO
- PCONSOLE_CURSOR_INFO
MS-HAID:
- '\_win32\_console\_cursor\_info\_str'
- base.console\_cursor\_info\_str
- consoles.console\_cursor\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0e71ce8c-e008-4bd7-922e-c44484b425ef
topic_type:
- apiref
api_name:
- CONSOLE_CURSOR_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: cdfcc00035738aa468d9795e4f6d32a54b96e1d0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037008"
---
# <a name="console_cursor_info-structure"></a><span data-ttu-id="88ae4-104">主控台資料 \_ 指標 \_ 資訊結構</span><span class="sxs-lookup"><span data-stu-id="88ae4-104">CONSOLE\_CURSOR\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="88ae4-105">包含主控台資料指標的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="88ae4-105">Contains information about the console cursor.</span></span>

## <a name="syntax"></a><span data-ttu-id="88ae4-106">語法</span><span class="sxs-lookup"><span data-stu-id="88ae4-106">Syntax</span></span>

```C
typedef struct _CONSOLE_CURSOR_INFO {
  DWORD dwSize;
  BOOL  bVisible;
} CONSOLE_CURSOR_INFO, *PCONSOLE_CURSOR_INFO;
```

## <a name="members"></a><span data-ttu-id="88ae4-107">成員</span><span class="sxs-lookup"><span data-stu-id="88ae4-107">Members</span></span>

<span data-ttu-id="88ae4-108">**dwSize**</span><span class="sxs-lookup"><span data-stu-id="88ae4-108">**dwSize**</span></span>  
<span data-ttu-id="88ae4-109">資料指標所填滿的字元資料格百分比。</span><span class="sxs-lookup"><span data-stu-id="88ae4-109">The percentage of the character cell that is filled by the cursor.</span></span> <span data-ttu-id="88ae4-110">此值介於1到100之間。</span><span class="sxs-lookup"><span data-stu-id="88ae4-110">This value is between 1 and 100.</span></span> <span data-ttu-id="88ae4-111">游標外觀會有所不同，範圍從完全填滿儲存格到顯示為數據格底部的水平線條。</span><span class="sxs-lookup"><span data-stu-id="88ae4-111">The cursor appearance varies, ranging from completely filling the cell to showing up as a horizontal line at the bottom of the cell.</span></span>

> [!NOTE]
><span data-ttu-id="88ae4-112">雖然 **dwSize** 值通常介於1到100之間，但在某些情況下，可能會傳回超出該範圍的值。</span><span class="sxs-lookup"><span data-stu-id="88ae4-112">While the **dwSize** value is normally between 1 and 100, under some circumstances a value outside of that range might be returned.</span></span> <span data-ttu-id="88ae4-113">例如，如果登錄中的 **CursorSize** 設定為0，則傳回的 **dwSize** 值會是0。</span><span class="sxs-lookup"><span data-stu-id="88ae4-113">For example, if **CursorSize** is set to 0 in the registry, the **dwSize** value returned would be 0.</span></span>

 <span data-ttu-id="88ae4-114">**bVisible**</span><span class="sxs-lookup"><span data-stu-id="88ae4-114">**bVisible**</span></span>  
<span data-ttu-id="88ae4-115">資料指標的可見度。</span><span class="sxs-lookup"><span data-stu-id="88ae4-115">The visibility of the cursor.</span></span> <span data-ttu-id="88ae4-116">如果資料指標是可見的，則這個成員是 **TRUE** 。</span><span class="sxs-lookup"><span data-stu-id="88ae4-116">If the cursor is visible, this member is **TRUE** .</span></span>

## <a name="requirements"></a><span data-ttu-id="88ae4-117">規格需求</span><span class="sxs-lookup"><span data-stu-id="88ae4-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="88ae4-118">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="88ae4-118">Minimum supported client</span></span> | <span data-ttu-id="88ae4-119">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="88ae4-119">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="88ae4-120">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="88ae4-120">Minimum supported server</span></span> | <span data-ttu-id="88ae4-121">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="88ae4-121">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="88ae4-122">標頭</span><span class="sxs-lookup"><span data-stu-id="88ae4-122">Header</span></span> | <span data-ttu-id="88ae4-123">WinCon (包含) 的 Windows。h</span><span class="sxs-lookup"><span data-stu-id="88ae4-123">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="88ae4-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="88ae4-124">See also</span></span>

[<span data-ttu-id="88ae4-125">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="88ae4-125">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="88ae4-126">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="88ae4-126">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

---
title: CONSOLE_FONT_INFO 結構
description: 請參閱 CONSOLE_FONT_INFO 結構的參考資訊，其中包含主控台字型的索引和大小。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- wincontypes/CONSOLE_FONT_INFO
- wincon/CONSOLE_FONT_INFO
- CONSOLE_FONT_INFO
- wincontypes/PCONSOLE_FONT_INFO
- wincon/PCONSOLE_FONT_INFO
- PCONSOLE_FONT_INFO
MS-HAID:
- '\_win32\_console\_font\_info\_str'
- base.console\_font\_info\_str
- consoles.console\_font\_info\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 380b8183-1964-46f2-a511-01f39f21f5c5
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 6c437e626ed6d207da4672a3a5ea60c2ea0ee008
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037136"
---
# <a name="console_font_info-structure"></a><span data-ttu-id="8c7f9-104">主控台 \_ 字型 \_ 資訊結構</span><span class="sxs-lookup"><span data-stu-id="8c7f9-104">CONSOLE\_FONT\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="8c7f9-105">包含主控台字型的資訊。</span><span class="sxs-lookup"><span data-stu-id="8c7f9-105">Contains information for a console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="8c7f9-106">語法</span><span class="sxs-lookup"><span data-stu-id="8c7f9-106">Syntax</span></span>

```C
typedef struct _CONSOLE_FONT_INFO {
  DWORD nFont;
  COORD dwFontSize;
} CONSOLE_FONT_INFO, *PCONSOLE_FONT_INFO;
```

## <a name="members"></a><span data-ttu-id="8c7f9-107">成員</span><span class="sxs-lookup"><span data-stu-id="8c7f9-107">Members</span></span>

<span data-ttu-id="8c7f9-108">**nFont**</span><span class="sxs-lookup"><span data-stu-id="8c7f9-108">**nFont**</span></span>  
<span data-ttu-id="8c7f9-109">系統的主控台字型表中的字型索引。</span><span class="sxs-lookup"><span data-stu-id="8c7f9-109">The index of the font in the system's console font table.</span></span>

<span data-ttu-id="8c7f9-110">**dwFontSize**</span><span class="sxs-lookup"><span data-stu-id="8c7f9-110">**dwFontSize**</span></span>  
<span data-ttu-id="8c7f9-111">[**COORD**](coord-str.md)結構，其中包含字型中每個字元的寬度和高度（以邏輯單位表示）。</span><span class="sxs-lookup"><span data-stu-id="8c7f9-111">A [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="8c7f9-112">**X** 成員包含寬度，而 **Y** 成員包含高度。</span><span class="sxs-lookup"><span data-stu-id="8c7f9-112">The **X** member contains the width, while the **Y** member contains the height.</span></span>

## <a name="remarks"></a><span data-ttu-id="8c7f9-113">備註</span><span class="sxs-lookup"><span data-stu-id="8c7f9-113">Remarks</span></span>

<span data-ttu-id="8c7f9-114">若要取得字型的大小，請將字型索引傳遞給 [**GetConsoleFontSize**](getconsolefontsize.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="8c7f9-114">To obtain the size of the font, pass the font index to the [**GetConsoleFontSize**](getconsolefontsize.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="8c7f9-115">規格需求</span><span class="sxs-lookup"><span data-stu-id="8c7f9-115">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="8c7f9-116">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="8c7f9-116">Minimum supported client</span></span> | <span data-ttu-id="8c7f9-117">\[僅限 WINDOWS XP desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="8c7f9-117">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="8c7f9-118">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="8c7f9-118">Minimum supported server</span></span> | <span data-ttu-id="8c7f9-119">僅限 Windows Server 2003 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="8c7f9-119">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="8c7f9-120">標頭</span><span class="sxs-lookup"><span data-stu-id="8c7f9-120">Header</span></span> | <span data-ttu-id="8c7f9-121">WinCon (包含) 的 Windows。h</span><span class="sxs-lookup"><span data-stu-id="8c7f9-121">WinCon.h (include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="8c7f9-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="8c7f9-122">See also</span></span>

[<span data-ttu-id="8c7f9-123">**COORD**</span><span class="sxs-lookup"><span data-stu-id="8c7f9-123">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="8c7f9-124">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="8c7f9-124">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)

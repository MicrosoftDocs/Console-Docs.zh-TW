---
title: CONSOLE_HISTORY_INFO 結構
description: 請參閱有關 CONSOLE_HISTORY_INFO 結構的參考資訊，其中包含主控台歷程記錄的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/CONSOLE_HISTORY_INFO
- wincon/CONSOLE_HISTORY_INFO
- CONSOLE_HISTORY_INFO
- consoleapi3/PCONSOLE_HISTORY_INFO
- wincon/PCONSOLE_HISTORY_INFO
- PCONSOLE_HISTORY_INFO
MS-HAID:
- base.console\_history\_info
- consoles.console\_history\_info
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: df7d2f12-5299-47ed-b1f6-2db903dba81b
topic_type:
- apiref
api_name:
- CONSOLE_HISTORY_INFO
api_location:
- WinCon.h
api_type:
- HeaderDef
ms.openlocfilehash: 24d41dca61146cc3e835f405889400ae0d168e7f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039216"
---
# <a name="console_history_info-structure"></a><span data-ttu-id="9cbcd-104">主控台歷程 \_ 記錄 \_ 資訊結構</span><span class="sxs-lookup"><span data-stu-id="9cbcd-104">CONSOLE\_HISTORY\_INFO structure</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="9cbcd-105">包含主控台歷程記錄的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9cbcd-105">Contains information about the console history.</span></span>

## <a name="syntax"></a><span data-ttu-id="9cbcd-106">語法</span><span class="sxs-lookup"><span data-stu-id="9cbcd-106">Syntax</span></span>

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

## <a name="members"></a><span data-ttu-id="9cbcd-107">成員</span><span class="sxs-lookup"><span data-stu-id="9cbcd-107">Members</span></span>

<span data-ttu-id="9cbcd-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="9cbcd-108">**cbSize**</span></span>  
<span data-ttu-id="9cbcd-109">結構的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="9cbcd-109">The size of the structure, in bytes.</span></span> <span data-ttu-id="9cbcd-110">將這個成員設定為 `sizeof(CONSOLE_HISTORY_INFO)` 。</span><span class="sxs-lookup"><span data-stu-id="9cbcd-110">Set this member to `sizeof(CONSOLE_HISTORY_INFO)`.</span></span>

<span data-ttu-id="9cbcd-111">**HistoryBufferSize**</span><span class="sxs-lookup"><span data-stu-id="9cbcd-111">**HistoryBufferSize**</span></span>  
<span data-ttu-id="9cbcd-112">每個記錄緩衝區中保留的命令數目。</span><span class="sxs-lookup"><span data-stu-id="9cbcd-112">The number of commands kept in each history buffer.</span></span>

<span data-ttu-id="9cbcd-113">**NumberOfHistoryBuffers**</span><span class="sxs-lookup"><span data-stu-id="9cbcd-113">**NumberOfHistoryBuffers**</span></span>  
<span data-ttu-id="9cbcd-114">為此主控台進程保留的記錄緩衝區數目。</span><span class="sxs-lookup"><span data-stu-id="9cbcd-114">The number of history buffers kept for this console process.</span></span>

<span data-ttu-id="9cbcd-115">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="9cbcd-115">**dwFlags**</span></span>  
<span data-ttu-id="9cbcd-116">此參數可以是零或以下值。</span><span class="sxs-lookup"><span data-stu-id="9cbcd-116">This parameter can be zero or the following value.</span></span>

| <span data-ttu-id="9cbcd-117">值</span><span class="sxs-lookup"><span data-stu-id="9cbcd-117">Value</span></span> | <span data-ttu-id="9cbcd-118">意義</span><span class="sxs-lookup"><span data-stu-id="9cbcd-118">Meaning</span></span> |
|-|-|
| <span data-ttu-id="9cbcd-119">**HISTORY_NO_DUP_FLAG** 0x1</span><span class="sxs-lookup"><span data-stu-id="9cbcd-119">**HISTORY_NO_DUP_FLAG** 0x1</span></span> | <span data-ttu-id="9cbcd-120">重複的專案將不會儲存在歷程記錄緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="9cbcd-120">Duplicate entries will not be stored in the history buffer.</span></span>

## <a name="requirements"></a><span data-ttu-id="9cbcd-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="9cbcd-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9cbcd-122">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="9cbcd-122">Minimum supported client</span></span> | <span data-ttu-id="9cbcd-123">\[僅限 Windows Vista 桌面應用程式\]</span><span class="sxs-lookup"><span data-stu-id="9cbcd-123">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="9cbcd-124">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="9cbcd-124">Minimum supported server</span></span> | <span data-ttu-id="9cbcd-125">僅限 Windows Server 2008 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="9cbcd-125">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="9cbcd-126">標頭</span><span class="sxs-lookup"><span data-stu-id="9cbcd-126">Header</span></span> | <span data-ttu-id="9cbcd-127">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="9cbcd-127">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |

## <a name="see-also"></a><span data-ttu-id="9cbcd-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="9cbcd-128">See also</span></span>

[<span data-ttu-id="9cbcd-129">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="9cbcd-129">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)

[<span data-ttu-id="9cbcd-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="9cbcd-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)

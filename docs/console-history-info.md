---
title: CONSOLE_HISTORY_INFO 結構
description: 請參閱有關 CONSOLE_HISTORY_INFO 結構的參考資訊，其中包含主控台歷程記錄的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: ee0161f0c4aac5a280fd18260ebbb1f7ca57d54a
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059499"
---
# <a name="console_history_info-structure"></a><span data-ttu-id="dec9c-104">主控台歷程 \_ 記錄 \_ 資訊結構</span><span class="sxs-lookup"><span data-stu-id="dec9c-104">CONSOLE\_HISTORY\_INFO structure</span></span>


<span data-ttu-id="dec9c-105">包含主控台歷程記錄的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="dec9c-105">Contains information about the console history.</span></span>

<a name="syntax"></a><span data-ttu-id="dec9c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="dec9c-106">Syntax</span></span>
------

```C
typedef struct {
  UINT  cbSize;
  UINT  HistoryBufferSize;
  UINT  NumberOfHistoryBuffers;
  DWORD dwFlags;
} CONSOLE_HISTORY_INFO, *PCONSOLE_HISTORY_INFO;
```

<a name="members"></a><span data-ttu-id="dec9c-107">成員</span><span class="sxs-lookup"><span data-stu-id="dec9c-107">Members</span></span>
-------

<span data-ttu-id="dec9c-108">**cbSize**</span><span class="sxs-lookup"><span data-stu-id="dec9c-108">**cbSize**</span></span>  
<span data-ttu-id="dec9c-109">結構的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="dec9c-109">The size of the structure, in bytes.</span></span> <span data-ttu-id="dec9c-110">將這個成員設定為 `sizeof(CONSOLE_HISTORY_INFO)` 。</span><span class="sxs-lookup"><span data-stu-id="dec9c-110">Set this member to `sizeof(CONSOLE_HISTORY_INFO)`.</span></span>

<span data-ttu-id="dec9c-111">**HistoryBufferSize**</span><span class="sxs-lookup"><span data-stu-id="dec9c-111">**HistoryBufferSize**</span></span>  
<span data-ttu-id="dec9c-112">每個記錄緩衝區中保留的命令數目。</span><span class="sxs-lookup"><span data-stu-id="dec9c-112">The number of commands kept in each history buffer.</span></span>

<span data-ttu-id="dec9c-113">**NumberOfHistoryBuffers**</span><span class="sxs-lookup"><span data-stu-id="dec9c-113">**NumberOfHistoryBuffers**</span></span>  
<span data-ttu-id="dec9c-114">為此主控台進程保留的記錄緩衝區數目。</span><span class="sxs-lookup"><span data-stu-id="dec9c-114">The number of history buffers kept for this console process.</span></span>

<span data-ttu-id="dec9c-115">**dwFlags**</span><span class="sxs-lookup"><span data-stu-id="dec9c-115">**dwFlags**</span></span>  
<span data-ttu-id="dec9c-116">此參數可以是零或以下值。</span><span class="sxs-lookup"><span data-stu-id="dec9c-116">This parameter can be zero or the following value.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="dec9c-117">值</span><span class="sxs-lookup"><span data-stu-id="dec9c-117">Value</span></span></th>
<th><span data-ttu-id="dec9c-118">意義</span><span class="sxs-lookup"><span data-stu-id="dec9c-118">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="dec9c-119"><span id="HISTORY_NO_DUP_FLAG"></span><span id="history_no_dup_flag"></span>
<strong>HISTORY_NO_DUP_FLAG</strong> 0x1</span><span class="sxs-lookup"><span data-stu-id="dec9c-119"><span id="HISTORY_NO_DUP_FLAG"></span><span id="history_no_dup_flag"></span>
<strong>HISTORY_NO_DUP_FLAG</strong> 0x1</span></span></td>
<td><p><span data-ttu-id="dec9c-120">重複的專案將不會儲存在歷程記錄緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="dec9c-120">Duplicate entries will not be stored in the history buffer.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="requirements"></a><span data-ttu-id="dec9c-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="dec9c-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="dec9c-122">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="dec9c-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="dec9c-123">Windows Vista [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="dec9c-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="dec9c-124">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="dec9c-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="dec9c-125">Windows Server 2008 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="dec9c-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="dec9c-126">標頭</span><span class="sxs-lookup"><span data-stu-id="dec9c-126">Header</span></span></p></td>
<td><span data-ttu-id="dec9c-127">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="dec9c-127">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="dec9c-128"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="dec9c-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="dec9c-129">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="dec9c-129">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)

[<span data-ttu-id="dec9c-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="dec9c-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)

 

 





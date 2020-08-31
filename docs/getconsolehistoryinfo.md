---
title: GetConsoleHistoryInfo 函式
description: 請參閱 GetConsoleHistoryInfo 函式的參考資訊，此函式會抓取呼叫進程主控台的歷程記錄設定。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi3/GetConsoleHistoryInfo
- wincon/GetConsoleHistoryInfo
- GetConsoleHistoryInfo
MS-HAID:
- base.getconsolehistoryinfo
- consoles.getconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 145008b3-8a4a-4e6a-9144-ee787ce90ef4
topic_type:
- apiref
api_name:
- GetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 176cf5517f18f022f00824de02872adcb916f231
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059142"
---
# <a name="getconsolehistoryinfo-function"></a><span data-ttu-id="b361c-104">GetConsoleHistoryInfo 函式</span><span class="sxs-lookup"><span data-stu-id="b361c-104">GetConsoleHistoryInfo function</span></span>


<span data-ttu-id="b361c-105">抓取呼叫進程主控台的歷程記錄設定。</span><span class="sxs-lookup"><span data-stu-id="b361c-105">Retrieves the history settings for the calling process's console.</span></span>

<a name="syntax"></a><span data-ttu-id="b361c-106">語法</span><span class="sxs-lookup"><span data-stu-id="b361c-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleHistoryInfo(
  _Out_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

<a name="parameters"></a><span data-ttu-id="b361c-107">參數</span><span class="sxs-lookup"><span data-stu-id="b361c-107">Parameters</span></span>
----------

<span data-ttu-id="b361c-108">*lpConsoleHistoryInfo* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="b361c-108">*lpConsoleHistoryInfo* \[out\]</span></span>  
<span data-ttu-id="b361c-109">[**主控台歷程 \_ 記錄 \_ 資訊**](console-history-info.md)結構的指標，此結構會接收呼叫進程主控台的歷程記錄設定。</span><span class="sxs-lookup"><span data-stu-id="b361c-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that receives the history settings for the calling process's console.</span></span>

<a name="return-value"></a><span data-ttu-id="b361c-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="b361c-110">Return value</span></span>
------------

<span data-ttu-id="b361c-111">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="b361c-111">If the function succeeds the return value is nonzero.</span></span>

<span data-ttu-id="b361c-112">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="b361c-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b361c-113">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="b361c-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="b361c-114">備註</span><span class="sxs-lookup"><span data-stu-id="b361c-114">Remarks</span></span>
-------

<span data-ttu-id="b361c-115">如果呼叫進程不是主控台進程，此函式會失敗，並將最後一個錯誤設定為 \*\* \_ \_ 拒絕存取錯誤\*\*。</span><span class="sxs-lookup"><span data-stu-id="b361c-115">If the calling process is not a console process, the function fails and sets the last error to **ERROR\_ACCESS\_DENIED**.</span></span>

<a name="requirements"></a><span data-ttu-id="b361c-116">規格需求</span><span class="sxs-lookup"><span data-stu-id="b361c-116">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="b361c-117">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="b361c-117">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="b361c-118">Windows Vista [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="b361c-118">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b361c-119">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="b361c-119">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="b361c-120">Windows Server 2008 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="b361c-120">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b361c-121">標頭</span><span class="sxs-lookup"><span data-stu-id="b361c-121">Header</span></span></p></td>
<td><span data-ttu-id="b361c-122">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="b361c-122">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="b361c-123">程式庫</span><span class="sxs-lookup"><span data-stu-id="b361c-123">Library</span></span></p></td>
<td><span data-ttu-id="b361c-124">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="b361c-124">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="b361c-125">DLL</span><span class="sxs-lookup"><span data-stu-id="b361c-125">DLL</span></span></p></td>
<td><span data-ttu-id="b361c-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b361c-126">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="b361c-127"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="b361c-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="b361c-128">主控台功能</span><span class="sxs-lookup"><span data-stu-id="b361c-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b361c-129">**主控台歷程 \_ 記錄 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="b361c-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="b361c-130">**SetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="b361c-130">**SetConsoleHistoryInfo**</span></span>](setconsolehistoryinfo.md)

 

 





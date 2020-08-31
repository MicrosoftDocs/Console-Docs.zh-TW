---
title: SetConsoleCursorInfo 函式
description: 為指定的主控台螢幕緩衝區設定資料指標的大小和可見度。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/SetConsoleCursorInfo
- wincon/SetConsoleCursorInfo
- SetConsoleCursorInfo
MS-HAID:
- '\_win32\_setconsolecursorinfo'
- base.setconsolecursorinfo
- consoles.setconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c98cbffb-18de-41e8-bba7-5fb46a0c5d25
topic_type:
- apiref
api_name:
- SetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 81f16e8c9d9cf90008bbd2e8619c2fa105d04212
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059414"
---
# <a name="setconsolecursorinfo-function"></a><span data-ttu-id="005ef-104">SetConsoleCursorInfo 函式</span><span class="sxs-lookup"><span data-stu-id="005ef-104">SetConsoleCursorInfo function</span></span>


<span data-ttu-id="005ef-105">為指定的主控台螢幕緩衝區設定資料指標的大小和可見度。</span><span class="sxs-lookup"><span data-stu-id="005ef-105">Sets the size and visibility of the cursor for the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="005ef-106">語法</span><span class="sxs-lookup"><span data-stu-id="005ef-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

<a name="parameters"></a><span data-ttu-id="005ef-107">參數</span><span class="sxs-lookup"><span data-stu-id="005ef-107">Parameters</span></span>
----------

<span data-ttu-id="005ef-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="005ef-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="005ef-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="005ef-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="005ef-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="005ef-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="005ef-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="005ef-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="005ef-112">*lpConsoleCursorInfo* \[在\]</span><span class="sxs-lookup"><span data-stu-id="005ef-112">*lpConsoleCursorInfo* \[in\]</span></span>  
<span data-ttu-id="005ef-113">主控台資料指標 [\*\* \_ \_ 資訊\*\*](console-cursor-info-str.md) 結構的指標，此結構會提供主控台螢幕緩衝區之游標的新規格。</span><span class="sxs-lookup"><span data-stu-id="005ef-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that provides the new specifications for the console screen buffer's cursor.</span></span>

<a name="return-value"></a><span data-ttu-id="005ef-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="005ef-114">Return value</span></span>
------------

<span data-ttu-id="005ef-115">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="005ef-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="005ef-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="005ef-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="005ef-117">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="005ef-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="005ef-118">備註</span><span class="sxs-lookup"><span data-stu-id="005ef-118">Remarks</span></span>
-------

<span data-ttu-id="005ef-119">當螢幕緩衝區的游標可見時，其外觀可能會有所不同，範圍從完全填滿字元儲存格到顯示為數據格底部的水平線條。</span><span class="sxs-lookup"><span data-stu-id="005ef-119">When a screen buffer's cursor is visible, its appearance can vary, ranging from completely filling a character cell to showing up as a horizontal line at the bottom of the cell.</span></span> <span data-ttu-id="005ef-120">[**主控台資料 \_ 指標 \_ 資訊**](console-cursor-info-str.md)結構的**dwSize**成員會指定資料指標所填滿的字元資料格百分比。</span><span class="sxs-lookup"><span data-stu-id="005ef-120">The **dwSize** member of the [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure specifies the percentage of a character cell that is filled by the cursor.</span></span> <span data-ttu-id="005ef-121">如果這個成員小於1或大於100， **SetConsoleCursorInfo** 就會失敗。</span><span class="sxs-lookup"><span data-stu-id="005ef-121">If this member is less than 1 or greater than 100, **SetConsoleCursorInfo** fails.</span></span>

<a name="requirements"></a><span data-ttu-id="005ef-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="005ef-122">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="005ef-123">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="005ef-123">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="005ef-124">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="005ef-124">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="005ef-125">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="005ef-125">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="005ef-126">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="005ef-126">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="005ef-127">標頭</span><span class="sxs-lookup"><span data-stu-id="005ef-127">Header</span></span></p></td>
<td><span data-ttu-id="005ef-128">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="005ef-128">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="005ef-129">程式庫</span><span class="sxs-lookup"><span data-stu-id="005ef-129">Library</span></span></p></td>
<td><span data-ttu-id="005ef-130">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="005ef-130">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="005ef-131">DLL</span><span class="sxs-lookup"><span data-stu-id="005ef-131">DLL</span></span></p></td>
<td><span data-ttu-id="005ef-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="005ef-132">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="005ef-133"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="005ef-133"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="005ef-134">主控台功能</span><span class="sxs-lookup"><span data-stu-id="005ef-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="005ef-135">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="005ef-135">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="005ef-136">**主控台資料 \_ 指標 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="005ef-136">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="005ef-137">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="005ef-137">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="005ef-138">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="005ef-138">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

 

 





---
title: GetLargestConsoleWindowSize 函式
description: 根據目前的字型和顯示器的大小，抓取最大可能主控台視窗的大小。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/GetLargestConsoleWindowSize
- wincon/GetLargestConsoleWindowSize
- GetLargestConsoleWindowSize
MS-HAID:
- '\_win32\_getlargestconsolewindowsize'
- base.getlargestconsolewindowsize
- consoles.getlargestconsolewindowsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3e5897f3-4987-4a82-ab19-06c0b231ba67
topic_type:
- apiref
api_name:
- GetLargestConsoleWindowSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 086c09b00ba15ad3e1922655fbd9b5f39d872d41
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059114"
---
# <a name="getlargestconsolewindowsize-function"></a><span data-ttu-id="0783d-104">GetLargestConsoleWindowSize 函式</span><span class="sxs-lookup"><span data-stu-id="0783d-104">GetLargestConsoleWindowSize function</span></span>


<span data-ttu-id="0783d-105">根據目前的字型和顯示器的大小，抓取最大可能主控台視窗的大小。</span><span class="sxs-lookup"><span data-stu-id="0783d-105">Retrieves the size of the largest possible console window, based on the current font and the size of the display.</span></span>

<a name="syntax"></a><span data-ttu-id="0783d-106">語法</span><span class="sxs-lookup"><span data-stu-id="0783d-106">Syntax</span></span>
------

```C
COORD WINAPI GetLargestConsoleWindowSize(
  _In_ HANDLE hConsoleOutput
);
```

<a name="parameters"></a><span data-ttu-id="0783d-107">參數</span><span class="sxs-lookup"><span data-stu-id="0783d-107">Parameters</span></span>
----------

<span data-ttu-id="0783d-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="0783d-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="0783d-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="0783d-109">A handle to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="0783d-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="0783d-110">Return value</span></span>
------------

<span data-ttu-id="0783d-111">如果函式成功，則傳回值是[**COORD**](coord-str.md)結構，可指定在最大可能的主控台視窗中， (**Y**成員) 的字元資料格資料行數目 (**X**成員) 和資料列。</span><span class="sxs-lookup"><span data-stu-id="0783d-111">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that specifies the number of character cell columns (**X** member) and rows (**Y** member) in the largest possible console window.</span></span> <span data-ttu-id="0783d-112">否則，結構的成員為零。</span><span class="sxs-lookup"><span data-stu-id="0783d-112">Otherwise, the members of the structure are zero.</span></span>

<span data-ttu-id="0783d-113">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="0783d-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="0783d-114">備註</span><span class="sxs-lookup"><span data-stu-id="0783d-114">Remarks</span></span>
-------

<span data-ttu-id="0783d-115">此函式不會考慮主控台螢幕緩衝區的大小，這表示傳回的視窗大小可能會大於主控台螢幕緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="0783d-115">The function does not take into consideration the size of the console screen buffer, which means that the window size returned may be larger than the size of the console screen buffer.</span></span> <span data-ttu-id="0783d-116">您可以使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函式來判斷主控台視窗的大小上限（指定目前的螢幕緩衝區大小、目前的字型和顯示大小）。</span><span class="sxs-lookup"><span data-stu-id="0783d-116">The [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function can be used to determine the maximum size of the console window, given the current screen buffer size, the current font, and the display size.</span></span>

<a name="requirements"></a><span data-ttu-id="0783d-117">規格需求</span><span class="sxs-lookup"><span data-stu-id="0783d-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="0783d-118">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="0783d-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="0783d-119">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="0783d-119">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0783d-120">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="0783d-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="0783d-121">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="0783d-121">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0783d-122">標頭</span><span class="sxs-lookup"><span data-stu-id="0783d-122">Header</span></span></p></td>
<td><span data-ttu-id="0783d-123">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="0783d-123">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0783d-124">程式庫</span><span class="sxs-lookup"><span data-stu-id="0783d-124">Library</span></span></p></td>
<td><span data-ttu-id="0783d-125">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="0783d-125">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0783d-126">DLL</span><span class="sxs-lookup"><span data-stu-id="0783d-126">DLL</span></span></p></td>
<td><span data-ttu-id="0783d-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0783d-127">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="0783d-128"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="0783d-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="0783d-129">主控台功能</span><span class="sxs-lookup"><span data-stu-id="0783d-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0783d-130">**COORD**</span><span class="sxs-lookup"><span data-stu-id="0783d-130">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="0783d-131">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="0783d-131">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="0783d-132">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="0783d-132">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="0783d-133">視窗和螢幕緩衝區大小</span><span class="sxs-lookup"><span data-stu-id="0783d-133">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)

 

 





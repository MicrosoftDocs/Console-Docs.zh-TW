---
title: SetStdHandle 函式
description: 設定指定標準裝置的控制碼 (標準輸入、標準輸出或標準錯誤) 。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 6ab17a2162d31c956ec64dbb33696c20ae085298
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059539"
---
# <a name="setstdhandle-function"></a><span data-ttu-id="87250-104">SetStdHandle 函式</span><span class="sxs-lookup"><span data-stu-id="87250-104">SetStdHandle function</span></span>


<span data-ttu-id="87250-105">設定指定標準裝置的控制碼 (標準輸入、標準輸出或標準錯誤) 。</span><span class="sxs-lookup"><span data-stu-id="87250-105">Sets the handle for the specified standard device (standard input, standard output, or standard error).</span></span>

<a name="syntax"></a><span data-ttu-id="87250-106">語法</span><span class="sxs-lookup"><span data-stu-id="87250-106">Syntax</span></span>
------

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

<a name="parameters"></a><span data-ttu-id="87250-107">參數</span><span class="sxs-lookup"><span data-stu-id="87250-107">Parameters</span></span>
----------

<span data-ttu-id="87250-108">*nStdHandle* \[在\]</span><span class="sxs-lookup"><span data-stu-id="87250-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="87250-109">要設定控制碼的標準裝置。</span><span class="sxs-lookup"><span data-stu-id="87250-109">The standard device for which the handle is to be set.</span></span> <span data-ttu-id="87250-110">這個參數可以是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="87250-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="87250-111">值</span><span class="sxs-lookup"><span data-stu-id="87250-111">Value</span></span></th>
<th><span data-ttu-id="87250-112">意義</span><span class="sxs-lookup"><span data-stu-id="87250-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="87250-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD) -10</span><span class="sxs-lookup"><span data-stu-id="87250-113"><span id="STD_INPUT_HANDLE"></span><span id="std_input_handle"></span>
<strong>STD_INPUT_HANDLE</strong> (DWORD)-10</span></span></td>
<td><p><span data-ttu-id="87250-114">標準輸入設備。</span><span class="sxs-lookup"><span data-stu-id="87250-114">The standard input device.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="87250-115"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD) -11</span><span class="sxs-lookup"><span data-stu-id="87250-115"><span id="STD_OUTPUT_HANDLE"></span><span id="std_output_handle"></span>
<strong>STD_OUTPUT_HANDLE</strong> (DWORD)-11</span></span></td>
<td><p><span data-ttu-id="87250-116">標準輸出裝置。</span><span class="sxs-lookup"><span data-stu-id="87250-116">The standard output device.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="87250-117"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD) -12</span><span class="sxs-lookup"><span data-stu-id="87250-117"><span id="STD_ERROR_HANDLE"></span><span id="std_error_handle"></span>
<strong>STD_ERROR_HANDLE</strong> (DWORD)-12</span></span></td>
<td><p><span data-ttu-id="87250-118">標準錯誤裝置。</span><span class="sxs-lookup"><span data-stu-id="87250-118">The standard error device.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="87250-119">*hHandle* \[在\]</span><span class="sxs-lookup"><span data-stu-id="87250-119">*hHandle* \[in\]</span></span>  
<span data-ttu-id="87250-120">標準裝置的控制碼。</span><span class="sxs-lookup"><span data-stu-id="87250-120">The handle for the standard device.</span></span>

<a name="return-value"></a><span data-ttu-id="87250-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="87250-121">Return value</span></span>
------------

<span data-ttu-id="87250-122">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="87250-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="87250-123">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="87250-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="87250-124">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="87250-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="87250-125">備註</span><span class="sxs-lookup"><span data-stu-id="87250-125">Remarks</span></span>
-------

<span data-ttu-id="87250-126">對 **SetStdHandle**的呼叫可能會重新導向進程的標準控制碼，在這種情況下， [**GetStdHandle**](getstdhandle.md) 會傳回重新導向的控制碼。</span><span class="sxs-lookup"><span data-stu-id="87250-126">The standard handles of a process may have been redirected by a call to **SetStdHandle**, in which case [**GetStdHandle**](getstdhandle.md) will return the redirected handle.</span></span> <span data-ttu-id="87250-127">如果已重新導向標準控制碼，您可以在 [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) 函式的呼叫中指定 CONIN $ 值，以取得主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="87250-127">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="87250-128">同樣地，您可以指定 CONOUT $ 值，以取得主控台的作用中螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="87250-128">Similarly, you can specify the CONOUT$ value to get a handle to the console's active screen buffer.</span></span>

<a name="examples"></a><span data-ttu-id="87250-129">範例</span><span class="sxs-lookup"><span data-stu-id="87250-129">Examples</span></span>
--------

<span data-ttu-id="87250-130">如需範例，請參閱 [使用重新導向的輸入和輸出建立子進程](https://msdn.microsoft.com/library/windows/desktop/ms682499)。</span><span class="sxs-lookup"><span data-stu-id="87250-130">For an example, see [Creating a Child Process with Redirected Input and Output](https://msdn.microsoft.com/library/windows/desktop/ms682499).</span></span>

<a name="requirements"></a><span data-ttu-id="87250-131">規格需求</span><span class="sxs-lookup"><span data-stu-id="87250-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="87250-132">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="87250-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="87250-133">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="87250-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="87250-134">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="87250-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="87250-135">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="87250-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="87250-136">標頭</span><span class="sxs-lookup"><span data-stu-id="87250-136">Header</span></span></p></td>
<td><span data-ttu-id="87250-137">ProcessEnv .h (via Winbase，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="87250-137">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="87250-138">程式庫</span><span class="sxs-lookup"><span data-stu-id="87250-138">Library</span></span></p></td>
<td><span data-ttu-id="87250-139">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="87250-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="87250-140">DLL</span><span class="sxs-lookup"><span data-stu-id="87250-140">DLL</span></span></p></td>
<td><span data-ttu-id="87250-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="87250-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="87250-142"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="87250-142"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="87250-143">主控台功能</span><span class="sxs-lookup"><span data-stu-id="87250-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="87250-144">主控台控制碼</span><span class="sxs-lookup"><span data-stu-id="87250-144">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="87250-145">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="87250-145">**CreateFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)

[<span data-ttu-id="87250-146">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="87250-146">**GetStdHandle**</span></span>](getstdhandle.md)

 

 





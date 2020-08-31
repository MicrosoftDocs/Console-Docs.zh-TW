---
title: SetConsoleActiveScreenBuffer 函式
description: 將指定的螢幕緩衝區設定為目前顯示的主控台螢幕緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/SetConsoleActiveScreenBuffer
- wincon/SetConsoleActiveScreenBuffer
- SetConsoleActiveScreenBuffer
MS-HAID:
- '\_win32\_setconsoleactivescreenbuffer'
- base.setconsoleactivescreenbuffer
- consoles.setconsoleactivescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c026cb94-c8ec-44ee-b432-3870ae3006c2
topic_type:
- apiref
api_name:
- SetConsoleActiveScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: f3fa9d79705c95fc0737597886b5562ce1045c45
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059419"
---
# <a name="setconsoleactivescreenbuffer-function"></a><span data-ttu-id="91e58-104">SetConsoleActiveScreenBuffer 函式</span><span class="sxs-lookup"><span data-stu-id="91e58-104">SetConsoleActiveScreenBuffer function</span></span>


<span data-ttu-id="91e58-105">將指定的螢幕緩衝區設定為目前顯示的主控台螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="91e58-105">Sets the specified screen buffer to be the currently displayed console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="91e58-106">語法</span><span class="sxs-lookup"><span data-stu-id="91e58-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleActiveScreenBuffer(
  _In_ HANDLE hConsoleOutput
);
```

<a name="parameters"></a><span data-ttu-id="91e58-107">參數</span><span class="sxs-lookup"><span data-stu-id="91e58-107">Parameters</span></span>
----------

<span data-ttu-id="91e58-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="91e58-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="91e58-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="91e58-109">A handle to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="91e58-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="91e58-110">Return value</span></span>
------------

<span data-ttu-id="91e58-111">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="91e58-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="91e58-112">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="91e58-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="91e58-113">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="91e58-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="91e58-114">備註</span><span class="sxs-lookup"><span data-stu-id="91e58-114">Remarks</span></span>
-------

<span data-ttu-id="91e58-115">主控台可以有多個螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="91e58-115">A console can have multiple screen buffers.</span></span> <span data-ttu-id="91e58-116">**SetConsoleActiveScreenBuffer** 會決定要顯示哪一個。</span><span class="sxs-lookup"><span data-stu-id="91e58-116">**SetConsoleActiveScreenBuffer** determines which one is displayed.</span></span> <span data-ttu-id="91e58-117">您可以寫入非使用中的螢幕緩衝區，然後使用 **SetConsoleActiveScreenBuffer** 來顯示緩衝區的內容。</span><span class="sxs-lookup"><span data-stu-id="91e58-117">You can write to an inactive screen buffer and then use **SetConsoleActiveScreenBuffer** to display the buffer's contents.</span></span>

<a name="examples"></a><span data-ttu-id="91e58-118">範例</span><span class="sxs-lookup"><span data-stu-id="91e58-118">Examples</span></span>
--------

<span data-ttu-id="91e58-119">如需範例，請參閱 [讀取和寫入字元和屬性的區塊](reading-and-writing-blocks-of-characters-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="91e58-119">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

<a name="requirements"></a><span data-ttu-id="91e58-120">規格需求</span><span class="sxs-lookup"><span data-stu-id="91e58-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="91e58-121">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="91e58-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="91e58-122">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="91e58-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="91e58-123">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="91e58-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="91e58-124">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="91e58-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="91e58-125">標頭</span><span class="sxs-lookup"><span data-stu-id="91e58-125">Header</span></span></p></td>
<td><span data-ttu-id="91e58-126">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="91e58-126">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="91e58-127">程式庫</span><span class="sxs-lookup"><span data-stu-id="91e58-127">Library</span></span></p></td>
<td><span data-ttu-id="91e58-128">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="91e58-128">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="91e58-129">DLL</span><span class="sxs-lookup"><span data-stu-id="91e58-129">DLL</span></span></p></td>
<td><span data-ttu-id="91e58-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="91e58-130">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="91e58-131"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="91e58-131"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="91e58-132">主控台功能</span><span class="sxs-lookup"><span data-stu-id="91e58-132">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="91e58-133">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="91e58-133">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="91e58-134">**CreateConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="91e58-134">**CreateConsoleScreenBuffer**</span></span>](createconsolescreenbuffer.md)

 

 





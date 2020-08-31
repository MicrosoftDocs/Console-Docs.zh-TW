---
title: GetConsoleDisplayMode 函式
description: 請參閱 GetConsoleDisplayMode 函式的參考資訊，此函數會抓取目前主控台的顯示模式。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 76b3354ac9b44c36ec4cfe3d12257583d10f2ee2
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059175"
---
# <a name="getconsoledisplaymode-function"></a><span data-ttu-id="e14cf-104">GetConsoleDisplayMode 函式</span><span class="sxs-lookup"><span data-stu-id="e14cf-104">GetConsoleDisplayMode function</span></span>


<span data-ttu-id="e14cf-105">抓取目前主控台的顯示模式。</span><span class="sxs-lookup"><span data-stu-id="e14cf-105">Retrieves the display mode of the current console.</span></span>

<a name="syntax"></a><span data-ttu-id="e14cf-106">語法</span><span class="sxs-lookup"><span data-stu-id="e14cf-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

<a name="parameters"></a><span data-ttu-id="e14cf-107">參數</span><span class="sxs-lookup"><span data-stu-id="e14cf-107">Parameters</span></span>
----------

<span data-ttu-id="e14cf-108">*lpModeFlags* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="e14cf-108">*lpModeFlags* \[out\]</span></span>  
<span data-ttu-id="e14cf-109">主控台的顯示模式。</span><span class="sxs-lookup"><span data-stu-id="e14cf-109">The display mode of the console.</span></span> <span data-ttu-id="e14cf-110">這個參數可以是下列一或多個值。</span><span class="sxs-lookup"><span data-stu-id="e14cf-110">This parameter can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="e14cf-111">值</span><span class="sxs-lookup"><span data-stu-id="e14cf-111">Value</span></span></th>
<th><span data-ttu-id="e14cf-112">意義</span><span class="sxs-lookup"><span data-stu-id="e14cf-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="e14cf-113"><span id="CONSOLE_FULLSCREEN"></span><span id="console_fullscreen"></span>
<strong>CONSOLE_FULLSCREEN</strong> 1</span><span class="sxs-lookup"><span data-stu-id="e14cf-113"><span id="CONSOLE_FULLSCREEN"></span><span id="console_fullscreen"></span>
<strong>CONSOLE_FULLSCREEN</strong> 1</span></span></td>
<td><p><span data-ttu-id="e14cf-114">全螢幕主控台。</span><span class="sxs-lookup"><span data-stu-id="e14cf-114">Full-screen console.</span></span> <span data-ttu-id="e14cf-115">當視窗最大化時，主控台便會處於此模式。</span><span class="sxs-lookup"><span data-stu-id="e14cf-115">The console is in this mode as soon as the window is maximized.</span></span> <span data-ttu-id="e14cf-116">到目前為止，轉換成全螢幕模式仍然可能失敗。</span><span class="sxs-lookup"><span data-stu-id="e14cf-116">At this point, the transition to full-screen mode can still fail.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e14cf-117"><span id="CONSOLE_FULLSCREEN_HARDWARE"></span><span id="console_fullscreen_hardware"></span>
<strong>CONSOLE_FULLSCREEN_HARDWARE</strong> 2</span><span class="sxs-lookup"><span data-stu-id="e14cf-117"><span id="CONSOLE_FULLSCREEN_HARDWARE"></span><span id="console_fullscreen_hardware"></span>
<strong>CONSOLE_FULLSCREEN_HARDWARE</strong> 2</span></span></td>
<td><p><span data-ttu-id="e14cf-118">全螢幕主控台會直接與影片硬體通訊。</span><span class="sxs-lookup"><span data-stu-id="e14cf-118">Full-screen console communicating directly with the video hardware.</span></span> <span data-ttu-id="e14cf-119">主控台處於 <strong>CONSOLE_FULLSCREEN</strong> 模式之後，就會設定此模式，以指出已完成轉換至全螢幕模式。</span><span class="sxs-lookup"><span data-stu-id="e14cf-119">This mode is set after the console is in <strong>CONSOLE_FULLSCREEN</strong> mode to indicate that the transition to full-screen mode has completed.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="e14cf-120">傳回值</span><span class="sxs-lookup"><span data-stu-id="e14cf-120">Return value</span></span>
------------

<span data-ttu-id="e14cf-121">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="e14cf-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e14cf-122">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="e14cf-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e14cf-123">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="e14cf-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="e14cf-124">備註</span><span class="sxs-lookup"><span data-stu-id="e14cf-124">Remarks</span></span>
-------

<span data-ttu-id="e14cf-125">若要編譯使用此函數的應用程式，請將\*\* \_ WIN32 \_ WINNT\*\*定義為0x0500 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="e14cf-125">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="e14cf-126">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="e14cf-126">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="e14cf-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="e14cf-127">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e14cf-128">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="e14cf-128">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e14cf-129">Windows XP [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="e14cf-129">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e14cf-130">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="e14cf-130">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e14cf-131">Windows Server 2003 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="e14cf-131">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e14cf-132">標頭</span><span class="sxs-lookup"><span data-stu-id="e14cf-132">Header</span></span></p></td>
<td><span data-ttu-id="e14cf-133">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="e14cf-133">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e14cf-134">程式庫</span><span class="sxs-lookup"><span data-stu-id="e14cf-134">Library</span></span></p></td>
<td><span data-ttu-id="e14cf-135">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="e14cf-135">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e14cf-136">DLL</span><span class="sxs-lookup"><span data-stu-id="e14cf-136">DLL</span></span></p></td>
<td><span data-ttu-id="e14cf-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e14cf-137">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e14cf-138"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="e14cf-138"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e14cf-139">主控台功能</span><span class="sxs-lookup"><span data-stu-id="e14cf-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e14cf-140">主控台模式</span><span class="sxs-lookup"><span data-stu-id="e14cf-140">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="e14cf-141">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="e14cf-141">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)

 

 





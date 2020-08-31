---
title: SetConsoleDisplayMode 函式
description: 請參閱 SetConsoleDisplayMode 函式的參考資訊，此函式會設定指定的主控台螢幕緩衝區的顯示模式。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0d4564b9a7562fb495c9834df98708d5faff5334
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059322"
---
# <a name="setconsoledisplaymode-function"></a><span data-ttu-id="7ba0b-104">SetConsoleDisplayMode 函式</span><span class="sxs-lookup"><span data-stu-id="7ba0b-104">SetConsoleDisplayMode function</span></span>


<span data-ttu-id="7ba0b-105">設定指定之主控台螢幕緩衝區的顯示模式。</span><span class="sxs-lookup"><span data-stu-id="7ba0b-105">Sets the display mode of the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="7ba0b-106">語法</span><span class="sxs-lookup"><span data-stu-id="7ba0b-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

<a name="parameters"></a><span data-ttu-id="7ba0b-107">參數</span><span class="sxs-lookup"><span data-stu-id="7ba0b-107">Parameters</span></span>
----------

<span data-ttu-id="7ba0b-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="7ba0b-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="7ba0b-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="7ba0b-109">A handle to the console screen buffer.</span></span>

<span data-ttu-id="7ba0b-110">*dwFlags* \[在\]</span><span class="sxs-lookup"><span data-stu-id="7ba0b-110">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="7ba0b-111">主控台的顯示模式。</span><span class="sxs-lookup"><span data-stu-id="7ba0b-111">The display mode of the console.</span></span> <span data-ttu-id="7ba0b-112">這個參數可以是下列一或多個值。</span><span class="sxs-lookup"><span data-stu-id="7ba0b-112">This parameter can be one or more of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="7ba0b-113">值</span><span class="sxs-lookup"><span data-stu-id="7ba0b-113">Value</span></span></th>
<th><span data-ttu-id="7ba0b-114">意義</span><span class="sxs-lookup"><span data-stu-id="7ba0b-114">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="7ba0b-115"><span id="CONSOLE_FULLSCREEN_MODE"></span><span id="console_fullscreen_mode"></span>
<strong>CONSOLE_FULLSCREEN_MODE</strong> 1</span><span class="sxs-lookup"><span data-stu-id="7ba0b-115"><span id="CONSOLE_FULLSCREEN_MODE"></span><span id="console_fullscreen_mode"></span>
<strong>CONSOLE_FULLSCREEN_MODE</strong> 1</span></span></td>
<td><p><span data-ttu-id="7ba0b-116">文字會以全螢幕模式顯示。</span><span class="sxs-lookup"><span data-stu-id="7ba0b-116">Text is displayed in full-screen mode.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="7ba0b-117"><span id="CONSOLE_WINDOWED_MODE"></span><span id="console_windowed_mode"></span>
<strong>CONSOLE_WINDOWED_MODE</strong> 2</span><span class="sxs-lookup"><span data-stu-id="7ba0b-117"><span id="CONSOLE_WINDOWED_MODE"></span><span id="console_windowed_mode"></span>
<strong>CONSOLE_WINDOWED_MODE</strong> 2</span></span></td>
<td><p><span data-ttu-id="7ba0b-118">文字會顯示在主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="7ba0b-118">Text is displayed in a console window.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="7ba0b-119">*lpNewScreenBufferDimensions* \[out、optional\]</span><span class="sxs-lookup"><span data-stu-id="7ba0b-119">*lpNewScreenBufferDimensions* \[out, optional\]</span></span>  
<span data-ttu-id="7ba0b-120">[**COORD**](coord-str.md)結構的指標，此結構會接收螢幕緩衝區的新維度（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="7ba0b-120">A pointer to a [**COORD**](coord-str.md) structure that receives the new dimensions of the screen buffer, in characters.</span></span>

<a name="return-value"></a><span data-ttu-id="7ba0b-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="7ba0b-121">Return value</span></span>
------------

<span data-ttu-id="7ba0b-122">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="7ba0b-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="7ba0b-123">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="7ba0b-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="7ba0b-124">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="7ba0b-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="7ba0b-125">規格需求</span><span class="sxs-lookup"><span data-stu-id="7ba0b-125">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="7ba0b-126">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="7ba0b-126">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="7ba0b-127">Windows XP [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="7ba0b-127">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7ba0b-128">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="7ba0b-128">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="7ba0b-129">Windows Server 2003 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="7ba0b-129">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7ba0b-130">標頭</span><span class="sxs-lookup"><span data-stu-id="7ba0b-130">Header</span></span></p></td>
<td><span data-ttu-id="7ba0b-131">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="7ba0b-131">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7ba0b-132">程式庫</span><span class="sxs-lookup"><span data-stu-id="7ba0b-132">Library</span></span></p></td>
<td><span data-ttu-id="7ba0b-133">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="7ba0b-133">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7ba0b-134">DLL</span><span class="sxs-lookup"><span data-stu-id="7ba0b-134">DLL</span></span></p></td>
<td><span data-ttu-id="7ba0b-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7ba0b-135">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="7ba0b-136"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ba0b-136"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="7ba0b-137">主控台功能</span><span class="sxs-lookup"><span data-stu-id="7ba0b-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="7ba0b-138">主控台模式</span><span class="sxs-lookup"><span data-stu-id="7ba0b-138">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="7ba0b-139">**GetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="7ba0b-139">**GetConsoleDisplayMode**</span></span>](getconsoledisplaymode.md)

 

 





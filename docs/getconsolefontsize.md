---
title: GetConsoleFontSize 函式
description: 抓取指定的主控台螢幕緩衝區所使用的字型大小。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi3/GetConsoleFontSize
- wincon/GetConsoleFontSize
- GetConsoleFontSize
MS-HAID:
- '\_win32\_getconsolefontsize'
- base.getconsolefontsize
- consoles.getconsolefontsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 51b1f58d-b3fb-4e09-8398-671b3959bb01
topic_type:
- apiref
api_name:
- GetConsoleFontSize
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: b992ddaab35cb5af25479426dca83ef6381e73dd
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059167"
---
# <a name="getconsolefontsize-function"></a><span data-ttu-id="230e9-104">GetConsoleFontSize 函式</span><span class="sxs-lookup"><span data-stu-id="230e9-104">GetConsoleFontSize function</span></span>


<span data-ttu-id="230e9-105">抓取指定的主控台螢幕緩衝區所使用的字型大小。</span><span class="sxs-lookup"><span data-stu-id="230e9-105">Retrieves the size of the font used by the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="230e9-106">語法</span><span class="sxs-lookup"><span data-stu-id="230e9-106">Syntax</span></span>
------

```C
COORD WINAPI GetConsoleFontSize(
  _In_ HANDLE hConsoleOutput,
  _In_ DWORD  nFont
);
```

<a name="parameters"></a><span data-ttu-id="230e9-107">參數</span><span class="sxs-lookup"><span data-stu-id="230e9-107">Parameters</span></span>
----------

<span data-ttu-id="230e9-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="230e9-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="230e9-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="230e9-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="230e9-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="230e9-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="230e9-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="230e9-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="230e9-112">*nFont* \[在\]</span><span class="sxs-lookup"><span data-stu-id="230e9-112">*nFont* \[in\]</span></span>  
<span data-ttu-id="230e9-113">要取出其大小的字型索引。</span><span class="sxs-lookup"><span data-stu-id="230e9-113">The index of the font whose size is to be retrieved.</span></span> <span data-ttu-id="230e9-114">藉由呼叫 [**GetCurrentConsoleFont**](getcurrentconsolefont.md) 函數來取得此索引。</span><span class="sxs-lookup"><span data-stu-id="230e9-114">This index is obtained by calling the [**GetCurrentConsoleFont**](getcurrentconsolefont.md) function.</span></span>

<a name="return-value"></a><span data-ttu-id="230e9-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="230e9-115">Return value</span></span>
------------

<span data-ttu-id="230e9-116">如果函式成功，則傳回值是 [**COORD**](coord-str.md) 結構，其中包含字型中每個字元的寬度和高度（以邏輯單位表示）。</span><span class="sxs-lookup"><span data-stu-id="230e9-116">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="230e9-117">**X**成員包含寬度，而**Y**成員包含高度。</span><span class="sxs-lookup"><span data-stu-id="230e9-117">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="230e9-118">如果函式失敗，則寬度和高度為零。</span><span class="sxs-lookup"><span data-stu-id="230e9-118">If the function fails, the width and the height are zero.</span></span> <span data-ttu-id="230e9-119">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="230e9-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="230e9-120">若要編譯使用此函數的應用程式，請將\*\* \_ WIN32 \_ WINNT\*\*定義為0x0500 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="230e9-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="230e9-121">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="230e9-121">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="230e9-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="230e9-122">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="230e9-123">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="230e9-123">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="230e9-124">Windows XP [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="230e9-124">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="230e9-125">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="230e9-125">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="230e9-126">Windows Server 2003 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="230e9-126">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="230e9-127">標頭</span><span class="sxs-lookup"><span data-stu-id="230e9-127">Header</span></span></p></td>
<td><span data-ttu-id="230e9-128">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="230e9-128">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="230e9-129">程式庫</span><span class="sxs-lookup"><span data-stu-id="230e9-129">Library</span></span></p></td>
<td><span data-ttu-id="230e9-130">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="230e9-130">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="230e9-131">DLL</span><span class="sxs-lookup"><span data-stu-id="230e9-131">DLL</span></span></p></td>
<td><span data-ttu-id="230e9-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="230e9-132">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="230e9-133"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="230e9-133"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="230e9-134">主控台功能</span><span class="sxs-lookup"><span data-stu-id="230e9-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="230e9-135">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="230e9-135">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="230e9-136">**COORD**</span><span class="sxs-lookup"><span data-stu-id="230e9-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="230e9-137">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="230e9-137">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)

 

 





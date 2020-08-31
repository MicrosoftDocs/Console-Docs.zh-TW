---
title: GetCurrentConsoleFont 函式
description: 針對指定的主控台螢幕緩衝區，抓取目前主控台字型的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi3/GetCurrentConsoleFont
- wincon/GetCurrentConsoleFont
- GetCurrentConsoleFont
MS-HAID:
- '\_win32\_getcurrentconsolefont'
- base.getcurrentconsolefont
- consoles.getcurrentconsolefont
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 347508ea-5c15-4568-b99f-1e7f5cdac8c1
topic_type:
- apiref
api_name:
- GetCurrentConsoleFont
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 4116dcf034c619544ed1689e3161f4eca4250a81
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059110"
---
# <a name="getcurrentconsolefont-function"></a><span data-ttu-id="c2f6c-104">GetCurrentConsoleFont 函式</span><span class="sxs-lookup"><span data-stu-id="c2f6c-104">GetCurrentConsoleFont function</span></span>


<span data-ttu-id="c2f6c-105">抓取目前主控台字型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c2f6c-105">Retrieves information about the current console font.</span></span>

<a name="syntax"></a><span data-ttu-id="c2f6c-106">語法</span><span class="sxs-lookup"><span data-stu-id="c2f6c-106">Syntax</span></span>
------

```C
BOOL WINAPI GetCurrentConsoleFont(
  _In_  HANDLE             hConsoleOutput,
  _In_  BOOL               bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFO lpConsoleCurrentFont
);
```

<a name="parameters"></a><span data-ttu-id="c2f6c-107">參數</span><span class="sxs-lookup"><span data-stu-id="c2f6c-107">Parameters</span></span>
----------

<span data-ttu-id="c2f6c-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="c2f6c-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="c2f6c-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="c2f6c-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="c2f6c-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="c2f6c-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="c2f6c-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="c2f6c-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="c2f6c-112">*bMaximumWindow* \[在\]</span><span class="sxs-lookup"><span data-stu-id="c2f6c-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="c2f6c-113">如果此參數為 **TRUE**，就會針對最大視窗大小抓取字型資訊。</span><span class="sxs-lookup"><span data-stu-id="c2f6c-113">If this parameter is **TRUE**, font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="c2f6c-114">如果此參數為 **FALSE**，則會針對目前的視窗大小抓取字型資訊。</span><span class="sxs-lookup"><span data-stu-id="c2f6c-114">If this parameter is **FALSE**, font information is retrieved for the current window size.</span></span>

<span data-ttu-id="c2f6c-115">*lpConsoleCurrentFont* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="c2f6c-115">*lpConsoleCurrentFont* \[out\]</span></span>  
<span data-ttu-id="c2f6c-116">[**主控台 \_ 字型 \_ 資訊**](console-font-info-str.md)結構的指標，此結構會接收要求的字型資訊。</span><span class="sxs-lookup"><span data-stu-id="c2f6c-116">A pointer to a [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) structure that receives the requested font information.</span></span>

<a name="return-value"></a><span data-ttu-id="c2f6c-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="c2f6c-117">Return value</span></span>
------------

<span data-ttu-id="c2f6c-118">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="c2f6c-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c2f6c-119">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="c2f6c-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c2f6c-120">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="c2f6c-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="c2f6c-121">備註</span><span class="sxs-lookup"><span data-stu-id="c2f6c-121">Remarks</span></span>
-------

<span data-ttu-id="c2f6c-122">若要編譯使用此函數的應用程式，請將\*\* \_ WIN32 \_ WINNT\*\*定義為0x0500 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c2f6c-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="c2f6c-123">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="c2f6c-123">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="c2f6c-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="c2f6c-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="c2f6c-125">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="c2f6c-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="c2f6c-126">Windows XP [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="c2f6c-126">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c2f6c-127">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="c2f6c-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="c2f6c-128">Windows Server 2003 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="c2f6c-128">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c2f6c-129">標頭</span><span class="sxs-lookup"><span data-stu-id="c2f6c-129">Header</span></span></p></td>
<td><span data-ttu-id="c2f6c-130">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="c2f6c-130">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c2f6c-131">程式庫</span><span class="sxs-lookup"><span data-stu-id="c2f6c-131">Library</span></span></p></td>
<td><span data-ttu-id="c2f6c-132">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="c2f6c-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c2f6c-133">DLL</span><span class="sxs-lookup"><span data-stu-id="c2f6c-133">DLL</span></span></p></td>
<td><span data-ttu-id="c2f6c-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c2f6c-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="c2f6c-135"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2f6c-135"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="c2f6c-136">主控台功能</span><span class="sxs-lookup"><span data-stu-id="c2f6c-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c2f6c-137">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="c2f6c-137">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="c2f6c-138">**主控台 \_ 字型 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="c2f6c-138">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="c2f6c-139">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="c2f6c-139">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)

 

 





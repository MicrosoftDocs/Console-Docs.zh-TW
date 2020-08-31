---
title: GetConsoleOriginalTitle 函式
description: 請參閱 GetConsoleOriginalTitle 函式的參考資訊，此函式會抓取目前主控台視窗的原始標題。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/GetConsoleOriginalTitle
- wincon/GetConsoleOriginalTitle
- GetConsoleOriginalTitle
- consoleapi2/GetConsoleOriginalTitleA
- wincon/GetConsoleOriginalTitleA
- GetConsoleOriginalTitleA
- consoleapi2/GetConsoleOriginalTitleW
- wincon/GetConsoleOriginalTitleW
- GetConsoleOriginalTitleW
MS-HAID:
- base.getconsoleoriginaltitle
- consoles.getconsoleoriginaltitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e3dd02f4-4899-4df0-a960-3b2625c15fee
topic_type:
- apiref
api_name:
- GetConsoleOriginalTitle
- GetConsoleOriginalTitleA
- GetConsoleOriginalTitleW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 109d41a141083fc4691ebaf2546ec8f412f7b861
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059138"
---
# <a name="getconsoleoriginaltitle-function"></a><span data-ttu-id="6f866-104">GetConsoleOriginalTitle 函式</span><span class="sxs-lookup"><span data-stu-id="6f866-104">GetConsoleOriginalTitle function</span></span>


<span data-ttu-id="6f866-105">抓取目前主控台視窗的原始標題。</span><span class="sxs-lookup"><span data-stu-id="6f866-105">Retrieves the original title for the current console window.</span></span>

<a name="syntax"></a><span data-ttu-id="6f866-106">語法</span><span class="sxs-lookup"><span data-stu-id="6f866-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a><span data-ttu-id="6f866-107">參數</span><span class="sxs-lookup"><span data-stu-id="6f866-107">Parameters</span></span>
----------

<span data-ttu-id="6f866-108">*lpConsoleTitle* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="6f866-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="6f866-109">緩衝區的指標，此緩衝區會接收以 null 終止的字串，其中包含原始標題。</span><span class="sxs-lookup"><span data-stu-id="6f866-109">A pointer to a buffer that receives a null-terminated string containing the original title.</span></span>

<span data-ttu-id="6f866-110">*nSize* \[在\]</span><span class="sxs-lookup"><span data-stu-id="6f866-110">*nSize* \[in\]</span></span>  
<span data-ttu-id="6f866-111">*LpConsoleTitle*緩衝區的大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="6f866-111">The size of the *lpConsoleTitle* buffer, in characters.</span></span>

<a name="return-value"></a><span data-ttu-id="6f866-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="6f866-112">Return value</span></span>
------------

<span data-ttu-id="6f866-113">如果函式成功，傳回值就是複製到緩衝區的字串長度（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="6f866-113">If the function succeeds, the return value is the length of the string copied to the buffer, in characters.</span></span>

<span data-ttu-id="6f866-114">如果緩衝區不夠大，無法儲存標題，則傳回值為零，而 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) 會傳回 **錯誤 \_ 成功**。</span><span class="sxs-lookup"><span data-stu-id="6f866-114">If the buffer is not large enough to store the title, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns **ERROR\_SUCCESS**.</span></span>

<span data-ttu-id="6f866-115">如果函式失敗，則傳回值為零，而 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) 會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="6f866-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

<a name="remarks"></a><span data-ttu-id="6f866-116">備註</span><span class="sxs-lookup"><span data-stu-id="6f866-116">Remarks</span></span>
-------

<span data-ttu-id="6f866-117">若要設定主控台視窗的標題，請使用 [**SetConsoleTitle**](setconsoletitle.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="6f866-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="6f866-118">若要取得目前的標題字串，請使用 [**GetConsoleTitle**](getconsoletitle.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="6f866-118">To retrieve the current title string, use the [**GetConsoleTitle**](getconsoletitle.md) function.</span></span>

<span data-ttu-id="6f866-119">若要編譯使用此函數的應用程式，請將\*\* \_ WIN32 \_ WINNT\*\*定義為0x0600 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="6f866-119">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0600 or later.</span></span> <span data-ttu-id="6f866-120">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="6f866-120">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="6f866-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="6f866-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="6f866-122">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="6f866-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="6f866-123">Windows Vista [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="6f866-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6f866-124">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="6f866-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="6f866-125">Windows Server 2008 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="6f866-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6f866-126">標頭</span><span class="sxs-lookup"><span data-stu-id="6f866-126">Header</span></span></p></td>
<td><span data-ttu-id="6f866-127">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="6f866-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6f866-128">程式庫</span><span class="sxs-lookup"><span data-stu-id="6f866-128">Library</span></span></p></td>
<td><span data-ttu-id="6f866-129">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="6f866-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6f866-130">DLL</span><span class="sxs-lookup"><span data-stu-id="6f866-130">DLL</span></span></p></td>
<td><span data-ttu-id="6f866-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6f866-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6f866-132">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="6f866-132">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="6f866-133"><strong>GetConsoleOriginalTitleW</strong> (Unicode) 和 <strong>GetConsoleOriginalTitleA</strong> (ANSI) </span><span class="sxs-lookup"><span data-stu-id="6f866-133"><strong>GetConsoleOriginalTitleW</strong> (Unicode) and <strong>GetConsoleOriginalTitleA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="6f866-134"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f866-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="6f866-135">主控台功能</span><span class="sxs-lookup"><span data-stu-id="6f866-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6f866-136">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="6f866-136">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="6f866-137">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="6f866-137">**SetConsoleTitle**</span></span>](setconsoletitle.md)

 

 





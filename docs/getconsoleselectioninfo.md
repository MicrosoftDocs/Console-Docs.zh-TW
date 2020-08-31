---
title: GetConsoleSelectionInfo 函式
description: 請參閱 GetConsoleSelectionInfo 函式的參考資訊，此函式會抓取目前主控台選取專案的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi3/GetConsoleSelectionInfo
- wincon/GetConsoleSelectionInfo
- GetConsoleSelectionInfo
MS-HAID:
- '\_win32\_getconsoleselectioninfo'
- base.getconsoleselectioninfo
- consoles.getconsoleselectioninfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 912efe9d-75dd-43bd-8dca-08671b5ed79c
topic_type:
- apiref
api_name:
- GetConsoleSelectionInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: d29a960bc6b8d96d98e0667084e31354f2aa9653
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059122"
---
# <a name="getconsoleselectioninfo-function"></a><span data-ttu-id="4b01f-104">GetConsoleSelectionInfo 函式</span><span class="sxs-lookup"><span data-stu-id="4b01f-104">GetConsoleSelectionInfo function</span></span>


<span data-ttu-id="4b01f-105">抓取目前主控台選取專案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4b01f-105">Retrieves information about the current console selection.</span></span>

<a name="syntax"></a><span data-ttu-id="4b01f-106">語法</span><span class="sxs-lookup"><span data-stu-id="4b01f-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleSelectionInfo(
  _Out_ PCONSOLE_SELECTION_INFO lpConsoleSelectionInfo
);
```

<a name="parameters"></a><span data-ttu-id="4b01f-107">參數</span><span class="sxs-lookup"><span data-stu-id="4b01f-107">Parameters</span></span>
----------

<span data-ttu-id="4b01f-108">*lpConsoleSelectionInfo* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="4b01f-108">*lpConsoleSelectionInfo* \[out\]</span></span>  
<span data-ttu-id="4b01f-109">[\*\*主控台 \_ 選取 \_ \*\*](console-selection-info-str.md)資訊結構的指標，此結構會接收選取資訊。</span><span class="sxs-lookup"><span data-stu-id="4b01f-109">A pointer to a [**CONSOLE\_SELECTION\_INFO**](console-selection-info-str.md) structure that receives the selection information.</span></span>

<a name="return-value"></a><span data-ttu-id="4b01f-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="4b01f-110">Return value</span></span>
------------

<span data-ttu-id="4b01f-111">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="4b01f-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4b01f-112">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="4b01f-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4b01f-113">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="4b01f-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="4b01f-114">備註</span><span class="sxs-lookup"><span data-stu-id="4b01f-114">Remarks</span></span>
-------

<span data-ttu-id="4b01f-115">若要編譯使用此函數的應用程式，請將\*\* \_ WIN32 \_ WINNT\*\*定義為0x0500 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="4b01f-115">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="4b01f-116">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="4b01f-116">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="4b01f-117">規格需求</span><span class="sxs-lookup"><span data-stu-id="4b01f-117">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="4b01f-118">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="4b01f-118">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="4b01f-119">Windows XP [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="4b01f-119">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4b01f-120">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="4b01f-120">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="4b01f-121">Windows Server 2003 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="4b01f-121">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4b01f-122">標頭</span><span class="sxs-lookup"><span data-stu-id="4b01f-122">Header</span></span></p></td>
<td><span data-ttu-id="4b01f-123">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="4b01f-123">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="4b01f-124">程式庫</span><span class="sxs-lookup"><span data-stu-id="4b01f-124">Library</span></span></p></td>
<td><span data-ttu-id="4b01f-125">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="4b01f-125">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="4b01f-126">DLL</span><span class="sxs-lookup"><span data-stu-id="4b01f-126">DLL</span></span></p></td>
<td><span data-ttu-id="4b01f-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4b01f-127">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="4b01f-128"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b01f-128"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="4b01f-129">主控台功能</span><span class="sxs-lookup"><span data-stu-id="4b01f-129">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4b01f-130">主控台選取專案</span><span class="sxs-lookup"><span data-stu-id="4b01f-130">Console Selection</span></span>](console-selection.md)

[<span data-ttu-id="4b01f-131">**主控台 \_ 選取 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="4b01f-131">**CONSOLE\_SELECTION\_INFO**</span></span>](console-selection-info-str.md)

 

 





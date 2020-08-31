---
title: GetCurrentConsoleFontEx 函式
description: 請參閱 GetCurrentConsoleFontEx 函式的參考資訊，此函式會抓取有關目前使用之主控台字型的延伸資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi3/GetCurrentConsoleFontEx
- wincon/GetCurrentConsoleFontEx
- GetCurrentConsoleFontEx
MS-HAID:
- base.getcurrentconsolefontex
- consoles.getcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 97d8e730-4110-4be5-b099-0acc1b6f8eb5
topic_type:
- apiref
api_name:
- GetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 0ea8d5ad928003d4039a6c8611073ab3c38ce34f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059115"
---
# <a name="getcurrentconsolefontex-function"></a><span data-ttu-id="6f6ca-104">GetCurrentConsoleFontEx 函式</span><span class="sxs-lookup"><span data-stu-id="6f6ca-104">GetCurrentConsoleFontEx function</span></span>


<span data-ttu-id="6f6ca-105">抓取有關目前主控台字型的延伸資訊。</span><span class="sxs-lookup"><span data-stu-id="6f6ca-105">Retrieves extended information about the current console font.</span></span>

<a name="syntax"></a><span data-ttu-id="6f6ca-106">語法</span><span class="sxs-lookup"><span data-stu-id="6f6ca-106">Syntax</span></span>
------

```C
BOOL WINAPI GetCurrentConsoleFontEx(
  _In_  HANDLE               hConsoleOutput,
  _In_  BOOL                 bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

<a name="parameters"></a><span data-ttu-id="6f6ca-107">參數</span><span class="sxs-lookup"><span data-stu-id="6f6ca-107">Parameters</span></span>
----------

<span data-ttu-id="6f6ca-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="6f6ca-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="6f6ca-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="6f6ca-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="6f6ca-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="6f6ca-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="6f6ca-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="6f6ca-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="6f6ca-112">*bMaximumWindow* \[在\]</span><span class="sxs-lookup"><span data-stu-id="6f6ca-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="6f6ca-113">如果此參數為 **TRUE**，就會針對最大視窗大小抓取字型資訊。</span><span class="sxs-lookup"><span data-stu-id="6f6ca-113">If this parameter is **TRUE**, font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="6f6ca-114">如果此參數為 **FALSE**，則會針對目前的視窗大小抓取字型資訊。</span><span class="sxs-lookup"><span data-stu-id="6f6ca-114">If this parameter is **FALSE**, font information is retrieved for the current window size.</span></span>

<span data-ttu-id="6f6ca-115">*lpConsoleCurrentFontEx* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="6f6ca-115">*lpConsoleCurrentFontEx* \[out\]</span></span>  
<span data-ttu-id="6f6ca-116">[**主控台 \_ 字型 \_ INFOEX**](console-font-infoex.md)結構的指標，此結構會接收要求的字型資訊。</span><span class="sxs-lookup"><span data-stu-id="6f6ca-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that receives the requested font information.</span></span>

<a name="return-value"></a><span data-ttu-id="6f6ca-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="6f6ca-117">Return value</span></span>
------------

<span data-ttu-id="6f6ca-118">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="6f6ca-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="6f6ca-119">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="6f6ca-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="6f6ca-120">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="6f6ca-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="6f6ca-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="6f6ca-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="6f6ca-122">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="6f6ca-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="6f6ca-123">Windows Vista [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="6f6ca-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6f6ca-124">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="6f6ca-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="6f6ca-125">Windows Server 2008 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="6f6ca-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6f6ca-126">標頭</span><span class="sxs-lookup"><span data-stu-id="6f6ca-126">Header</span></span></p></td>
<td><span data-ttu-id="6f6ca-127">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="6f6ca-127">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="6f6ca-128">程式庫</span><span class="sxs-lookup"><span data-stu-id="6f6ca-128">Library</span></span></p></td>
<td><span data-ttu-id="6f6ca-129">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="6f6ca-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="6f6ca-130">DLL</span><span class="sxs-lookup"><span data-stu-id="6f6ca-130">DLL</span></span></p></td>
<td><span data-ttu-id="6f6ca-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="6f6ca-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="6f6ca-132"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f6ca-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="6f6ca-133">主控台功能</span><span class="sxs-lookup"><span data-stu-id="6f6ca-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="6f6ca-134">**主控台 \_ 字型 \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="6f6ca-134">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)

 

 





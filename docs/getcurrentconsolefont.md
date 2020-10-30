---
title: GetCurrentConsoleFont 函式
description: 針對指定的主控台螢幕緩衝區，抓取目前主控台字型的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
ms.openlocfilehash: b394f116a75e3c8fb7fddbdc3335e89fbca96652
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037856"
---
# <a name="getcurrentconsolefont-function"></a><span data-ttu-id="64a2a-104">GetCurrentConsoleFont 函式</span><span class="sxs-lookup"><span data-stu-id="64a2a-104">GetCurrentConsoleFont function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="64a2a-105">抓取目前主控台字型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="64a2a-105">Retrieves information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="64a2a-106">語法</span><span class="sxs-lookup"><span data-stu-id="64a2a-106">Syntax</span></span>

```C
BOOL WINAPI GetCurrentConsoleFont(
  _In_  HANDLE             hConsoleOutput,
  _In_  BOOL               bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFO lpConsoleCurrentFont
);
```

## <a name="parameters"></a><span data-ttu-id="64a2a-107">參數</span><span class="sxs-lookup"><span data-stu-id="64a2a-107">Parameters</span></span>

<span data-ttu-id="64a2a-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="64a2a-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="64a2a-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="64a2a-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="64a2a-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="64a2a-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="64a2a-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="64a2a-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="64a2a-112">*bMaximumWindow* \[在\]</span><span class="sxs-lookup"><span data-stu-id="64a2a-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="64a2a-113">如果此參數為 **TRUE** ，就會針對最大視窗大小抓取字型資訊。</span><span class="sxs-lookup"><span data-stu-id="64a2a-113">If this parameter is **TRUE** , font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="64a2a-114">如果此參數為 **FALSE** ，則會針對目前的視窗大小抓取字型資訊。</span><span class="sxs-lookup"><span data-stu-id="64a2a-114">If this parameter is **FALSE** , font information is retrieved for the current window size.</span></span>

<span data-ttu-id="64a2a-115">*lpConsoleCurrentFont* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="64a2a-115">*lpConsoleCurrentFont* \[out\]</span></span>  
<span data-ttu-id="64a2a-116">[**主控台 \_ 字型 \_ 資訊**](console-font-info-str.md)結構的指標，此結構會接收要求的字型資訊。</span><span class="sxs-lookup"><span data-stu-id="64a2a-116">A pointer to a [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) structure that receives the requested font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="64a2a-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="64a2a-117">Return value</span></span>

<span data-ttu-id="64a2a-118">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="64a2a-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="64a2a-119">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="64a2a-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="64a2a-120">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="64a2a-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="64a2a-121">備註</span><span class="sxs-lookup"><span data-stu-id="64a2a-121">Remarks</span></span>

<span data-ttu-id="64a2a-122">若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0500 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="64a2a-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="64a2a-123">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="64a2a-123">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="64a2a-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="64a2a-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="64a2a-125">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="64a2a-125">Minimum supported client</span></span> | <span data-ttu-id="64a2a-126">\[僅限 WINDOWS XP desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="64a2a-126">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="64a2a-127">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="64a2a-127">Minimum supported server</span></span> | <span data-ttu-id="64a2a-128">僅限 Windows Server 2003 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="64a2a-128">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="64a2a-129">標頭</span><span class="sxs-lookup"><span data-stu-id="64a2a-129">Header</span></span> | <span data-ttu-id="64a2a-130">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="64a2a-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="64a2a-131">程式庫</span><span class="sxs-lookup"><span data-stu-id="64a2a-131">Library</span></span> | <span data-ttu-id="64a2a-132">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="64a2a-132">Kernel32.lib</span></span> |
| <span data-ttu-id="64a2a-133">DLL</span><span class="sxs-lookup"><span data-stu-id="64a2a-133">DLL</span></span> | <span data-ttu-id="64a2a-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="64a2a-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="64a2a-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="64a2a-135">See also</span></span>

[<span data-ttu-id="64a2a-136">主控台功能</span><span class="sxs-lookup"><span data-stu-id="64a2a-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="64a2a-137">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="64a2a-137">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="64a2a-138">**主控台 \_ 字型 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="64a2a-138">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="64a2a-139">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="64a2a-139">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)

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
ms.openlocfilehash: 93f22e1b1d1fa6d60e5d97b7650809d19e01f03c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357258"
---
# <a name="getcurrentconsolefont-function"></a><span data-ttu-id="d9706-104">GetCurrentConsoleFont 函式</span><span class="sxs-lookup"><span data-stu-id="d9706-104">GetCurrentConsoleFont function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="d9706-105">抓取目前主控台字型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d9706-105">Retrieves information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="d9706-106">語法</span><span class="sxs-lookup"><span data-stu-id="d9706-106">Syntax</span></span>

```C
BOOL WINAPI GetCurrentConsoleFont(
  _In_  HANDLE             hConsoleOutput,
  _In_  BOOL               bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFO lpConsoleCurrentFont
);
```

## <a name="parameters"></a><span data-ttu-id="d9706-107">參數</span><span class="sxs-lookup"><span data-stu-id="d9706-107">Parameters</span></span>

<span data-ttu-id="d9706-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="d9706-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="d9706-109">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="d9706-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="d9706-110">控制代碼必須具有 **GENERIC\_READ** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="d9706-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="d9706-111">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="d9706-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="d9706-112">*bMaximumWindow* \[在\]</span><span class="sxs-lookup"><span data-stu-id="d9706-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="d9706-113">如果此參數為 **TRUE**，就會針對最大視窗大小抓取字型資訊。</span><span class="sxs-lookup"><span data-stu-id="d9706-113">If this parameter is **TRUE**, font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="d9706-114">如果此參數為 **FALSE**，則會針對目前的視窗大小抓取字型資訊。</span><span class="sxs-lookup"><span data-stu-id="d9706-114">If this parameter is **FALSE**, font information is retrieved for the current window size.</span></span>

<span data-ttu-id="d9706-115">*lpConsoleCurrentFont* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="d9706-115">*lpConsoleCurrentFont* \[out\]</span></span>  
<span data-ttu-id="d9706-116">[**主控台 \_ 字型 \_ 資訊**](console-font-info-str.md)結構的指標，此結構會接收要求的字型資訊。</span><span class="sxs-lookup"><span data-stu-id="d9706-116">A pointer to a [**CONSOLE\_FONT\_INFO**](console-font-info-str.md) structure that receives the requested font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="d9706-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="d9706-117">Return value</span></span>

<span data-ttu-id="d9706-118">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="d9706-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d9706-119">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="d9706-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d9706-120">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="d9706-120">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="d9706-121">備註</span><span class="sxs-lookup"><span data-stu-id="d9706-121">Remarks</span></span>

<span data-ttu-id="d9706-122">若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0500 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="d9706-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="d9706-123">如需詳細資訊，請參閱 [使用 Windows 標頭](/windows/win32/winprog/using-the-windows-headers)。</span><span class="sxs-lookup"><span data-stu-id="d9706-123">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="d9706-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="d9706-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="d9706-125">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="d9706-125">Minimum supported client</span></span> | <span data-ttu-id="d9706-126">\[僅限 WINDOWS XP desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="d9706-126">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="d9706-127">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="d9706-127">Minimum supported server</span></span> | <span data-ttu-id="d9706-128">僅限 Windows Server 2003 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="d9706-128">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="d9706-129">標頭</span><span class="sxs-lookup"><span data-stu-id="d9706-129">Header</span></span> | <span data-ttu-id="d9706-130">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="d9706-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="d9706-131">程式庫</span><span class="sxs-lookup"><span data-stu-id="d9706-131">Library</span></span> | <span data-ttu-id="d9706-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="d9706-132">Kernel32.lib</span></span> |
| <span data-ttu-id="d9706-133">DLL</span><span class="sxs-lookup"><span data-stu-id="d9706-133">DLL</span></span> | <span data-ttu-id="d9706-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d9706-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="d9706-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9706-135">See also</span></span>

[<span data-ttu-id="d9706-136">主控台函式</span><span class="sxs-lookup"><span data-stu-id="d9706-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d9706-137">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="d9706-137">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="d9706-138">**主控台 \_ 字型 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="d9706-138">**CONSOLE\_FONT\_INFO**</span></span>](console-font-info-str.md)

[<span data-ttu-id="d9706-139">**GetConsoleFontSize**</span><span class="sxs-lookup"><span data-stu-id="d9706-139">**GetConsoleFontSize**</span></span>](getconsolefontsize.md)
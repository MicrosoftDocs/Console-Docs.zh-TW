---
title: GetCurrentConsoleFontEx 函式
description: 請參閱 GetCurrentConsoleFontEx 函式的參考資訊，此函式會抓取有關目前使用之主控台字型的延伸資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
ms.openlocfilehash: e499cdb51a5ca71948dd40ebd3d4d151f2d71a8a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038726"
---
# <a name="getcurrentconsolefontex-function"></a><span data-ttu-id="52325-104">GetCurrentConsoleFontEx 函式</span><span class="sxs-lookup"><span data-stu-id="52325-104">GetCurrentConsoleFontEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="52325-105">抓取有關目前主控台字型的延伸資訊。</span><span class="sxs-lookup"><span data-stu-id="52325-105">Retrieves extended information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="52325-106">語法</span><span class="sxs-lookup"><span data-stu-id="52325-106">Syntax</span></span>

```C
BOOL WINAPI GetCurrentConsoleFontEx(
  _In_  HANDLE               hConsoleOutput,
  _In_  BOOL                 bMaximumWindow,
  _Out_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a><span data-ttu-id="52325-107">參數</span><span class="sxs-lookup"><span data-stu-id="52325-107">Parameters</span></span>

<span data-ttu-id="52325-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="52325-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="52325-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="52325-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="52325-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="52325-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="52325-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="52325-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="52325-112">*bMaximumWindow* \[在\]</span><span class="sxs-lookup"><span data-stu-id="52325-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="52325-113">如果此參數為 **TRUE** ，就會針對最大視窗大小抓取字型資訊。</span><span class="sxs-lookup"><span data-stu-id="52325-113">If this parameter is **TRUE** , font information is retrieved for the maximum window size.</span></span> <span data-ttu-id="52325-114">如果此參數為 **FALSE** ，則會針對目前的視窗大小抓取字型資訊。</span><span class="sxs-lookup"><span data-stu-id="52325-114">If this parameter is **FALSE** , font information is retrieved for the current window size.</span></span>

<span data-ttu-id="52325-115">*lpConsoleCurrentFontEx* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="52325-115">*lpConsoleCurrentFontEx* \[out\]</span></span>  
<span data-ttu-id="52325-116">[**主控台 \_ 字型 \_ INFOEX**](console-font-infoex.md)結構的指標，此結構會接收要求的字型資訊。</span><span class="sxs-lookup"><span data-stu-id="52325-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that receives the requested font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="52325-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="52325-117">Return value</span></span>

<span data-ttu-id="52325-118">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="52325-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="52325-119">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="52325-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="52325-120">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="52325-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="52325-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="52325-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="52325-122">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="52325-122">Minimum supported client</span></span> | <span data-ttu-id="52325-123">\[僅限 Windows Vista 桌面應用程式\]</span><span class="sxs-lookup"><span data-stu-id="52325-123">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="52325-124">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="52325-124">Minimum supported server</span></span> | <span data-ttu-id="52325-125">僅限 Windows Server 2008 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="52325-125">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="52325-126">標頭</span><span class="sxs-lookup"><span data-stu-id="52325-126">Header</span></span> | <span data-ttu-id="52325-127">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="52325-127">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="52325-128">程式庫</span><span class="sxs-lookup"><span data-stu-id="52325-128">Library</span></span> | <span data-ttu-id="52325-129">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="52325-129">Kernel32.lib</span></span> |
| <span data-ttu-id="52325-130">DLL</span><span class="sxs-lookup"><span data-stu-id="52325-130">DLL</span></span> | <span data-ttu-id="52325-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="52325-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="52325-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="52325-132">See also</span></span>

[<span data-ttu-id="52325-133">主控台功能</span><span class="sxs-lookup"><span data-stu-id="52325-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="52325-134">**主控台 \_ 字型 \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="52325-134">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)

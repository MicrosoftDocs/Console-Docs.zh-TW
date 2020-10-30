---
title: SetCurrentConsoleFontEx 函式
description: 請參閱 SetCurrentConsoleFontEx 函式的參考資訊，此函式會設定目前主控台字型的延伸資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/SetCurrentConsoleFontEx
- wincon/SetCurrentConsoleFontEx
- SetCurrentConsoleFontEx
MS-HAID:
- base.setcurrentconsolefontex
- consoles.setcurrentconsolefontex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: fbc31e2a-31df-4e9e-9f61-35a4ff812f8f
topic_type:
- apiref
api_name:
- SetCurrentConsoleFontEx
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 1ba89b90a0362261aafbe5ac6462224b3c0172dc
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037048"
---
# <a name="setcurrentconsolefontex-function"></a><span data-ttu-id="baec2-104">SetCurrentConsoleFontEx 函式</span><span class="sxs-lookup"><span data-stu-id="baec2-104">SetCurrentConsoleFontEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="baec2-105">設定目前主控台字型的延伸資訊。</span><span class="sxs-lookup"><span data-stu-id="baec2-105">Sets extended information about the current console font.</span></span>

## <a name="syntax"></a><span data-ttu-id="baec2-106">語法</span><span class="sxs-lookup"><span data-stu-id="baec2-106">Syntax</span></span>

```C
BOOL WINAPI SetCurrentConsoleFontEx(
  _In_ HANDLE               hConsoleOutput,
  _In_ BOOL                 bMaximumWindow,
  _In_ PCONSOLE_FONT_INFOEX lpConsoleCurrentFontEx
);
```

## <a name="parameters"></a><span data-ttu-id="baec2-107">參數</span><span class="sxs-lookup"><span data-stu-id="baec2-107">Parameters</span></span>

<span data-ttu-id="baec2-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="baec2-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="baec2-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="baec2-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="baec2-110">控制碼必須有 **一般 \_ 寫入** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="baec2-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="baec2-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="baec2-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="baec2-112">*bMaximumWindow* \[在\]</span><span class="sxs-lookup"><span data-stu-id="baec2-112">*bMaximumWindow* \[in\]</span></span>  
<span data-ttu-id="baec2-113">如果此參數為 **TRUE** ，就會為最大視窗大小設定字型資訊。</span><span class="sxs-lookup"><span data-stu-id="baec2-113">If this parameter is **TRUE** , font information is set for the maximum window size.</span></span> <span data-ttu-id="baec2-114">如果此參數為 **FALSE** ，則會針對目前的視窗大小設定字型資訊。</span><span class="sxs-lookup"><span data-stu-id="baec2-114">If this parameter is **FALSE** , font information is set for the current window size.</span></span>

<span data-ttu-id="baec2-115">*lpConsoleCurrentFontEx* \[在\]</span><span class="sxs-lookup"><span data-stu-id="baec2-115">*lpConsoleCurrentFontEx* \[in\]</span></span>  
<span data-ttu-id="baec2-116">[**主控台 \_ 字型 \_ INFOEX**](console-font-infoex.md)結構的指標，其中包含字型資訊。</span><span class="sxs-lookup"><span data-stu-id="baec2-116">A pointer to a [**CONSOLE\_FONT\_INFOEX**](console-font-infoex.md) structure that contains the font information.</span></span>

## <a name="return-value"></a><span data-ttu-id="baec2-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="baec2-117">Return value</span></span>

<span data-ttu-id="baec2-118">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="baec2-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="baec2-119">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="baec2-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="baec2-120">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="baec2-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="baec2-121">備註</span><span class="sxs-lookup"><span data-stu-id="baec2-121">Remarks</span></span>

<span data-ttu-id="baec2-122">若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0500 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="baec2-122">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="baec2-123">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="baec2-123">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="baec2-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="baec2-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="baec2-125">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="baec2-125">Minimum supported client</span></span> | <span data-ttu-id="baec2-126">\[僅限 Windows Vista 桌面應用程式\]</span><span class="sxs-lookup"><span data-stu-id="baec2-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="baec2-127">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="baec2-127">Minimum supported server</span></span> | <span data-ttu-id="baec2-128">僅限 Windows Server 2008 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="baec2-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="baec2-129">標頭</span><span class="sxs-lookup"><span data-stu-id="baec2-129">Header</span></span> | <span data-ttu-id="baec2-130">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="baec2-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="baec2-131">程式庫</span><span class="sxs-lookup"><span data-stu-id="baec2-131">Library</span></span> | <span data-ttu-id="baec2-132">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="baec2-132">Kernel32.lib</span></span> |
| <span data-ttu-id="baec2-133">DLL</span><span class="sxs-lookup"><span data-stu-id="baec2-133">DLL</span></span> | <span data-ttu-id="baec2-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="baec2-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="baec2-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="baec2-135">See also</span></span>

[<span data-ttu-id="baec2-136">主控台功能</span><span class="sxs-lookup"><span data-stu-id="baec2-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="baec2-137">**主控台 \_ 字型 \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="baec2-137">**CONSOLE\_FONT\_INFOEX**</span></span>](console-font-infoex.md)

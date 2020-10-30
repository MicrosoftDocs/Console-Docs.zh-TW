---
title: GetConsoleOriginalTitle 函式
description: 請參閱 GetConsoleOriginalTitle 函式的參考資訊，此函式會抓取目前主控台視窗的原始標題。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
ms.openlocfilehash: ad12ff7b931b6bbc36a7fb0e9e0ee2ac3512a1f5
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037996"
---
# <a name="getconsoleoriginaltitle-function"></a><span data-ttu-id="2d31e-104">GetConsoleOriginalTitle 函式</span><span class="sxs-lookup"><span data-stu-id="2d31e-104">GetConsoleOriginalTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="2d31e-105">抓取目前主控台視窗的原始標題。</span><span class="sxs-lookup"><span data-stu-id="2d31e-105">Retrieves the original title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="2d31e-106">語法</span><span class="sxs-lookup"><span data-stu-id="2d31e-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleOriginalTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a><span data-ttu-id="2d31e-107">參數</span><span class="sxs-lookup"><span data-stu-id="2d31e-107">Parameters</span></span>

<span data-ttu-id="2d31e-108">*lpConsoleTitle* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="2d31e-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="2d31e-109">緩衝區的指標，此緩衝區會接收以 null 終止的字串，其中包含原始標題。</span><span class="sxs-lookup"><span data-stu-id="2d31e-109">A pointer to a buffer that receives a null-terminated string containing the original title.</span></span>

<span data-ttu-id="2d31e-110">*nSize* \[在\]</span><span class="sxs-lookup"><span data-stu-id="2d31e-110">*nSize* \[in\]</span></span>  
<span data-ttu-id="2d31e-111">*LpConsoleTitle* 緩衝區的大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="2d31e-111">The size of the *lpConsoleTitle* buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="2d31e-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="2d31e-112">Return value</span></span>

<span data-ttu-id="2d31e-113">如果函式成功，傳回值就是複製到緩衝區的字串長度（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="2d31e-113">If the function succeeds, the return value is the length of the string copied to the buffer, in characters.</span></span>

<span data-ttu-id="2d31e-114">如果緩衝區不夠大，無法儲存標題，則傳回值為零，而 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) 會傳回 **錯誤 \_ 成功** 。</span><span class="sxs-lookup"><span data-stu-id="2d31e-114">If the buffer is not large enough to store the title, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns **ERROR\_SUCCESS** .</span></span>

<span data-ttu-id="2d31e-115">如果函式失敗，則傳回值為零，而 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) 會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="2d31e-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2d31e-116">備註</span><span class="sxs-lookup"><span data-stu-id="2d31e-116">Remarks</span></span>

<span data-ttu-id="2d31e-117">若要設定主控台視窗的標題，請使用 [**SetConsoleTitle**](setconsoletitle.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="2d31e-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="2d31e-118">若要取得目前的標題字串，請使用 [**GetConsoleTitle**](getconsoletitle.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="2d31e-118">To retrieve the current title string, use the [**GetConsoleTitle**](getconsoletitle.md) function.</span></span>

<span data-ttu-id="2d31e-119">若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0600 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="2d31e-119">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0600 or later.</span></span> <span data-ttu-id="2d31e-120">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="2d31e-120">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

> [!TIP]
> <span data-ttu-id="2d31e-121">不建議使用此 API，也不會有對等的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="2d31e-121">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="2d31e-122">這種決策刻意將 Windows 平臺與其他作業系統對齊。</span><span class="sxs-lookup"><span data-stu-id="2d31e-122">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="2d31e-123">使用此 API 時，透過跨平臺公用程式和傳輸（如 SSH）的應用程式遠端執行可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="2d31e-123">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="2d31e-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="2d31e-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="2d31e-125">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="2d31e-125">Minimum supported client</span></span> | <span data-ttu-id="2d31e-126">\[僅限 Windows Vista 桌面應用程式\]</span><span class="sxs-lookup"><span data-stu-id="2d31e-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="2d31e-127">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="2d31e-127">Minimum supported server</span></span> | <span data-ttu-id="2d31e-128">僅限 Windows Server 2008 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="2d31e-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="2d31e-129">標頭</span><span class="sxs-lookup"><span data-stu-id="2d31e-129">Header</span></span> | <span data-ttu-id="2d31e-130">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="2d31e-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="2d31e-131">程式庫</span><span class="sxs-lookup"><span data-stu-id="2d31e-131">Library</span></span> | <span data-ttu-id="2d31e-132">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="2d31e-132">Kernel32.lib</span></span> |
| <span data-ttu-id="2d31e-133">DLL</span><span class="sxs-lookup"><span data-stu-id="2d31e-133">DLL</span></span> | <span data-ttu-id="2d31e-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2d31e-134">Kernel32.dll</span></span> |
| <span data-ttu-id="2d31e-135">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="2d31e-135">Unicode and ANSI names</span></span> | <span data-ttu-id="2d31e-136">**GetConsoleOriginalTitleW** (Unicode) 和 **GetConsoleOriginalTitleA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="2d31e-136">**GetConsoleOriginalTitleW** (Unicode) and **GetConsoleOriginalTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="2d31e-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="2d31e-137">See also</span></span>

[<span data-ttu-id="2d31e-138">主控台功能</span><span class="sxs-lookup"><span data-stu-id="2d31e-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2d31e-139">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="2d31e-139">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="2d31e-140">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="2d31e-140">**SetConsoleTitle**</span></span>](setconsoletitle.md)

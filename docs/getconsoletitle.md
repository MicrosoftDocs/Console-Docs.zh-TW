---
title: GetConsoleTitle 函式
description: 抓取目前主控台視窗之標題的標題和大小。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- base.getconsoletitle
- consoles.getconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79
topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
ms.openlocfilehash: 23b52ba1d5dde40ef842297249fdd2f87cebcb12
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037876"
---
# <a name="getconsoletitle-function"></a><span data-ttu-id="97c40-104">GetConsoleTitle 函式</span><span class="sxs-lookup"><span data-stu-id="97c40-104">GetConsoleTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="97c40-105">抓取目前主控台視窗的標題。</span><span class="sxs-lookup"><span data-stu-id="97c40-105">Retrieves the title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="97c40-106">語法</span><span class="sxs-lookup"><span data-stu-id="97c40-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

## <a name="parameters"></a><span data-ttu-id="97c40-107">參數</span><span class="sxs-lookup"><span data-stu-id="97c40-107">Parameters</span></span>

<span data-ttu-id="97c40-108">*lpConsoleTitle* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="97c40-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="97c40-109">緩衝區的指標，此緩衝區會接收包含標題之以 null 結束的字串。</span><span class="sxs-lookup"><span data-stu-id="97c40-109">A pointer to a buffer that receives a null-terminated string containing the title.</span></span> <span data-ttu-id="97c40-110">如果緩衝區太小而無法儲存標題，此函式會將標題的任意多個字元儲存為緩衝區中容納的字元，並以 null 結束字元結尾。</span><span class="sxs-lookup"><span data-stu-id="97c40-110">If the buffer is too small to store the title, the function stores as many characters of the title as will fit in the buffer, ending with a null terminator.</span></span>

<span data-ttu-id="97c40-111">*nSize* \[在\]</span><span class="sxs-lookup"><span data-stu-id="97c40-111">*nSize* \[in\]</span></span>  
<span data-ttu-id="97c40-112">*LpConsoleTitle* 參數所指向的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="97c40-112">The size of the buffer pointed to by the *lpConsoleTitle* parameter, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="97c40-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="97c40-113">Return value</span></span>

<span data-ttu-id="97c40-114">如果函式成功，則傳回值為主控台視窗標題的長度（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="97c40-114">If the function succeeds, the return value is the length of the console window's title, in characters.</span></span>

<span data-ttu-id="97c40-115">如果函式失敗，則傳回值為零，而 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) 會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="97c40-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="97c40-116">備註</span><span class="sxs-lookup"><span data-stu-id="97c40-116">Remarks</span></span>

<span data-ttu-id="97c40-117">若要設定主控台視窗的標題，請使用 [**SetConsoleTitle**](setconsoletitle.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="97c40-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="97c40-118">若要取出原始的標題字串，請使用 [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="97c40-118">To retrieve the original title string, use the [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="97c40-119">不建議使用此 API，也不會有對等的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="97c40-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="97c40-120">這種決策刻意將 Windows 平臺與其他作業系統對齊。</span><span class="sxs-lookup"><span data-stu-id="97c40-120">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="97c40-121">使用此 API 時，透過跨平臺公用程式和傳輸（如 SSH）的應用程式遠端執行可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="97c40-121">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="examples"></a><span data-ttu-id="97c40-122">範例</span><span class="sxs-lookup"><span data-stu-id="97c40-122">Examples</span></span>

<span data-ttu-id="97c40-123">如需範例，請參閱 [**SetConsoleTitle**](setconsoletitle.md)。</span><span class="sxs-lookup"><span data-stu-id="97c40-123">For an example, see [**SetConsoleTitle**](setconsoletitle.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="97c40-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="97c40-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="97c40-125">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="97c40-125">Minimum supported client</span></span> | <span data-ttu-id="97c40-126">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="97c40-126">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="97c40-127">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="97c40-127">Minimum supported server</span></span> | <span data-ttu-id="97c40-128">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="97c40-128">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="97c40-129">標頭</span><span class="sxs-lookup"><span data-stu-id="97c40-129">Header</span></span> | <span data-ttu-id="97c40-130">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="97c40-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="97c40-131">程式庫</span><span class="sxs-lookup"><span data-stu-id="97c40-131">Library</span></span> | <span data-ttu-id="97c40-132">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="97c40-132">Kernel32.lib</span></span> |
| <span data-ttu-id="97c40-133">DLL</span><span class="sxs-lookup"><span data-stu-id="97c40-133">DLL</span></span> | <span data-ttu-id="97c40-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="97c40-134">Kernel32.dll</span></span> |
| <span data-ttu-id="97c40-135">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="97c40-135">Unicode and ANSI names</span></span> | <span data-ttu-id="97c40-136">**GetConsoleTitleW** (Unicode) 和 **GetConsoleTitleA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="97c40-136">**GetConsoleTitleW** (Unicode) and **GetConsoleTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="97c40-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="97c40-137">See also</span></span>

[<span data-ttu-id="97c40-138">主控台功能</span><span class="sxs-lookup"><span data-stu-id="97c40-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="97c40-139">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="97c40-139">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="97c40-140">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="97c40-140">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="97c40-141">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="97c40-141">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="97c40-142">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="97c40-142">**SetConsoleTitle**</span></span>](setconsoletitle.md)

---
title: GetConsoleFontSize 函式
description: 抓取指定的主控台螢幕緩衝區所使用的字型大小。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetConsoleFontSize
- wincon/GetConsoleFontSize
- GetConsoleFontSize
MS-HAID:
- '\_win32\_getconsolefontsize'
- base.getconsolefontsize
- consoles.getconsolefontsize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 51b1f58d-b3fb-4e09-8398-671b3959bb01
topic_type:
- apiref
api_name:
- GetConsoleFontSize
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 96086720ee2c4ae787d2b52eee5439d54f081b8e
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358338"
---
# <a name="getconsolefontsize-function"></a><span data-ttu-id="f2240-104">GetConsoleFontSize 函式</span><span class="sxs-lookup"><span data-stu-id="f2240-104">GetConsoleFontSize function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="f2240-105">抓取指定的主控台螢幕緩衝區所使用的字型大小。</span><span class="sxs-lookup"><span data-stu-id="f2240-105">Retrieves the size of the font used by the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2240-106">語法</span><span class="sxs-lookup"><span data-stu-id="f2240-106">Syntax</span></span>

```C
COORD WINAPI GetConsoleFontSize(
  _In_ HANDLE hConsoleOutput,
  _In_ DWORD  nFont
);
```

## <a name="parameters"></a><span data-ttu-id="f2240-107">參數</span><span class="sxs-lookup"><span data-stu-id="f2240-107">Parameters</span></span>

<span data-ttu-id="f2240-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f2240-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="f2240-109">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="f2240-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="f2240-110">控制代碼必須具有 **GENERIC\_READ** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="f2240-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="f2240-111">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="f2240-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="f2240-112">*nFont* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f2240-112">*nFont* \[in\]</span></span>  
<span data-ttu-id="f2240-113">要取出其大小的字型索引。</span><span class="sxs-lookup"><span data-stu-id="f2240-113">The index of the font whose size is to be retrieved.</span></span> <span data-ttu-id="f2240-114">藉由呼叫 [**GetCurrentConsoleFont**](getcurrentconsolefont.md) 函數來取得此索引。</span><span class="sxs-lookup"><span data-stu-id="f2240-114">This index is obtained by calling the [**GetCurrentConsoleFont**](getcurrentconsolefont.md) function.</span></span>

## <a name="return-value"></a><span data-ttu-id="f2240-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="f2240-115">Return value</span></span>

<span data-ttu-id="f2240-116">如果函式成功，則傳回值是 [**COORD**](coord-str.md) 結構，其中包含字型中每個字元的寬度和高度（以邏輯單位表示）。</span><span class="sxs-lookup"><span data-stu-id="f2240-116">If the function succeeds, the return value is a [**COORD**](coord-str.md) structure that contains the width and height of each character in the font, in logical units.</span></span> <span data-ttu-id="f2240-117">**X** 成員包含寬度，而 **Y** 成員包含高度。</span><span class="sxs-lookup"><span data-stu-id="f2240-117">The **X** member contains the width, while the **Y** member contains the height.</span></span>

<span data-ttu-id="f2240-118">如果函式失敗，則寬度和高度為零。</span><span class="sxs-lookup"><span data-stu-id="f2240-118">If the function fails, the width and the height are zero.</span></span> <span data-ttu-id="f2240-119">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="f2240-119">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="f2240-120">備註</span><span class="sxs-lookup"><span data-stu-id="f2240-120">Remarks</span></span>

<span data-ttu-id="f2240-121">若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0500 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="f2240-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="f2240-122">如需詳細資訊，請參閱 [使用 Windows 標頭](/windows/win32/winprog/using-the-windows-headers)。</span><span class="sxs-lookup"><span data-stu-id="f2240-122">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="f2240-123">規格需求</span><span class="sxs-lookup"><span data-stu-id="f2240-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="f2240-124">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="f2240-124">Minimum supported client</span></span> | <span data-ttu-id="f2240-125">\[僅限 WINDOWS XP desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="f2240-125">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="f2240-126">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="f2240-126">Minimum supported server</span></span> | <span data-ttu-id="f2240-127">僅限 Windows Server 2003 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="f2240-127">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="f2240-128">標頭</span><span class="sxs-lookup"><span data-stu-id="f2240-128">Header</span></span> | <span data-ttu-id="f2240-129">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="f2240-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="f2240-130">程式庫</span><span class="sxs-lookup"><span data-stu-id="f2240-130">Library</span></span> | <span data-ttu-id="f2240-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="f2240-131">Kernel32.lib</span></span> |
| <span data-ttu-id="f2240-132">DLL</span><span class="sxs-lookup"><span data-stu-id="f2240-132">DLL</span></span> | <span data-ttu-id="f2240-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f2240-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="f2240-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2240-134">See also</span></span>

[<span data-ttu-id="f2240-135">主控台函式</span><span class="sxs-lookup"><span data-stu-id="f2240-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f2240-136">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="f2240-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="f2240-137">**COORD**</span><span class="sxs-lookup"><span data-stu-id="f2240-137">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="f2240-138">**GetCurrentConsoleFont**</span><span class="sxs-lookup"><span data-stu-id="f2240-138">**GetCurrentConsoleFont**</span></span>](getcurrentconsolefont.md)
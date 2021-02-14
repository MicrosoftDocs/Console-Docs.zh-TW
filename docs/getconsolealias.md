---
title: GetConsoleAlias 函式
description: 抓取指定之主控台別名的文字和可執行檔的名稱。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetConsoleAlias
- wincon/GetConsoleAlias
- GetConsoleAlias
- consoleapi3/GetConsoleAliasA
- wincon/GetConsoleAliasA
- GetConsoleAliasA
- consoleapi3/GetConsoleAliasW
- wincon/GetConsoleAliasW
- GetConsoleAliasW
MS-HAID:
- base.getconsolealias
- consoles.getconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e8514f24-8121-4fad-94bb-c9eedf7a700d
topic_type:
- apiref
api_name:
- GetConsoleAlias
- GetConsoleAliasA
- GetConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: d3706ddb86c270aeaf22f46e08e5381c79fea0bb
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357538"
---
# <a name="getconsolealias-function"></a><span data-ttu-id="4a213-104">GetConsoleAlias 函式</span><span class="sxs-lookup"><span data-stu-id="4a213-104">GetConsoleAlias function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="4a213-105">抓取指定的主控台別名和可執行檔的文字。</span><span class="sxs-lookup"><span data-stu-id="4a213-105">Retrieves the text for the specified console alias and executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="4a213-106">語法</span><span class="sxs-lookup"><span data-stu-id="4a213-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAlias(
  _In_  LPTSTR lpSource,
  _Out_ LPTSTR lpTargetBuffer,
  _In_  DWORD  TargetBufferLength,
  _In_  LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="4a213-107">參數</span><span class="sxs-lookup"><span data-stu-id="4a213-107">Parameters</span></span>

<span data-ttu-id="4a213-108">*lpSource* \[在\]</span><span class="sxs-lookup"><span data-stu-id="4a213-108">*lpSource* \[in\]</span></span>  
<span data-ttu-id="4a213-109">要取出其文字的主控台別名。</span><span class="sxs-lookup"><span data-stu-id="4a213-109">The console alias whose text is to be retrieved.</span></span>

<span data-ttu-id="4a213-110">*lpTargetBuffer* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="4a213-110">*lpTargetBuffer* \[out\]</span></span>  
<span data-ttu-id="4a213-111">接收與主控台別名相關聯之文字的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="4a213-111">A pointer to a buffer that receives the text associated with the console alias.</span></span>

<span data-ttu-id="4a213-112">*TargetBufferLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="4a213-112">*TargetBufferLength* \[in\]</span></span>  
<span data-ttu-id="4a213-113">*LpTargetBuffer* 所指向的緩衝區大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="4a213-113">The size of the buffer pointed to by *lpTargetBuffer*, in bytes.</span></span>

<span data-ttu-id="4a213-114">*lpExeName* \[在\]</span><span class="sxs-lookup"><span data-stu-id="4a213-114">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="4a213-115">可執行檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="4a213-115">The name of the executable file.</span></span>

## <a name="return-value"></a><span data-ttu-id="4a213-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="4a213-116">Return value</span></span>

<span data-ttu-id="4a213-117">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="4a213-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4a213-118">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="4a213-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4a213-119">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="4a213-119">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="4a213-120">備註</span><span class="sxs-lookup"><span data-stu-id="4a213-120">Remarks</span></span>

<span data-ttu-id="4a213-121">若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0501 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="4a213-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="4a213-122">如需詳細資訊，請參閱 [使用 Windows 標頭](/windows/win32/winprog/using-the-windows-headers)。</span><span class="sxs-lookup"><span data-stu-id="4a213-122">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="4a213-123">規格需求</span><span class="sxs-lookup"><span data-stu-id="4a213-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4a213-124">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="4a213-124">Minimum supported client</span></span> | <span data-ttu-id="4a213-125">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="4a213-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="4a213-126">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="4a213-126">Minimum supported server</span></span> | <span data-ttu-id="4a213-127">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="4a213-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="4a213-128">標頭</span><span class="sxs-lookup"><span data-stu-id="4a213-128">Header</span></span> | <span data-ttu-id="4a213-129">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="4a213-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="4a213-130">程式庫</span><span class="sxs-lookup"><span data-stu-id="4a213-130">Library</span></span> | <span data-ttu-id="4a213-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="4a213-131">Kernel32.lib</span></span> |
| <span data-ttu-id="4a213-132">DLL</span><span class="sxs-lookup"><span data-stu-id="4a213-132">DLL</span></span> | <span data-ttu-id="4a213-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4a213-133">Kernel32.dll</span></span> |
| <span data-ttu-id="4a213-134">Unicode 與 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="4a213-134">Unicode and ANSI names</span></span> | <span data-ttu-id="4a213-135">**GetConsoleAliasW** (Unicode) 和 **GetConsoleAliasA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="4a213-135">**GetConsoleAliasW** (Unicode) and **GetConsoleAliasA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="4a213-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a213-136">See also</span></span>

[<span data-ttu-id="4a213-137">主控台別名</span><span class="sxs-lookup"><span data-stu-id="4a213-137">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="4a213-138">主控台函式</span><span class="sxs-lookup"><span data-stu-id="4a213-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4a213-139">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="4a213-139">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="4a213-140">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="4a213-140">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="4a213-141">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="4a213-141">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
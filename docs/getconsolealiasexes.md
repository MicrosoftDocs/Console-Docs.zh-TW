---
title: GetConsoleAliasExes 函式
description: 使用定義的主控台別名，抓取所有可執行檔的名稱。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetConsoleAliasExes
- wincon/GetConsoleAliasExes
- GetConsoleAliasExes
- consoleapi3/GetConsoleAliasExesA
- wincon/GetConsoleAliasExesA
- GetConsoleAliasExesA
- consoleapi3/GetConsoleAliasExesW
- wincon/GetConsoleAliasExesW
- GetConsoleAliasExesW
MS-HAID:
- base.getconsolealiasexes
- consoles.getconsolealiasexes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c229de09-cfa6-4829-9c9a-8ff63500eaf4
topic_type:
- apiref
api_name:
- GetConsoleAliasExes
- GetConsoleAliasExesA
- GetConsoleAliasExesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 1a97df0c22f084389e9bd6df1c4a2e8863090b45
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357490"
---
# <a name="getconsolealiasexes-function"></a><span data-ttu-id="550e8-104">GetConsoleAliasExes 函式</span><span class="sxs-lookup"><span data-stu-id="550e8-104">GetConsoleAliasExes function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="550e8-105">使用定義的主控台別名，抓取所有可執行檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="550e8-105">Retrieves the names of all executable files with console aliases defined.</span></span>

## <a name="syntax"></a><span data-ttu-id="550e8-106">語法</span><span class="sxs-lookup"><span data-stu-id="550e8-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasExes(
  _Out_ LPTSTR lpExeNameBuffer,
  _In_  DWORD  ExeNameBufferLength
);
```

## <a name="parameters"></a><span data-ttu-id="550e8-107">參數</span><span class="sxs-lookup"><span data-stu-id="550e8-107">Parameters</span></span>

<span data-ttu-id="550e8-108">*lpExeNameBuffer* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="550e8-108">*lpExeNameBuffer* \[out\]</span></span>  
<span data-ttu-id="550e8-109">接收可執行檔名稱之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="550e8-109">A pointer to a buffer that receives the names of the executable files.</span></span>

<span data-ttu-id="550e8-110">*ExeNameBufferLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="550e8-110">*ExeNameBufferLength* \[in\]</span></span>  
<span data-ttu-id="550e8-111">*LpExeNameBuffer* 所指向的緩衝區大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="550e8-111">The size of the buffer pointed to by *lpExeNameBuffer*, in bytes.</span></span>

## <a name="return-value"></a><span data-ttu-id="550e8-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="550e8-112">Return value</span></span>

<span data-ttu-id="550e8-113">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="550e8-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="550e8-114">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="550e8-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="550e8-115">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="550e8-115">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="550e8-116">備註</span><span class="sxs-lookup"><span data-stu-id="550e8-116">Remarks</span></span>

<span data-ttu-id="550e8-117">若要判斷 *lpExeNameBuffer* 緩衝區所需的大小，請使用 [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="550e8-117">To determine the required size for the *lpExeNameBuffer* buffer, use the [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) function.</span></span>

<span data-ttu-id="550e8-118">若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0501 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="550e8-118">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="550e8-119">如需詳細資訊，請參閱 [使用 Windows 標頭](/windows/win32/winprog/using-the-windows-headers)。</span><span class="sxs-lookup"><span data-stu-id="550e8-119">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="550e8-120">規格需求</span><span class="sxs-lookup"><span data-stu-id="550e8-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="550e8-121">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="550e8-121">Minimum supported client</span></span> | <span data-ttu-id="550e8-122">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="550e8-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="550e8-123">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="550e8-123">Minimum supported server</span></span> | <span data-ttu-id="550e8-124">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="550e8-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="550e8-125">標頭</span><span class="sxs-lookup"><span data-stu-id="550e8-125">Header</span></span> | <span data-ttu-id="550e8-126">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="550e8-126">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="550e8-127">程式庫</span><span class="sxs-lookup"><span data-stu-id="550e8-127">Library</span></span> | <span data-ttu-id="550e8-128">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="550e8-128">Kernel32.lib</span></span> |
| <span data-ttu-id="550e8-129">DLL</span><span class="sxs-lookup"><span data-stu-id="550e8-129">DLL</span></span> | <span data-ttu-id="550e8-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="550e8-130">Kernel32.dll</span></span> |
| <span data-ttu-id="550e8-131">Unicode 與 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="550e8-131">Unicode and ANSI names</span></span> | <span data-ttu-id="550e8-132">**GetConsoleAliasExesW** (Unicode) 和 **GetConsoleAliasExesA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="550e8-132">**GetConsoleAliasExesW** (Unicode) and **GetConsoleAliasExesA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="550e8-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="550e8-133">See also</span></span>

[<span data-ttu-id="550e8-134">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="550e8-134">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="550e8-135">主控台別名</span><span class="sxs-lookup"><span data-stu-id="550e8-135">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="550e8-136">主控台函式</span><span class="sxs-lookup"><span data-stu-id="550e8-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="550e8-137">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="550e8-137">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="550e8-138">**GetConsoleAliasExesLength**</span><span class="sxs-lookup"><span data-stu-id="550e8-138">**GetConsoleAliasExesLength**</span></span>](getconsolealiasexeslength.md)

[<span data-ttu-id="550e8-139">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="550e8-139">**GetConsoleAliases**</span></span>](getconsolealiases.md)
---
title: GetConsoleAliasesLength 函式
description: 抓取 GetConsoleAliases 函式所使用之緩衝區的必要大小。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetConsoleAliasesLength
- wincon/GetConsoleAliasesLength
- GetConsoleAliasesLength
- consoleapi3/GetConsoleAliasesLengthA
- wincon/GetConsoleAliasesLengthA
- GetConsoleAliasesLengthA
- consoleapi3/GetConsoleAliasesLengthW
- wincon/GetConsoleAliasesLengthW
- GetConsoleAliasesLengthW
MS-HAID:
- base.getconsolealiaseslength
- consoles.getconsolealiaseslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 29e49eba-0864-4ed7-af82-1ba639261c40
topic_type:
- apiref
api_name:
- GetConsoleAliasesLength
- GetConsoleAliasesLengthA
- GetConsoleAliasesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 78f9d718c960478e491b76a12f2a670c03529242
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357491"
---
# <a name="getconsolealiaseslength-function"></a><span data-ttu-id="73879-104">GetConsoleAliasesLength 函式</span><span class="sxs-lookup"><span data-stu-id="73879-104">GetConsoleAliasesLength function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="73879-105">抓取 [**GetConsoleAliases**](getconsolealiases.md) 函式所使用之緩衝區的必要大小。</span><span class="sxs-lookup"><span data-stu-id="73879-105">Retrieves the required size for the buffer used by the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="73879-106">語法</span><span class="sxs-lookup"><span data-stu-id="73879-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasesLength(
  _In_ LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="73879-107">參數</span><span class="sxs-lookup"><span data-stu-id="73879-107">Parameters</span></span>

<span data-ttu-id="73879-108">*lpExeName* \[在\]</span><span class="sxs-lookup"><span data-stu-id="73879-108">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="73879-109">要取出其主控台別名的可執行檔名稱。</span><span class="sxs-lookup"><span data-stu-id="73879-109">The name of the executable file whose console aliases are to be retrieved.</span></span>

## <a name="return-value"></a><span data-ttu-id="73879-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="73879-110">Return value</span></span>

<span data-ttu-id="73879-111">儲存這個可執行檔所定義之所有主控台別名所需的緩衝區大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="73879-111">The size of the buffer required to store all console aliases defined for this executable file, in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="73879-112">備註</span><span class="sxs-lookup"><span data-stu-id="73879-112">Remarks</span></span>

<span data-ttu-id="73879-113">若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0501 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="73879-113">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="73879-114">如需詳細資訊，請參閱 [使用 Windows 標頭](/windows/win32/winprog/using-the-windows-headers)。</span><span class="sxs-lookup"><span data-stu-id="73879-114">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="73879-115">規格需求</span><span class="sxs-lookup"><span data-stu-id="73879-115">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="73879-116">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="73879-116">Minimum supported client</span></span> | <span data-ttu-id="73879-117">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="73879-117">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="73879-118">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="73879-118">Minimum supported server</span></span> | <span data-ttu-id="73879-119">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="73879-119">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="73879-120">標頭</span><span class="sxs-lookup"><span data-stu-id="73879-120">Header</span></span> | <span data-ttu-id="73879-121">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="73879-121">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="73879-122">程式庫</span><span class="sxs-lookup"><span data-stu-id="73879-122">Library</span></span> | <span data-ttu-id="73879-123">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="73879-123">Kernel32.lib</span></span> |
| <span data-ttu-id="73879-124">DLL</span><span class="sxs-lookup"><span data-stu-id="73879-124">DLL</span></span> | <span data-ttu-id="73879-125">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="73879-125">Kernel32.dll</span></span> |
| <span data-ttu-id="73879-126">Unicode 與 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="73879-126">Unicode and ANSI names</span></span> | <span data-ttu-id="73879-127">**GetConsoleAliasesLengthW** (Unicode) 和 **GetConsoleAliasesLengthA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="73879-127">**GetConsoleAliasesLengthW** (Unicode) and **GetConsoleAliasesLengthA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="73879-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73879-128">See also</span></span>

[<span data-ttu-id="73879-129">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="73879-129">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="73879-130">主控台別名</span><span class="sxs-lookup"><span data-stu-id="73879-130">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="73879-131">主控台函式</span><span class="sxs-lookup"><span data-stu-id="73879-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="73879-132">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="73879-132">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="73879-133">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="73879-133">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="73879-134">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="73879-134">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
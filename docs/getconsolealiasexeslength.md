---
title: GetConsoleAliasExesLength 函式
description: 抓取 GetConsoleAliasExes 函式所使用之緩衝區的必要大小。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapie/GetConsoleAliasExesLength
- wincon/GetConsoleAliasExesLength
- GetConsoleAliasExesLength
- consoleapie/GetConsoleAliasExesLengthA
- wincon/GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthA
- consoleapie/GetConsoleAliasExesLengthW
- wincon/GetConsoleAliasExesLengthW
- GetConsoleAliasExesLengthW
MS-HAID:
- base.getconsolealiasexeslength
- consoles.getconsolealiasexeslength
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4f23bbb1-3e43-47a9-b91a-e91529b07fb5
topic_type:
- apiref
api_name:
- GetConsoleAliasExesLength
- GetConsoleAliasExesLengthA
- GetConsoleAliasExesLengthW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 4285bb64e919851a38494383a440afa6b94c8032
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358468"
---
# <a name="getconsolealiasexeslength-function"></a><span data-ttu-id="2d7d3-104">GetConsoleAliasExesLength 函式</span><span class="sxs-lookup"><span data-stu-id="2d7d3-104">GetConsoleAliasExesLength function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="2d7d3-105">抓取 [**GetConsoleAliasExes**](getconsolealiasexes.md) 函式所使用之緩衝區的必要大小。</span><span class="sxs-lookup"><span data-stu-id="2d7d3-105">Retrieves the required size for the buffer used by the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.</span></span>

## <a name="syntax"></a><span data-ttu-id="2d7d3-106">語法</span><span class="sxs-lookup"><span data-stu-id="2d7d3-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliasExesLength(void);
```

## <a name="parameters"></a><span data-ttu-id="2d7d3-107">參數</span><span class="sxs-lookup"><span data-stu-id="2d7d3-107">Parameters</span></span>

<span data-ttu-id="2d7d3-108">此函式沒有參數。</span><span class="sxs-lookup"><span data-stu-id="2d7d3-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="2d7d3-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="2d7d3-109">Return value</span></span>

<span data-ttu-id="2d7d3-110">儲存所有已定義主控台別名之可執行檔的名稱所需的緩衝區大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="2d7d3-110">The size of the buffer required to store the names of all executable files that have console aliases defined, in bytes.</span></span>

## <a name="remarks"></a><span data-ttu-id="2d7d3-111">備註</span><span class="sxs-lookup"><span data-stu-id="2d7d3-111">Remarks</span></span>

<span data-ttu-id="2d7d3-112">若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0501 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="2d7d3-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="2d7d3-113">如需詳細資訊，請參閱 [使用 Windows 標頭](/windows/win32/winprog/using-the-windows-headers)。</span><span class="sxs-lookup"><span data-stu-id="2d7d3-113">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="2d7d3-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="2d7d3-114">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="2d7d3-115">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="2d7d3-115">Minimum supported client</span></span> | <span data-ttu-id="2d7d3-116">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="2d7d3-116">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="2d7d3-117">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="2d7d3-117">Minimum supported server</span></span> | <span data-ttu-id="2d7d3-118">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="2d7d3-118">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="2d7d3-119">標頭</span><span class="sxs-lookup"><span data-stu-id="2d7d3-119">Header</span></span> | <span data-ttu-id="2d7d3-120">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="2d7d3-120">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="2d7d3-121">程式庫</span><span class="sxs-lookup"><span data-stu-id="2d7d3-121">Library</span></span> | <span data-ttu-id="2d7d3-122">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="2d7d3-122">Kernel32.lib</span></span> |
| <span data-ttu-id="2d7d3-123">DLL</span><span class="sxs-lookup"><span data-stu-id="2d7d3-123">DLL</span></span> | <span data-ttu-id="2d7d3-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2d7d3-124">Kernel32.dll</span></span> |
| <span data-ttu-id="2d7d3-125">Unicode 與 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="2d7d3-125">Unicode and ANSI names</span></span> | <span data-ttu-id="2d7d3-126">**GetConsoleAliasExesLengthW** (Unicode) 和 **GetConsoleAliasExesLengthA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="2d7d3-126">**GetConsoleAliasExesLengthW** (Unicode) and **GetConsoleAliasExesLengthA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="2d7d3-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d7d3-127">See also</span></span>

[<span data-ttu-id="2d7d3-128">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="2d7d3-128">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="2d7d3-129">主控台別名</span><span class="sxs-lookup"><span data-stu-id="2d7d3-129">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="2d7d3-130">主控台函式</span><span class="sxs-lookup"><span data-stu-id="2d7d3-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2d7d3-131">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="2d7d3-131">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="2d7d3-132">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="2d7d3-132">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="2d7d3-133">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="2d7d3-133">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
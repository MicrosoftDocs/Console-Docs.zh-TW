---
title: AddConsoleAlias 函式
description: 請參閱 AddConsoleAlias 函式的參考資訊，此函式會定義指定之可執行檔的主控台別名。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/AddConsoleAlias
- consoleapi3/AddConsoleAliasA
- consoleapi3/AddConsoleAliasW
- wincon/AddConsoleAlias
- wincon/AddConsoleAliasA
- wincon/AddConsoleAliasW
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
MS-HAID:
- base.addconsolealias
- consoles.addconsolealias
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e4072c3c-cf32-4992-847e-efdb846e5784
topic_type:
- apiref
api_name:
- AddConsoleAlias
- AddConsoleAliasA
- AddConsoleAliasW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 9ff901615fa2a17ee9902bd028a2f63ee6b7a4b4
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357868"
---
# <a name="addconsolealias-function"></a><span data-ttu-id="0f3f0-104">AddConsoleAlias 函式</span><span class="sxs-lookup"><span data-stu-id="0f3f0-104">AddConsoleAlias function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="0f3f0-105">定義指定之可執行檔的主控台別名。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-105">Defines a console alias for the specified executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f3f0-106">語法</span><span class="sxs-lookup"><span data-stu-id="0f3f0-106">Syntax</span></span>

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

## <a name="parameters"></a><span data-ttu-id="0f3f0-107">參數</span><span class="sxs-lookup"><span data-stu-id="0f3f0-107">Parameters</span></span>

<span data-ttu-id="0f3f0-108">*來源* \[在\]</span><span class="sxs-lookup"><span data-stu-id="0f3f0-108">*Source* \[in\]</span></span>  
<span data-ttu-id="0f3f0-109">要對應至 *目標* 所指定之文字的主控台別名。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-109">The console alias to be mapped to the text specified by *Target*.</span></span>

<span data-ttu-id="0f3f0-110">*目標* \[在\]</span><span class="sxs-lookup"><span data-stu-id="0f3f0-110">*Target* \[in\]</span></span>  
<span data-ttu-id="0f3f0-111">要取代為 *來源* 的文字。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-111">The text to be substituted for *Source*.</span></span> <span data-ttu-id="0f3f0-112">如果此參數為 **Null**，則會移除主控台別名。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-112">If this parameter is **NULL**, then the console alias is removed.</span></span>

<span data-ttu-id="0f3f0-113">*ExeName* \[在\]</span><span class="sxs-lookup"><span data-stu-id="0f3f0-113">*ExeName* \[in\]</span></span>  
<span data-ttu-id="0f3f0-114">要定義的主控台別名之可執行檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-114">The name of the executable file for which the console alias is to be defined.</span></span>

## <a name="return-value"></a><span data-ttu-id="0f3f0-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="0f3f0-115">Return value</span></span>

<span data-ttu-id="0f3f0-116">如果函式成功，則傳回值為 **TRUE**。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-116">If the function succeeds, the return value is **TRUE**.</span></span>

<span data-ttu-id="0f3f0-117">如果函式失敗，則傳回值為 **FALSE**。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-117">If the function fails, the return value is **FALSE**.</span></span> <span data-ttu-id="0f3f0-118">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-118">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="0f3f0-119">備註</span><span class="sxs-lookup"><span data-stu-id="0f3f0-119">Remarks</span></span>

<span data-ttu-id="0f3f0-120">若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0501 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="0f3f0-121">如需詳細資訊，請參閱 [使用 Windows 標頭](/windows/win32/winprog/using-the-windows-headers)。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-121">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="examples"></a><span data-ttu-id="0f3f0-122">範例</span><span class="sxs-lookup"><span data-stu-id="0f3f0-122">Examples</span></span>

<span data-ttu-id="0f3f0-123">如需範例，請參閱 [主控台別名](console-aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="0f3f0-123">For an example, see [Console Aliases](console-aliases.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="0f3f0-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="0f3f0-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0f3f0-125">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="0f3f0-125">Minimum supported client</span></span> | <span data-ttu-id="0f3f0-126">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="0f3f0-126">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="0f3f0-127">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="0f3f0-127">Minimum supported server</span></span> | <span data-ttu-id="0f3f0-128">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="0f3f0-128">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="0f3f0-129">標頭</span><span class="sxs-lookup"><span data-stu-id="0f3f0-129">Header</span></span> | <span data-ttu-id="0f3f0-130">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="0f3f0-130">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="0f3f0-131">程式庫</span><span class="sxs-lookup"><span data-stu-id="0f3f0-131">Library</span></span> | <span data-ttu-id="0f3f0-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="0f3f0-132">Kernel32.lib</span></span> |
| <span data-ttu-id="0f3f0-133">DLL</span><span class="sxs-lookup"><span data-stu-id="0f3f0-133">DLL</span></span> | <span data-ttu-id="0f3f0-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0f3f0-134">Kernel32.dll</span></span> |
| <span data-ttu-id="0f3f0-135">Unicode 與 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="0f3f0-135">Unicode and ANSI names</span></span> | <span data-ttu-id="0f3f0-136">**AddConsoleAliasW** (Unicode) 和 **AddConsoleAliasA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="0f3f0-136">**AddConsoleAliasW** (Unicode) and **AddConsoleAliasA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="0f3f0-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f3f0-137">See also</span></span>

[<span data-ttu-id="0f3f0-138">主控台別名</span><span class="sxs-lookup"><span data-stu-id="0f3f0-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="0f3f0-139">主控台函式</span><span class="sxs-lookup"><span data-stu-id="0f3f0-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0f3f0-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="0f3f0-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="0f3f0-141">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="0f3f0-141">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="0f3f0-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="0f3f0-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)
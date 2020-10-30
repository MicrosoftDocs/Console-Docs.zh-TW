---
title: GetConsoleAliases 函式
description: 針對指定的可執行檔，抓取所有已定義的主控台別名。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetConsoleAliases
- wincon/GetConsoleAliases
- GetConsoleAliases
- consoleapi3/GetConsoleAliasesA
- wincon/GetConsoleAliasesA
- GetConsoleAliasesA
- consoleapi3/GetConsoleAliasesW
- wincon/GetConsoleAliasesW
- GetConsoleAliasesW
MS-HAID:
- base.getconsolealiases
- consoles.getconsolealiases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 92eefa4e-ffde-4886-afde-5aecf450b425
topic_type:
- apiref
api_name:
- GetConsoleAliases
- GetConsoleAliasesA
- GetConsoleAliasesW
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: a84579ce7bf27787e986ded2e1f21520f8d442b9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038116"
---
# <a name="getconsolealiases-function"></a><span data-ttu-id="748b4-104">GetConsoleAliases 函式</span><span class="sxs-lookup"><span data-stu-id="748b4-104">GetConsoleAliases function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="748b4-105">針對指定的可執行檔，抓取所有已定義的主控台別名。</span><span class="sxs-lookup"><span data-stu-id="748b4-105">Retrieves all defined console aliases for the specified executable.</span></span>

## <a name="syntax"></a><span data-ttu-id="748b4-106">語法</span><span class="sxs-lookup"><span data-stu-id="748b4-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleAliases(
  _Out_ LPTSTR lpAliasBuffer,
  _In_  DWORD  AliasBufferLength,
  _In_  LPTSTR lpExeName
);
```

## <a name="parameters"></a><span data-ttu-id="748b4-107">參數</span><span class="sxs-lookup"><span data-stu-id="748b4-107">Parameters</span></span>

<span data-ttu-id="748b4-108">*lpAliasBuffer* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="748b4-108">*lpAliasBuffer* \[out\]</span></span>  
<span data-ttu-id="748b4-109">接收別名的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="748b4-109">A pointer to a buffer that receives the aliases.</span></span>

<span data-ttu-id="748b4-110">資料的格式如下： *source1.rc* = *Target1* \\ 0 *>source2* = *Target2* \\ 0 .。。 *SourceN* =*TargetN* \\0，其中 *N* 是已定義的主控台別名數目。</span><span class="sxs-lookup"><span data-stu-id="748b4-110">The format of the data is as follows: *Source1*=*Target1*\\0 *Source2*=*Target2*\\0... *SourceN*=*TargetN*\\0, where *N* is the number of console aliases defined.</span></span>

<span data-ttu-id="748b4-111">*AliasBufferLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="748b4-111">*AliasBufferLength* \[in\]</span></span>  
<span data-ttu-id="748b4-112">*LpAliasBuffer* 所指向的緩衝區大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="748b4-112">The size of the buffer pointed to by *lpAliasBuffer* , in bytes.</span></span>

<span data-ttu-id="748b4-113">*lpExeName* \[在\]</span><span class="sxs-lookup"><span data-stu-id="748b4-113">*lpExeName* \[in\]</span></span>  
<span data-ttu-id="748b4-114">要取出其別名的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="748b4-114">The executable file whose aliases are to be retrieved.</span></span>

## <a name="return-value"></a><span data-ttu-id="748b4-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="748b4-115">Return value</span></span>

<span data-ttu-id="748b4-116">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="748b4-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="748b4-117">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="748b4-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="748b4-118">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="748b4-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="748b4-119">備註</span><span class="sxs-lookup"><span data-stu-id="748b4-119">Remarks</span></span>

<span data-ttu-id="748b4-120">若要判斷 *lpExeName* 緩衝區所需的大小，請使用 [**GetConsoleAliasesLength**](getconsolealiaseslength.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="748b4-120">To determine the required size for the *lpExeName* buffer, use the [**GetConsoleAliasesLength**](getconsolealiaseslength.md) function.</span></span>

<span data-ttu-id="748b4-121">若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0501 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="748b4-121">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="748b4-122">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="748b4-122">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="748b4-123">規格需求</span><span class="sxs-lookup"><span data-stu-id="748b4-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="748b4-124">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="748b4-124">Minimum supported client</span></span> | <span data-ttu-id="748b4-125">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="748b4-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="748b4-126">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="748b4-126">Minimum supported server</span></span> | <span data-ttu-id="748b4-127">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="748b4-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="748b4-128">標頭</span><span class="sxs-lookup"><span data-stu-id="748b4-128">Header</span></span> | <span data-ttu-id="748b4-129">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="748b4-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="748b4-130">程式庫</span><span class="sxs-lookup"><span data-stu-id="748b4-130">Library</span></span> | <span data-ttu-id="748b4-131">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="748b4-131">Kernel32.lib</span></span> |
| <span data-ttu-id="748b4-132">DLL</span><span class="sxs-lookup"><span data-stu-id="748b4-132">DLL</span></span> | <span data-ttu-id="748b4-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="748b4-133">Kernel32.dll</span></span> |
| <span data-ttu-id="748b4-134">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="748b4-134">Unicode and ANSI names</span></span> | <span data-ttu-id="748b4-135">**GetConsoleAliasesW** (Unicode) 和 **GetConsoleAliasesA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="748b4-135">**GetConsoleAliasesW** (Unicode) and **GetConsoleAliasesA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="748b4-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="748b4-136">See also</span></span>

[<span data-ttu-id="748b4-137">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="748b4-137">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="748b4-138">主控台別名</span><span class="sxs-lookup"><span data-stu-id="748b4-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="748b4-139">主控台功能</span><span class="sxs-lookup"><span data-stu-id="748b4-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="748b4-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="748b4-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="748b4-141">**GetConsoleAliasesLength**</span><span class="sxs-lookup"><span data-stu-id="748b4-141">**GetConsoleAliasesLength**</span></span>](getconsolealiaseslength.md)

[<span data-ttu-id="748b4-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="748b4-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

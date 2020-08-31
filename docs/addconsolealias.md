---
title: AddConsoleAlias 函式
description: 請參閱 AddConsoleAlias 函式的參考資訊，此函式會定義指定之可執行檔的主控台別名。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
ms.openlocfilehash: 108a77b3178e7695e7477ea198df616fa8bcb199
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059390"
---
# <a name="addconsolealias-function"></a><span data-ttu-id="97a21-104">AddConsoleAlias 函式</span><span class="sxs-lookup"><span data-stu-id="97a21-104">AddConsoleAlias function</span></span>


<span data-ttu-id="97a21-105">定義指定之可執行檔的主控台別名。</span><span class="sxs-lookup"><span data-stu-id="97a21-105">Defines a console alias for the specified executable.</span></span>

<a name="syntax"></a><span data-ttu-id="97a21-106">語法</span><span class="sxs-lookup"><span data-stu-id="97a21-106">Syntax</span></span>
------

```C
BOOL WINAPI AddConsoleAlias(
  _In_ LPCTSTR Source,
  _In_ LPCTSTR Target,
  _In_ LPCTSTR ExeName
);
```

<a name="parameters"></a><span data-ttu-id="97a21-107">參數</span><span class="sxs-lookup"><span data-stu-id="97a21-107">Parameters</span></span>
----------

<span data-ttu-id="97a21-108">*來源* \[在\]</span><span class="sxs-lookup"><span data-stu-id="97a21-108">*Source* \[in\]</span></span>  
<span data-ttu-id="97a21-109">要對應至 *目標*所指定之文字的主控台別名。</span><span class="sxs-lookup"><span data-stu-id="97a21-109">The console alias to be mapped to the text specified by *Target*.</span></span>

<span data-ttu-id="97a21-110">*目標* \[在\]</span><span class="sxs-lookup"><span data-stu-id="97a21-110">*Target* \[in\]</span></span>  
<span data-ttu-id="97a21-111">要取代為 *來源*的文字。</span><span class="sxs-lookup"><span data-stu-id="97a21-111">The text to be substituted for *Source*.</span></span> <span data-ttu-id="97a21-112">如果此參數為 **Null**，則會移除主控台別名。</span><span class="sxs-lookup"><span data-stu-id="97a21-112">If this parameter is **NULL**, then the console alias is removed.</span></span>

<span data-ttu-id="97a21-113">*ExeName* \[在\]</span><span class="sxs-lookup"><span data-stu-id="97a21-113">*ExeName* \[in\]</span></span>  
<span data-ttu-id="97a21-114">要定義的主控台別名之可執行檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="97a21-114">The name of the executable file for which the console alias is to be defined.</span></span>

<a name="return-value"></a><span data-ttu-id="97a21-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="97a21-115">Return value</span></span>
------------

<span data-ttu-id="97a21-116">如果函式成功，則傳回值為 **TRUE**。</span><span class="sxs-lookup"><span data-stu-id="97a21-116">If the function succeeds, the return value is **TRUE**.</span></span>

<span data-ttu-id="97a21-117">如果函式失敗，則傳回值為 **FALSE**。</span><span class="sxs-lookup"><span data-stu-id="97a21-117">If the function fails, the return value is **FALSE**.</span></span> <span data-ttu-id="97a21-118">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="97a21-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="97a21-119">備註</span><span class="sxs-lookup"><span data-stu-id="97a21-119">Remarks</span></span>
-------

<span data-ttu-id="97a21-120">若要編譯使用此函數的應用程式，請將\*\* \_ WIN32 \_ WINNT\*\*定義為0x0501 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="97a21-120">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="97a21-121">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="97a21-121">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="examples"></a><span data-ttu-id="97a21-122">範例</span><span class="sxs-lookup"><span data-stu-id="97a21-122">Examples</span></span>
--------

<span data-ttu-id="97a21-123">如需範例，請參閱 [主控台別名](console-aliases.md)。</span><span class="sxs-lookup"><span data-stu-id="97a21-123">For an example, see [Console Aliases](console-aliases.md).</span></span>

<a name="requirements"></a><span data-ttu-id="97a21-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="97a21-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="97a21-125">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="97a21-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="97a21-126">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="97a21-126">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="97a21-127">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="97a21-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="97a21-128">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="97a21-128">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="97a21-129">標頭</span><span class="sxs-lookup"><span data-stu-id="97a21-129">Header</span></span></p></td>
<td><span data-ttu-id="97a21-130">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="97a21-130">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="97a21-131">程式庫</span><span class="sxs-lookup"><span data-stu-id="97a21-131">Library</span></span></p></td>
<td><span data-ttu-id="97a21-132">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="97a21-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="97a21-133">DLL</span><span class="sxs-lookup"><span data-stu-id="97a21-133">DLL</span></span></p></td>
<td><span data-ttu-id="97a21-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="97a21-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="97a21-135">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="97a21-135">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="97a21-136"><strong>AddConsoleAliasW</strong> (Unicode) 和 <strong>AddConsoleAliasA</strong> (ANSI) </span><span class="sxs-lookup"><span data-stu-id="97a21-136"><strong>AddConsoleAliasW</strong> (Unicode) and <strong>AddConsoleAliasA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="97a21-137"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="97a21-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="97a21-138">主控台別名</span><span class="sxs-lookup"><span data-stu-id="97a21-138">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="97a21-139">主控台功能</span><span class="sxs-lookup"><span data-stu-id="97a21-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="97a21-140">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="97a21-140">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="97a21-141">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="97a21-141">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="97a21-142">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="97a21-142">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 





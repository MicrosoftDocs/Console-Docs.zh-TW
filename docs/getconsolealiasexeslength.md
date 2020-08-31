---
title: GetConsoleAliasExesLength 函式
description: 抓取 GetConsoleAliasExes 函式所使用之緩衝區的必要大小。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
ms.openlocfilehash: 0f4459254e9382a0c784ceb2c214af056087ab1b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059170"
---
# <a name="getconsolealiasexeslength-function"></a><span data-ttu-id="71afe-104">GetConsoleAliasExesLength 函式</span><span class="sxs-lookup"><span data-stu-id="71afe-104">GetConsoleAliasExesLength function</span></span>


<span data-ttu-id="71afe-105">抓取 [**GetConsoleAliasExes**](getconsolealiasexes.md) 函式所使用之緩衝區的必要大小。</span><span class="sxs-lookup"><span data-stu-id="71afe-105">Retrieves the required size for the buffer used by the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.</span></span>

<a name="syntax"></a><span data-ttu-id="71afe-106">語法</span><span class="sxs-lookup"><span data-stu-id="71afe-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliasExesLength(void);
```

<a name="parameters"></a><span data-ttu-id="71afe-107">參數</span><span class="sxs-lookup"><span data-stu-id="71afe-107">Parameters</span></span>
----------

<span data-ttu-id="71afe-108">此函式沒有參數。</span><span class="sxs-lookup"><span data-stu-id="71afe-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="71afe-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="71afe-109">Return value</span></span>
------------

<span data-ttu-id="71afe-110">儲存所有已定義主控台別名之可執行檔的名稱所需的緩衝區大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="71afe-110">The size of the buffer required to store the names of all executable files that have console aliases defined, in bytes.</span></span>

<a name="remarks"></a><span data-ttu-id="71afe-111">備註</span><span class="sxs-lookup"><span data-stu-id="71afe-111">Remarks</span></span>
-------

<span data-ttu-id="71afe-112">若要編譯使用此函數的應用程式，請將\*\* \_ WIN32 \_ WINNT\*\*定義為0x0501 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="71afe-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="71afe-113">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="71afe-113">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="71afe-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="71afe-114">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="71afe-115">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="71afe-115">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="71afe-116">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="71afe-116">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="71afe-117">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="71afe-117">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="71afe-118">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="71afe-118">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="71afe-119">標頭</span><span class="sxs-lookup"><span data-stu-id="71afe-119">Header</span></span></p></td>
<td><span data-ttu-id="71afe-120">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="71afe-120">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="71afe-121">程式庫</span><span class="sxs-lookup"><span data-stu-id="71afe-121">Library</span></span></p></td>
<td><span data-ttu-id="71afe-122">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="71afe-122">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="71afe-123">DLL</span><span class="sxs-lookup"><span data-stu-id="71afe-123">DLL</span></span></p></td>
<td><span data-ttu-id="71afe-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="71afe-124">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="71afe-125">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="71afe-125">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="71afe-126"><strong>GetConsoleAliasExesLengthW</strong> (Unicode) 和 <strong>GetConsoleAliasExesLengthA</strong> (ANSI) </span><span class="sxs-lookup"><span data-stu-id="71afe-126"><strong>GetConsoleAliasExesLengthW</strong> (Unicode) and <strong>GetConsoleAliasExesLengthA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="71afe-127"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="71afe-127"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="71afe-128">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="71afe-128">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="71afe-129">主控台別名</span><span class="sxs-lookup"><span data-stu-id="71afe-129">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="71afe-130">主控台功能</span><span class="sxs-lookup"><span data-stu-id="71afe-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="71afe-131">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="71afe-131">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="71afe-132">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="71afe-132">**GetConsoleAliases**</span></span>](getconsolealiases.md)

[<span data-ttu-id="71afe-133">**GetConsoleAliasExes**</span><span class="sxs-lookup"><span data-stu-id="71afe-133">**GetConsoleAliasExes**</span></span>](getconsolealiasexes.md)

 

 





---
title: GetConsoleAliasExes 函式
description: 使用定義的主控台別名，抓取所有可執行檔的名稱。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
ms.openlocfilehash: e112112fc1510ab4c3f0a99ff9b208cc364e361a
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059179"
---
# <a name="getconsolealiasexes-function"></a><span data-ttu-id="5e52c-104">GetConsoleAliasExes 函式</span><span class="sxs-lookup"><span data-stu-id="5e52c-104">GetConsoleAliasExes function</span></span>


<span data-ttu-id="5e52c-105">使用定義的主控台別名，抓取所有可執行檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e52c-105">Retrieves the names of all executable files with console aliases defined.</span></span>

<a name="syntax"></a><span data-ttu-id="5e52c-106">語法</span><span class="sxs-lookup"><span data-stu-id="5e52c-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleAliasExes(
  _Out_ LPTSTR lpExeNameBuffer,
  _In_  DWORD  ExeNameBufferLength
);
```

<a name="parameters"></a><span data-ttu-id="5e52c-107">參數</span><span class="sxs-lookup"><span data-stu-id="5e52c-107">Parameters</span></span>
----------

<span data-ttu-id="5e52c-108">*lpExeNameBuffer* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="5e52c-108">*lpExeNameBuffer* \[out\]</span></span>  
<span data-ttu-id="5e52c-109">接收可執行檔名稱之緩衝區的指標。</span><span class="sxs-lookup"><span data-stu-id="5e52c-109">A pointer to a buffer that receives the names of the executable files.</span></span>

<span data-ttu-id="5e52c-110">*ExeNameBufferLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="5e52c-110">*ExeNameBufferLength* \[in\]</span></span>  
<span data-ttu-id="5e52c-111">*LpExeNameBuffer*所指向的緩衝區大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="5e52c-111">The size of the buffer pointed to by *lpExeNameBuffer*, in bytes.</span></span>

<a name="return-value"></a><span data-ttu-id="5e52c-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="5e52c-112">Return value</span></span>
------------

<span data-ttu-id="5e52c-113">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="5e52c-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="5e52c-114">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="5e52c-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="5e52c-115">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="5e52c-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="5e52c-116">備註</span><span class="sxs-lookup"><span data-stu-id="5e52c-116">Remarks</span></span>
-------

<span data-ttu-id="5e52c-117">若要判斷 *lpExeNameBuffer* 緩衝區所需的大小，請使用 [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="5e52c-117">To determine the required size for the *lpExeNameBuffer* buffer, use the [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) function.</span></span>

<span data-ttu-id="5e52c-118">若要編譯使用此函數的應用程式，請將\*\* \_ WIN32 \_ WINNT\*\*定義為0x0501 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="5e52c-118">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="5e52c-119">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="5e52c-119">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="5e52c-120">規格需求</span><span class="sxs-lookup"><span data-stu-id="5e52c-120">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="5e52c-121">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="5e52c-121">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="5e52c-122">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="5e52c-122">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5e52c-123">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="5e52c-123">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="5e52c-124">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="5e52c-124">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5e52c-125">標頭</span><span class="sxs-lookup"><span data-stu-id="5e52c-125">Header</span></span></p></td>
<td><span data-ttu-id="5e52c-126">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="5e52c-126">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5e52c-127">程式庫</span><span class="sxs-lookup"><span data-stu-id="5e52c-127">Library</span></span></p></td>
<td><span data-ttu-id="5e52c-128">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="5e52c-128">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="5e52c-129">DLL</span><span class="sxs-lookup"><span data-stu-id="5e52c-129">DLL</span></span></p></td>
<td><span data-ttu-id="5e52c-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="5e52c-130">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="5e52c-131">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="5e52c-131">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="5e52c-132"><strong>GetConsoleAliasExesW</strong> (Unicode) 和 <strong>GetConsoleAliasExesA</strong> (ANSI) </span><span class="sxs-lookup"><span data-stu-id="5e52c-132"><strong>GetConsoleAliasExesW</strong> (Unicode) and <strong>GetConsoleAliasExesA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="5e52c-133"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e52c-133"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="5e52c-134">**AddConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="5e52c-134">**AddConsoleAlias**</span></span>](addconsolealias.md)

[<span data-ttu-id="5e52c-135">主控台別名</span><span class="sxs-lookup"><span data-stu-id="5e52c-135">Console Aliases</span></span>](console-aliases.md)

[<span data-ttu-id="5e52c-136">主控台功能</span><span class="sxs-lookup"><span data-stu-id="5e52c-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="5e52c-137">**GetConsoleAlias**</span><span class="sxs-lookup"><span data-stu-id="5e52c-137">**GetConsoleAlias**</span></span>](getconsolealias.md)

[<span data-ttu-id="5e52c-138">**GetConsoleAliasExesLength**</span><span class="sxs-lookup"><span data-stu-id="5e52c-138">**GetConsoleAliasExesLength**</span></span>](getconsolealiasexeslength.md)

[<span data-ttu-id="5e52c-139">**GetConsoleAliases**</span><span class="sxs-lookup"><span data-stu-id="5e52c-139">**GetConsoleAliases**</span></span>](getconsolealiases.md)

 

 





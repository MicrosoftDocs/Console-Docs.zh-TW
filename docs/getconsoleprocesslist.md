---
title: GetConsoleProcessList 函式
description: 請參閱 GetConsoleProcessList 函式的參考資訊，此函式會抓取連接到目前主控台的進程清單。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi3/GetConsoleProcessList
- wincon/GetConsoleProcessList
- GetConsoleProcessList
MS-HAID:
- '\_win32\_getconsoleprocesslist'
- base.getconsoleprocesslist
- consoles.getconsoleprocesslist
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3d21103b-662d-4393-ae3f-773cd9e4a930
topic_type:
- apiref
api_name:
- GetConsoleProcessList
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 5b032754172886fd83a8152caeb5e2228b917930
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059158"
---
# <a name="getconsoleprocesslist-function"></a><span data-ttu-id="c24f3-104">GetConsoleProcessList 函式</span><span class="sxs-lookup"><span data-stu-id="c24f3-104">GetConsoleProcessList function</span></span>


<span data-ttu-id="c24f3-105">抓取附加至目前主控台的進程清單。</span><span class="sxs-lookup"><span data-stu-id="c24f3-105">Retrieves a list of the processes attached to the current console.</span></span>

<a name="syntax"></a><span data-ttu-id="c24f3-106">語法</span><span class="sxs-lookup"><span data-stu-id="c24f3-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleProcessList(
  _Out_ LPDWORD lpdwProcessList,
  _In_  DWORD   dwProcessCount
);
```

<a name="parameters"></a><span data-ttu-id="c24f3-107">參數</span><span class="sxs-lookup"><span data-stu-id="c24f3-107">Parameters</span></span>
----------

<span data-ttu-id="c24f3-108">*lpdwProcessList* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="c24f3-108">*lpdwProcessList* \[out\]</span></span>  
<span data-ttu-id="c24f3-109">在成功時收到進程識別碼陣列的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="c24f3-109">A pointer to a buffer that receives an array of process identifiers upon success.</span></span> <span data-ttu-id="c24f3-110">這必須是有效的緩衝區，而且不能是 `NULL` 。</span><span class="sxs-lookup"><span data-stu-id="c24f3-110">This must be a valid buffer and cannot be `NULL`.</span></span> <span data-ttu-id="c24f3-111">緩衝區必須有空間，才能接收至少一個傳回的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="c24f3-111">The buffer must have space to receive at least 1 returned process id.</span></span>

<span data-ttu-id="c24f3-112">*dwProcessCount* \[在\]</span><span class="sxs-lookup"><span data-stu-id="c24f3-112">*dwProcessCount* \[in\]</span></span>  
<span data-ttu-id="c24f3-113">可以儲存在 *lpdwProcessList* 緩衝區中的處理序識別碼數目上限。</span><span class="sxs-lookup"><span data-stu-id="c24f3-113">The maximum number of process identifiers that can be stored in the *lpdwProcessList* buffer.</span></span> <span data-ttu-id="c24f3-114">這必須大於0。</span><span class="sxs-lookup"><span data-stu-id="c24f3-114">This must be greater than 0.</span></span>

<a name="return-value"></a><span data-ttu-id="c24f3-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="c24f3-115">Return value</span></span>
------------

<span data-ttu-id="c24f3-116">如果函式成功，則傳回值小於或等於 *dwProcessCount* ，而且代表 *lpdwProcessList* 緩衝區中儲存的進程識別碼數目。</span><span class="sxs-lookup"><span data-stu-id="c24f3-116">If the function succeeds, the return value is less than or equal to *dwProcessCount* and represents the number of process identifiers stored in the *lpdwProcessList* buffer.</span></span>

<span data-ttu-id="c24f3-117">如果緩衝區太小而無法容納所有有效的處理序識別碼，則傳回值是必要的陣列元素數目。</span><span class="sxs-lookup"><span data-stu-id="c24f3-117">If the buffer is too small to hold all the valid process identifiers, the return value is the required number of array elements.</span></span> <span data-ttu-id="c24f3-118">此函數將不會在緩衝區中儲存任何識別碼。</span><span class="sxs-lookup"><span data-stu-id="c24f3-118">The function will have stored no identifiers in the buffer.</span></span> <span data-ttu-id="c24f3-119">在這種情況下，請使用傳回值配置夠大的緩衝區來儲存整個清單，然後再次呼叫函數。</span><span class="sxs-lookup"><span data-stu-id="c24f3-119">In this situation, use the return value to allocate a buffer that is large enough to store the entire list and call the function again.</span></span>

<span data-ttu-id="c24f3-120">如果傳回值為零，則函式失敗，因為每個主控台至少有一個相關聯的進程。</span><span class="sxs-lookup"><span data-stu-id="c24f3-120">If the return value is zero, the function has failed, because every console has at least one process associated with it.</span></span> <span data-ttu-id="c24f3-121">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="c24f3-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<span data-ttu-id="c24f3-122">如果 `NULL` 提供了進程清單，或進程計數是0，則呼叫會傳回0，而且 `GetLastError` 會傳回 `ERROR_INVALID_PARAMETER` 。</span><span class="sxs-lookup"><span data-stu-id="c24f3-122">If a `NULL` process list was provided or the process count was 0, the call will return 0 and `GetLastError` will return `ERROR_INVALID_PARAMETER`.</span></span> <span data-ttu-id="c24f3-123">請提供至少一個元素的緩衝區，以呼叫此函數。</span><span class="sxs-lookup"><span data-stu-id="c24f3-123">Please provide a buffer of at least one element to call this function.</span></span> <span data-ttu-id="c24f3-124">配置較大的緩衝區，並在傳回碼大於所提供緩衝區的長度時再呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="c24f3-124">Allocate a larger buffer and call again if the return code is larger than the length of the provided buffer.</span></span>

<a name="remarks"></a><span data-ttu-id="c24f3-125">備註</span><span class="sxs-lookup"><span data-stu-id="c24f3-125">Remarks</span></span>
-------

<span data-ttu-id="c24f3-126">若要編譯使用此函數的應用程式，請將\*\* \_ WIN32 \_ WINNT\*\*定義為0x0501 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c24f3-126">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="c24f3-127">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="c24f3-127">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="c24f3-128">規格需求</span><span class="sxs-lookup"><span data-stu-id="c24f3-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="c24f3-129">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="c24f3-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="c24f3-130">Windows XP [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="c24f3-130">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c24f3-131">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="c24f3-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="c24f3-132">Windows Server 2003 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="c24f3-132">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c24f3-133">標頭</span><span class="sxs-lookup"><span data-stu-id="c24f3-133">Header</span></span></p></td>
<td><span data-ttu-id="c24f3-134">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="c24f3-134">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="c24f3-135">程式庫</span><span class="sxs-lookup"><span data-stu-id="c24f3-135">Library</span></span></p></td>
<td><span data-ttu-id="c24f3-136">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="c24f3-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="c24f3-137">DLL</span><span class="sxs-lookup"><span data-stu-id="c24f3-137">DLL</span></span></p></td>
<td><span data-ttu-id="c24f3-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c24f3-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="c24f3-139"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="c24f3-139"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="c24f3-140">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="c24f3-140">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="c24f3-141">主控台功能</span><span class="sxs-lookup"><span data-stu-id="c24f3-141">Console Functions</span></span>](console-functions.md)

 

 





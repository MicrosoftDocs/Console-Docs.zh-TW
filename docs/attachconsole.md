---
title: AttachConsole 函式
description: 請參閱 AttachConsole 函式的參考資訊，此函式會將呼叫進程附加至指定進程的主控台。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c4048a2fb4c93d9f286ffc1ef7f38923836f37bf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059386"
---
# <a name="attachconsole-function"></a><span data-ttu-id="082ab-104">AttachConsole 函式</span><span class="sxs-lookup"><span data-stu-id="082ab-104">AttachConsole function</span></span>


<span data-ttu-id="082ab-105">將呼叫進程附加至指定進程的主控台。</span><span class="sxs-lookup"><span data-stu-id="082ab-105">Attaches the calling process to the console of the specified process.</span></span>

<a name="syntax"></a><span data-ttu-id="082ab-106">語法</span><span class="sxs-lookup"><span data-stu-id="082ab-106">Syntax</span></span>
------

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

<a name="parameters"></a><span data-ttu-id="082ab-107">參數</span><span class="sxs-lookup"><span data-stu-id="082ab-107">Parameters</span></span>
----------

<span data-ttu-id="082ab-108">*dwProcessId* \[在\]</span><span class="sxs-lookup"><span data-stu-id="082ab-108">*dwProcessId* \[in\]</span></span>  
<span data-ttu-id="082ab-109">要使用其主控台的進程識別碼。</span><span class="sxs-lookup"><span data-stu-id="082ab-109">The identifier of the process whose console is to be used.</span></span> <span data-ttu-id="082ab-110">這個參數可以是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="082ab-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="082ab-111">值</span><span class="sxs-lookup"><span data-stu-id="082ab-111">Value</span></span></th>
<th><span data-ttu-id="082ab-112">意義</span><span class="sxs-lookup"><span data-stu-id="082ab-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="082ab-113"><em>Pid</em></span><span class="sxs-lookup"><span data-stu-id="082ab-113"><em>pid</em></span></span></td>
<td><p><span data-ttu-id="082ab-114">使用指定進程的主控台。</span><span class="sxs-lookup"><span data-stu-id="082ab-114">Use the console of the specified process.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="082ab-115"><span id="ATTACH_PARENT_PROCESS"></span><span id="attach_parent_process"></span>
<strong>ATTACH_PARENT_PROCESS</strong> (DWORD) -1</span><span class="sxs-lookup"><span data-stu-id="082ab-115"><span id="ATTACH_PARENT_PROCESS"></span><span id="attach_parent_process"></span>
<strong>ATTACH_PARENT_PROCESS</strong> (DWORD)-1</span></span></td>
<td><p><span data-ttu-id="082ab-116">使用目前進程父系的主控台。</span><span class="sxs-lookup"><span data-stu-id="082ab-116">Use the console of the parent of the current process.</span></span></p></td>
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="082ab-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="082ab-117">Return value</span></span>
------------

<span data-ttu-id="082ab-118">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="082ab-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="082ab-119">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="082ab-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="082ab-120">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="082ab-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="082ab-121">備註</span><span class="sxs-lookup"><span data-stu-id="082ab-121">Remarks</span></span>
-------

<span data-ttu-id="082ab-122">一個進程最多可以附加至一個主控台。</span><span class="sxs-lookup"><span data-stu-id="082ab-122">A process can be attached to at most one console.</span></span> <span data-ttu-id="082ab-123">如果呼叫的進程已附加至主控台，則傳回的錯誤碼會是 \*\* \_ \_ 拒絕存取\*\* (5) 錯誤。</span><span class="sxs-lookup"><span data-stu-id="082ab-123">If the calling process is already attached to a console, the error code returned is **ERROR\_ACCESS\_DENIED** (5).</span></span> <span data-ttu-id="082ab-124">如果指定的進程沒有主控台，則傳回的錯誤碼會是 **錯誤不正確 \_ \_ 控制碼** (6) 。</span><span class="sxs-lookup"><span data-stu-id="082ab-124">If the specified process does not have a console, the error code returned is **ERROR\_INVALID\_HANDLE** (6).</span></span> <span data-ttu-id="082ab-125">如果指定的處理常式不存在，則傳回的錯誤碼會是 **錯誤 \_ 不正確 \_ 參數** (87) 。</span><span class="sxs-lookup"><span data-stu-id="082ab-125">If the specified process does not exist, the error code returned is **ERROR\_INVALID\_PARAMETER** (87).</span></span>

<span data-ttu-id="082ab-126">進程可以使用 [**FreeConsole**](freeconsole.md) 函式，從其主控台卸離本身。</span><span class="sxs-lookup"><span data-stu-id="082ab-126">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console.</span></span> <span data-ttu-id="082ab-127">如果有其他進程共用主控台，主控台就不會終結，但呼叫 **FreeConsole** 的進程無法參考它。</span><span class="sxs-lookup"><span data-stu-id="082ab-127">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="082ab-128">當最後一個附加至它的進程終止或呼叫 **FreeConsole**時，主控台就會關閉。</span><span class="sxs-lookup"><span data-stu-id="082ab-128">A console is closed when the last process attached to it terminates or calls **FreeConsole**.</span></span> <span data-ttu-id="082ab-129">在進程呼叫 **FreeConsole**之後，它就可以呼叫 [**AllocConsole**](allocconsole.md) 函式來建立新的主控台或 **AttachConsole** ，以附加至另一個主控台。</span><span class="sxs-lookup"><span data-stu-id="082ab-129">After a process calls **FreeConsole**, it can call the [**AllocConsole**](allocconsole.md) function to create a new console or **AttachConsole** to attach to another console.</span></span>

<span data-ttu-id="082ab-130">若要編譯使用此函數的應用程式，請將\*\* \_ WIN32 \_ WINNT\*\*定義為0x0501 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="082ab-130">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="082ab-131">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="082ab-131">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="082ab-132">規格需求</span><span class="sxs-lookup"><span data-stu-id="082ab-132">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="082ab-133">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="082ab-133">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="082ab-134">Windows XP [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="082ab-134">Windows XP [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="082ab-135">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="082ab-135">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="082ab-136">Windows Server 2003 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="082ab-136">Windows Server 2003 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="082ab-137">標頭</span><span class="sxs-lookup"><span data-stu-id="082ab-137">Header</span></span></p></td>
<td><span data-ttu-id="082ab-138">ConsoleApi .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="082ab-138">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="082ab-139">程式庫</span><span class="sxs-lookup"><span data-stu-id="082ab-139">Library</span></span></p></td>
<td><span data-ttu-id="082ab-140">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="082ab-140">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="082ab-141">DLL</span><span class="sxs-lookup"><span data-stu-id="082ab-141">DLL</span></span></p></td>
<td><span data-ttu-id="082ab-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="082ab-142">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="082ab-143"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="082ab-143"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="082ab-144">主控台功能</span><span class="sxs-lookup"><span data-stu-id="082ab-144">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="082ab-145">機</span><span class="sxs-lookup"><span data-stu-id="082ab-145">Consoles</span></span>](consoles.md)

[<span data-ttu-id="082ab-146">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="082ab-146">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="082ab-147">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="082ab-147">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="082ab-148">**GetConsoleProcessList**</span><span class="sxs-lookup"><span data-stu-id="082ab-148">**GetConsoleProcessList**</span></span>](getconsoleprocesslist.md)

 

 





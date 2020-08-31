---
title: FlushConsoleInputBuffer 函式
description: 清空主控台輸入緩衝區。 目前在輸入緩衝區中的所有輸入記錄都會被捨棄。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/FlushConsoleInputBuffer
- wincon/FlushConsoleInputBuffer
- FlushConsoleInputBuffer
MS-HAID:
- '\_win32\_flushconsoleinputbuffer'
- base.flushconsoleinputbuffer
- consoles.flushconsoleinputbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6f7832d6-1fb2-4ca8-bd07-43123c990851
topic_type:
- apiref
api_name:
- FlushConsoleInputBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: dd184e1fc1f788912be00e9270ccb239c20b8ce8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059207"
---
# <a name="flushconsoleinputbuffer-function"></a><span data-ttu-id="efe24-105">FlushConsoleInputBuffer 函式</span><span class="sxs-lookup"><span data-stu-id="efe24-105">FlushConsoleInputBuffer function</span></span>


<span data-ttu-id="efe24-106">清空主控台輸入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="efe24-106">Flushes the console input buffer.</span></span> <span data-ttu-id="efe24-107">目前在輸入緩衝區中的所有輸入記錄都會被捨棄。</span><span class="sxs-lookup"><span data-stu-id="efe24-107">All input records currently in the input buffer are discarded.</span></span>

<a name="syntax"></a><span data-ttu-id="efe24-108">語法</span><span class="sxs-lookup"><span data-stu-id="efe24-108">Syntax</span></span>
------

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

<a name="parameters"></a><span data-ttu-id="efe24-109">參數</span><span class="sxs-lookup"><span data-stu-id="efe24-109">Parameters</span></span>
----------

<span data-ttu-id="efe24-110">*hConsoleInput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="efe24-110">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="efe24-111">主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="efe24-111">A handle to the console input buffer.</span></span> <span data-ttu-id="efe24-112">控制碼必須有 **一般 \_ 寫入** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="efe24-112">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="efe24-113">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="efe24-113">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<a name="return-value"></a><span data-ttu-id="efe24-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="efe24-114">Return value</span></span>
------------

<span data-ttu-id="efe24-115">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="efe24-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="efe24-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="efe24-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="efe24-117">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="efe24-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="efe24-118">規格需求</span><span class="sxs-lookup"><span data-stu-id="efe24-118">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="efe24-119">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="efe24-119">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="efe24-120">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="efe24-120">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="efe24-121">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="efe24-121">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="efe24-122">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="efe24-122">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="efe24-123">標頭</span><span class="sxs-lookup"><span data-stu-id="efe24-123">Header</span></span></p></td>
<td><span data-ttu-id="efe24-124">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="efe24-124">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="efe24-125">程式庫</span><span class="sxs-lookup"><span data-stu-id="efe24-125">Library</span></span></p></td>
<td><span data-ttu-id="efe24-126">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="efe24-126">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="efe24-127">DLL</span><span class="sxs-lookup"><span data-stu-id="efe24-127">DLL</span></span></p></td>
<td><span data-ttu-id="efe24-128">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="efe24-128">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="efe24-129"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="efe24-129"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="efe24-130">主控台功能</span><span class="sxs-lookup"><span data-stu-id="efe24-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="efe24-131">低層級主控台輸入函式</span><span class="sxs-lookup"><span data-stu-id="efe24-131">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="efe24-132">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="efe24-132">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="efe24-133">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="efe24-133">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="efe24-134">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="efe24-134">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="efe24-135">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="efe24-135">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 





---
title: GetNumberOfConsoleInputEvents 函式
description: 抓取主控台輸入緩衝區中未讀取的輸入記錄數目。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi/GetNumberOfConsoleInputEvents
- wincon/GetNumberOfConsoleInputEvents
- GetNumberOfConsoleInputEvents
MS-HAID:
- '\_win32\_getnumberofconsoleinputevents'
- base.getnumberofconsoleinputevents
- consoles.getnumberofconsoleinputevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1083b4f1-8fa6-4054-a516-3b447c3b0130
topic_type:
- apiref
api_name:
- GetNumberOfConsoleInputEvents
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: c5e3a59308239898f78796170d08f8b21ca1b667
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059118"
---
# <a name="getnumberofconsoleinputevents-function"></a><span data-ttu-id="63ba9-104">GetNumberOfConsoleInputEvents 函式</span><span class="sxs-lookup"><span data-stu-id="63ba9-104">GetNumberOfConsoleInputEvents function</span></span>


<span data-ttu-id="63ba9-105">抓取主控台輸入緩衝區中未讀取的輸入記錄數目。</span><span class="sxs-lookup"><span data-stu-id="63ba9-105">Retrieves the number of unread input records in the console's input buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="63ba9-106">語法</span><span class="sxs-lookup"><span data-stu-id="63ba9-106">Syntax</span></span>
------

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

<a name="parameters"></a><span data-ttu-id="63ba9-107">參數</span><span class="sxs-lookup"><span data-stu-id="63ba9-107">Parameters</span></span>
----------

<span data-ttu-id="63ba9-108">*hConsoleInput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="63ba9-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="63ba9-109">主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="63ba9-109">A handle to the console input buffer.</span></span> <span data-ttu-id="63ba9-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="63ba9-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="63ba9-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="63ba9-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="63ba9-112">*lpcNumberOfEvents* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="63ba9-112">*lpcNumberOfEvents* \[out\]</span></span>  
<span data-ttu-id="63ba9-113">變數的指標，此變數會接收主控台輸入緩衝區中未讀取的輸入記錄數目。</span><span class="sxs-lookup"><span data-stu-id="63ba9-113">A pointer to a variable that receives the number of unread input records in the console's input buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="63ba9-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="63ba9-114">Return value</span></span>
------------

<span data-ttu-id="63ba9-115">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="63ba9-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="63ba9-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="63ba9-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="63ba9-117">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="63ba9-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="63ba9-118">備註</span><span class="sxs-lookup"><span data-stu-id="63ba9-118">Remarks</span></span>
-------

<span data-ttu-id="63ba9-119">**GetNumberOfConsoleInputEvents**函式會報告輸入緩衝區中未讀取的輸入記錄總數，包括鍵盤、滑鼠和視窗大小的輸入記錄。</span><span class="sxs-lookup"><span data-stu-id="63ba9-119">The **GetNumberOfConsoleInputEvents** function reports the total number of unread input records in the input buffer, including keyboard, mouse, and window-resizing input records.</span></span> <span data-ttu-id="63ba9-120">使用 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 或 [**ReadConsole**](readconsole.md) 函數的進程只能讀取鍵盤輸入。</span><span class="sxs-lookup"><span data-stu-id="63ba9-120">Processes using the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function can only read keyboard input.</span></span> <span data-ttu-id="63ba9-121">使用 [**ReadConsoleInput**](readconsoleinput.md) 函數的進程可以讀取所有類型的輸入記錄。</span><span class="sxs-lookup"><span data-stu-id="63ba9-121">Processes using the [**ReadConsoleInput**](readconsoleinput.md) function can read all types of input records.</span></span>

<span data-ttu-id="63ba9-122">進程可以在其中一個 [等候](https://msdn.microsoft.com/library/windows/desktop/ms687069) 函式中指定主控台輸入緩衝區控制碼，以判斷何時有未讀取的主控台輸入。</span><span class="sxs-lookup"><span data-stu-id="63ba9-122">A process can specify a console input buffer handle in one of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069) to determine when there is unread console input.</span></span> <span data-ttu-id="63ba9-123">當輸入緩衝區不是空的時，主控台輸入緩衝區控制碼的狀態就會收到信號。</span><span class="sxs-lookup"><span data-stu-id="63ba9-123">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="63ba9-124">若要從主控台輸入緩衝區讀取輸入記錄，而不會影響未讀取的記錄數目，請使用 [**PeekConsoleInput**](peekconsoleinput.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="63ba9-124">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="63ba9-125">若要捨棄主控台輸入緩衝區中的所有未讀取記錄，請使用 [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="63ba9-125">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

<a name="requirements"></a><span data-ttu-id="63ba9-126">規格需求</span><span class="sxs-lookup"><span data-stu-id="63ba9-126">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="63ba9-127">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="63ba9-127">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="63ba9-128">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="63ba9-128">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="63ba9-129">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="63ba9-129">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="63ba9-130">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="63ba9-130">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="63ba9-131">標頭</span><span class="sxs-lookup"><span data-stu-id="63ba9-131">Header</span></span></p></td>
<td><span data-ttu-id="63ba9-132">ConsoleApi .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="63ba9-132">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="63ba9-133">程式庫</span><span class="sxs-lookup"><span data-stu-id="63ba9-133">Library</span></span></p></td>
<td><span data-ttu-id="63ba9-134">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="63ba9-134">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="63ba9-135">DLL</span><span class="sxs-lookup"><span data-stu-id="63ba9-135">DLL</span></span></p></td>
<td><span data-ttu-id="63ba9-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="63ba9-136">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="63ba9-137"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="63ba9-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="63ba9-138">主控台功能</span><span class="sxs-lookup"><span data-stu-id="63ba9-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="63ba9-139">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="63ba9-139">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="63ba9-140">低層級主控台輸入函式</span><span class="sxs-lookup"><span data-stu-id="63ba9-140">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="63ba9-141">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="63ba9-141">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="63ba9-142">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="63ba9-142">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="63ba9-143">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="63ba9-143">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="63ba9-144">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="63ba9-144">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

 

 





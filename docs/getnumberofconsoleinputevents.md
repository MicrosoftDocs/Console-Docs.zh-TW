---
title: GetNumberOfConsoleInputEvents 函式
description: 抓取主控台輸入緩衝區中未讀取的輸入記錄數目。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
ms.openlocfilehash: 622dc96598df9a851934c73645afb7691f77f1be
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358858"
---
# <a name="getnumberofconsoleinputevents-function"></a><span data-ttu-id="bdeef-104">GetNumberOfConsoleInputEvents 函式</span><span class="sxs-lookup"><span data-stu-id="bdeef-104">GetNumberOfConsoleInputEvents function</span></span>

<span data-ttu-id="bdeef-105">抓取主控台輸入緩衝區中未讀取的輸入記錄數目。</span><span class="sxs-lookup"><span data-stu-id="bdeef-105">Retrieves the number of unread input records in the console's input buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="bdeef-106">語法</span><span class="sxs-lookup"><span data-stu-id="bdeef-106">Syntax</span></span>

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

## <a name="parameters"></a><span data-ttu-id="bdeef-107">參數</span><span class="sxs-lookup"><span data-stu-id="bdeef-107">Parameters</span></span>

<span data-ttu-id="bdeef-108">*hConsoleInput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="bdeef-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="bdeef-109">主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="bdeef-109">A handle to the console input buffer.</span></span> <span data-ttu-id="bdeef-110">控制代碼必須具有 **GENERIC\_READ** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="bdeef-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="bdeef-111">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="bdeef-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="bdeef-112">*lpcNumberOfEvents* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="bdeef-112">*lpcNumberOfEvents* \[out\]</span></span>  
<span data-ttu-id="bdeef-113">變數的指標，此變數會接收主控台輸入緩衝區中未讀取的輸入記錄數目。</span><span class="sxs-lookup"><span data-stu-id="bdeef-113">A pointer to a variable that receives the number of unread input records in the console's input buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="bdeef-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="bdeef-114">Return value</span></span>

<span data-ttu-id="bdeef-115">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="bdeef-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="bdeef-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="bdeef-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="bdeef-117">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="bdeef-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="bdeef-118">備註</span><span class="sxs-lookup"><span data-stu-id="bdeef-118">Remarks</span></span>

<span data-ttu-id="bdeef-119">**GetNumberOfConsoleInputEvents** 函式會報告輸入緩衝區中未讀取的輸入記錄總數，包括鍵盤、滑鼠和視窗大小的輸入記錄。</span><span class="sxs-lookup"><span data-stu-id="bdeef-119">The **GetNumberOfConsoleInputEvents** function reports the total number of unread input records in the input buffer, including keyboard, mouse, and window-resizing input records.</span></span> <span data-ttu-id="bdeef-120">使用 [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) 或 [**ReadConsole**](readconsole.md) 函數的進程只能讀取鍵盤輸入。</span><span class="sxs-lookup"><span data-stu-id="bdeef-120">Processes using the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) or [**ReadConsole**](readconsole.md) function can only read keyboard input.</span></span> <span data-ttu-id="bdeef-121">使用 [**ReadConsoleInput**](readconsoleinput.md) 函數的進程可以讀取所有類型的輸入記錄。</span><span class="sxs-lookup"><span data-stu-id="bdeef-121">Processes using the [**ReadConsoleInput**](readconsoleinput.md) function can read all types of input records.</span></span>

<span data-ttu-id="bdeef-122">進程可以在其中一個 [等候](/windows/win32/sync/wait-functions) 函式中指定主控台輸入緩衝區控制碼，以判斷何時有未讀取的主控台輸入。</span><span class="sxs-lookup"><span data-stu-id="bdeef-122">A process can specify a console input buffer handle in one of the [wait functions](/windows/win32/sync/wait-functions) to determine when there is unread console input.</span></span> <span data-ttu-id="bdeef-123">當輸入緩衝區不是空的時，主控台輸入緩衝區控制碼的狀態就會收到信號。</span><span class="sxs-lookup"><span data-stu-id="bdeef-123">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="bdeef-124">若要從主控台輸入緩衝區讀取輸入記錄，而不會影響未讀取的記錄數目，請使用 [**PeekConsoleInput**](peekconsoleinput.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="bdeef-124">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="bdeef-125">若要捨棄主控台輸入緩衝區中的所有未讀取記錄，請使用 [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="bdeef-125">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="bdeef-126">規格需求</span><span class="sxs-lookup"><span data-stu-id="bdeef-126">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="bdeef-127">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="bdeef-127">Minimum supported client</span></span> | <span data-ttu-id="bdeef-128">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="bdeef-128">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="bdeef-129">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="bdeef-129">Minimum supported server</span></span> | <span data-ttu-id="bdeef-130">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="bdeef-130">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="bdeef-131">標頭</span><span class="sxs-lookup"><span data-stu-id="bdeef-131">Header</span></span> | <span data-ttu-id="bdeef-132">ConsoleApi.h (透過 WinCon.h，包括 Windows.h)</span><span class="sxs-lookup"><span data-stu-id="bdeef-132">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="bdeef-133">程式庫</span><span class="sxs-lookup"><span data-stu-id="bdeef-133">Library</span></span> | <span data-ttu-id="bdeef-134">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="bdeef-134">Kernel32.lib</span></span> |
| <span data-ttu-id="bdeef-135">DLL</span><span class="sxs-lookup"><span data-stu-id="bdeef-135">DLL</span></span> | <span data-ttu-id="bdeef-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="bdeef-136">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="bdeef-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdeef-137">See also</span></span>

[<span data-ttu-id="bdeef-138">主控台函式</span><span class="sxs-lookup"><span data-stu-id="bdeef-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="bdeef-139">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="bdeef-139">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="bdeef-140">低層級主控台輸入函式</span><span class="sxs-lookup"><span data-stu-id="bdeef-140">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="bdeef-141">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="bdeef-141">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="bdeef-142">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="bdeef-142">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="bdeef-143">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="bdeef-143">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="bdeef-144">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="bdeef-144">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)
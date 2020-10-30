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
ms.openlocfilehash: b4cad78d35114c509f4e810a858e6ae3b8bfb644
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038686"
---
# <a name="getnumberofconsoleinputevents-function"></a><span data-ttu-id="8a06f-104">GetNumberOfConsoleInputEvents 函式</span><span class="sxs-lookup"><span data-stu-id="8a06f-104">GetNumberOfConsoleInputEvents function</span></span>

<span data-ttu-id="8a06f-105">抓取主控台輸入緩衝區中未讀取的輸入記錄數目。</span><span class="sxs-lookup"><span data-stu-id="8a06f-105">Retrieves the number of unread input records in the console's input buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a06f-106">語法</span><span class="sxs-lookup"><span data-stu-id="8a06f-106">Syntax</span></span>

```C
BOOL WINAPI GetNumberOfConsoleInputEvents(
  _In_  HANDLE  hConsoleInput,
  _Out_ LPDWORD lpcNumberOfEvents
);
```

## <a name="parameters"></a><span data-ttu-id="8a06f-107">參數</span><span class="sxs-lookup"><span data-stu-id="8a06f-107">Parameters</span></span>

<span data-ttu-id="8a06f-108">*hConsoleInput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="8a06f-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="8a06f-109">主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="8a06f-109">A handle to the console input buffer.</span></span> <span data-ttu-id="8a06f-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="8a06f-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="8a06f-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="8a06f-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="8a06f-112">*lpcNumberOfEvents* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="8a06f-112">*lpcNumberOfEvents* \[out\]</span></span>  
<span data-ttu-id="8a06f-113">變數的指標，此變數會接收主控台輸入緩衝區中未讀取的輸入記錄數目。</span><span class="sxs-lookup"><span data-stu-id="8a06f-113">A pointer to a variable that receives the number of unread input records in the console's input buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="8a06f-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="8a06f-114">Return value</span></span>

<span data-ttu-id="8a06f-115">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="8a06f-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="8a06f-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="8a06f-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="8a06f-117">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="8a06f-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="8a06f-118">備註</span><span class="sxs-lookup"><span data-stu-id="8a06f-118">Remarks</span></span>

<span data-ttu-id="8a06f-119">**GetNumberOfConsoleInputEvents** 函式會報告輸入緩衝區中未讀取的輸入記錄總數，包括鍵盤、滑鼠和視窗大小的輸入記錄。</span><span class="sxs-lookup"><span data-stu-id="8a06f-119">The **GetNumberOfConsoleInputEvents** function reports the total number of unread input records in the input buffer, including keyboard, mouse, and window-resizing input records.</span></span> <span data-ttu-id="8a06f-120">使用 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 或 [**ReadConsole**](readconsole.md) 函數的進程只能讀取鍵盤輸入。</span><span class="sxs-lookup"><span data-stu-id="8a06f-120">Processes using the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function can only read keyboard input.</span></span> <span data-ttu-id="8a06f-121">使用 [**ReadConsoleInput**](readconsoleinput.md) 函數的進程可以讀取所有類型的輸入記錄。</span><span class="sxs-lookup"><span data-stu-id="8a06f-121">Processes using the [**ReadConsoleInput**](readconsoleinput.md) function can read all types of input records.</span></span>

<span data-ttu-id="8a06f-122">進程可以在其中一個 [等候](https://msdn.microsoft.com/library/windows/desktop/ms687069) 函式中指定主控台輸入緩衝區控制碼，以判斷何時有未讀取的主控台輸入。</span><span class="sxs-lookup"><span data-stu-id="8a06f-122">A process can specify a console input buffer handle in one of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069) to determine when there is unread console input.</span></span> <span data-ttu-id="8a06f-123">當輸入緩衝區不是空的時，主控台輸入緩衝區控制碼的狀態就會收到信號。</span><span class="sxs-lookup"><span data-stu-id="8a06f-123">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="8a06f-124">若要從主控台輸入緩衝區讀取輸入記錄，而不會影響未讀取的記錄數目，請使用 [**PeekConsoleInput**](peekconsoleinput.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="8a06f-124">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="8a06f-125">若要捨棄主控台輸入緩衝區中的所有未讀取記錄，請使用 [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="8a06f-125">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="8a06f-126">規格需求</span><span class="sxs-lookup"><span data-stu-id="8a06f-126">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="8a06f-127">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="8a06f-127">Minimum supported client</span></span> | <span data-ttu-id="8a06f-128">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="8a06f-128">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="8a06f-129">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="8a06f-129">Minimum supported server</span></span> | <span data-ttu-id="8a06f-130">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="8a06f-130">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="8a06f-131">標頭</span><span class="sxs-lookup"><span data-stu-id="8a06f-131">Header</span></span> | <span data-ttu-id="8a06f-132">ConsoleApi .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="8a06f-132">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="8a06f-133">程式庫</span><span class="sxs-lookup"><span data-stu-id="8a06f-133">Library</span></span> | <span data-ttu-id="8a06f-134">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="8a06f-134">Kernel32.lib</span></span> |
| <span data-ttu-id="8a06f-135">DLL</span><span class="sxs-lookup"><span data-stu-id="8a06f-135">DLL</span></span> | <span data-ttu-id="8a06f-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="8a06f-136">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="8a06f-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="8a06f-137">See also</span></span>

[<span data-ttu-id="8a06f-138">主控台功能</span><span class="sxs-lookup"><span data-stu-id="8a06f-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="8a06f-139">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="8a06f-139">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="8a06f-140">低層級主控台輸入函式</span><span class="sxs-lookup"><span data-stu-id="8a06f-140">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="8a06f-141">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="8a06f-141">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="8a06f-142">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="8a06f-142">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="8a06f-143">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="8a06f-143">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="8a06f-144">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="8a06f-144">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

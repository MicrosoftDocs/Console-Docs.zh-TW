---
title: FlushConsoleInputBuffer 函式
description: 清空主控台輸入緩衝區。 目前在輸入緩衝區中的所有輸入記錄都會被捨棄。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
ms.openlocfilehash: c36191738e09911dc9cc7c441371616001d250db
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357558"
---
# <a name="flushconsoleinputbuffer-function"></a><span data-ttu-id="89c66-105">FlushConsoleInputBuffer 函式</span><span class="sxs-lookup"><span data-stu-id="89c66-105">FlushConsoleInputBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="89c66-106">清空主控台輸入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="89c66-106">Flushes the console input buffer.</span></span> <span data-ttu-id="89c66-107">目前在輸入緩衝區中的所有輸入記錄都會被捨棄。</span><span class="sxs-lookup"><span data-stu-id="89c66-107">All input records currently in the input buffer are discarded.</span></span>

## <a name="syntax"></a><span data-ttu-id="89c66-108">語法</span><span class="sxs-lookup"><span data-stu-id="89c66-108">Syntax</span></span>

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

## <a name="parameters"></a><span data-ttu-id="89c66-109">參數</span><span class="sxs-lookup"><span data-stu-id="89c66-109">Parameters</span></span>

<span data-ttu-id="89c66-110">*hConsoleInput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="89c66-110">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="89c66-111">主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="89c66-111">A handle to the console input buffer.</span></span> <span data-ttu-id="89c66-112">控點必須具有 **GENERIC\_WRITE** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="89c66-112">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="89c66-113">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="89c66-113">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="89c66-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="89c66-114">Return value</span></span>

<span data-ttu-id="89c66-115">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="89c66-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="89c66-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="89c66-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="89c66-117">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="89c66-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="89c66-118">備註</span><span class="sxs-lookup"><span data-stu-id="89c66-118">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="89c66-119">不建議使用此 API，也不會有對等的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="89c66-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="89c66-120">若嘗試一次清空輸入佇列，則會以非預期的方式損毀佇列中的狀態。</span><span class="sxs-lookup"><span data-stu-id="89c66-120">Attempting to empty the input queue all at once can destroy state in the queue in an unexpected manner.</span></span>

## <a name="requirements"></a><span data-ttu-id="89c66-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="89c66-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="89c66-122">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="89c66-122">Minimum supported client</span></span> | <span data-ttu-id="89c66-123">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="89c66-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="89c66-124">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="89c66-124">Minimum supported server</span></span> | <span data-ttu-id="89c66-125">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="89c66-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="89c66-126">標頭</span><span class="sxs-lookup"><span data-stu-id="89c66-126">Header</span></span> | <span data-ttu-id="89c66-127">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="89c66-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="89c66-128">程式庫</span><span class="sxs-lookup"><span data-stu-id="89c66-128">Library</span></span> | <span data-ttu-id="89c66-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="89c66-129">Kernel32.lib</span></span> |
| <span data-ttu-id="89c66-130">DLL</span><span class="sxs-lookup"><span data-stu-id="89c66-130">DLL</span></span> | <span data-ttu-id="89c66-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="89c66-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="89c66-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89c66-132">See also</span></span>

[<span data-ttu-id="89c66-133">主控台函式</span><span class="sxs-lookup"><span data-stu-id="89c66-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="89c66-134">低層級主控台輸入函式</span><span class="sxs-lookup"><span data-stu-id="89c66-134">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="89c66-135">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="89c66-135">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="89c66-136">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="89c66-136">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="89c66-137">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="89c66-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="89c66-138">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="89c66-138">**WriteConsoleInput**</span></span>](writeconsoleinput.md)
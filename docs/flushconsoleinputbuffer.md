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
ms.openlocfilehash: 543552e9252c1f28701a0b316b43597cdd9cd2c9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039046"
---
# <a name="flushconsoleinputbuffer-function"></a><span data-ttu-id="bf71b-105">FlushConsoleInputBuffer 函式</span><span class="sxs-lookup"><span data-stu-id="bf71b-105">FlushConsoleInputBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="bf71b-106">清空主控台輸入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="bf71b-106">Flushes the console input buffer.</span></span> <span data-ttu-id="bf71b-107">目前在輸入緩衝區中的所有輸入記錄都會被捨棄。</span><span class="sxs-lookup"><span data-stu-id="bf71b-107">All input records currently in the input buffer are discarded.</span></span>

## <a name="syntax"></a><span data-ttu-id="bf71b-108">語法</span><span class="sxs-lookup"><span data-stu-id="bf71b-108">Syntax</span></span>

```C
BOOL WINAPI FlushConsoleInputBuffer(
  _In_ HANDLE hConsoleInput
);
```

## <a name="parameters"></a><span data-ttu-id="bf71b-109">參數</span><span class="sxs-lookup"><span data-stu-id="bf71b-109">Parameters</span></span>

<span data-ttu-id="bf71b-110">*hConsoleInput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="bf71b-110">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="bf71b-111">主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="bf71b-111">A handle to the console input buffer.</span></span> <span data-ttu-id="bf71b-112">控制碼必須有 **一般 \_ 寫入** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="bf71b-112">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="bf71b-113">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="bf71b-113">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="bf71b-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="bf71b-114">Return value</span></span>

<span data-ttu-id="bf71b-115">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="bf71b-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="bf71b-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="bf71b-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="bf71b-117">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="bf71b-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="bf71b-118">備註</span><span class="sxs-lookup"><span data-stu-id="bf71b-118">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="bf71b-119">不建議使用此 API，也不會有對等的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="bf71b-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="bf71b-120">若嘗試一次清空輸入佇列，則會以非預期的方式損毀佇列中的狀態。</span><span class="sxs-lookup"><span data-stu-id="bf71b-120">Attempting to empty the input queue all at once can destroy state in the queue in an unexpected manner.</span></span>

## <a name="requirements"></a><span data-ttu-id="bf71b-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="bf71b-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="bf71b-122">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="bf71b-122">Minimum supported client</span></span> | <span data-ttu-id="bf71b-123">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="bf71b-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="bf71b-124">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="bf71b-124">Minimum supported server</span></span> | <span data-ttu-id="bf71b-125">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="bf71b-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="bf71b-126">標頭</span><span class="sxs-lookup"><span data-stu-id="bf71b-126">Header</span></span> | <span data-ttu-id="bf71b-127">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="bf71b-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="bf71b-128">程式庫</span><span class="sxs-lookup"><span data-stu-id="bf71b-128">Library</span></span> | <span data-ttu-id="bf71b-129">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="bf71b-129">Kernel32.lib</span></span> |
| <span data-ttu-id="bf71b-130">DLL</span><span class="sxs-lookup"><span data-stu-id="bf71b-130">DLL</span></span> | <span data-ttu-id="bf71b-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="bf71b-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="bf71b-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="bf71b-132">See also</span></span>

[<span data-ttu-id="bf71b-133">主控台功能</span><span class="sxs-lookup"><span data-stu-id="bf71b-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="bf71b-134">低層級主控台輸入函式</span><span class="sxs-lookup"><span data-stu-id="bf71b-134">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="bf71b-135">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="bf71b-135">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="bf71b-136">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="bf71b-136">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="bf71b-137">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="bf71b-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="bf71b-138">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="bf71b-138">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

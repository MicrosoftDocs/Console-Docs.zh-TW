---
title: ReadConsoleInput 函式
description: 從主控台輸入緩衝區讀取資料，並將其從緩衝區中移除。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/ReadConsoleInput
- wincon/ReadConsoleInput
- ReadConsoleInput
- consoleapi/ReadConsoleInputA
- wincon/ReadConsoleInputA
- ReadConsoleInputA
- consoleapi/ReadConsoleInputW
- wincon/ReadConsoleInputW
- ReadConsoleInputW
MS-HAID:
- '\_win32\_readconsoleinput'
- base.readconsoleinput
- consoles.readconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5a9f7b18-cdea-4041-a377-5532d30e0105
topic_type:
- apiref
api_name:
- ReadConsoleInput
- ReadConsoleInputA
- ReadConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 38778931522dff8d1d000bb6f0ce13c2849d76db
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039486"
---
# <a name="readconsoleinput-function"></a><span data-ttu-id="b9d53-104">ReadConsoleInput 函式</span><span class="sxs-lookup"><span data-stu-id="b9d53-104">ReadConsoleInput function</span></span>

<span data-ttu-id="b9d53-105">從主控台輸入緩衝區讀取資料，並將其從緩衝區中移除。</span><span class="sxs-lookup"><span data-stu-id="b9d53-105">Reads data from a console input buffer and removes it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="b9d53-106">語法</span><span class="sxs-lookup"><span data-stu-id="b9d53-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## <a name="parameters"></a><span data-ttu-id="b9d53-107">參數</span><span class="sxs-lookup"><span data-stu-id="b9d53-107">Parameters</span></span>

<span data-ttu-id="b9d53-108">*hConsoleInput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="b9d53-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="b9d53-109">主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="b9d53-109">A handle to the console input buffer.</span></span> <span data-ttu-id="b9d53-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="b9d53-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="b9d53-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="b9d53-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="b9d53-112">*lpBuffer* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="b9d53-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="b9d53-113">接收輸入緩衝區資料之 [**輸入 \_ 記錄**](input-record-str.md) 結構陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="b9d53-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="b9d53-114">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="b9d53-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="b9d53-115">陣列元素中 *lpBuffer* 參數所指向的陣列大小。</span><span class="sxs-lookup"><span data-stu-id="b9d53-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="b9d53-116">*lpNumberOfEventsRead* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="b9d53-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="b9d53-117">變數的指標，此變數會接收讀取的輸入記錄數目。</span><span class="sxs-lookup"><span data-stu-id="b9d53-117">A pointer to a variable that receives the number of input records read.</span></span>

## <a name="return-value"></a><span data-ttu-id="b9d53-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="b9d53-118">Return value</span></span>

<span data-ttu-id="b9d53-119">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="b9d53-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b9d53-120">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="b9d53-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b9d53-121">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="b9d53-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="b9d53-122">備註</span><span class="sxs-lookup"><span data-stu-id="b9d53-122">Remarks</span></span>

<span data-ttu-id="b9d53-123">如果 *nLength* 參數中要求的記錄數目超過緩衝區中的可用記錄數目，則會讀取可用的數目。</span><span class="sxs-lookup"><span data-stu-id="b9d53-123">If the number of records requested in the *nLength* parameter exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="b9d53-124">在至少讀取一個輸入記錄之前，函式不會傳回。</span><span class="sxs-lookup"><span data-stu-id="b9d53-124">The function does not return until at least one input record has been read.</span></span>

<span data-ttu-id="b9d53-125">進程可以在其中一個 [等候](https://msdn.microsoft.com/library/windows/desktop/ms687069) 函式中指定主控台輸入緩衝區控制碼，以判斷何時有未讀取的主控台輸入。</span><span class="sxs-lookup"><span data-stu-id="b9d53-125">A process can specify a console input buffer handle in one of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069) to determine when there is unread console input.</span></span> <span data-ttu-id="b9d53-126">當輸入緩衝區不是空的時，主控台輸入緩衝區控制碼的狀態就會收到信號。</span><span class="sxs-lookup"><span data-stu-id="b9d53-126">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="b9d53-127">若要判斷主控台輸入緩衝區中未讀取的輸入記錄數目，請使用 [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="b9d53-127">To determine the number of unread input records in a console's input buffer, use the [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) function.</span></span> <span data-ttu-id="b9d53-128">若要從主控台輸入緩衝區讀取輸入記錄，而不會影響未讀取的記錄數目，請使用 [**PeekConsoleInput**](peekconsoleinput.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="b9d53-128">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="b9d53-129">若要捨棄主控台輸入緩衝區中的所有未讀取記錄，請使用 [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="b9d53-129">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="examples"></a><span data-ttu-id="b9d53-130">範例</span><span class="sxs-lookup"><span data-stu-id="b9d53-130">Examples</span></span>

<span data-ttu-id="b9d53-131">如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。</span><span class="sxs-lookup"><span data-stu-id="b9d53-131">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="b9d53-132">規格需求</span><span class="sxs-lookup"><span data-stu-id="b9d53-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b9d53-133">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="b9d53-133">Minimum supported client</span></span> | <span data-ttu-id="b9d53-134">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="b9d53-134">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="b9d53-135">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="b9d53-135">Minimum supported server</span></span> | <span data-ttu-id="b9d53-136">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="b9d53-136">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="b9d53-137">標頭</span><span class="sxs-lookup"><span data-stu-id="b9d53-137">Header</span></span> | <span data-ttu-id="b9d53-138">ConsoleApi .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="b9d53-138">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="b9d53-139">程式庫</span><span class="sxs-lookup"><span data-stu-id="b9d53-139">Library</span></span> | <span data-ttu-id="b9d53-140">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="b9d53-140">Kernel32.lib</span></span> |
| <span data-ttu-id="b9d53-141">DLL</span><span class="sxs-lookup"><span data-stu-id="b9d53-141">DLL</span></span> | <span data-ttu-id="b9d53-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b9d53-142">Kernel32.dll</span></span> |
| <span data-ttu-id="b9d53-143">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="b9d53-143">Unicode and ANSI names</span></span> | <span data-ttu-id="b9d53-144">**ReadConsoleInputW** (Unicode) 和 **ReadConsoleInputA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="b9d53-144">**ReadConsoleInputW** (Unicode) and **ReadConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="b9d53-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="b9d53-145">See also</span></span>

[<span data-ttu-id="b9d53-146">主控台功能</span><span class="sxs-lookup"><span data-stu-id="b9d53-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b9d53-147">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="b9d53-147">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="b9d53-148">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="b9d53-148">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="b9d53-149">**輸入 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="b9d53-149">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="b9d53-150">低層級主控台輸入函式</span><span class="sxs-lookup"><span data-stu-id="b9d53-150">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="b9d53-151">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="b9d53-151">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="b9d53-152">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="b9d53-152">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="b9d53-153">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="b9d53-153">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="b9d53-154">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="b9d53-154">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="b9d53-155">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="b9d53-155">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="b9d53-156">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="b9d53-156">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

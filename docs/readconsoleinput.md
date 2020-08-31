---
title: ReadConsoleInput 函式
description: 從主控台輸入緩衝區讀取資料，並將其從緩衝區中移除。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
ms.openlocfilehash: 38a5ee0d1572d6e40ab103cfc402d616a99d2ca5
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059470"
---
# <a name="readconsoleinput-function"></a><span data-ttu-id="3ce4c-104">ReadConsoleInput 函式</span><span class="sxs-lookup"><span data-stu-id="3ce4c-104">ReadConsoleInput function</span></span>


<span data-ttu-id="3ce4c-105">從主控台輸入緩衝區讀取資料，並將其從緩衝區中移除。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-105">Reads data from a console input buffer and removes it from the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="3ce4c-106">語法</span><span class="sxs-lookup"><span data-stu-id="3ce4c-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

<a name="parameters"></a><span data-ttu-id="3ce4c-107">參數</span><span class="sxs-lookup"><span data-stu-id="3ce4c-107">Parameters</span></span>
----------

<span data-ttu-id="3ce4c-108">*hConsoleInput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="3ce4c-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="3ce4c-109">主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-109">A handle to the console input buffer.</span></span> <span data-ttu-id="3ce4c-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="3ce4c-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="3ce4c-112">*lpBuffer* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="3ce4c-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="3ce4c-113">接收輸入緩衝區資料之 [**輸入 \_ 記錄**](input-record-str.md) 結構陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="3ce4c-114">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="3ce4c-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="3ce4c-115">陣列元素中 *lpBuffer* 參數所指向的陣列大小。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="3ce4c-116">*lpNumberOfEventsRead* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="3ce4c-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="3ce4c-117">變數的指標，此變數會接收讀取的輸入記錄數目。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-117">A pointer to a variable that receives the number of input records read.</span></span>

<a name="return-value"></a><span data-ttu-id="3ce4c-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="3ce4c-118">Return value</span></span>
------------

<span data-ttu-id="3ce4c-119">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="3ce4c-120">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="3ce4c-121">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="3ce4c-122">備註</span><span class="sxs-lookup"><span data-stu-id="3ce4c-122">Remarks</span></span>
-------

<span data-ttu-id="3ce4c-123">如果 *nLength* 參數中要求的記錄數目超過緩衝區中的可用記錄數目，則會讀取可用的數目。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-123">If the number of records requested in the *nLength* parameter exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="3ce4c-124">在至少讀取一個輸入記錄之前，函式不會傳回。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-124">The function does not return until at least one input record has been read.</span></span>

<span data-ttu-id="3ce4c-125">進程可以在其中一個 [等候](https://msdn.microsoft.com/library/windows/desktop/ms687069) 函式中指定主控台輸入緩衝區控制碼，以判斷何時有未讀取的主控台輸入。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-125">A process can specify a console input buffer handle in one of the [wait functions](https://msdn.microsoft.com/library/windows/desktop/ms687069) to determine when there is unread console input.</span></span> <span data-ttu-id="3ce4c-126">當輸入緩衝區不是空的時，主控台輸入緩衝區控制碼的狀態就會收到信號。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-126">When the input buffer is not empty, the state of a console input buffer handle is signaled.</span></span>

<span data-ttu-id="3ce4c-127">若要判斷主控台輸入緩衝區中未讀取的輸入記錄數目，請使用 [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-127">To determine the number of unread input records in a console's input buffer, use the [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) function.</span></span> <span data-ttu-id="3ce4c-128">若要從主控台輸入緩衝區讀取輸入記錄，而不會影響未讀取的記錄數目，請使用 [**PeekConsoleInput**](peekconsoleinput.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-128">To read input records from a console input buffer without affecting the number of unread records, use the [**PeekConsoleInput**](peekconsoleinput.md) function.</span></span> <span data-ttu-id="3ce4c-129">若要捨棄主控台輸入緩衝區中的所有未讀取記錄，請使用 [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-129">To discard all unread records in a console's input buffer, use the [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) function.</span></span>

<span data-ttu-id="3ce4c-130">此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-130">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="3ce4c-131">主控台的字碼頁一開始預設為系統的 OEM 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-131">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="3ce4c-132">若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 或 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函式，或使用 **chcp** 或 **mode con cp select =** 命令。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-132">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="3ce4c-133">範例</span><span class="sxs-lookup"><span data-stu-id="3ce4c-133">Examples</span></span>
--------

<span data-ttu-id="3ce4c-134">如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce4c-134">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="3ce4c-135">規格需求</span><span class="sxs-lookup"><span data-stu-id="3ce4c-135">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="3ce4c-136">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="3ce4c-136">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="3ce4c-137">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="3ce4c-137">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3ce4c-138">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="3ce4c-138">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="3ce4c-139">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="3ce4c-139">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3ce4c-140">標頭</span><span class="sxs-lookup"><span data-stu-id="3ce4c-140">Header</span></span></p></td>
<td><span data-ttu-id="3ce4c-141">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="3ce4c-141">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3ce4c-142">程式庫</span><span class="sxs-lookup"><span data-stu-id="3ce4c-142">Library</span></span></p></td>
<td><span data-ttu-id="3ce4c-143">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="3ce4c-143">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3ce4c-144">DLL</span><span class="sxs-lookup"><span data-stu-id="3ce4c-144">DLL</span></span></p></td>
<td><span data-ttu-id="3ce4c-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3ce4c-145">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3ce4c-146">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="3ce4c-146">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="3ce4c-147"><strong>ReadConsoleInputW</strong> (Unicode) 和 <strong>ReadConsoleInputA</strong> (ANSI) </span><span class="sxs-lookup"><span data-stu-id="3ce4c-147"><strong>ReadConsoleInputW</strong> (Unicode) and <strong>ReadConsoleInputA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="3ce4c-148"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ce4c-148"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="3ce4c-149">主控台功能</span><span class="sxs-lookup"><span data-stu-id="3ce4c-149">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3ce4c-150">**FlushConsoleInputBuffer**</span><span class="sxs-lookup"><span data-stu-id="3ce4c-150">**FlushConsoleInputBuffer**</span></span>](flushconsoleinputbuffer.md)

[<span data-ttu-id="3ce4c-151">**GetNumberOfConsoleInputEvents**</span><span class="sxs-lookup"><span data-stu-id="3ce4c-151">**GetNumberOfConsoleInputEvents**</span></span>](getnumberofconsoleinputevents.md)

[<span data-ttu-id="3ce4c-152">**輸入 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="3ce4c-152">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="3ce4c-153">低層級主控台輸入函式</span><span class="sxs-lookup"><span data-stu-id="3ce4c-153">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="3ce4c-154">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="3ce4c-154">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="3ce4c-155">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="3ce4c-155">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="3ce4c-156">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="3ce4c-156">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="3ce4c-157">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="3ce4c-157">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="3ce4c-158">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="3ce4c-158">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="3ce4c-159">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="3ce4c-159">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

 

 





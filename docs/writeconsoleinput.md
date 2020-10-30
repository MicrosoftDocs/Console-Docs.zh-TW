---
title: WriteConsoleInput 函式
description: 請參閱 WriteConsoleInput 函式的參考資訊，此函式會將資料直接寫入主控台輸入緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/WriteConsoleInput
- wincon/WriteConsoleInput
- WriteConsoleInput
- consoleapi2/WriteConsoleInputA
- wincon/WriteConsoleInputA
- WriteConsoleInputA
- consoleapi2/WriteConsoleInputW
- wincon/WriteConsoleInputW
- WriteConsoleInputW
MS-HAID:
- '\_win32\_writeconsoleinput'
- base.writeconsoleinput
- consoles.writeconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad06231f-5063-4aff-b14d-8df5e6e42430
topic_type:
- apiref
api_name:
- WriteConsoleInput
- WriteConsoleInputA
- WriteConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: dc2c7930ab76587edc9ae1991d4493c858b0ec30
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039286"
---
# <a name="writeconsoleinput-function"></a><span data-ttu-id="0f568-104">WriteConsoleInput 函式</span><span class="sxs-lookup"><span data-stu-id="0f568-104">WriteConsoleInput function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="0f568-105">將資料直接寫入主控台輸入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0f568-105">Writes data directly to the console input buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f568-106">語法</span><span class="sxs-lookup"><span data-stu-id="0f568-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="0f568-107">參數</span><span class="sxs-lookup"><span data-stu-id="0f568-107">Parameters</span></span>

<span data-ttu-id="0f568-108">*hConsoleInput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="0f568-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="0f568-109">主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="0f568-109">A handle to the console input buffer.</span></span> <span data-ttu-id="0f568-110">控制碼必須有 **一般 \_ 寫入** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="0f568-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="0f568-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="0f568-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="0f568-112">*lpBuffer* \[在\]</span><span class="sxs-lookup"><span data-stu-id="0f568-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="0f568-113">[**輸入 \_ 記錄**](input-record-str.md)結構陣列的指標，其中包含要寫入至輸入緩衝區的資料。</span><span class="sxs-lookup"><span data-stu-id="0f568-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that contain data to be written to the input buffer.</span></span>

<span data-ttu-id="0f568-114">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="0f568-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="0f568-115">要寫入的輸入記錄數目。</span><span class="sxs-lookup"><span data-stu-id="0f568-115">The number of input records to be written.</span></span>

<span data-ttu-id="0f568-116">*lpNumberOfEventsWritten* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="0f568-116">*lpNumberOfEventsWritten* \[out\]</span></span>  
<span data-ttu-id="0f568-117">變數的指標，此變數會接收實際寫入之輸入記錄的數目。</span><span class="sxs-lookup"><span data-stu-id="0f568-117">A pointer to a variable that receives the number of input records actually written.</span></span>

## <a name="return-value"></a><span data-ttu-id="0f568-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="0f568-118">Return value</span></span>

<span data-ttu-id="0f568-119">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="0f568-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0f568-120">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="0f568-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0f568-121">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="0f568-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="0f568-122">備註</span><span class="sxs-lookup"><span data-stu-id="0f568-122">Remarks</span></span>

<span data-ttu-id="0f568-123">**WriteConsoleInput** 會將輸入記錄放入緩衝區中任何暫止事件後方的輸入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="0f568-123">**WriteConsoleInput** places input records into the input buffer behind any pending events in the buffer.</span></span> <span data-ttu-id="0f568-124">視需要，輸入緩衝區會動態成長，以保存所寫入的事件數目。</span><span class="sxs-lookup"><span data-stu-id="0f568-124">The input buffer grows dynamically, if necessary, to hold as many events as are written.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="0f568-125">不建議使用此 API，也不會有對等的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="0f568-125">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="0f568-126">這種決策刻意將 Windows 平臺與其他作業系統對齊。</span><span class="sxs-lookup"><span data-stu-id="0f568-126">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="0f568-127">這項作業會被視為這個緩衝區的 **[錯誤方式動詞](console-buffer-security-and-access-rights.md#wrong-way-verbs)** 。</span><span class="sxs-lookup"><span data-stu-id="0f568-127">This operation is considered the **[wrong-way verb](console-buffer-security-and-access-rights.md#wrong-way-verbs)** for this buffer.</span></span> <span data-ttu-id="0f568-128">使用此 API 時，透過跨平臺公用程式和傳輸（如 SSH）的應用程式遠端執行可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="0f568-128">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="0f568-129">規格需求</span><span class="sxs-lookup"><span data-stu-id="0f568-129">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0f568-130">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="0f568-130">Minimum supported client</span></span> | <span data-ttu-id="0f568-131">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="0f568-131">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="0f568-132">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="0f568-132">Minimum supported server</span></span> | <span data-ttu-id="0f568-133">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="0f568-133">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="0f568-134">標頭</span><span class="sxs-lookup"><span data-stu-id="0f568-134">Header</span></span> | <span data-ttu-id="0f568-135">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="0f568-135">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="0f568-136">程式庫</span><span class="sxs-lookup"><span data-stu-id="0f568-136">Library</span></span> | <span data-ttu-id="0f568-137">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="0f568-137">Kernel32.lib</span></span> |
| <span data-ttu-id="0f568-138">DLL</span><span class="sxs-lookup"><span data-stu-id="0f568-138">DLL</span></span> | <span data-ttu-id="0f568-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0f568-139">Kernel32.dll</span></span> |
| <span data-ttu-id="0f568-140">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="0f568-140">Unicode and ANSI names</span></span> | <span data-ttu-id="0f568-141">**WriteConsoleInputW** (Unicode) 和 **WriteConsoleInputA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="0f568-141">**WriteConsoleInputW** (Unicode) and **WriteConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="0f568-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="0f568-142">See also</span></span>

[<span data-ttu-id="0f568-143">主控台功能</span><span class="sxs-lookup"><span data-stu-id="0f568-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0f568-144">**輸入 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="0f568-144">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="0f568-145">低層級主控台輸入函式</span><span class="sxs-lookup"><span data-stu-id="0f568-145">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="0f568-146">**MapVirtualKey**</span><span class="sxs-lookup"><span data-stu-id="0f568-146">**MapVirtualKey**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646306)

[<span data-ttu-id="0f568-147">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="0f568-147">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="0f568-148">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="0f568-148">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="0f568-149">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="0f568-149">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="0f568-150">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="0f568-150">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="0f568-151">**VkKeyScan**</span><span class="sxs-lookup"><span data-stu-id="0f568-151">**VkKeyScan**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646329)

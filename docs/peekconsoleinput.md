---
title: PeekConsoleInput 函式
description: 從指定的主控台輸入緩衝區讀取資料，而不將它從緩衝區中移除。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/PeekConsoleInput
- wincon/PeekConsoleInput
- PeekConsoleInput
- consoleapi/PeekConsoleInputA
- wincon/PeekConsoleInputA
- PeekConsoleInputA
- consoleapi/PeekConsoleInputW
- wincon/PeekConsoleInputW
- PeekConsoleInputW
MS-HAID:
- '\_win32\_peekconsoleinput'
- base.peekconsoleinput
- consoles.peekconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9982dc20-43bd-4ee3-a68d-157c9134daca
topic_type:
- apiref
api_name:
- PeekConsoleInput
- PeekConsoleInputA
- PeekConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 9052f15b36e16dd2ddf7fe46d3d201aa21403f91
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039496"
---
# <a name="peekconsoleinput-function"></a><span data-ttu-id="04a87-104">PeekConsoleInput 函式</span><span class="sxs-lookup"><span data-stu-id="04a87-104">PeekConsoleInput function</span></span>

<span data-ttu-id="04a87-105">從指定的主控台輸入緩衝區讀取資料，而不將它從緩衝區中移除。</span><span class="sxs-lookup"><span data-stu-id="04a87-105">Reads data from the specified console input buffer without removing it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="04a87-106">語法</span><span class="sxs-lookup"><span data-stu-id="04a87-106">Syntax</span></span>

```C
BOOL WINAPI PeekConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

## <a name="parameters"></a><span data-ttu-id="04a87-107">參數</span><span class="sxs-lookup"><span data-stu-id="04a87-107">Parameters</span></span>

<span data-ttu-id="04a87-108">*hConsoleInput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="04a87-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="04a87-109">主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="04a87-109">A handle to the console input buffer.</span></span> <span data-ttu-id="04a87-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="04a87-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="04a87-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="04a87-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="04a87-112">*lpBuffer* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="04a87-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="04a87-113">接收輸入緩衝區資料之 [**輸入 \_ 記錄**](input-record-str.md) 結構陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="04a87-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="04a87-114">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="04a87-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="04a87-115">陣列元素中 *lpBuffer* 參數所指向的陣列大小。</span><span class="sxs-lookup"><span data-stu-id="04a87-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="04a87-116">*lpNumberOfEventsRead* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="04a87-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="04a87-117">變數的指標，此變數會接收讀取的輸入記錄數目。</span><span class="sxs-lookup"><span data-stu-id="04a87-117">A pointer to a variable that receives the number of input records read.</span></span>

## <a name="return-value"></a><span data-ttu-id="04a87-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="04a87-118">Return value</span></span>

<span data-ttu-id="04a87-119">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="04a87-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="04a87-120">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="04a87-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="04a87-121">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="04a87-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="04a87-122">備註</span><span class="sxs-lookup"><span data-stu-id="04a87-122">Remarks</span></span>

<span data-ttu-id="04a87-123">如果要求的記錄數目超過緩衝區中可用的記錄數目，則會讀取可用的數目。</span><span class="sxs-lookup"><span data-stu-id="04a87-123">If the number of records requested exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="04a87-124">如果沒有可用的資料，函數會立即傳回。</span><span class="sxs-lookup"><span data-stu-id="04a87-124">If no data is available, the function returns immediately.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

## <a name="requirements"></a><span data-ttu-id="04a87-125">規格需求</span><span class="sxs-lookup"><span data-stu-id="04a87-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="04a87-126">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="04a87-126">Minimum supported client</span></span> | <span data-ttu-id="04a87-127">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="04a87-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="04a87-128">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="04a87-128">Minimum supported server</span></span> | <span data-ttu-id="04a87-129">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="04a87-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="04a87-130">標頭</span><span class="sxs-lookup"><span data-stu-id="04a87-130">Header</span></span> | <span data-ttu-id="04a87-131">ConsoleApi .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="04a87-131">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="04a87-132">程式庫</span><span class="sxs-lookup"><span data-stu-id="04a87-132">Library</span></span> | <span data-ttu-id="04a87-133">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="04a87-133">Kernel32.lib</span></span> |
| <span data-ttu-id="04a87-134">DLL</span><span class="sxs-lookup"><span data-stu-id="04a87-134">DLL</span></span> | <span data-ttu-id="04a87-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="04a87-135">Kernel32.dll</span></span> |
| <span data-ttu-id="04a87-136">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="04a87-136">Unicode and ANSI names</span></span> | <span data-ttu-id="04a87-137">**PeekConsoleInputW** (Unicode) 和 **PeekConsoleInputA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="04a87-137">**PeekConsoleInputW** (Unicode) and **PeekConsoleInputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="04a87-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="04a87-138">See also</span></span>

[<span data-ttu-id="04a87-139">主控台功能</span><span class="sxs-lookup"><span data-stu-id="04a87-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="04a87-140">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="04a87-140">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="04a87-141">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="04a87-141">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="04a87-142">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="04a87-142">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="04a87-143">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="04a87-143">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

[<span data-ttu-id="04a87-144">**輸入 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="04a87-144">**INPUT\_RECORD**</span></span>](input-record-str.md)

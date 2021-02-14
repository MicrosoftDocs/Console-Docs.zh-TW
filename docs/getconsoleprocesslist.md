---
title: GetConsoleProcessList 函式
description: 請參閱 GetConsoleProcessList 函式的參考資訊，此函式會抓取連接到目前主控台的進程清單。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetConsoleProcessList
- wincon/GetConsoleProcessList
- GetConsoleProcessList
MS-HAID:
- '\_win32\_getconsoleprocesslist'
- base.getconsoleprocesslist
- consoles.getconsoleprocesslist
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3d21103b-662d-4393-ae3f-773cd9e4a930
topic_type:
- apiref
api_name:
- GetConsoleProcessList
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: b067d701b2568165a4cf0f9368c37a06ba6863c8
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358938"
---
# <a name="getconsoleprocesslist-function"></a><span data-ttu-id="7a717-104">GetConsoleProcessList 函式</span><span class="sxs-lookup"><span data-stu-id="7a717-104">GetConsoleProcessList function</span></span>

<span data-ttu-id="7a717-105">抓取附加至目前主控台的進程清單。</span><span class="sxs-lookup"><span data-stu-id="7a717-105">Retrieves a list of the processes attached to the current console.</span></span>

## <a name="syntax"></a><span data-ttu-id="7a717-106">語法</span><span class="sxs-lookup"><span data-stu-id="7a717-106">Syntax</span></span>

```C
DWORD WINAPI GetConsoleProcessList(
  _Out_ LPDWORD lpdwProcessList,
  _In_  DWORD   dwProcessCount
);
```

## <a name="parameters"></a><span data-ttu-id="7a717-107">參數</span><span class="sxs-lookup"><span data-stu-id="7a717-107">Parameters</span></span>

<span data-ttu-id="7a717-108">*lpdwProcessList* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="7a717-108">*lpdwProcessList* \[out\]</span></span>  
<span data-ttu-id="7a717-109">在成功時收到進程識別碼陣列的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="7a717-109">A pointer to a buffer that receives an array of process identifiers upon success.</span></span> <span data-ttu-id="7a717-110">這必須是有效的緩衝區，而且不能是 `NULL` 。</span><span class="sxs-lookup"><span data-stu-id="7a717-110">This must be a valid buffer and cannot be `NULL`.</span></span> <span data-ttu-id="7a717-111">緩衝區必須有空間，才能接收至少一個傳回的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="7a717-111">The buffer must have space to receive at least 1 returned process id.</span></span>

<span data-ttu-id="7a717-112">*dwProcessCount* \[在\]</span><span class="sxs-lookup"><span data-stu-id="7a717-112">*dwProcessCount* \[in\]</span></span>  
<span data-ttu-id="7a717-113">可以儲存在 *lpdwProcessList* 緩衝區中的處理序識別碼數目上限。</span><span class="sxs-lookup"><span data-stu-id="7a717-113">The maximum number of process identifiers that can be stored in the *lpdwProcessList* buffer.</span></span> <span data-ttu-id="7a717-114">這必須大於0。</span><span class="sxs-lookup"><span data-stu-id="7a717-114">This must be greater than 0.</span></span>

## <a name="return-value"></a><span data-ttu-id="7a717-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="7a717-115">Return value</span></span>

<span data-ttu-id="7a717-116">如果函式成功，則傳回值小於或等於 *dwProcessCount* ，而且代表 *lpdwProcessList* 緩衝區中儲存的進程識別碼數目。</span><span class="sxs-lookup"><span data-stu-id="7a717-116">If the function succeeds, the return value is less than or equal to *dwProcessCount* and represents the number of process identifiers stored in the *lpdwProcessList* buffer.</span></span>

<span data-ttu-id="7a717-117">如果緩衝區太小而無法容納所有有效的處理序識別碼，則傳回值是必要的陣列元素數目。</span><span class="sxs-lookup"><span data-stu-id="7a717-117">If the buffer is too small to hold all the valid process identifiers, the return value is the required number of array elements.</span></span> <span data-ttu-id="7a717-118">此函數將不會在緩衝區中儲存任何識別碼。</span><span class="sxs-lookup"><span data-stu-id="7a717-118">The function will have stored no identifiers in the buffer.</span></span> <span data-ttu-id="7a717-119">在這種情況下，請使用傳回值配置夠大的緩衝區來儲存整個清單，然後再次呼叫函數。</span><span class="sxs-lookup"><span data-stu-id="7a717-119">In this situation, use the return value to allocate a buffer that is large enough to store the entire list and call the function again.</span></span>

<span data-ttu-id="7a717-120">如果傳回值為零，則函式失敗，因為每個主控台至少有一個相關聯的進程。</span><span class="sxs-lookup"><span data-stu-id="7a717-120">If the return value is zero, the function has failed, because every console has at least one process associated with it.</span></span> <span data-ttu-id="7a717-121">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="7a717-121">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

<span data-ttu-id="7a717-122">如果 `NULL` 提供了進程清單，或進程計數是0，則呼叫會傳回0，而且 `GetLastError` 會傳回 `ERROR_INVALID_PARAMETER` 。</span><span class="sxs-lookup"><span data-stu-id="7a717-122">If a `NULL` process list was provided or the process count was 0, the call will return 0 and `GetLastError` will return `ERROR_INVALID_PARAMETER`.</span></span> <span data-ttu-id="7a717-123">請提供至少一個元素的緩衝區，以呼叫此函數。</span><span class="sxs-lookup"><span data-stu-id="7a717-123">Please provide a buffer of at least one element to call this function.</span></span> <span data-ttu-id="7a717-124">配置較大的緩衝區，並在傳回碼大於所提供緩衝區的長度時再呼叫一次。</span><span class="sxs-lookup"><span data-stu-id="7a717-124">Allocate a larger buffer and call again if the return code is larger than the length of the provided buffer.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a717-125">備註</span><span class="sxs-lookup"><span data-stu-id="7a717-125">Remarks</span></span>

<span data-ttu-id="7a717-126">若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0501 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7a717-126">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0501 or later.</span></span> <span data-ttu-id="7a717-127">如需詳細資訊，請參閱 [使用 Windows 標頭](/windows/win32/winprog/using-the-windows-headers)。</span><span class="sxs-lookup"><span data-stu-id="7a717-127">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

## <a name="requirements"></a><span data-ttu-id="7a717-128">規格需求</span><span class="sxs-lookup"><span data-stu-id="7a717-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="7a717-129">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="7a717-129">Minimum supported client</span></span> | <span data-ttu-id="7a717-130">\[僅限 WINDOWS XP desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="7a717-130">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="7a717-131">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="7a717-131">Minimum supported server</span></span> | <span data-ttu-id="7a717-132">僅限 Windows Server 2003 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="7a717-132">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="7a717-133">標頭</span><span class="sxs-lookup"><span data-stu-id="7a717-133">Header</span></span> | <span data-ttu-id="7a717-134">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="7a717-134">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="7a717-135">程式庫</span><span class="sxs-lookup"><span data-stu-id="7a717-135">Library</span></span> | <span data-ttu-id="7a717-136">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="7a717-136">Kernel32.lib</span></span> |
| <span data-ttu-id="7a717-137">DLL</span><span class="sxs-lookup"><span data-stu-id="7a717-137">DLL</span></span> | <span data-ttu-id="7a717-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7a717-138">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="7a717-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a717-139">See also</span></span>

[<span data-ttu-id="7a717-140">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="7a717-140">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="7a717-141">主控台函式</span><span class="sxs-lookup"><span data-stu-id="7a717-141">Console Functions</span></span>](console-functions.md)
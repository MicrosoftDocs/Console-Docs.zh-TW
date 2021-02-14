---
title: SetStdHandle 函式
description: 設定指定標準裝置的控制碼 (標準輸入、標準輸出或標準錯誤) 。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- processenv/SetStdHandle
- winbase/SetStdHandle
- SetStdHandle
MS-HAID:
- '\_win32\_setstdhandle'
- base.setstdhandle
- consoles.setstdhandle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f5952460-1839-415e-b400-2f04425f288a
topic_type:
- apiref
api_name:
- SetStdHandle
api_location:
- Kernel32.dll
- API-MS-Win-Core-ProcessEnvironment-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-ProcessEnvironment-l1-2-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 317acd84289e5138e1a947251e745077ba581083
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358508"
---
# <a name="setstdhandle-function"></a><span data-ttu-id="e8c39-104">SetStdHandle 函式</span><span class="sxs-lookup"><span data-stu-id="e8c39-104">SetStdHandle function</span></span>

<span data-ttu-id="e8c39-105">設定指定標準裝置的控制碼 (標準輸入、標準輸出或標準錯誤) 。</span><span class="sxs-lookup"><span data-stu-id="e8c39-105">Sets the handle for the specified standard device (standard input, standard output, or standard error).</span></span>

## <a name="syntax"></a><span data-ttu-id="e8c39-106">語法</span><span class="sxs-lookup"><span data-stu-id="e8c39-106">Syntax</span></span>

```cpp
BOOL WINAPI SetStdHandle(
  _In_ DWORD  nStdHandle,
  _In_ HANDLE hHandle
);
```

## <a name="parameters"></a><span data-ttu-id="e8c39-107">參數</span><span class="sxs-lookup"><span data-stu-id="e8c39-107">Parameters</span></span>

<span data-ttu-id="e8c39-108">*nStdHandle* \[輸入\]</span><span class="sxs-lookup"><span data-stu-id="e8c39-108">*nStdHandle* \[in\]</span></span>  
<span data-ttu-id="e8c39-109">要設定控制碼的標準裝置。</span><span class="sxs-lookup"><span data-stu-id="e8c39-109">The standard device for which the handle is to be set.</span></span> <span data-ttu-id="e8c39-110">此參數可以是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="e8c39-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="e8c39-111">值</span><span class="sxs-lookup"><span data-stu-id="e8c39-111">Value</span></span> | <span data-ttu-id="e8c39-112">意義</span><span class="sxs-lookup"><span data-stu-id="e8c39-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="e8c39-113">**STD_INPUT_HANDLE** (DWORD) -10</span><span class="sxs-lookup"><span data-stu-id="e8c39-113">**STD_INPUT_HANDLE** (DWORD) -10</span></span> | <span data-ttu-id="e8c39-114">標準輸入裝置。</span><span class="sxs-lookup"><span data-stu-id="e8c39-114">The standard input device.</span></span> <span data-ttu-id="e8c39-115">一開始，這是主控台輸入緩衝區 `CONIN$`。</span><span class="sxs-lookup"><span data-stu-id="e8c39-115">Initially, this is the console input buffer, `CONIN$`.</span></span> |
| <span data-ttu-id="e8c39-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span><span class="sxs-lookup"><span data-stu-id="e8c39-116">**STD_OUTPUT_HANDLE** (DWORD) -11</span></span> | <span data-ttu-id="e8c39-117">標準輸出裝置。</span><span class="sxs-lookup"><span data-stu-id="e8c39-117">The standard output device.</span></span> <span data-ttu-id="e8c39-118">一開始，這是作用中的主控台畫面緩衝區 `CONOUT$`。</span><span class="sxs-lookup"><span data-stu-id="e8c39-118">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |
| <span data-ttu-id="e8c39-119">**STD_ERROR_HANDLE** (DWORD) -12</span><span class="sxs-lookup"><span data-stu-id="e8c39-119">**STD_ERROR_HANDLE** (DWORD) -12</span></span> | <span data-ttu-id="e8c39-120">標準錯誤裝置。</span><span class="sxs-lookup"><span data-stu-id="e8c39-120">The standard error device.</span></span> <span data-ttu-id="e8c39-121">一開始，這是作用中的主控台畫面緩衝區 `CONOUT$`。</span><span class="sxs-lookup"><span data-stu-id="e8c39-121">Initially, this is the active console screen buffer, `CONOUT$`.</span></span> |

<span data-ttu-id="e8c39-122">*hHandle* \[在\]</span><span class="sxs-lookup"><span data-stu-id="e8c39-122">*hHandle* \[in\]</span></span>  
<span data-ttu-id="e8c39-123">標準裝置的控制碼。</span><span class="sxs-lookup"><span data-stu-id="e8c39-123">The handle for the standard device.</span></span>

## <a name="return-value"></a><span data-ttu-id="e8c39-124">傳回值</span><span class="sxs-lookup"><span data-stu-id="e8c39-124">Return value</span></span>

<span data-ttu-id="e8c39-125">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="e8c39-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e8c39-126">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="e8c39-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e8c39-127">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="e8c39-127">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="e8c39-128">備註</span><span class="sxs-lookup"><span data-stu-id="e8c39-128">Remarks</span></span>

<span data-ttu-id="e8c39-129">對 **SetStdHandle** 的呼叫可能會重新導向進程的標準控制碼，在這種情況下， [**GetStdHandle**](getstdhandle.md) 會傳回重新導向的控制碼。</span><span class="sxs-lookup"><span data-stu-id="e8c39-129">The standard handles of a process may have been redirected by a call to **SetStdHandle**, in which case [**GetStdHandle**](getstdhandle.md) will return the redirected handle.</span></span> <span data-ttu-id="e8c39-130">如果已重新導向標準控制碼，您可以在 [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) 函式的呼叫中指定 CONIN $ 值，以取得主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="e8c39-130">If the standard handles have been redirected, you can specify the CONIN$ value in a call to the [**CreateFile**](/windows/win32/api/fileapi/nf-fileapi-createfilea) function to get a handle to a console's input buffer.</span></span> <span data-ttu-id="e8c39-131">同樣地，您可以指定 CONOUT $ 值，以取得主控台的作用中螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="e8c39-131">Similarly, you can specify the CONOUT$ value to get a handle to the console's active screen buffer.</span></span>

## <a name="examples"></a><span data-ttu-id="e8c39-132">範例</span><span class="sxs-lookup"><span data-stu-id="e8c39-132">Examples</span></span>

<span data-ttu-id="e8c39-133">如需範例，請參閱 [使用重新導向的輸入和輸出建立子進程](/windows/win32/procthread/creating-a-child-process-with-redirected-input-and-output)。</span><span class="sxs-lookup"><span data-stu-id="e8c39-133">For an example, see [Creating a Child Process with Redirected Input and Output](/windows/win32/procthread/creating-a-child-process-with-redirected-input-and-output).</span></span>

## <a name="requirements"></a><span data-ttu-id="e8c39-134">規格需求</span><span class="sxs-lookup"><span data-stu-id="e8c39-134">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e8c39-135">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="e8c39-135">Minimum supported client</span></span> | <span data-ttu-id="e8c39-136">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="e8c39-136">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="e8c39-137">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="e8c39-137">Minimum supported server</span></span> | <span data-ttu-id="e8c39-138">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="e8c39-138">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="e8c39-139">標頭</span><span class="sxs-lookup"><span data-stu-id="e8c39-139">Header</span></span> | <span data-ttu-id="e8c39-140">ProcessEnv.h (透過 Winbase.h，包括 Windows.h)</span><span class="sxs-lookup"><span data-stu-id="e8c39-140">ProcessEnv.h (via Winbase.h, include Windows.h)</span></span> |
| <span data-ttu-id="e8c39-141">程式庫</span><span class="sxs-lookup"><span data-stu-id="e8c39-141">Library</span></span> | <span data-ttu-id="e8c39-142">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="e8c39-142">Kernel32.lib</span></span> |
| <span data-ttu-id="e8c39-143">DLL</span><span class="sxs-lookup"><span data-stu-id="e8c39-143">DLL</span></span> | <span data-ttu-id="e8c39-144">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e8c39-144">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="e8c39-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8c39-145">See also</span></span>

[<span data-ttu-id="e8c39-146">主控台函式</span><span class="sxs-lookup"><span data-stu-id="e8c39-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e8c39-147">主控台控制代碼</span><span class="sxs-lookup"><span data-stu-id="e8c39-147">Console Handles</span></span>](console-handles.md)

[<span data-ttu-id="e8c39-148">**CreateFile**</span><span class="sxs-lookup"><span data-stu-id="e8c39-148">**CreateFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-createfilea)

[<span data-ttu-id="e8c39-149">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="e8c39-149">**GetStdHandle**</span></span>](getstdhandle.md)
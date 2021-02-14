---
title: SetConsoleMode 函式
description: 設定主控台輸入緩衝區的輸入模式，或主控台畫面緩衝區的輸出模式。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/SetConsoleMode
- wincon/SetConsoleMode
- SetConsoleMode
MS-HAID:
- '\_win32\_setconsolemode'
- base.setconsolemode
- consoles.setconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 77508d58-8a7a-4c47-9ec5-dc61e5c4beac
topic_type:
- apiref
api_name:
- SetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: b4e165610288a04af653f052a2f1071d7e45937d
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357658"
---
# <a name="setconsolemode-function"></a><span data-ttu-id="32499-104">SetConsoleMode 函式</span><span class="sxs-lookup"><span data-stu-id="32499-104">SetConsoleMode function</span></span>

<span data-ttu-id="32499-105">設定主控台輸入緩衝區的輸入模式，或主控台畫面緩衝區的輸出模式。</span><span class="sxs-lookup"><span data-stu-id="32499-105">Sets the input mode of a console's input buffer or the output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="32499-106">語法</span><span class="sxs-lookup"><span data-stu-id="32499-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

## <a name="parameters"></a><span data-ttu-id="32499-107">參數</span><span class="sxs-lookup"><span data-stu-id="32499-107">Parameters</span></span>

<span data-ttu-id="32499-108">*hConsoleHandle* \[輸入\]</span><span class="sxs-lookup"><span data-stu-id="32499-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="32499-109">主控台輸入緩衝區或主控台畫面緩衝區的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="32499-109">A handle to the console input buffer or a console screen buffer.</span></span> <span data-ttu-id="32499-110">控制代碼必須具有 **GENERIC\_READ** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="32499-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="32499-111">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="32499-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="32499-112">*dwMode* \[輸入\]</span><span class="sxs-lookup"><span data-stu-id="32499-112">*dwMode* \[in\]</span></span>  
<span data-ttu-id="32499-113">要設定的輸入或輸出模式。</span><span class="sxs-lookup"><span data-stu-id="32499-113">The input or output mode to be set.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="32499-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="32499-114">Return value</span></span>

<span data-ttu-id="32499-115">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="32499-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="32499-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="32499-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="32499-117">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="32499-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="32499-118">備註</span><span class="sxs-lookup"><span data-stu-id="32499-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="32499-119">若要判斷主控台輸入緩衝區或畫面緩衝區的目前模式，請使用 [**GetConsoleMode**](getconsolemode.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="32499-119">To determine the current mode of a console input buffer or a screen buffer, use the [**GetConsoleMode**](getconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="32499-120">範例</span><span class="sxs-lookup"><span data-stu-id="32499-120">Examples</span></span>

<span data-ttu-id="32499-121">如需範例，請參閱[讀取輸入緩衝區事件](reading-input-buffer-events.md)。</span><span class="sxs-lookup"><span data-stu-id="32499-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="32499-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="32499-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="32499-123">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="32499-123">Minimum supported client</span></span> | <span data-ttu-id="32499-124">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="32499-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="32499-125">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="32499-125">Minimum supported server</span></span> | <span data-ttu-id="32499-126">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="32499-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="32499-127">標頭</span><span class="sxs-lookup"><span data-stu-id="32499-127">Header</span></span> | <span data-ttu-id="32499-128">ConsoleApi.h (透過 WinCon.h，包括 Windows.h)</span><span class="sxs-lookup"><span data-stu-id="32499-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="32499-129">程式庫</span><span class="sxs-lookup"><span data-stu-id="32499-129">Library</span></span> | <span data-ttu-id="32499-130">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="32499-130">Kernel32.lib</span></span> |
| <span data-ttu-id="32499-131">DLL</span><span class="sxs-lookup"><span data-stu-id="32499-131">DLL</span></span> | <span data-ttu-id="32499-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="32499-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="32499-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32499-133">See also</span></span>

[<span data-ttu-id="32499-134">主控台函式</span><span class="sxs-lookup"><span data-stu-id="32499-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="32499-135">主控台模式</span><span class="sxs-lookup"><span data-stu-id="32499-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="32499-136">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="32499-136">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="32499-137">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="32499-137">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="32499-138">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="32499-138">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="32499-139">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="32499-139">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="32499-140">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="32499-140">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="32499-141">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="32499-141">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="32499-142">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="32499-142">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)
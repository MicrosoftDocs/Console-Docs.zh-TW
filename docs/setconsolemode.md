---
title: SetConsoleMode 函式
description: 設定主控台之輸入緩衝區的輸入模式或主控台螢幕緩衝區的輸出模式。
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
ms.openlocfilehash: 2af598f465be6e1a33f5a8f9a2c9abe98d6ed0d2
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420297"
---
# <a name="setconsolemode-function"></a><span data-ttu-id="e911b-104">SetConsoleMode 函式</span><span class="sxs-lookup"><span data-stu-id="e911b-104">SetConsoleMode function</span></span>

<span data-ttu-id="e911b-105">設定主控台之輸入緩衝區的輸入模式或主控台螢幕緩衝區的輸出模式。</span><span class="sxs-lookup"><span data-stu-id="e911b-105">Sets the input mode of a console's input buffer or the output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="e911b-106">語法</span><span class="sxs-lookup"><span data-stu-id="e911b-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

## <a name="parameters"></a><span data-ttu-id="e911b-107">參數</span><span class="sxs-lookup"><span data-stu-id="e911b-107">Parameters</span></span>

<span data-ttu-id="e911b-108">*hConsoleHandle* \[在\]</span><span class="sxs-lookup"><span data-stu-id="e911b-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="e911b-109">主控台輸入緩衝區或主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="e911b-109">A handle to the console input buffer or a console screen buffer.</span></span> <span data-ttu-id="e911b-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="e911b-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="e911b-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="e911b-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="e911b-112">*dwMode* \[在\]</span><span class="sxs-lookup"><span data-stu-id="e911b-112">*dwMode* \[in\]</span></span>  
<span data-ttu-id="e911b-113">要設定的輸入或輸出模式。</span><span class="sxs-lookup"><span data-stu-id="e911b-113">The input or output mode to be set.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="e911b-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="e911b-114">Return value</span></span>

<span data-ttu-id="e911b-115">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="e911b-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e911b-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="e911b-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e911b-117">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="e911b-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="e911b-118">備註</span><span class="sxs-lookup"><span data-stu-id="e911b-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="e911b-119">若要判斷主控台輸入緩衝區或螢幕緩衝區的目前模式，請使用 [**GetConsoleMode**](getconsolemode.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="e911b-119">To determine the current mode of a console input buffer or a screen buffer, use the [**GetConsoleMode**](getconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="e911b-120">範例</span><span class="sxs-lookup"><span data-stu-id="e911b-120">Examples</span></span>

<span data-ttu-id="e911b-121">如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。</span><span class="sxs-lookup"><span data-stu-id="e911b-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="e911b-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="e911b-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e911b-123">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="e911b-123">Minimum supported client</span></span> | <span data-ttu-id="e911b-124">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="e911b-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="e911b-125">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="e911b-125">Minimum supported server</span></span> | <span data-ttu-id="e911b-126">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="e911b-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="e911b-127">標頭</span><span class="sxs-lookup"><span data-stu-id="e911b-127">Header</span></span> | <span data-ttu-id="e911b-128">ConsoleApi .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="e911b-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="e911b-129">程式庫</span><span class="sxs-lookup"><span data-stu-id="e911b-129">Library</span></span> | <span data-ttu-id="e911b-130">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="e911b-130">Kernel32.lib</span></span> |
| <span data-ttu-id="e911b-131">DLL</span><span class="sxs-lookup"><span data-stu-id="e911b-131">DLL</span></span> | <span data-ttu-id="e911b-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e911b-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="e911b-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e911b-133">See also</span></span>

[<span data-ttu-id="e911b-134">主控台功能</span><span class="sxs-lookup"><span data-stu-id="e911b-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e911b-135">主控台模式</span><span class="sxs-lookup"><span data-stu-id="e911b-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="e911b-136">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="e911b-136">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="e911b-137">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="e911b-137">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="e911b-138">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="e911b-138">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="e911b-139">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="e911b-139">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="e911b-140">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="e911b-140">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="e911b-141">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="e911b-141">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="e911b-142">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="e911b-142">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

---
title: GetConsoleMode 函式
description: 抓取主控台之輸入緩衝區的目前輸入模式，或主控台螢幕緩衝區目前的輸出模式。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/GetConsoleMode
- wincon/GetConsoleMode
- GetConsoleMode
MS-HAID:
- '\_win32\_getconsolemode'
- base.getconsolemode
- consoles.getconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 49adf618-196d-4490-93ca-cd177807f58e
topic_type:
- apiref
api_name:
- GetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 54667d92509687111cb562f517d488c8adbc2181
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038868"
---
# <a name="getconsolemode-function"></a><span data-ttu-id="bb516-104">GetConsoleMode 函式</span><span class="sxs-lookup"><span data-stu-id="bb516-104">GetConsoleMode function</span></span>

<span data-ttu-id="bb516-105">抓取主控台之輸入緩衝區的目前輸入模式，或主控台螢幕緩衝區目前的輸出模式。</span><span class="sxs-lookup"><span data-stu-id="bb516-105">Retrieves the current input mode of a console's input buffer or the current output mode of a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="bb516-106">語法</span><span class="sxs-lookup"><span data-stu-id="bb516-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleMode(
  _In_  HANDLE  hConsoleHandle,
  _Out_ LPDWORD lpMode
);
```

## <a name="parameters"></a><span data-ttu-id="bb516-107">參數</span><span class="sxs-lookup"><span data-stu-id="bb516-107">Parameters</span></span>

<span data-ttu-id="bb516-108">*hConsoleHandle* \[在\]</span><span class="sxs-lookup"><span data-stu-id="bb516-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="bb516-109">主控台輸入緩衝區或主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="bb516-109">A handle to the console input buffer or the console screen buffer.</span></span> <span data-ttu-id="bb516-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="bb516-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="bb516-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="bb516-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="bb516-112">*lpMode* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="bb516-112">*lpMode* \[out\]</span></span>  
<span data-ttu-id="bb516-113">變數的指標，此變數會接收指定緩衝區的目前模式。</span><span class="sxs-lookup"><span data-stu-id="bb516-113">A pointer to a variable that receives the current mode of the specified buffer.</span></span>

[!INCLUDE [console-mode-flags](./includes/console-mode-flags.md)]

## <a name="return-value"></a><span data-ttu-id="bb516-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="bb516-114">Return value</span></span>

<span data-ttu-id="bb516-115">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="bb516-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="bb516-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="bb516-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="bb516-117">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="bb516-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="bb516-118">備註</span><span class="sxs-lookup"><span data-stu-id="bb516-118">Remarks</span></span>

[!INCLUDE [console-mode-remarks](./includes/console-mode-remarks.md)]

<span data-ttu-id="bb516-119">若要變更控制台的 i/o 模式，請呼叫 [**SetConsoleMode**](setconsolemode.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="bb516-119">To change a console's I/O modes, call [**SetConsoleMode**](setconsolemode.md) function.</span></span>

## <a name="examples"></a><span data-ttu-id="bb516-120">範例</span><span class="sxs-lookup"><span data-stu-id="bb516-120">Examples</span></span>

<span data-ttu-id="bb516-121">如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。</span><span class="sxs-lookup"><span data-stu-id="bb516-121">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="bb516-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="bb516-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="bb516-123">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="bb516-123">Minimum supported client</span></span> | <span data-ttu-id="bb516-124">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="bb516-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="bb516-125">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="bb516-125">Minimum supported server</span></span> | <span data-ttu-id="bb516-126">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="bb516-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="bb516-127">標頭</span><span class="sxs-lookup"><span data-stu-id="bb516-127">Header</span></span> | <span data-ttu-id="bb516-128">ConsoleApi .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="bb516-128">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="bb516-129">程式庫</span><span class="sxs-lookup"><span data-stu-id="bb516-129">Library</span></span> | <span data-ttu-id="bb516-130">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="bb516-130">Kernel32.lib</span></span> |
| <span data-ttu-id="bb516-131">DLL</span><span class="sxs-lookup"><span data-stu-id="bb516-131">DLL</span></span> | <span data-ttu-id="bb516-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="bb516-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="bb516-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="bb516-133">See also</span></span>

[<span data-ttu-id="bb516-134">主控台功能</span><span class="sxs-lookup"><span data-stu-id="bb516-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="bb516-135">主控台模式</span><span class="sxs-lookup"><span data-stu-id="bb516-135">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="bb516-136">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="bb516-136">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="bb516-137">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="bb516-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="bb516-138">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="bb516-138">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="bb516-139">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="bb516-139">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="bb516-140">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="bb516-140">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="bb516-141">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="bb516-141">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

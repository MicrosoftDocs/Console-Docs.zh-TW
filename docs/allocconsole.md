---
title: AllocConsole 函式
description: 請參閱 AllocConsole 函式的參考資訊，此函式會為呼叫進程配置新的主控台。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/AllocConsole
- wincon/AllocConsole
- AllocConsole
MS-HAID:
- '\_win32\_allocconsole'
- base.allocconsole
- consoles.allocconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: bdf3bf2f-8eb8-4ba6-bf3a-a67b29dffda2
topic_type:
- apiref
api_name:
- AllocConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: c63c9a176c0d8ca2ef4342f7bee1b427eae00014
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420167"
---
# <a name="allocconsole-function"></a><span data-ttu-id="8a4ca-104">AllocConsole 函式</span><span class="sxs-lookup"><span data-stu-id="8a4ca-104">AllocConsole function</span></span>

<span data-ttu-id="8a4ca-105">配置呼叫進程的新主控台。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-105">Allocates a new console for the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="8a4ca-106">語法</span><span class="sxs-lookup"><span data-stu-id="8a4ca-106">Syntax</span></span>

```C
BOOL WINAPI AllocConsole(void);
```

## <a name="parameters"></a><span data-ttu-id="8a4ca-107">參數</span><span class="sxs-lookup"><span data-stu-id="8a4ca-107">Parameters</span></span>

<span data-ttu-id="8a4ca-108">此函式沒有參數。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="8a4ca-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="8a4ca-109">Return value</span></span>

<span data-ttu-id="8a4ca-110">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="8a4ca-111">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="8a4ca-112">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-112">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="8a4ca-113">備註</span><span class="sxs-lookup"><span data-stu-id="8a4ca-113">Remarks</span></span>

<span data-ttu-id="8a4ca-114">進程只能與一個主控台相關聯，因此，如果呼叫的進程已經有主控台， **AllocConsole** 函式就會失敗。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-114">A process can be associated with only one console, so the **AllocConsole** function fails if the calling process already has a console.</span></span> <span data-ttu-id="8a4ca-115">進程可以使用 [**FreeConsole**](freeconsole.md) 函式，從其目前的主控台卸離本身，然後呼叫 **AllocConsole** 來建立新的主控台或 [**AttachConsole**](attachconsole.md) ，以附加至另一個主控台。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-115">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its current console, then it can call **AllocConsole** to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="8a4ca-116">如果呼叫進程建立子進程，則子系會繼承新的主控台。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-116">If the calling process creates a child process, the child inherits the new console.</span></span>

<span data-ttu-id="8a4ca-117">**AllocConsole** 會初始化新主控台的標準輸入、標準輸出和標準錯誤控制碼。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-117">**AllocConsole** initializes standard input, standard output, and standard error handles for the new console.</span></span> <span data-ttu-id="8a4ca-118">標準輸入控制碼是主控台輸入緩衝區的控制碼，而標準輸出和標準錯誤控制碼則是主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-118">The standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles to the console's screen buffer.</span></span> <span data-ttu-id="8a4ca-119">若要取出這些控制碼，請使用 [**GetStdHandle**](getstdhandle.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-119">To retrieve these handles, use the [**GetStdHandle**](getstdhandle.md) function.</span></span>

<span data-ttu-id="8a4ca-120">這項功能主要是由圖形化使用者介面 (GUI) 應用程式用來建立主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-120">This function is primarily used by a graphical user interface (GUI) application to create a console window.</span></span> <span data-ttu-id="8a4ca-121">GUI 應用程式會在沒有主控台的情況下初始化。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-121">GUI applications are initialized without a console.</span></span> <span data-ttu-id="8a4ca-122">主控台應用程式會使用主控台來初始化，除非它們建立為卸離的進程 (藉由使用卸 **離的 \_ 進程** 旗標) 來呼叫 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)函數。</span><span class="sxs-lookup"><span data-stu-id="8a4ca-122">Console applications are initialized with a console, unless they are created as detached processes (by calling the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function with the **DETACHED\_PROCESS** flag).</span></span>

## <a name="requirements"></a><span data-ttu-id="8a4ca-123">規格需求</span><span class="sxs-lookup"><span data-stu-id="8a4ca-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="8a4ca-124">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="8a4ca-124">Minimum supported client</span></span> | <span data-ttu-id="8a4ca-125">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="8a4ca-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="8a4ca-126">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="8a4ca-126">Minimum supported server</span></span> | <span data-ttu-id="8a4ca-127">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="8a4ca-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="8a4ca-128">標頭</span><span class="sxs-lookup"><span data-stu-id="8a4ca-128">Header</span></span> | <span data-ttu-id="8a4ca-129">ConsoleApi .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="8a4ca-129">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="8a4ca-130">程式庫</span><span class="sxs-lookup"><span data-stu-id="8a4ca-130">Library</span></span> | <span data-ttu-id="8a4ca-131">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="8a4ca-131">Kernel32.lib</span></span> |
| <span data-ttu-id="8a4ca-132">DLL</span><span class="sxs-lookup"><span data-stu-id="8a4ca-132">DLL</span></span> | <span data-ttu-id="8a4ca-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="8a4ca-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="8a4ca-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a4ca-134">See also</span></span>

[<span data-ttu-id="8a4ca-135">主控台功能</span><span class="sxs-lookup"><span data-stu-id="8a4ca-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="8a4ca-136">機</span><span class="sxs-lookup"><span data-stu-id="8a4ca-136">Consoles</span></span>](consoles.md)

[<span data-ttu-id="8a4ca-137">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="8a4ca-137">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="8a4ca-138">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="8a4ca-138">**CreateProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[<span data-ttu-id="8a4ca-139">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="8a4ca-139">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="8a4ca-140">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="8a4ca-140">**GetStdHandle**</span></span>](getstdhandle.md)

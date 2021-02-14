---
title: AllocConsole 函式
description: 請參閱 AllocConsole 函式的參考資訊，此函式會為呼叫程序配置新的主控台。
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
ms.openlocfilehash: 3b48570424a4c60a56094f5c41934f9946f67203
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357858"
---
# <a name="allocconsole-function"></a><span data-ttu-id="32334-104">AllocConsole 函式</span><span class="sxs-lookup"><span data-stu-id="32334-104">AllocConsole function</span></span>

<span data-ttu-id="32334-105">為呼叫程序配置新的主控台。</span><span class="sxs-lookup"><span data-stu-id="32334-105">Allocates a new console for the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="32334-106">語法</span><span class="sxs-lookup"><span data-stu-id="32334-106">Syntax</span></span>

```C
BOOL WINAPI AllocConsole(void);
```

## <a name="parameters"></a><span data-ttu-id="32334-107">參數</span><span class="sxs-lookup"><span data-stu-id="32334-107">Parameters</span></span>

<span data-ttu-id="32334-108">此函式沒有參數。</span><span class="sxs-lookup"><span data-stu-id="32334-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="32334-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="32334-109">Return value</span></span>

<span data-ttu-id="32334-110">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="32334-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="32334-111">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="32334-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="32334-112">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="32334-112">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="32334-113">備註</span><span class="sxs-lookup"><span data-stu-id="32334-113">Remarks</span></span>

<span data-ttu-id="32334-114">一個程序只能與一個主控台相關聯，因此，如果呼叫程序已經有主控台，**AllocConsole** 函式就會失敗。</span><span class="sxs-lookup"><span data-stu-id="32334-114">A process can be associated with only one console, so the **AllocConsole** function fails if the calling process already has a console.</span></span> <span data-ttu-id="32334-115">程序可以使用 [**FreeConsole**](freeconsole.md) 函式將其本身從目前的主控台卸離，然後呼叫 **AllocConsole** 來建立新的主控台，或呼叫 [**AttachConsole**](attachconsole.md) 來連結至另一個主控台。</span><span class="sxs-lookup"><span data-stu-id="32334-115">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its current console, then it can call **AllocConsole** to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

<span data-ttu-id="32334-116">如果呼叫程序建立了子程序，則子程序會繼承新的主控台。</span><span class="sxs-lookup"><span data-stu-id="32334-116">If the calling process creates a child process, the child inherits the new console.</span></span>

<span data-ttu-id="32334-117">**AllocConsole** 會初始化新主控台的標準輸入、標準輸出和標準錯誤控制代碼。</span><span class="sxs-lookup"><span data-stu-id="32334-117">**AllocConsole** initializes standard input, standard output, and standard error handles for the new console.</span></span> <span data-ttu-id="32334-118">標準輸入控制代碼是主控台輸入緩衝區的控制代碼，而標準輸出和標準錯誤控制代碼則是主控台畫面緩衝區的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="32334-118">The standard input handle is a handle to the console's input buffer, and the standard output and standard error handles are handles to the console's screen buffer.</span></span> <span data-ttu-id="32334-119">若要取得這些控制代碼，請使用 [**GetStdHandle**](getstdhandle.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="32334-119">To retrieve these handles, use the [**GetStdHandle**](getstdhandle.md) function.</span></span>

<span data-ttu-id="32334-120">此函式的主要用途是讓圖形使用者介面 (GUI) 應用程式用來建立主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="32334-120">This function is primarily used by a graphical user interface (GUI) application to create a console window.</span></span> <span data-ttu-id="32334-121">GUI 應用程式會在沒有主控台的情況下進行初始化。</span><span class="sxs-lookup"><span data-stu-id="32334-121">GUI applications are initialized without a console.</span></span> <span data-ttu-id="32334-122">除非是建立為卸離的程序 (呼叫 [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) 函式搭配 **DETACHED\_PROCESS** 旗標)，否則主控台應用程式會使用主控台進行初始化。</span><span class="sxs-lookup"><span data-stu-id="32334-122">Console applications are initialized with a console, unless they are created as detached processes (by calling the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) function with the **DETACHED\_PROCESS** flag).</span></span>

## <a name="requirements"></a><span data-ttu-id="32334-123">規格需求</span><span class="sxs-lookup"><span data-stu-id="32334-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="32334-124">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="32334-124">Minimum supported client</span></span> | <span data-ttu-id="32334-125">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="32334-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="32334-126">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="32334-126">Minimum supported server</span></span> | <span data-ttu-id="32334-127">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="32334-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="32334-128">標頭</span><span class="sxs-lookup"><span data-stu-id="32334-128">Header</span></span> | <span data-ttu-id="32334-129">ConsoleApi.h (透過 WinCon.h，包括 Windows.h)</span><span class="sxs-lookup"><span data-stu-id="32334-129">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="32334-130">程式庫</span><span class="sxs-lookup"><span data-stu-id="32334-130">Library</span></span> | <span data-ttu-id="32334-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="32334-131">Kernel32.lib</span></span> |
| <span data-ttu-id="32334-132">DLL</span><span class="sxs-lookup"><span data-stu-id="32334-132">DLL</span></span> | <span data-ttu-id="32334-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="32334-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="32334-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32334-134">See also</span></span>

[<span data-ttu-id="32334-135">主控台函式</span><span class="sxs-lookup"><span data-stu-id="32334-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="32334-136">主控台</span><span class="sxs-lookup"><span data-stu-id="32334-136">Consoles</span></span>](consoles.md)

[<span data-ttu-id="32334-137">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="32334-137">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="32334-138">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="32334-138">**CreateProcess**</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)

[<span data-ttu-id="32334-139">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="32334-139">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="32334-140">**GetStdHandle**</span><span class="sxs-lookup"><span data-stu-id="32334-140">**GetStdHandle**</span></span>](getstdhandle.md)
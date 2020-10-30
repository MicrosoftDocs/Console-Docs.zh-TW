---
title: AttachConsole 函式
description: 請參閱 AttachConsole 函式的參考資訊，此函式會將呼叫進程附加至指定進程的主控台。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/AttachConsole
- wincon/AttachConsole
- AttachConsole
MS-HAID:
- '\_win32\_attachconsole'
- base.attachconsole
- consoles.attachconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c00691c3-5878-4a06-9bf3-6073326f36c4
topic_type:
- apiref
api_name:
- AttachConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: bfc71c10a02e9ed8a0bc18fd26cffa855012c692
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037476"
---
# <a name="attachconsole-function"></a><span data-ttu-id="050c4-104">AttachConsole 函式</span><span class="sxs-lookup"><span data-stu-id="050c4-104">AttachConsole function</span></span>

<span data-ttu-id="050c4-105">將呼叫進程附加至指定進程的主控台做為用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="050c4-105">Attaches the calling process to the console of the specified process as a client application.</span></span>

## <a name="syntax"></a><span data-ttu-id="050c4-106">語法</span><span class="sxs-lookup"><span data-stu-id="050c4-106">Syntax</span></span>

```C
BOOL WINAPI AttachConsole(
  _In_ DWORD dwProcessId
);
```

## <a name="parameters"></a><span data-ttu-id="050c4-107">參數</span><span class="sxs-lookup"><span data-stu-id="050c4-107">Parameters</span></span>

<span data-ttu-id="050c4-108">*dwProcessId* \[在\]</span><span class="sxs-lookup"><span data-stu-id="050c4-108">*dwProcessId* \[in\]</span></span>  
<span data-ttu-id="050c4-109">要使用其主控台的進程識別碼。</span><span class="sxs-lookup"><span data-stu-id="050c4-109">The identifier of the process whose console is to be used.</span></span> <span data-ttu-id="050c4-110">這個參數可以是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="050c4-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="050c4-111">值</span><span class="sxs-lookup"><span data-stu-id="050c4-111">Value</span></span> | <span data-ttu-id="050c4-112">意義</span><span class="sxs-lookup"><span data-stu-id="050c4-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="050c4-113">*Pid*</span><span class="sxs-lookup"><span data-stu-id="050c4-113">*pid*</span></span> | <span data-ttu-id="050c4-114">使用指定進程的主控台。</span><span class="sxs-lookup"><span data-stu-id="050c4-114">Use the console of the specified process.</span></span> |
| <span data-ttu-id="050c4-115">**附加 \_父 \_ 進程**`(DWORD)-1`</span><span class="sxs-lookup"><span data-stu-id="050c4-115">**ATTACH\_PARENT\_PROCESS** `(DWORD)-1`</span></span> | <span data-ttu-id="050c4-116">使用目前進程父系的主控台。</span><span class="sxs-lookup"><span data-stu-id="050c4-116">Use the console of the parent of the current process.</span></span> |

## <a name="return-value"></a><span data-ttu-id="050c4-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="050c4-117">Return value</span></span>

<span data-ttu-id="050c4-118">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="050c4-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="050c4-119">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="050c4-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="050c4-120">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="050c4-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="050c4-121">備註</span><span class="sxs-lookup"><span data-stu-id="050c4-121">Remarks</span></span>

<span data-ttu-id="050c4-122">一個進程最多可以附加至一個主控台。</span><span class="sxs-lookup"><span data-stu-id="050c4-122">A process can be attached to at most one console.</span></span> <span data-ttu-id="050c4-123">如果呼叫的進程已附加至主控台，則傳回的錯誤碼會是 **\_ \_ 拒絕存取** () 錯誤 `5` 。</span><span class="sxs-lookup"><span data-stu-id="050c4-123">If the calling process is already attached to a console, the error code returned is **ERROR\_ACCESS\_DENIED** (`5`).</span></span> <span data-ttu-id="050c4-124">如果指定的進程沒有主控台，則傳回的錯誤碼會是 **錯誤不正確 \_ \_ 控制碼** (`6`) 。</span><span class="sxs-lookup"><span data-stu-id="050c4-124">If the specified process does not have a console, the error code returned is **ERROR\_INVALID\_HANDLE** (`6`).</span></span> <span data-ttu-id="050c4-125">如果指定的處理常式不存在，則傳回的錯誤碼會是 **錯誤 \_ 不正確 \_ 參數** (`87`) 。</span><span class="sxs-lookup"><span data-stu-id="050c4-125">If the specified process does not exist, the error code returned is **ERROR\_INVALID\_PARAMETER** (`87`).</span></span>

<span data-ttu-id="050c4-126">進程可以使用 [**FreeConsole**](freeconsole.md) 函式，從其主控台卸離本身。</span><span class="sxs-lookup"><span data-stu-id="050c4-126">A process can use the [**FreeConsole**](freeconsole.md) function to detach itself from its console.</span></span> <span data-ttu-id="050c4-127">如果有其他進程共用主控台，主控台就不會終結，但呼叫 **FreeConsole** 的進程無法參考它。</span><span class="sxs-lookup"><span data-stu-id="050c4-127">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="050c4-128">當最後一個附加至它的進程終止或呼叫 **FreeConsole** 時，主控台就會關閉。</span><span class="sxs-lookup"><span data-stu-id="050c4-128">A console is closed when the last process attached to it terminates or calls **FreeConsole** .</span></span> <span data-ttu-id="050c4-129">在進程呼叫 **FreeConsole** 之後，它就可以呼叫 [**AllocConsole**](allocconsole.md) 函式來建立新的主控台或 **AttachConsole** ，以附加至另一個主控台。</span><span class="sxs-lookup"><span data-stu-id="050c4-129">After a process calls **FreeConsole** , it can call the [**AllocConsole**](allocconsole.md) function to create a new console or **AttachConsole** to attach to another console.</span></span>

<span data-ttu-id="050c4-130">這項功能主要適用于與 [**/SUBSYSTEM： WINDOWS**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem)連結的應用程式，這表示在輸入程式的 main 方法之前，不需要主控台。</span><span class="sxs-lookup"><span data-stu-id="050c4-130">This function is primarily useful to applications that were linked with [**/SUBSYSTEM:WINDOWS**](https://docs.microsoft.com/cpp/build/reference/subsystem-specify-subsystem), which implies to the operating system that a console is not needed before entering the program's main method.</span></span> <span data-ttu-id="050c4-131">在該實例中，使用 [**GetStdHandle**](getstdhandle.md) 抓取的標準處理常式在啟動時可能會無效，直到呼叫 **AttachConsole** 為止。</span><span class="sxs-lookup"><span data-stu-id="050c4-131">In that instance, the standard handles retrieved with [**GetStdHandle**](getstdhandle.md) will likely be invalid on startup until **AttachConsole** is called.</span></span> <span data-ttu-id="050c4-132">例外狀況是，如果應用程式是由其父進程的控制碼繼承啟動的。</span><span class="sxs-lookup"><span data-stu-id="050c4-132">The exception to this is if the application is launched with handle inheritance by its parent process.</span></span>

<span data-ttu-id="050c4-133">若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為 `0x0501` 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="050c4-133">To compile an application that uses this function, define **\_WIN32\_WINNT** as `0x0501` or later.</span></span> <span data-ttu-id="050c4-134">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="050c4-134">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

## <a name="requirements"></a><span data-ttu-id="050c4-135">規格需求</span><span class="sxs-lookup"><span data-stu-id="050c4-135">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="050c4-136">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="050c4-136">Minimum supported client</span></span> | <span data-ttu-id="050c4-137">\[僅限 WINDOWS XP desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="050c4-137">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="050c4-138">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="050c4-138">Minimum supported server</span></span> | <span data-ttu-id="050c4-139">僅限 Windows Server 2003 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="050c4-139">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="050c4-140">標頭</span><span class="sxs-lookup"><span data-stu-id="050c4-140">Header</span></span> | <span data-ttu-id="050c4-141">ConsoleApi .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="050c4-141">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="050c4-142">程式庫</span><span class="sxs-lookup"><span data-stu-id="050c4-142">Library</span></span> | <span data-ttu-id="050c4-143">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="050c4-143">Kernel32.lib</span></span> |
| <span data-ttu-id="050c4-144">DLL</span><span class="sxs-lookup"><span data-stu-id="050c4-144">DLL</span></span> | <span data-ttu-id="050c4-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="050c4-145">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="050c4-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="050c4-146">See also</span></span>

[<span data-ttu-id="050c4-147">主控台功能</span><span class="sxs-lookup"><span data-stu-id="050c4-147">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="050c4-148">機</span><span class="sxs-lookup"><span data-stu-id="050c4-148">Consoles</span></span>](consoles.md)

[<span data-ttu-id="050c4-149">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="050c4-149">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="050c4-150">**FreeConsole**</span><span class="sxs-lookup"><span data-stu-id="050c4-150">**FreeConsole**</span></span>](freeconsole.md)

[<span data-ttu-id="050c4-151">**GetConsoleProcessList**</span><span class="sxs-lookup"><span data-stu-id="050c4-151">**GetConsoleProcessList**</span></span>](getconsoleprocesslist.md)

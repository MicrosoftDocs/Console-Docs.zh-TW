---
title: GenerateConsoleCtrlEvent 函式
description: 將指定的信號傳送至主控台進程群組，該群組會共用與呼叫進程相關聯的主控台。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/GenerateConsoleCtrlEvent
- wincon/GenerateConsoleCtrlEvent
- GenerateConsoleCtrlEvent
MS-HAID:
- '\_win32\_generateconsolectrlevent'
- base.generateconsolectrlevent
- consoles.generateconsolectrlevent
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ed392d97-6fd0-4256-a783-bc7d27d01a10
topic_type:
- apiref
api_name:
- GenerateConsoleCtrlEvent
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4002ec67000edda38c7b14476528a0167e521bbf
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357528"
---
# <a name="generateconsolectrlevent-function"></a><span data-ttu-id="b0acf-104">GenerateConsoleCtrlEvent 函式</span><span class="sxs-lookup"><span data-stu-id="b0acf-104">GenerateConsoleCtrlEvent function</span></span>

<span data-ttu-id="b0acf-105">將指定的信號傳送至主控台進程群組，該群組會共用與呼叫進程相關聯的主控台。</span><span class="sxs-lookup"><span data-stu-id="b0acf-105">Sends a specified signal to a console process group that shares the console associated with the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="b0acf-106">語法</span><span class="sxs-lookup"><span data-stu-id="b0acf-106">Syntax</span></span>

```C
BOOL WINAPI GenerateConsoleCtrlEvent(
  _In_ DWORD dwCtrlEvent,
  _In_ DWORD dwProcessGroupId
);
```

## <a name="parameters"></a><span data-ttu-id="b0acf-107">參數</span><span class="sxs-lookup"><span data-stu-id="b0acf-107">Parameters</span></span>

<span data-ttu-id="b0acf-108">*dwCtrlEvent* \[在\]</span><span class="sxs-lookup"><span data-stu-id="b0acf-108">*dwCtrlEvent* \[in\]</span></span>  
<span data-ttu-id="b0acf-109">要產生的信號類型。</span><span class="sxs-lookup"><span data-stu-id="b0acf-109">The type of signal to be generated.</span></span> <span data-ttu-id="b0acf-110">此參數可以是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="b0acf-110">This parameter can be one of the following values.</span></span>

| <span data-ttu-id="b0acf-111">值</span><span class="sxs-lookup"><span data-stu-id="b0acf-111">Value</span></span> | <span data-ttu-id="b0acf-112">意義</span><span class="sxs-lookup"><span data-stu-id="b0acf-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="b0acf-113">**CTRL_C_EVENT** 0</span><span class="sxs-lookup"><span data-stu-id="b0acf-113">**CTRL_C_EVENT** 0</span></span> | <span data-ttu-id="b0acf-114">產生 CTRL + C 信號。</span><span class="sxs-lookup"><span data-stu-id="b0acf-114">Generates a CTRL+C signal.</span></span> <span data-ttu-id="b0acf-115">無法產生進程群組的這個信號。</span><span class="sxs-lookup"><span data-stu-id="b0acf-115">This signal cannot be generated for process groups.</span></span> <span data-ttu-id="b0acf-116">如果 *dwProcessGroupId* 為非零值，則此函式會成功，但是在指定的進程群組內，進程將不會收到 CTRL + C 信號。</span><span class="sxs-lookup"><span data-stu-id="b0acf-116">If *dwProcessGroupId* is nonzero, this function will succeed, but the CTRL+C signal will not be received by processes within the specified process group.</span></span> |
| <span data-ttu-id="b0acf-117">**CTRL_BREAK_EVENT** 1</span><span class="sxs-lookup"><span data-stu-id="b0acf-117">**CTRL_BREAK_EVENT** 1</span></span> | <span data-ttu-id="b0acf-118">產生 CTRL + BREAK 信號。</span><span class="sxs-lookup"><span data-stu-id="b0acf-118">Generates a CTRL+BREAK signal.</span></span> |

<span data-ttu-id="b0acf-119">*dwProcessGroupId* \[在\]</span><span class="sxs-lookup"><span data-stu-id="b0acf-119">*dwProcessGroupId* \[in\]</span></span>  
<span data-ttu-id="b0acf-120">要接收信號之進程群組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b0acf-120">The identifier of the process group to receive the signal.</span></span> <span data-ttu-id="b0acf-121">在對 [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)函式的呼叫中指定了 **建立 \_ 新的 \_ 進程 \_ 群組** 旗標時，就會建立進程群組。</span><span class="sxs-lookup"><span data-stu-id="b0acf-121">A process group is created when the **CREATE\_NEW\_PROCESS\_GROUP** flag is specified in a call to the [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) function.</span></span> <span data-ttu-id="b0acf-122">新進程的處理序識別碼也是新進程群組的進程群組識別碼。</span><span class="sxs-lookup"><span data-stu-id="b0acf-122">The process identifier of the new process is also the process group identifier of a new process group.</span></span> <span data-ttu-id="b0acf-123">進程群組包含根進程下階的所有進程。</span><span class="sxs-lookup"><span data-stu-id="b0acf-123">The process group includes all processes that are descendants of the root process.</span></span> <span data-ttu-id="b0acf-124">只有群組中與呼叫進程共用相同主控台的進程會收到信號。</span><span class="sxs-lookup"><span data-stu-id="b0acf-124">Only those processes in the group that share the same console as the calling process receive the signal.</span></span> <span data-ttu-id="b0acf-125">換句話說，如果群組中的進程會建立新的主控台，該進程就不會收到信號，也不會有其子系。</span><span class="sxs-lookup"><span data-stu-id="b0acf-125">In other words, if a process in the group creates a new console, that process does not receive the signal, nor do its descendants.</span></span>

<span data-ttu-id="b0acf-126">如果此參數為零，則會在共用呼叫進程主控台的所有進程中產生信號。</span><span class="sxs-lookup"><span data-stu-id="b0acf-126">If this parameter is zero, the signal is generated in all processes that share the console of the calling process.</span></span>

## <a name="return-value"></a><span data-ttu-id="b0acf-127">傳回值</span><span class="sxs-lookup"><span data-stu-id="b0acf-127">Return value</span></span>

<span data-ttu-id="b0acf-128">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="b0acf-128">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b0acf-129">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="b0acf-129">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b0acf-130">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="b0acf-130">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="b0acf-131">備註</span><span class="sxs-lookup"><span data-stu-id="b0acf-131">Remarks</span></span>

<span data-ttu-id="b0acf-132">**GenerateConsoleCtrlEvent** 會在目標群組中呼叫進程的控制項處理常式函式。</span><span class="sxs-lookup"><span data-stu-id="b0acf-132">**GenerateConsoleCtrlEvent** causes the control handler functions of processes in the target group to be called.</span></span> <span data-ttu-id="b0acf-133">所有主控台進程都有一個呼叫 [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) 函式的預設處理函式。</span><span class="sxs-lookup"><span data-stu-id="b0acf-133">All console processes have a default handler function that calls the [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) function.</span></span> <span data-ttu-id="b0acf-134">主控台處理常式可以使用 [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) 函數來安裝或移除其他處理常式函式。</span><span class="sxs-lookup"><span data-stu-id="b0acf-134">A console process can use the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function to install or remove other handler functions.</span></span>

<span data-ttu-id="b0acf-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) 也可以啟用可繼承的屬性，使呼叫進程忽略 CTRL + C 信號。</span><span class="sxs-lookup"><span data-stu-id="b0acf-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) can also enable an inheritable attribute that causes the calling process to ignore CTRL+C signals.</span></span> <span data-ttu-id="b0acf-136">如果 **GenerateConsoleCtrlEvent** 將 CTRL + C 信號傳送給已啟用這個屬性的進程，就不會呼叫該處理常式的處理常式函式。</span><span class="sxs-lookup"><span data-stu-id="b0acf-136">If **GenerateConsoleCtrlEvent** sends a CTRL+C signal to a process for which this attribute is enabled, the handler functions for that process are not called.</span></span> <span data-ttu-id="b0acf-137">CTRL + BREAK 信號一律會導致呼叫處理函式。</span><span class="sxs-lookup"><span data-stu-id="b0acf-137">CTRL+BREAK signals always cause the handler functions to be called.</span></span>

## <a name="requirements"></a><span data-ttu-id="b0acf-138">規格需求</span><span class="sxs-lookup"><span data-stu-id="b0acf-138">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b0acf-139">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="b0acf-139">Minimum supported client</span></span> | <span data-ttu-id="b0acf-140">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="b0acf-140">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="b0acf-141">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="b0acf-141">Minimum supported server</span></span> | <span data-ttu-id="b0acf-142">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="b0acf-142">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="b0acf-143">標頭</span><span class="sxs-lookup"><span data-stu-id="b0acf-143">Header</span></span> | <span data-ttu-id="b0acf-144">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="b0acf-144">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="b0acf-145">程式庫</span><span class="sxs-lookup"><span data-stu-id="b0acf-145">Library</span></span> | <span data-ttu-id="b0acf-146">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="b0acf-146">Kernel32.lib</span></span> |
| <span data-ttu-id="b0acf-147">DLL</span><span class="sxs-lookup"><span data-stu-id="b0acf-147">DLL</span></span> | <span data-ttu-id="b0acf-148">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b0acf-148">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="b0acf-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0acf-149">See also</span></span>

[<span data-ttu-id="b0acf-150">主控台控制處理常式</span><span class="sxs-lookup"><span data-stu-id="b0acf-150">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="b0acf-151">主控台函式</span><span class="sxs-lookup"><span data-stu-id="b0acf-151">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b0acf-152">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="b0acf-152">**CreateProcess**</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)

[<span data-ttu-id="b0acf-153">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="b0acf-153">**ExitProcess**</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess)

[<span data-ttu-id="b0acf-154">**SetConsoleCtrlHandler**</span><span class="sxs-lookup"><span data-stu-id="b0acf-154">**SetConsoleCtrlHandler**</span></span>](setconsolectrlhandler.md)
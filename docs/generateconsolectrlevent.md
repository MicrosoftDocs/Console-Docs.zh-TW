---
title: GenerateConsoleCtrlEvent 函式
description: 將指定的信號傳送至主控台進程群組，該群組會共用與呼叫進程相關聯的主控台。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
ms.openlocfilehash: 31c0330a002362542a799ab7e038d3f65497ded3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059199"
---
# <a name="generateconsolectrlevent-function"></a><span data-ttu-id="7d80a-104">GenerateConsoleCtrlEvent 函式</span><span class="sxs-lookup"><span data-stu-id="7d80a-104">GenerateConsoleCtrlEvent function</span></span>


<span data-ttu-id="7d80a-105">將指定的信號傳送至主控台進程群組，該群組會共用與呼叫進程相關聯的主控台。</span><span class="sxs-lookup"><span data-stu-id="7d80a-105">Sends a specified signal to a console process group that shares the console associated with the calling process.</span></span>

<a name="syntax"></a><span data-ttu-id="7d80a-106">語法</span><span class="sxs-lookup"><span data-stu-id="7d80a-106">Syntax</span></span>
------

```C
BOOL WINAPI GenerateConsoleCtrlEvent(
  _In_ DWORD dwCtrlEvent,
  _In_ DWORD dwProcessGroupId
);
```

<a name="parameters"></a><span data-ttu-id="7d80a-107">參數</span><span class="sxs-lookup"><span data-stu-id="7d80a-107">Parameters</span></span>
----------

<span data-ttu-id="7d80a-108">*dwCtrlEvent* \[在\]</span><span class="sxs-lookup"><span data-stu-id="7d80a-108">*dwCtrlEvent* \[in\]</span></span>  
<span data-ttu-id="7d80a-109">要產生的信號類型。</span><span class="sxs-lookup"><span data-stu-id="7d80a-109">The type of signal to be generated.</span></span> <span data-ttu-id="7d80a-110">這個參數可以是下列其中一個值。</span><span class="sxs-lookup"><span data-stu-id="7d80a-110">This parameter can be one of the following values.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="7d80a-111">值</span><span class="sxs-lookup"><span data-stu-id="7d80a-111">Value</span></span></th>
<th><span data-ttu-id="7d80a-112">意義</span><span class="sxs-lookup"><span data-stu-id="7d80a-112">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="7d80a-113"><span id="CTRL_C_EVENT"></span><span id="ctrl_c_event"></span>
<strong>CTRL_C_EVENT</strong> 0</span><span class="sxs-lookup"><span data-stu-id="7d80a-113"><span id="CTRL_C_EVENT"></span><span id="ctrl_c_event"></span>
<strong>CTRL_C_EVENT</strong> 0</span></span></td>
<td><p><span data-ttu-id="7d80a-114">產生 CTRL + C 信號。</span><span class="sxs-lookup"><span data-stu-id="7d80a-114">Generates a CTRL+C signal.</span></span> <span data-ttu-id="7d80a-115">無法產生進程群組的這個信號。</span><span class="sxs-lookup"><span data-stu-id="7d80a-115">This signal cannot be generated for process groups.</span></span> <span data-ttu-id="7d80a-116">如果 <em>dwProcessGroupId</em> 為非零值，則此函式會成功，但是在指定的進程群組內，進程將不會收到 CTRL + C 信號。</span><span class="sxs-lookup"><span data-stu-id="7d80a-116">If <em>dwProcessGroupId</em> is nonzero, this function will succeed, but the CTRL+C signal will not be received by processes within the specified process group.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="7d80a-117"><span id="CTRL_BREAK_EVENT"></span><span id="ctrl_break_event"></span>
<strong>CTRL_BREAK_EVENT</strong> 1</span><span class="sxs-lookup"><span data-stu-id="7d80a-117"><span id="CTRL_BREAK_EVENT"></span><span id="ctrl_break_event"></span>
<strong>CTRL_BREAK_EVENT</strong> 1</span></span></td>
<td><p><span data-ttu-id="7d80a-118">產生 CTRL + BREAK 信號。</span><span class="sxs-lookup"><span data-stu-id="7d80a-118">Generates a CTRL+BREAK signal.</span></span></p></td>
</tr>
</tbody>
</table>

 

<span data-ttu-id="7d80a-119">*dwProcessGroupId* \[在\]</span><span class="sxs-lookup"><span data-stu-id="7d80a-119">*dwProcessGroupId* \[in\]</span></span>  
<span data-ttu-id="7d80a-120">要接收信號之進程群組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7d80a-120">The identifier of the process group to receive the signal.</span></span> <span data-ttu-id="7d80a-121">在對[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)函式的呼叫中指定了**建立 \_ 新的 \_ 進程 \_ 群組**旗標時，就會建立進程群組。</span><span class="sxs-lookup"><span data-stu-id="7d80a-121">A process group is created when the **CREATE\_NEW\_PROCESS\_GROUP** flag is specified in a call to the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function.</span></span> <span data-ttu-id="7d80a-122">新進程的處理序識別碼也是新進程群組的進程群組識別碼。</span><span class="sxs-lookup"><span data-stu-id="7d80a-122">The process identifier of the new process is also the process group identifier of a new process group.</span></span> <span data-ttu-id="7d80a-123">進程群組包含根進程下階的所有進程。</span><span class="sxs-lookup"><span data-stu-id="7d80a-123">The process group includes all processes that are descendants of the root process.</span></span> <span data-ttu-id="7d80a-124">只有群組中與呼叫進程共用相同主控台的進程會收到信號。</span><span class="sxs-lookup"><span data-stu-id="7d80a-124">Only those processes in the group that share the same console as the calling process receive the signal.</span></span> <span data-ttu-id="7d80a-125">換句話說，如果群組中的進程會建立新的主控台，該進程就不會收到信號，也不會有其子系。</span><span class="sxs-lookup"><span data-stu-id="7d80a-125">In other words, if a process in the group creates a new console, that process does not receive the signal, nor do its descendants.</span></span>

<span data-ttu-id="7d80a-126">如果此參數為零，則會在共用呼叫進程主控台的所有進程中產生信號。</span><span class="sxs-lookup"><span data-stu-id="7d80a-126">If this parameter is zero, the signal is generated in all processes that share the console of the calling process.</span></span>

<a name="return-value"></a><span data-ttu-id="7d80a-127">傳回值</span><span class="sxs-lookup"><span data-stu-id="7d80a-127">Return value</span></span>
------------

<span data-ttu-id="7d80a-128">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="7d80a-128">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="7d80a-129">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="7d80a-129">If the function fails, the return value is zero.</span></span> <span data-ttu-id="7d80a-130">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="7d80a-130">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="7d80a-131">備註</span><span class="sxs-lookup"><span data-stu-id="7d80a-131">Remarks</span></span>
-------

<span data-ttu-id="7d80a-132">**GenerateConsoleCtrlEvent** 會在目標群組中呼叫進程的控制項處理常式函式。</span><span class="sxs-lookup"><span data-stu-id="7d80a-132">**GenerateConsoleCtrlEvent** causes the control handler functions of processes in the target group to be called.</span></span> <span data-ttu-id="7d80a-133">所有主控台進程都有一個呼叫 [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) 函式的預設處理函式。</span><span class="sxs-lookup"><span data-stu-id="7d80a-133">All console processes have a default handler function that calls the [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) function.</span></span> <span data-ttu-id="7d80a-134">主控台處理常式可以使用 [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) 函數來安裝或移除其他處理常式函式。</span><span class="sxs-lookup"><span data-stu-id="7d80a-134">A console process can use the [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) function to install or remove other handler functions.</span></span>

<span data-ttu-id="7d80a-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) 也可以啟用可繼承的屬性，使呼叫進程忽略 CTRL + C 信號。</span><span class="sxs-lookup"><span data-stu-id="7d80a-135">[**SetConsoleCtrlHandler**](setconsolectrlhandler.md) can also enable an inheritable attribute that causes the calling process to ignore CTRL+C signals.</span></span> <span data-ttu-id="7d80a-136">如果 **GenerateConsoleCtrlEvent** 將 CTRL + C 信號傳送給已啟用這個屬性的進程，就不會呼叫該處理常式的處理常式函式。</span><span class="sxs-lookup"><span data-stu-id="7d80a-136">If **GenerateConsoleCtrlEvent** sends a CTRL+C signal to a process for which this attribute is enabled, the handler functions for that process are not called.</span></span> <span data-ttu-id="7d80a-137">CTRL + BREAK 信號一律會導致呼叫處理函式。</span><span class="sxs-lookup"><span data-stu-id="7d80a-137">CTRL+BREAK signals always cause the handler functions to be called.</span></span>

<a name="requirements"></a><span data-ttu-id="7d80a-138">規格需求</span><span class="sxs-lookup"><span data-stu-id="7d80a-138">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="7d80a-139">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="7d80a-139">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="7d80a-140">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="7d80a-140">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7d80a-141">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="7d80a-141">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="7d80a-142">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="7d80a-142">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7d80a-143">標頭</span><span class="sxs-lookup"><span data-stu-id="7d80a-143">Header</span></span></p></td>
<td><span data-ttu-id="7d80a-144">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="7d80a-144">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7d80a-145">程式庫</span><span class="sxs-lookup"><span data-stu-id="7d80a-145">Library</span></span></p></td>
<td><span data-ttu-id="7d80a-146">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="7d80a-146">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7d80a-147">DLL</span><span class="sxs-lookup"><span data-stu-id="7d80a-147">DLL</span></span></p></td>
<td><span data-ttu-id="7d80a-148">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7d80a-148">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="7d80a-149"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d80a-149"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="7d80a-150">主控台控制處理常式</span><span class="sxs-lookup"><span data-stu-id="7d80a-150">Console Control Handlers</span></span>](console-control-handlers.md)

[<span data-ttu-id="7d80a-151">主控台功能</span><span class="sxs-lookup"><span data-stu-id="7d80a-151">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="7d80a-152">**CreateProcess**</span><span class="sxs-lookup"><span data-stu-id="7d80a-152">**CreateProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)

[<span data-ttu-id="7d80a-153">**ExitProcess**</span><span class="sxs-lookup"><span data-stu-id="7d80a-153">**ExitProcess**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682658)

[<span data-ttu-id="7d80a-154">**SetConsoleCtrlHandler**</span><span class="sxs-lookup"><span data-stu-id="7d80a-154">**SetConsoleCtrlHandler**</span></span>](setconsolectrlhandler.md)

 

 





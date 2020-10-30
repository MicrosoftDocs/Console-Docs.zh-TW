---
title: FreeConsole 函式
description: 請參閱 FreeConsole 函式的參考資訊，此函式會從其主控台卸離呼叫進程。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/FreeConsole
- wincon/FreeConsole
- FreeConsole
MS-HAID:
- '\_win32\_freeconsole'
- base.freeconsole
- consoles.freeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6c525325-696e-4d8b-8337-cbf9e31c900c
topic_type:
- apiref
api_name:
- FreeConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: af4382026b8e6455319e16ee21255fbc9352e3cd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039016"
---
# <a name="freeconsole-function"></a><span data-ttu-id="94a69-104">FreeConsole 函式</span><span class="sxs-lookup"><span data-stu-id="94a69-104">FreeConsole function</span></span>

<span data-ttu-id="94a69-105">從其主控台卸離呼叫進程。</span><span class="sxs-lookup"><span data-stu-id="94a69-105">Detaches the calling process from its console.</span></span>

## <a name="syntax"></a><span data-ttu-id="94a69-106">語法</span><span class="sxs-lookup"><span data-stu-id="94a69-106">Syntax</span></span>

```C
BOOL WINAPI FreeConsole(void);
```

## <a name="parameters"></a><span data-ttu-id="94a69-107">參數</span><span class="sxs-lookup"><span data-stu-id="94a69-107">Parameters</span></span>

<span data-ttu-id="94a69-108">此函式沒有參數。</span><span class="sxs-lookup"><span data-stu-id="94a69-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="94a69-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="94a69-109">Return value</span></span>

<span data-ttu-id="94a69-110">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="94a69-110">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="94a69-111">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="94a69-111">If the function fails, the return value is zero.</span></span> <span data-ttu-id="94a69-112">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="94a69-112">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="94a69-113">備註</span><span class="sxs-lookup"><span data-stu-id="94a69-113">Remarks</span></span>

<span data-ttu-id="94a69-114">一個進程最多可以附加至一個主控台。</span><span class="sxs-lookup"><span data-stu-id="94a69-114">A process can be attached to at most one console.</span></span> <span data-ttu-id="94a69-115">如果呼叫進程尚未附加到主控台，則傳回的錯誤碼會是 **錯誤 \_ 不正確 \_ 參數** (87) 。</span><span class="sxs-lookup"><span data-stu-id="94a69-115">If the calling process is not already attached to a console, the error code returned is **ERROR\_INVALID\_PARAMETER** (87).</span></span>

<span data-ttu-id="94a69-116">進程可以使用 **FreeConsole** 函式，從其主控台卸離本身。</span><span class="sxs-lookup"><span data-stu-id="94a69-116">A process can use the **FreeConsole** function to detach itself from its console.</span></span> <span data-ttu-id="94a69-117">如果有其他進程共用主控台，主控台就不會終結，但呼叫 **FreeConsole** 的進程無法參考它。</span><span class="sxs-lookup"><span data-stu-id="94a69-117">If other processes share the console, the console is not destroyed, but the process that called **FreeConsole** cannot refer to it.</span></span> <span data-ttu-id="94a69-118">當最後一個附加至它的進程終止或呼叫 **FreeConsole** 時，主控台就會關閉。</span><span class="sxs-lookup"><span data-stu-id="94a69-118">A console is closed when the last process attached to it terminates or calls **FreeConsole** .</span></span> <span data-ttu-id="94a69-119">在進程呼叫 **FreeConsole** 之後，它就可以呼叫 [**AllocConsole**](allocconsole.md) 函式來建立新的主控台或 [**AttachConsole**](attachconsole.md) ，以附加至另一個主控台。</span><span class="sxs-lookup"><span data-stu-id="94a69-119">After a process calls **FreeConsole** , it can call the [**AllocConsole**](allocconsole.md) function to create a new console or [**AttachConsole**](attachconsole.md) to attach to another console.</span></span>

## <a name="requirements"></a><span data-ttu-id="94a69-120">規格需求</span><span class="sxs-lookup"><span data-stu-id="94a69-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="94a69-121">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="94a69-121">Minimum supported client</span></span> | <span data-ttu-id="94a69-122">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="94a69-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="94a69-123">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="94a69-123">Minimum supported server</span></span> | <span data-ttu-id="94a69-124">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="94a69-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="94a69-125">標頭</span><span class="sxs-lookup"><span data-stu-id="94a69-125">Header</span></span> | <span data-ttu-id="94a69-126">ConsoleApi .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="94a69-126">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="94a69-127">程式庫</span><span class="sxs-lookup"><span data-stu-id="94a69-127">Library</span></span> | <span data-ttu-id="94a69-128">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="94a69-128">Kernel32.lib</span></span> |
| <span data-ttu-id="94a69-129">DLL</span><span class="sxs-lookup"><span data-stu-id="94a69-129">DLL</span></span> | <span data-ttu-id="94a69-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="94a69-130">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="94a69-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="94a69-131">See also</span></span>

[<span data-ttu-id="94a69-132">**AllocConsole**</span><span class="sxs-lookup"><span data-stu-id="94a69-132">**AllocConsole**</span></span>](allocconsole.md)

[<span data-ttu-id="94a69-133">**AttachConsole**</span><span class="sxs-lookup"><span data-stu-id="94a69-133">**AttachConsole**</span></span>](attachconsole.md)

[<span data-ttu-id="94a69-134">主控台功能</span><span class="sxs-lookup"><span data-stu-id="94a69-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="94a69-135">機</span><span class="sxs-lookup"><span data-stu-id="94a69-135">Consoles</span></span>](consoles.md)

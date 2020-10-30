---
title: ClosePseudoConsole 函式
description: 請參閱 ClosePseudoConsole 函式的參考資訊，此函式會從指定的控制碼關閉 pseudoconsole。
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api，conpty，pseudoconsole
topic_type:
- apiref
api_name:
- ClosePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 067fa732f5badfe46ee6391c892aa037613cb4dd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037286"
---
# <a name="closepseudoconsole-function"></a><span data-ttu-id="f0cdf-104">ClosePseudoConsole 函式</span><span class="sxs-lookup"><span data-stu-id="f0cdf-104">ClosePseudoConsole function</span></span>

<span data-ttu-id="f0cdf-105">從給定的控制碼關閉 pseudoconsole。</span><span class="sxs-lookup"><span data-stu-id="f0cdf-105">Closes a pseudoconsole from the given handle.</span></span>

## <a name="syntax"></a><span data-ttu-id="f0cdf-106">語法</span><span class="sxs-lookup"><span data-stu-id="f0cdf-106">Syntax</span></span>

```C
void WINAPI ClosePseudoConsole(
    _In_ HPCON hPC
);
```

## <a name="parameters"></a><span data-ttu-id="f0cdf-107">參數</span><span class="sxs-lookup"><span data-stu-id="f0cdf-107">Parameters</span></span>

<span data-ttu-id="f0cdf-108">*hPC* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f0cdf-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="f0cdf-109">由 [CreatePseudoConsole](createpseudoconsole.md)開啟之作用中 pseudoconsole 的控制碼。</span><span class="sxs-lookup"><span data-stu-id="f0cdf-109">A handle to an active pseudoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

## <a name="return-value"></a><span data-ttu-id="f0cdf-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="f0cdf-110">Return value</span></span>

<span data-ttu-id="f0cdf-111">無</span><span class="sxs-lookup"><span data-stu-id="f0cdf-111">*none*</span></span>

## <a name="remarks"></a><span data-ttu-id="f0cdf-112">備註</span><span class="sxs-lookup"><span data-stu-id="f0cdf-112">Remarks</span></span>

<span data-ttu-id="f0cdf-113">在關閉 pseudoconsole 時，附加至會話的用戶端應用程式也會終止。</span><span class="sxs-lookup"><span data-stu-id="f0cdf-113">Upon closing a pseudoconsole, client applications attached to the session will be terminated as well.</span></span>

<span data-ttu-id="f0cdf-114">當呼叫此 API 時，最後繪製的框架可能會抵達 `hOutput` 最初提供給 [CreatePsuedoConsole](createpseudoconsole.md) 的控制碼。</span><span class="sxs-lookup"><span data-stu-id="f0cdf-114">A final painted frame may arrive on the `hOutput` handle originally provided to [CreatePsuedoConsole](createpseudoconsole.md) when this API is called.</span></span> <span data-ttu-id="f0cdf-115">呼叫端應該會清空通道緩衝區中的這項資訊，並將其呈現或捨棄。</span><span class="sxs-lookup"><span data-stu-id="f0cdf-115">It is expected that the caller will drain this information from the communication channel buffer and either present it or discard it.</span></span> <span data-ttu-id="f0cdf-116">若無法清空緩衝區，可能會導致關閉呼叫無限期等候，直到它被清空或通道以另一種方式中斷為止。</span><span class="sxs-lookup"><span data-stu-id="f0cdf-116">Failure to drain the buffer may cause the Close call to wait indefinitely until it is drained or the communication channels are broken another way.</span></span>

## <a name="requirements"></a><span data-ttu-id="f0cdf-117">規格需求</span><span class="sxs-lookup"><span data-stu-id="f0cdf-117">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="f0cdf-118">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="f0cdf-118">Minimum supported client</span></span> | <span data-ttu-id="f0cdf-119">Windows 10 2018 年10月更新 (1809 版) \[ 桌面應用程式\]</span><span class="sxs-lookup"><span data-stu-id="f0cdf-119">Windows 10 October 2018 Update (version 1809) \[desktop apps only\]</span></span> |
| <span data-ttu-id="f0cdf-120">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="f0cdf-120">Minimum supported server</span></span> | <span data-ttu-id="f0cdf-121">僅限 Windows Server 2019 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="f0cdf-121">Windows Server 2019 \[desktop apps only\]</span></span> |
| <span data-ttu-id="f0cdf-122">標頭</span><span class="sxs-lookup"><span data-stu-id="f0cdf-122">Header</span></span> | <span data-ttu-id="f0cdf-123">ConsoleApi .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="f0cdf-123">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="f0cdf-124">程式庫</span><span class="sxs-lookup"><span data-stu-id="f0cdf-124">Library</span></span> | <span data-ttu-id="f0cdf-125">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="f0cdf-125">Kernel32.lib</span></span> |
| <span data-ttu-id="f0cdf-126">DLL</span><span class="sxs-lookup"><span data-stu-id="f0cdf-126">DLL</span></span> | <span data-ttu-id="f0cdf-127">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f0cdf-127">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="f0cdf-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="f0cdf-128">See also</span></span>

[<span data-ttu-id="f0cdf-129">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="f0cdf-129">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="f0cdf-130">**CreatePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="f0cdf-130">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="f0cdf-131">**ResizePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="f0cdf-131">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)

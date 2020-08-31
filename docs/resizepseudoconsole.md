---
title: ResizePseudoConsole 函式
description: 請參閱 ResizePseudoConsole 函式的參考資訊，此函式會將 pseudoconsole 的內部緩衝區大小調整為指定的大小。
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api，conpty，pseudoconsole
f1_keywords:
- consoleapi/ResizePseudoConsole
- ResizePseudoConsole
topic_type:
- apiref
api_name:
- ResizePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a4f6ff773538eda4d4c84c4b0bac2e647f6b80d8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059443"
---
# <a name="resizepseudoconsole-function"></a><span data-ttu-id="87624-104">ResizePseudoConsole 函式</span><span class="sxs-lookup"><span data-stu-id="87624-104">ResizePseudoConsole function</span></span>


<span data-ttu-id="87624-105">將 pseudoconsole 的內部緩衝區大小調整為指定的大小。</span><span class="sxs-lookup"><span data-stu-id="87624-105">Resizes the internal buffers for a pseudoconsole to the given size.</span></span>

<a name="syntax"></a><span data-ttu-id="87624-106">語法</span><span class="sxs-lookup"><span data-stu-id="87624-106">Syntax</span></span>
------

```C
HRESULT WINAPI ResizePseudoConsole(
    _In_ HPCON hPC ,
    _In_ COORD size
);
```

<a name="parameters"></a><span data-ttu-id="87624-107">參數</span><span class="sxs-lookup"><span data-stu-id="87624-107">Parameters</span></span>
----------

<span data-ttu-id="87624-108">*hPC* \[在\]</span><span class="sxs-lookup"><span data-stu-id="87624-108">*hPC* \[in\]</span></span>  
<span data-ttu-id="87624-109">由 [CreatePseudoConsole](createpseudoconsole.md)開啟之作用中 psuedoconsole 的控制碼。</span><span class="sxs-lookup"><span data-stu-id="87624-109">A handle to an active psuedoconsole as opened by [CreatePseudoConsole](createpseudoconsole.md).</span></span>

<span data-ttu-id="87624-110">*大小* \[在\]</span><span class="sxs-lookup"><span data-stu-id="87624-110">*size* \[in\]</span></span>  
<span data-ttu-id="87624-111">視窗/緩衝區的大小（以字元數為單位），將用於此 pseudoconsole 的內部緩衝區。</span><span class="sxs-lookup"><span data-stu-id="87624-111">The dimensions of the window/buffer in count of characters that will be used for the internal buffer of this pseudoconsole.</span></span> 

<a name="return-value"></a><span data-ttu-id="87624-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="87624-112">Return value</span></span>
------------

<span data-ttu-id="87624-113">類型： **HRESULT**</span><span class="sxs-lookup"><span data-stu-id="87624-113">Type: **HRESULT**</span></span>

<span data-ttu-id="87624-114">如果這個方法成功，它會傳回 **S_OK**。</span><span class="sxs-lookup"><span data-stu-id="87624-114">If this method succeeds, it returns **S_OK**.</span></span> <span data-ttu-id="87624-115">否則，它會傳回 **HRESULT** 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="87624-115">Otherwise, it returns an **HRESULT** error code.</span></span>

<a name="remarks"></a><span data-ttu-id="87624-116">備註</span><span class="sxs-lookup"><span data-stu-id="87624-116">Remarks</span></span>
-------

<span data-ttu-id="87624-117">此函數可以調整 pseudoconsole 會話中的內部緩衝區大小，以符合終端機端上所用的視窗/緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="87624-117">This function can resize the internal buffers in the pseudoconsole session to match the window/buffer size being used for display on the terminal end.</span></span> <span data-ttu-id="87624-118">這可確保使用 [主控台](console-functions.md) 函式進行通訊的附加命令列介面 (CUI) 應用程式將會在其呼叫中傳回正確的維度。</span><span class="sxs-lookup"><span data-stu-id="87624-118">This ensures that attached Command-Line Interface (CUI) applications using the [Console Functions](console-functions.md) to communicate will have the correct dimensions returned in their calls.</span></span>

<a name="requirements"></a><span data-ttu-id="87624-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="87624-119">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="87624-120">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="87624-120">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="87624-121">Windows 10 1809 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="87624-121">Windows 10 1809 [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="87624-122">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="87624-122">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="87624-123">Windows Server 2019 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="87624-123">Windows Server 2019 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="87624-124">標頭</span><span class="sxs-lookup"><span data-stu-id="87624-124">Header</span></span></p></td>
<td><span data-ttu-id="87624-125">ConsoleApi .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="87624-125">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="87624-126">程式庫</span><span class="sxs-lookup"><span data-stu-id="87624-126">Library</span></span></p></td>
<td><span data-ttu-id="87624-127">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="87624-127">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="87624-128">DLL</span><span class="sxs-lookup"><span data-stu-id="87624-128">DLL</span></span></p></td>
<td><span data-ttu-id="87624-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="87624-129">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="87624-130"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="87624-130"><span id="see_also"></span>See also</span></span>

[<span data-ttu-id="87624-131">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="87624-131">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="87624-132">**CreatePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="87624-132">**CreatePseudoConsole**</span></span>](createpseudoconsole.md)

[<span data-ttu-id="87624-133">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="87624-133">**ClosePseudoConsole**</span></span>](closepseudoconsole.md)

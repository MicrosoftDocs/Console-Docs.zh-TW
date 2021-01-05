---
title: CreatePseudoConsole 函式
description: 請參閱 CreatePseudoConsole 函式的參考資訊，此函式會為呼叫進程配置新的 pseudoconsole。
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api，conpty，pseudoconsole
f1_keywords:
- consoleapi/CreatePseudoConsole
- CreatePseudoConsole
topic_type:
- apiref
api_name:
- CreatePseudoConsole
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-2-1.dll
- KernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: b015f224684a53a8bb654f04b1797ac1af794fc3
ms.sourcegitcommit: f16996b9c7deead9bcfa44954be93a6ba087abcb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/16/2020
ms.locfileid: "97601475"
---
# <a name="createpseudoconsole-function"></a><span data-ttu-id="cf6fc-104">CreatePseudoConsole 函式</span><span class="sxs-lookup"><span data-stu-id="cf6fc-104">CreatePseudoConsole function</span></span>

<span data-ttu-id="cf6fc-105">為呼叫進程建立新的 pseudoconsole 物件。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-105">Creates a new pseudoconsole object for the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="cf6fc-106">語法</span><span class="sxs-lookup"><span data-stu-id="cf6fc-106">Syntax</span></span>

```C
HRESULT WINAPI CreatePseudoConsole(
    _In_ COORD size,
    _In_ HANDLE hInput,
    _In_ HANDLE hOutput,
    _In_ DWORD dwFlags,
    _Out_ HPCON* phPC
);
```

## <a name="parameters"></a><span data-ttu-id="cf6fc-107">參數</span><span class="sxs-lookup"><span data-stu-id="cf6fc-107">Parameters</span></span>

<span data-ttu-id="cf6fc-108">*大小* \[在\]</span><span class="sxs-lookup"><span data-stu-id="cf6fc-108">*size* \[in\]</span></span>  
<span data-ttu-id="cf6fc-109">將在初始建立 pseudoconsole 時使用的視窗/緩衝區維度（以字元數為單位）。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-109">The dimensions of the window/buffer in count of characters that will be used on initial creation of the pseudoconsole.</span></span> <span data-ttu-id="cf6fc-110">這可以在稍後使用 [ResizePseudoConsole](resizepseudoconsole.md)進行調整。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-110">This can be adjusted later with [ResizePseudoConsole](resizepseudoconsole.md).</span></span>

<span data-ttu-id="cf6fc-111">*hInput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="cf6fc-111">*hInput* \[in\]</span></span>  
<span data-ttu-id="cf6fc-112">表示使用者輸入至裝置之資料流程的開啟控制碼。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-112">An open handle to a stream of data that represents user input to the device.</span></span> <span data-ttu-id="cf6fc-113">這目前僅限於 [同步](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) i/o。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-113">This is currently restricted to [synchronous](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.</span></span>

<span data-ttu-id="cf6fc-114">*hOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="cf6fc-114">*hOutput* \[in\]</span></span>  
<span data-ttu-id="cf6fc-115">代表裝置應用程式輸出的資料流程的開啟控制碼。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-115">An open handle to a stream of data that represents application output from the device.</span></span> <span data-ttu-id="cf6fc-116">這目前僅限於 [同步](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) i/o。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-116">This is currently restricted to [synchronous](https://docs.microsoft.com/windows/desktop/Sync/synchronization-and-overlapped-input-and-output) I/O.</span></span>

<span data-ttu-id="cf6fc-117">*dwFlags* \[在\]</span><span class="sxs-lookup"><span data-stu-id="cf6fc-117">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="cf6fc-118">這個值可以是下列值之一：</span><span class="sxs-lookup"><span data-stu-id="cf6fc-118">The value can be one of the following:</span></span>

| <span data-ttu-id="cf6fc-119">值</span><span class="sxs-lookup"><span data-stu-id="cf6fc-119">Value</span></span> | <span data-ttu-id="cf6fc-120">意義</span><span class="sxs-lookup"><span data-stu-id="cf6fc-120">Meaning</span></span> |
|-|-|
| <span data-ttu-id="cf6fc-121">**0**</span><span class="sxs-lookup"><span data-stu-id="cf6fc-121">**0**</span></span> | <span data-ttu-id="cf6fc-122">執行標準 pseudoconsole 建立。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-122">Perform a standard pseudoconsole creation.</span></span> |
| <span data-ttu-id="cf6fc-123">**PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD) 1</span><span class="sxs-lookup"><span data-stu-id="cf6fc-123">**PSEUDOCONSOLE_INHERIT_CURSOR** (DWORD)1</span></span> | <span data-ttu-id="cf6fc-124">建立的 pseudoconsole 會話將嘗試繼承父主控台的游標位置。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-124">The created pseudoconsole session will attempt to inherit the cursor position of the parent console.</span></span> |

<span data-ttu-id="cf6fc-125">*phPC* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="cf6fc-125">*phPC* \[out\]</span></span>  
<span data-ttu-id="cf6fc-126">將接收新 pseudoconsole 裝置之控制碼的位置指標。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-126">Pointer to a location that will receive a handle to the new pseudoconsole device.</span></span>

## <a name="return-value"></a><span data-ttu-id="cf6fc-127">傳回值</span><span class="sxs-lookup"><span data-stu-id="cf6fc-127">Return value</span></span>

<span data-ttu-id="cf6fc-128">類型： **HRESULT**</span><span class="sxs-lookup"><span data-stu-id="cf6fc-128">Type: **HRESULT**</span></span>

<span data-ttu-id="cf6fc-129">如果這個方法成功，它會傳回 **S_OK**。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-129">If this method succeeds, it returns **S_OK**.</span></span> <span data-ttu-id="cf6fc-130">否則，它會傳回 **HRESULT** 錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-130">Otherwise, it returns an **HRESULT** error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cf6fc-131">備註</span><span class="sxs-lookup"><span data-stu-id="cf6fc-131">Remarks</span></span>

<span data-ttu-id="cf6fc-132">這項功能主要是由應用程式嘗試作為命令列使用者介面的終端機視窗所使用 (CUI) 應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-132">This function is primarily used by applications attempting to be a terminal window for a command-line user interface (CUI) application.</span></span> <span data-ttu-id="cf6fc-133">呼叫端會負責呈現輸出資料流程上的資訊，以及收集使用者輸入並將其序列化至輸入資料流程中。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-133">The callers become responsible for presentation of the information on the output stream and for collecting user input and serializing it into the input stream.</span></span>

<span data-ttu-id="cf6fc-134">編碼為 UTF-8 的輸入和輸出資料流程，包含以 [虛擬終端序列](console-virtual-terminal-sequences.md)交錯的純文字。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-134">The input and output streams encoded as UTF-8 contain plain text interleaved with [Virtual Terminal Sequences](console-virtual-terminal-sequences.md).</span></span>

<span data-ttu-id="cf6fc-135">在輸出資料流程中，呼叫應用程式可以將 [虛擬終端機序列](console-virtual-terminal-sequences.md) 解碼為版面配置，並在顯示視窗中顯示純文字。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-135">On the output stream, the [virtual terminal sequences](console-virtual-terminal-sequences.md) can be decoded by the calling application to layout and present the plain text in a display window.</span></span>

<span data-ttu-id="cf6fc-136">在輸入資料流程中，純文字代表使用者輸入的標準鍵盤按鍵。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-136">On the input stream, plain text represents standard keyboard keys input by a user.</span></span> <span data-ttu-id="cf6fc-137">更複雜的作業會以編碼控制鍵和滑鼠移動來表示，作為內嵌于此資料流程中的 [虛擬終端機序列](console-virtual-terminal-sequences.md) 。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-137">More complicated operations are represented by encoding control keys and mouse movements as [virtual terminal sequences](console-virtual-terminal-sequences.md) embedded in this stream.</span></span>

<span data-ttu-id="cf6fc-138">當作業完成時，此函式所建立的控制碼必須在 [ClosePseudoConsole](closepseudoconsole.md) 中關閉。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-138">The handle created by this function must be closed with [ClosePseudoConsole](closepseudoconsole.md) when operations are complete.</span></span>

<span data-ttu-id="cf6fc-139">如果使用 `PSEUDOCONSOLE_INHERIT_CURSOR` ，則呼叫的應用程式應該準備好在背景執行緒上以非同步方式回應資料指標狀態的要求，方法是轉送或解讀將在其上接收和回復的資料指標資訊要求 `hOutput` `hInput` 。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-139">If using `PSEUDOCONSOLE_INHERIT_CURSOR`, the calling application should be prepared to respond to the request for the cursor state in an asynchronous fashion on a background thread by forwarding or interpreting the request for cursor information that will be received on `hOutput` and replying on `hInput`.</span></span> <span data-ttu-id="cf6fc-140">若未這麼做，可能會導致呼叫的應用程式在提出另一個 pseudoconsole 系統要求時停止回應。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-140">Failure to do so may cause the calling application to hang while making another request of the pseudoconsole system.</span></span>

## <a name="examples"></a><span data-ttu-id="cf6fc-141">範例</span><span class="sxs-lookup"><span data-stu-id="cf6fc-141">Examples</span></span>

<span data-ttu-id="cf6fc-142">如需使用此函數建立 pseudoconsole 會話的完整逐步解說，請參閱建立 [Pseudoconsole 會話](creating-a-pseudoconsole-session.md)。</span><span class="sxs-lookup"><span data-stu-id="cf6fc-142">For a full walkthrough on using this function to establish a pseudoconsole session, please see [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="cf6fc-143">規格需求</span><span class="sxs-lookup"><span data-stu-id="cf6fc-143">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="cf6fc-144">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="cf6fc-144">Minimum supported client</span></span> | <span data-ttu-id="cf6fc-145">Windows 10 2018 年10月更新 (1809 版) \[ 桌面應用程式\]</span><span class="sxs-lookup"><span data-stu-id="cf6fc-145">Windows 10 October 2018 Update (version 1809) \[desktop apps only\]</span></span> |
| <span data-ttu-id="cf6fc-146">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="cf6fc-146">Minimum supported server</span></span> | <span data-ttu-id="cf6fc-147">僅限 Windows Server 2019 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="cf6fc-147">Windows Server 2019 \[desktop apps only\]</span></span> |
| <span data-ttu-id="cf6fc-148">標頭</span><span class="sxs-lookup"><span data-stu-id="cf6fc-148">Header</span></span> | <span data-ttu-id="cf6fc-149">ConsoleApi.h (透過 WinCon.h，包括 Windows.h)</span><span class="sxs-lookup"><span data-stu-id="cf6fc-149">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="cf6fc-150">程式庫</span><span class="sxs-lookup"><span data-stu-id="cf6fc-150">Library</span></span> | <span data-ttu-id="cf6fc-151">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="cf6fc-151">Kernel32.lib</span></span> |
| <span data-ttu-id="cf6fc-152">DLL</span><span class="sxs-lookup"><span data-stu-id="cf6fc-152">DLL</span></span> | <span data-ttu-id="cf6fc-153">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="cf6fc-153">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="cf6fc-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf6fc-154">See also</span></span>

[<span data-ttu-id="cf6fc-155">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="cf6fc-155">Pseudoconsoles</span></span>](pseudoconsoles.md)

[<span data-ttu-id="cf6fc-156">建立 Pseudoconsole 工作階段</span><span class="sxs-lookup"><span data-stu-id="cf6fc-156">Creating a Pseudoconsole Session</span></span>](creating-a-pseudoconsole-session.md)

[<span data-ttu-id="cf6fc-157">**ResizePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="cf6fc-157">**ResizePseudoConsole**</span></span>](resizepseudoconsole.md)

[<span data-ttu-id="cf6fc-158">**ClosePseudoConsole**</span><span class="sxs-lookup"><span data-stu-id="cf6fc-158">**ClosePseudoConsole**</span></span>](closepseudoconsole.md)

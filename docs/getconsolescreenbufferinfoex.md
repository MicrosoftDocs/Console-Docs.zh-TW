---
title: GetConsoleScreenBufferInfoEx 函式
description: 抓取指定的主控台螢幕緩衝區的延伸資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfoEx
- wincon/GetConsoleScreenBufferInfoEx
- GetConsoleScreenBufferInfoEx
MS-HAID:
- base.getconsolescreenbufferinfoex
- consoles.getconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 60534226-d26f-44e2-a4cc-64811882e308
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 5f4b0f11821b7d5b61c61d4ab8f9774c4a69eec0
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037936"
---
# <a name="getconsolescreenbufferinfoex-function"></a><span data-ttu-id="0fe59-104">GetConsoleScreenBufferInfoEx 函式</span><span class="sxs-lookup"><span data-stu-id="0fe59-104">GetConsoleScreenBufferInfoEx function</span></span>

<span data-ttu-id="0fe59-105">抓取指定的主控台螢幕緩衝區的延伸資訊。</span><span class="sxs-lookup"><span data-stu-id="0fe59-105">Retrieves extended information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="0fe59-106">語法</span><span class="sxs-lookup"><span data-stu-id="0fe59-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleScreenBufferInfoEx(
  _In_  HANDLE                        hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a><span data-ttu-id="0fe59-107">參數</span><span class="sxs-lookup"><span data-stu-id="0fe59-107">Parameters</span></span>

<span data-ttu-id="0fe59-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="0fe59-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="0fe59-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="0fe59-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="0fe59-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="0fe59-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="0fe59-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="0fe59-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="0fe59-112">*lpConsoleScreenBufferInfoEx* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="0fe59-112">*lpConsoleScreenBufferInfoEx* \[out\]</span></span>  
<span data-ttu-id="0fe59-113">[**主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX**](console-screen-buffer-infoex.md)結構，此結構會接收要求的主控台畫面緩衝區資訊。</span><span class="sxs-lookup"><span data-stu-id="0fe59-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that receives the requested console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="0fe59-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="0fe59-114">Return value</span></span>

<span data-ttu-id="0fe59-115">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="0fe59-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0fe59-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="0fe59-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0fe59-117">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="0fe59-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="0fe59-118">備註</span><span class="sxs-lookup"><span data-stu-id="0fe59-118">Remarks</span></span>

<span data-ttu-id="0fe59-119">您可以修改 [**主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX**](console-screen-buffer-infoex.md)結構的 **srWindow** 成員中所傳回的矩形，然後將其傳遞至 [**SetConsoleWindowInfo**](setconsolewindowinfo.md)函式，以在視窗中滾動主控台畫面緩衝區、變更視窗的大小，或兩者。</span><span class="sxs-lookup"><span data-stu-id="0fe59-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="0fe59-120">在 [**主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX**](console-screen-buffer-infoex.md) 結構中傳回的所有座標都是在字元儲存格座標中，其中源 (0、0) 位於主控台螢幕緩衝區的左上角。</span><span class="sxs-lookup"><span data-stu-id="0fe59-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

> [!TIP]
> <span data-ttu-id="0fe59-121">此 API 沒有對等的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="0fe59-121">This API does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="0fe59-122">嘗試繪製資料行、格線或填滿顯示以抓取視窗大小的應用程式，可能仍需要使用它。</span><span class="sxs-lookup"><span data-stu-id="0fe59-122">Its use may still be required for applications that are attempting to draw columns, grids, or fill the display to retrieve the window size.</span></span> <span data-ttu-id="0fe59-123">此視窗狀態是由一般資料流程流程之外的 TTY/PTY/Pseudoconsole 所管理，而且通常會被視為用戶端應用程式無法調整的使用者特殊許可權。</span><span class="sxs-lookup"><span data-stu-id="0fe59-123">This window state is managed by the TTY/PTY/Pseudoconsole outside of the normal stream flow and is generally considered a user privilege not adjustable by the client application.</span></span> <span data-ttu-id="0fe59-124">您可以在 [**ReadConsoleInput**](readconsoleinput.md)上收到更新。</span><span class="sxs-lookup"><span data-stu-id="0fe59-124">Updates can be received on [**ReadConsoleInput**](readconsoleinput.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="0fe59-125">規格需求</span><span class="sxs-lookup"><span data-stu-id="0fe59-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0fe59-126">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="0fe59-126">Minimum supported client</span></span> | <span data-ttu-id="0fe59-127">\[僅限 Windows Vista 桌面應用程式\]</span><span class="sxs-lookup"><span data-stu-id="0fe59-127">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="0fe59-128">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="0fe59-128">Minimum supported server</span></span> | <span data-ttu-id="0fe59-129">僅限 Windows Server 2008 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="0fe59-129">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="0fe59-130">標頭</span><span class="sxs-lookup"><span data-stu-id="0fe59-130">Header</span></span> | <span data-ttu-id="0fe59-131">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="0fe59-131">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="0fe59-132">程式庫</span><span class="sxs-lookup"><span data-stu-id="0fe59-132">Library</span></span> | <span data-ttu-id="0fe59-133">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="0fe59-133">Kernel32.lib</span></span> |
| <span data-ttu-id="0fe59-134">DLL</span><span class="sxs-lookup"><span data-stu-id="0fe59-134">DLL</span></span> | <span data-ttu-id="0fe59-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0fe59-135">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="0fe59-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="0fe59-136">See also</span></span>

[<span data-ttu-id="0fe59-137">主控台功能</span><span class="sxs-lookup"><span data-stu-id="0fe59-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0fe59-138">**主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="0fe59-138">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="0fe59-139">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="0fe59-139">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)

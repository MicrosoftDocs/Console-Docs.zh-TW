---
title: GetConsoleScreenBufferInfo 函式
description: 請參閱 GetConsoleScreenBufferInfo 函式的參考資訊，此函式會抓取指定的主控台螢幕緩衝區的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfo
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 2f80f77b749fc9e9dc0aebf4507b0c41f589e40c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358908"
---
# <a name="getconsolescreenbufferinfo-function"></a><span data-ttu-id="df9b9-104">GetConsoleScreenBufferInfo 函式</span><span class="sxs-lookup"><span data-stu-id="df9b9-104">GetConsoleScreenBufferInfo function</span></span>

<span data-ttu-id="df9b9-105">抓取指定的主控台螢幕緩衝區的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="df9b9-105">Retrieves information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="df9b9-106">語法</span><span class="sxs-lookup"><span data-stu-id="df9b9-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

## <a name="parameters"></a><span data-ttu-id="df9b9-107">參數</span><span class="sxs-lookup"><span data-stu-id="df9b9-107">Parameters</span></span>

<span data-ttu-id="df9b9-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="df9b9-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="df9b9-109">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="df9b9-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="df9b9-110">控制代碼必須具有 **GENERIC\_READ** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="df9b9-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="df9b9-111">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="df9b9-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="df9b9-112">*lpConsoleScreenBufferInfo* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="df9b9-112">*lpConsoleScreenBufferInfo* \[out\]</span></span>  
<span data-ttu-id="df9b9-113">[**主控台 \_ 螢幕 \_ 緩衝區 \_**](console-screen-buffer-info-str.md)資訊結構的指標，此結構會接收主控台螢幕緩衝區資訊。</span><span class="sxs-lookup"><span data-stu-id="df9b9-113">A pointer to a [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure that receives the console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="df9b9-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="df9b9-114">Return value</span></span>

<span data-ttu-id="df9b9-115">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="df9b9-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="df9b9-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="df9b9-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="df9b9-117">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="df9b9-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="df9b9-118">備註</span><span class="sxs-lookup"><span data-stu-id="df9b9-118">Remarks</span></span>

<span data-ttu-id="df9b9-119">您可以修改 [**主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊**](console-screen-buffer-info-str.md)結構的 **srWindow** 成員中所傳回的矩形，然後將其傳遞至 [**SetConsoleWindowInfo**](setconsolewindowinfo.md)函式，以在視窗中滾動主控台畫面緩衝區、變更視窗的大小，或兩者。</span><span class="sxs-lookup"><span data-stu-id="df9b9-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="df9b9-120">[**主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊**](console-screen-buffer-info-str.md)結構中傳回的所有座標都是在字元儲存格座標中，其中源 (0、0) 位於主控台螢幕緩衝區的左上角。</span><span class="sxs-lookup"><span data-stu-id="df9b9-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

> [!TIP]
> <span data-ttu-id="df9b9-121">此 API 沒有對等的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="df9b9-121">This API does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="df9b9-122">嘗試繪製資料行、格線或填滿顯示以抓取視窗大小的應用程式，可能仍需要使用它。</span><span class="sxs-lookup"><span data-stu-id="df9b9-122">Its use may still be required for applications that are attempting to draw columns, grids, or fill the display to retrieve the window size.</span></span> <span data-ttu-id="df9b9-123">此視窗狀態是由一般資料流程流程之外的 TTY/PTY/Pseudoconsole 所管理，而且通常會被視為用戶端應用程式無法調整的使用者特殊許可權。</span><span class="sxs-lookup"><span data-stu-id="df9b9-123">This window state is managed by the TTY/PTY/Pseudoconsole outside of the normal stream flow and is generally considered a user privilege not adjustable by the client application.</span></span> <span data-ttu-id="df9b9-124">您可以在 [**ReadConsoleInput**](readconsoleinput.md)上收到更新。</span><span class="sxs-lookup"><span data-stu-id="df9b9-124">Updates can be received on [**ReadConsoleInput**](readconsoleinput.md).</span></span>

## <a name="examples"></a><span data-ttu-id="df9b9-125">範例</span><span class="sxs-lookup"><span data-stu-id="df9b9-125">Examples</span></span>

<span data-ttu-id="df9b9-126">如需範例，請參閱 [滾動螢幕緩衝區視窗](scrolling-a-screen-buffer-s-window.md)。</span><span class="sxs-lookup"><span data-stu-id="df9b9-126">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="df9b9-127">規格需求</span><span class="sxs-lookup"><span data-stu-id="df9b9-127">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="df9b9-128">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="df9b9-128">Minimum supported client</span></span> | <span data-ttu-id="df9b9-129">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="df9b9-129">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="df9b9-130">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="df9b9-130">Minimum supported server</span></span> | <span data-ttu-id="df9b9-131">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="df9b9-131">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="df9b9-132">標頭</span><span class="sxs-lookup"><span data-stu-id="df9b9-132">Header</span></span> | <span data-ttu-id="df9b9-133">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="df9b9-133">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="df9b9-134">程式庫</span><span class="sxs-lookup"><span data-stu-id="df9b9-134">Library</span></span> | <span data-ttu-id="df9b9-135">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="df9b9-135">Kernel32.lib</span></span> |
| <span data-ttu-id="df9b9-136">DLL</span><span class="sxs-lookup"><span data-stu-id="df9b9-136">DLL</span></span> | <span data-ttu-id="df9b9-137">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="df9b9-137">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="df9b9-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df9b9-138">See also</span></span>

[<span data-ttu-id="df9b9-139">主控台函式</span><span class="sxs-lookup"><span data-stu-id="df9b9-139">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="df9b9-140">**主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="df9b9-140">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="df9b9-141">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="df9b9-141">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="df9b9-142">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="df9b9-142">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="df9b9-143">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="df9b9-143">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="df9b9-144">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="df9b9-144">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="df9b9-145">視窗和螢幕緩衝區大小</span><span class="sxs-lookup"><span data-stu-id="df9b9-145">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)
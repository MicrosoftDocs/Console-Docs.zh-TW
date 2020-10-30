---
title: SetConsoleWindowInfo 函式
description: 設定主控台螢幕緩衝區視窗的目前大小和位置。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleWindowInfo
- wincon/SetConsoleWindowInfo
- SetConsoleWindowInfo
MS-HAID:
- '\_win32\_setconsolewindowinfo'
- base.setconsolewindowinfo
- consoles.setconsolewindowinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad16a8fe-ca91-41d6-93b1-8cce6d54b1da
topic_type:
- apiref
api_name:
- SetConsoleWindowInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: dc1190aee7cb1a29c60579f5e00daf1f7280d292
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039306"
---
# <a name="setconsolewindowinfo-function"></a><span data-ttu-id="1552b-104">SetConsoleWindowInfo 函式</span><span class="sxs-lookup"><span data-stu-id="1552b-104">SetConsoleWindowInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="1552b-105">設定主控台螢幕緩衝區視窗的目前大小和位置。</span><span class="sxs-lookup"><span data-stu-id="1552b-105">Sets the current size and position of a console screen buffer's window.</span></span>

## <a name="syntax"></a><span data-ttu-id="1552b-106">語法</span><span class="sxs-lookup"><span data-stu-id="1552b-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleWindowInfo(
  _In_       HANDLE     hConsoleOutput,
  _In_       BOOL       bAbsolute,
  _In_ const SMALL_RECT *lpConsoleWindow
);
```

## <a name="parameters"></a><span data-ttu-id="1552b-107">參數</span><span class="sxs-lookup"><span data-stu-id="1552b-107">Parameters</span></span>

<span data-ttu-id="1552b-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="1552b-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="1552b-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="1552b-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="1552b-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="1552b-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="1552b-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="1552b-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="1552b-112">*bAbsolute* \[在\]</span><span class="sxs-lookup"><span data-stu-id="1552b-112">*bAbsolute* \[in\]</span></span>  
<span data-ttu-id="1552b-113">如果此參數為 **TRUE** ，座標會指定視窗的新左上角和右下角。</span><span class="sxs-lookup"><span data-stu-id="1552b-113">If this parameter is **TRUE** , the coordinates specify the new upper-left and lower-right corners of the window.</span></span> <span data-ttu-id="1552b-114">如果為 **FALSE** ，則座標相對於目前的視窗邊角座標。</span><span class="sxs-lookup"><span data-stu-id="1552b-114">If it is **FALSE** , the coordinates are relative to the current window-corner coordinates.</span></span>

<span data-ttu-id="1552b-115">*lpConsoleWindow* \[在\]</span><span class="sxs-lookup"><span data-stu-id="1552b-115">*lpConsoleWindow* \[in\]</span></span>  
<span data-ttu-id="1552b-116">[**小 \_ 矩形**](small-rect-str.md)結構的指標，指定視窗的新左上角和右下角。</span><span class="sxs-lookup"><span data-stu-id="1552b-116">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure that specifies the new upper-left and lower-right corners of the window.</span></span>

## <a name="return-value"></a><span data-ttu-id="1552b-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="1552b-117">Return value</span></span>

<span data-ttu-id="1552b-118">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="1552b-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1552b-119">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="1552b-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1552b-120">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="1552b-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="1552b-121">備註</span><span class="sxs-lookup"><span data-stu-id="1552b-121">Remarks</span></span>

<span data-ttu-id="1552b-122">如果指定的視窗矩形延伸超過主控台螢幕緩衝區的界限，則函式會失敗。</span><span class="sxs-lookup"><span data-stu-id="1552b-122">The function fails if the specified window rectangle extends beyond the boundaries of the console screen buffer.</span></span> <span data-ttu-id="1552b-123">這表示，如果 *bAbsolute* 為 FALSE，則 *LpConsoleWindow* 矩形的 **top** 和 **left** 成員 (或計算的上和左座標，) 不能小於零。</span><span class="sxs-lookup"><span data-stu-id="1552b-123">This means that the **Top** and **Left** members of the *lpConsoleWindow* rectangle (or the calculated top and left coordinates, if *bAbsolute* is FALSE) cannot be less than zero.</span></span> <span data-ttu-id="1552b-124">同樣地， **底部** 和 **右邊** 的成員 (或計算的右下座標) 不能大於 (螢幕緩衝區高度– 1) 和 (螢幕緩衝區寬度-1) 。</span><span class="sxs-lookup"><span data-stu-id="1552b-124">Similarly, the **Bottom** and **Right** members (or the calculated bottom and right coordinates) cannot be greater than (screen buffer height – 1) and (screen buffer width – 1), respectively.</span></span> <span data-ttu-id="1552b-125">如果 **右邊** 的成員 (或計算的右座標) 小於或等於 **左邊** 的成員 (或計算的左座標) 或 **底部** 成員 (或計算下座標) 小於或等於 **最上層** 成員 (或計算出的最上層座標) ，則函式也會失敗。</span><span class="sxs-lookup"><span data-stu-id="1552b-125">The function also fails if the **Right** member (or calculated right coordinate) is less than or equal to the **Left** member (or calculated left coordinate) or if the **Bottom** member (or calculated bottom coordinate) is less than or equal to the **Top** member (or calculated top coordinate).</span></span>

<span data-ttu-id="1552b-126">針對具有多個螢幕緩衝區的主控台，變更一個螢幕緩衝區的視窗位置並不會影響其他螢幕緩衝區的視窗位置。</span><span class="sxs-lookup"><span data-stu-id="1552b-126">For consoles with more than one screen buffer, changing the window location for one screen buffer does not affect the window locations of the other screen buffers.</span></span>

<span data-ttu-id="1552b-127">若要判斷螢幕緩衝區視窗目前的大小和位置，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="1552b-127">To determine the current size and position of a screen buffer's window, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span> <span data-ttu-id="1552b-128">這個函式也會根據目前的螢幕緩衝區大小、目前的字型大小和螢幕大小，傳回視窗的大小上限。</span><span class="sxs-lookup"><span data-stu-id="1552b-128">This function also returns the maximum size of the window, given the current screen buffer size, the current font size, and the screen size.</span></span> <span data-ttu-id="1552b-129">[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)函式會傳回目前的字型和螢幕大小的最大視窗大小，但不會考慮主控台畫面緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="1552b-129">The [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) function returns the maximum window size given the current font and screen sizes, but it does not consider the size of the console screen buffer.</span></span>

<span data-ttu-id="1552b-130">**SetConsoleWindowInfo** 可以用來滾動視窗矩形的位置，而不需要變更其大小。</span><span class="sxs-lookup"><span data-stu-id="1552b-130">**SetConsoleWindowInfo** can be used to scroll the contents of the console screen buffer by shifting the position of the window rectangle without changing its size.</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="examples"></a><span data-ttu-id="1552b-131">範例</span><span class="sxs-lookup"><span data-stu-id="1552b-131">Examples</span></span>

<span data-ttu-id="1552b-132">如需範例，請參閱 [滾動螢幕緩衝區視窗](scrolling-a-screen-buffer-s-window.md)。</span><span class="sxs-lookup"><span data-stu-id="1552b-132">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="1552b-133">規格需求</span><span class="sxs-lookup"><span data-stu-id="1552b-133">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1552b-134">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="1552b-134">Minimum supported client</span></span> | <span data-ttu-id="1552b-135">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="1552b-135">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1552b-136">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="1552b-136">Minimum supported server</span></span> | <span data-ttu-id="1552b-137">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="1552b-137">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1552b-138">標頭</span><span class="sxs-lookup"><span data-stu-id="1552b-138">Header</span></span> | <span data-ttu-id="1552b-139">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="1552b-139">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="1552b-140">程式庫</span><span class="sxs-lookup"><span data-stu-id="1552b-140">Library</span></span> | <span data-ttu-id="1552b-141">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="1552b-141">Kernel32.lib</span></span> |
| <span data-ttu-id="1552b-142">DLL</span><span class="sxs-lookup"><span data-stu-id="1552b-142">DLL</span></span> | <span data-ttu-id="1552b-143">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1552b-143">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="1552b-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="1552b-144">See also</span></span>

[<span data-ttu-id="1552b-145">主控台功能</span><span class="sxs-lookup"><span data-stu-id="1552b-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1552b-146">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="1552b-146">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="1552b-147">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="1552b-147">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="1552b-148">**ScrollConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="1552b-148">**ScrollConsoleScreenBuffer**</span></span>](scrollconsolescreenbuffer.md)

[<span data-ttu-id="1552b-149">滾動螢幕緩衝區</span><span class="sxs-lookup"><span data-stu-id="1552b-149">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

[<span data-ttu-id="1552b-150">**小型 \_ 矩形**</span><span class="sxs-lookup"><span data-stu-id="1552b-150">**SMALL\_RECT**</span></span>](small-rect-str.md)

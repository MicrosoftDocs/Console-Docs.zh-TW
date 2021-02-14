---
title: ScrollConsoleScreenBuffer 函式
description: 請參閱 ScrollConsoleScreenBuffer 函式的參考資訊，此函式會在螢幕緩衝區中移動資料區塊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/ScrollConsoleScreenBuffer
- wincon/ScrollConsoleScreenBuffer
- ScrollConsoleScreenBuffer
- consoleapi2/ScrollConsoleScreenBufferA
- wincon/ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferA
- consoleapi2/ScrollConsoleScreenBufferW
- wincon/ScrollConsoleScreenBufferW
- ScrollConsoleScreenBufferW
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d78bf4c9-2314-466c-b617-619259c824b5
topic_type:
- apiref
api_name:
- ScrollConsoleScreenBuffer
- ScrollConsoleScreenBufferA
- ScrollConsoleScreenBufferW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 1bf009a91063c12ad14604349d68ca0de1d8eaa1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358668"
---
# <a name="scrollconsolescreenbuffer-function"></a><span data-ttu-id="c3fbe-104">ScrollConsoleScreenBuffer 函式</span><span class="sxs-lookup"><span data-stu-id="c3fbe-104">ScrollConsoleScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="c3fbe-105">移動螢幕緩衝區中的資料區塊。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-105">Moves a block of data in a screen buffer.</span></span> <span data-ttu-id="c3fbe-106">您可以藉由指定裁剪矩形來限制移動的效果，如此一來，裁剪矩形外的主控台螢幕緩衝區內容就不會變更。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-106">The effects of the move can be limited by specifying a clipping rectangle, so the contents of the console screen buffer outside the clipping rectangle are unchanged.</span></span>

## <a name="syntax"></a><span data-ttu-id="c3fbe-107">語法</span><span class="sxs-lookup"><span data-stu-id="c3fbe-107">Syntax</span></span>

```C
BOOL WINAPI ScrollConsoleScreenBuffer(
  _In_           HANDLE     hConsoleOutput,
  _In_     const SMALL_RECT *lpScrollRectangle,
  _In_opt_ const SMALL_RECT *lpClipRectangle,
  _In_           COORD      dwDestinationOrigin,
  _In_     const CHAR_INFO  *lpFill
);
```

## <a name="parameters"></a><span data-ttu-id="c3fbe-108">參數</span><span class="sxs-lookup"><span data-stu-id="c3fbe-108">Parameters</span></span>

<span data-ttu-id="c3fbe-109">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="c3fbe-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="c3fbe-110">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="c3fbe-111">控制代碼必須具有 **GENERIC\_READ** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="c3fbe-112">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="c3fbe-113">*lpScrollRectangle* \[在\]</span><span class="sxs-lookup"><span data-stu-id="c3fbe-113">*lpScrollRectangle* \[in\]</span></span>  
<span data-ttu-id="c3fbe-114">[**小型 \_ 矩形**](small-rect-str.md)結構的指標，其成員指定要移動之主控台螢幕緩衝區矩形的左上角和右下角座標。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-114">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure whose members specify the upper-left and lower-right coordinates of the console screen buffer rectangle to be moved.</span></span>

<span data-ttu-id="c3fbe-115">*lpClipRectangle* \[在中，選擇性\]</span><span class="sxs-lookup"><span data-stu-id="c3fbe-115">*lpClipRectangle* \[in, optional\]</span></span>  
<span data-ttu-id="c3fbe-116">[**小型 \_ 矩形**](small-rect-str.md)結構的指標，其成員會指定受捲軸影響的主控台螢幕緩衝區矩形左上角和右下角的座標。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-116">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure whose members specify the upper-left and lower-right coordinates of the console screen buffer rectangle that is affected by the scrolling.</span></span> <span data-ttu-id="c3fbe-117">此指標可以是 **Null**。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-117">This pointer can be **NULL**.</span></span>

<span data-ttu-id="c3fbe-118">*dwDestinationOrigin* \[在\]</span><span class="sxs-lookup"><span data-stu-id="c3fbe-118">*dwDestinationOrigin* \[in\]</span></span>  
<span data-ttu-id="c3fbe-119">[**COORD**](coord-str.md)結構，指定 *lpScrollRectangle* 內容新位置的左上角（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-119">A [**COORD**](coord-str.md) structure that specifies the upper-left corner of the new location of the *lpScrollRectangle* contents, in characters.</span></span>

<span data-ttu-id="c3fbe-120">*lpFill* \[在\]</span><span class="sxs-lookup"><span data-stu-id="c3fbe-120">*lpFill* \[in\]</span></span>  
<span data-ttu-id="c3fbe-121">字元 [**\_ 資訊**](char-info-str.md) 結構的指標，指定字元和色彩屬性，以用於填滿 *lpScrollRectangle* 和 *lpClipRectangle* 交集內的資料格，而這些資料格會在移動時保留空白。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-121">A pointer to a [**CHAR\_INFO**](char-info-str.md) structure that specifies the character and color attributes to be used in filling the cells within the intersection of *lpScrollRectangle* and *lpClipRectangle* that were left empty as a result of the move.</span></span>

## <a name="return-value"></a><span data-ttu-id="c3fbe-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="c3fbe-122">Return value</span></span>

<span data-ttu-id="c3fbe-123">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="c3fbe-124">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="c3fbe-125">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-125">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="c3fbe-126">備註</span><span class="sxs-lookup"><span data-stu-id="c3fbe-126">Remarks</span></span>

<span data-ttu-id="c3fbe-127">**ScrollConsoleScreenBuffer** 會將螢幕緩衝區的矩形區域內容（由 *lpScrollRectangle* 參數指定）複製到主控台螢幕緩衝區的另一個區域。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-127">**ScrollConsoleScreenBuffer** copies the contents of a rectangular region of a screen buffer, specified by the *lpScrollRectangle* parameter, to another area of the console screen buffer.</span></span> <span data-ttu-id="c3fbe-128">目標矩形具有與 *lpScrollRectangle* 矩形相同的維度，其左上角位於 *dwDestinationOrigin* 參數所指定的座標上。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-128">The target rectangle has the same dimensions as the *lpScrollRectangle* rectangle with its upper-left corner at the coordinates specified by the *dwDestinationOrigin* parameter.</span></span> <span data-ttu-id="c3fbe-129">與目標矩形不重迭的 *lpScrollRectangle* 部分，會填入 *lpFill* 參數所指定的字元和色彩屬性。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-129">Those parts of *lpScrollRectangle* that do not overlap with the target rectangle are filled in with the character and color attributes specified by the *lpFill* parameter.</span></span>

<span data-ttu-id="c3fbe-130">裁剪矩形適用于在 *lpScrollRectangle* 矩形和目標矩形中所做的變更。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-130">The clipping rectangle applies to changes made in both the *lpScrollRectangle* rectangle and the target rectangle.</span></span> <span data-ttu-id="c3fbe-131">例如，如果裁剪矩形未包含已由 *lpFill* 內容填滿的區域，則該區域的原始內容會保持不變。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-131">For example, if the clipping rectangle does not include a region that would have been filled by the contents of *lpFill*, the original contents of the region are left unchanged.</span></span>

<span data-ttu-id="c3fbe-132">如果捲軸或目的地區域延伸超過主控台螢幕緩衝區的維度，則會將其裁剪。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-132">If the scroll or target regions extend beyond the dimensions of the console screen buffer, they are clipped.</span></span> <span data-ttu-id="c3fbe-133">例如，如果 *lpScrollRectangle* 是 (0、0) 和 (19、19) 和 *dwDestinationOrigin* 為 (10，15) 的區域，則目標矩形是 (10、15) 和 (29、34) 所包含的區域。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-133">For example, if *lpScrollRectangle* is the region contained by (0,0) and (19,19) and *dwDestinationOrigin* is (10,15), the target rectangle is the region contained by (10,15) and (29,34).</span></span> <span data-ttu-id="c3fbe-134">但是，如果主控台畫面緩衝區的寬度為50個字元，且高達30個字元，則會將目標矩形裁剪成 (10、15) 和 (29，29) 。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-134">However, if the console screen buffer is 50 characters wide and 30 characters high, the target rectangle is clipped to (10,15) and (29,29).</span></span> <span data-ttu-id="c3fbe-135">如果參數指定 [**小型的 \_ RECT**](small-rect-str.md)結構，則根據 *lpClipRectangle*，也會裁剪主控台螢幕緩衝區的變更。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-135">Changes to the console screen buffer are also clipped according to *lpClipRectangle*, if the parameter specifies a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="c3fbe-136">如果裁剪矩形指定為 (0、0) 和 (49、19) ，則只會進行在主控台螢幕緩衝區的該區域中發生的變更。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-136">If the clipping rectangle is specified as (0,0) and (49,19), only the changes that occur in that region of the console screen buffer are made.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="c3fbe-137">不建議使用此 API，也不會有對等的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-137">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="c3fbe-138">使用可近似于 **[滾動邊界](console-virtual-terminal-sequences.md#scrolling-margins)** 來修正畫面區域、將 **[游標定位](console-virtual-terminal-sequences.md#cursor-positioning)** 設定為區域外的使用中位置，以及使用分行符號來強制移動文字。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-138">Use can be approximated with **[scroll margins](console-virtual-terminal-sequences.md#scrolling-margins)** to fix an area of the screen, **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** to set the active position outside the region, and newlines to force text to move.</span></span> <span data-ttu-id="c3fbe-139">您可以藉由移動游標、 **[設定圖形屬性](console-virtual-terminal-sequences.md#text-formatting)** 和寫入一般文字來填滿剩餘的空間。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-139">The remaining space can be filled by moving the cursor, **[setting graphical attributes](console-virtual-terminal-sequences.md#text-formatting)**, and writing normal text.</span></span>

## <a name="examples"></a><span data-ttu-id="c3fbe-140">範例</span><span class="sxs-lookup"><span data-stu-id="c3fbe-140">Examples</span></span>

<span data-ttu-id="c3fbe-141">如需範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="c3fbe-141">For an example, see [Scrolling a Screen Buffer's Contents](scrolling-a-screen-buffer-s-contents.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="c3fbe-142">規格需求</span><span class="sxs-lookup"><span data-stu-id="c3fbe-142">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="c3fbe-143">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="c3fbe-143">Minimum supported client</span></span> | <span data-ttu-id="c3fbe-144">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="c3fbe-144">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="c3fbe-145">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="c3fbe-145">Minimum supported server</span></span> | <span data-ttu-id="c3fbe-146">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="c3fbe-146">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="c3fbe-147">標頭</span><span class="sxs-lookup"><span data-stu-id="c3fbe-147">Header</span></span> | <span data-ttu-id="c3fbe-148">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="c3fbe-148">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="c3fbe-149">程式庫</span><span class="sxs-lookup"><span data-stu-id="c3fbe-149">Library</span></span> | <span data-ttu-id="c3fbe-150">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="c3fbe-150">Kernel32.lib</span></span> |
| <span data-ttu-id="c3fbe-151">DLL</span><span class="sxs-lookup"><span data-stu-id="c3fbe-151">DLL</span></span> | <span data-ttu-id="c3fbe-152">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="c3fbe-152">Kernel32.dll</span></span> |
| <span data-ttu-id="c3fbe-153">Unicode 與 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="c3fbe-153">Unicode and ANSI names</span></span> | <span data-ttu-id="c3fbe-154">**ScrollConsoleScreenBufferW** (Unicode) 和 **ScrollConsoleScreenBufferA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="c3fbe-154">**ScrollConsoleScreenBufferW** (Unicode) and **ScrollConsoleScreenBufferA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="c3fbe-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3fbe-155">See also</span></span>

[<span data-ttu-id="c3fbe-156">**字元 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="c3fbe-156">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="c3fbe-157">主控台函式</span><span class="sxs-lookup"><span data-stu-id="c3fbe-157">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="c3fbe-158">**COORD**</span><span class="sxs-lookup"><span data-stu-id="c3fbe-158">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="c3fbe-159">滾動螢幕緩衝區</span><span class="sxs-lookup"><span data-stu-id="c3fbe-159">Scrolling the Screen Buffer</span></span>](scrolling-the-screen-buffer.md)

[<span data-ttu-id="c3fbe-160">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="c3fbe-160">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="c3fbe-161">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="c3fbe-161">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="c3fbe-162">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="c3fbe-162">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="c3fbe-163">**小型 \_ 矩形**</span><span class="sxs-lookup"><span data-stu-id="c3fbe-163">**SMALL\_RECT**</span></span>](small-rect-str.md)
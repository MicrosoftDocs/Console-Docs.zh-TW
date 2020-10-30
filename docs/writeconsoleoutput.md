---
title: WriteConsoleOutput 函式
description: 將字元和色彩屬性資料寫入主控台螢幕緩衝區中指定之字元資料格的矩形區塊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/WriteConsoleOutput
- wincon/WriteConsoleOutput
- WriteConsoleOutput
- consoleapi2/WriteConsoleOutputA
- wincon/WriteConsoleOutputA
- WriteConsoleOutputA
- consoleapi2/WriteConsoleOutputW
- wincon/WriteConsoleOutputW
- WriteConsoleOutputW
MS-HAID:
- '\_win32\_writeconsoleoutput'
- base.writeconsoleoutput
- consoles.writeconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a98b8118-97ce-4dd4-a337-122d4a76f232
topic_type:
- apiref
api_name:
- WriteConsoleOutput
- WriteConsoleOutputA
- WriteConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: b67f741aafcb067e85d339d550646261a46c273a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037256"
---
# <a name="writeconsoleoutput-function"></a><span data-ttu-id="fbda9-104">WriteConsoleOutput 函式</span><span class="sxs-lookup"><span data-stu-id="fbda9-104">WriteConsoleOutput function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="fbda9-105">將字元和色彩屬性資料寫入主控台螢幕緩衝區中指定之字元資料格的矩形區塊。</span><span class="sxs-lookup"><span data-stu-id="fbda9-105">Writes character and color attribute data to a specified rectangular block of character cells in a console screen buffer.</span></span> <span data-ttu-id="fbda9-106">要寫入的資料是取自來源緩衝區中指定位置的相對大小矩形區塊。</span><span class="sxs-lookup"><span data-stu-id="fbda9-106">The data to be written is taken from a correspondingly sized rectangular block at a specified location in the source buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="fbda9-107">語法</span><span class="sxs-lookup"><span data-stu-id="fbda9-107">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleOutput(
  _In_          HANDLE      hConsoleOutput,
  _In_    const CHAR_INFO   *lpBuffer,
  _In_          COORD       dwBufferSize,
  _In_          COORD       dwBufferCoord,
  _Inout_       PSMALL_RECT lpWriteRegion
);
```

## <a name="parameters"></a><span data-ttu-id="fbda9-108">參數</span><span class="sxs-lookup"><span data-stu-id="fbda9-108">Parameters</span></span>

<span data-ttu-id="fbda9-109">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="fbda9-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="fbda9-110">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="fbda9-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="fbda9-111">控制碼必須有 **一般 \_ 寫入** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="fbda9-111">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="fbda9-112">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="fbda9-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="fbda9-113">*lpBuffer* \[在\]</span><span class="sxs-lookup"><span data-stu-id="fbda9-113">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="fbda9-114">要寫入主控台螢幕緩衝區的資料。</span><span class="sxs-lookup"><span data-stu-id="fbda9-114">The data to be written to the console screen buffer.</span></span> <span data-ttu-id="fbda9-115">此指標會被視為 [**CHAR \_ 資訊**](char-info-str.md) 結構之二維陣列的來源，其大小是由 *dwBufferSize* 參數所指定。</span><span class="sxs-lookup"><span data-stu-id="fbda9-115">This pointer is treated as the origin of a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures whose size is specified by the *dwBufferSize* parameter.</span></span>

<span data-ttu-id="fbda9-116">*dwBufferSize* \[在\]</span><span class="sxs-lookup"><span data-stu-id="fbda9-116">*dwBufferSize* \[in\]</span></span>  
<span data-ttu-id="fbda9-117">*LpBuffer* 參數所指向的緩衝區大小（以字元資料格為限）。</span><span class="sxs-lookup"><span data-stu-id="fbda9-117">The size of the buffer pointed to by the *lpBuffer* parameter, in character cells.</span></span> <span data-ttu-id="fbda9-118">[**COORD**](coord-str.md)結構的 **X** 成員是資料行的數目; **Y** 成員是資料列的數目。</span><span class="sxs-lookup"><span data-stu-id="fbda9-118">The **X** member of the [**COORD**](coord-str.md) structure is the number of columns; the **Y** member is the number of rows.</span></span>

<span data-ttu-id="fbda9-119">*dwBufferCoord* \[在\]</span><span class="sxs-lookup"><span data-stu-id="fbda9-119">*dwBufferCoord* \[in\]</span></span>  
<span data-ttu-id="fbda9-120">*LpBuffer* 參數所指向之緩衝區中左上角資料格的座標。</span><span class="sxs-lookup"><span data-stu-id="fbda9-120">The coordinates of the upper-left cell in the buffer pointed to by the *lpBuffer* parameter.</span></span> <span data-ttu-id="fbda9-121">[**COORD**](coord-str.md)結構的 **X** 成員是資料行，而 **Y** 成員是資料列。</span><span class="sxs-lookup"><span data-stu-id="fbda9-121">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="fbda9-122">*lpWriteRegion* \[in、out\]</span><span class="sxs-lookup"><span data-stu-id="fbda9-122">*lpWriteRegion* \[in, out\]</span></span>  
<span data-ttu-id="fbda9-123">[**小 \_ RECT**](small-rect-str.md)結構的指標。</span><span class="sxs-lookup"><span data-stu-id="fbda9-123">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="fbda9-124">在輸入時，結構成員會指定要寫入的主控台螢幕緩衝區矩形左上角和右下角的座標。</span><span class="sxs-lookup"><span data-stu-id="fbda9-124">On input, the structure members specify the upper-left and lower-right coordinates of the console screen buffer rectangle to write to.</span></span> <span data-ttu-id="fbda9-125">在輸出時，結構成員會指定所使用的實際矩形。</span><span class="sxs-lookup"><span data-stu-id="fbda9-125">On output, the structure members specify the actual rectangle that was used.</span></span>

## <a name="return-value"></a><span data-ttu-id="fbda9-126">傳回值</span><span class="sxs-lookup"><span data-stu-id="fbda9-126">Return value</span></span>

<span data-ttu-id="fbda9-127">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="fbda9-127">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="fbda9-128">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="fbda9-128">If the function fails, the return value is zero.</span></span> <span data-ttu-id="fbda9-129">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="fbda9-129">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="fbda9-130">備註</span><span class="sxs-lookup"><span data-stu-id="fbda9-130">Remarks</span></span>

<span data-ttu-id="fbda9-131">**WriteConsoleOutput** 會將來源緩衝區和目的畫面緩衝區視為二維陣列， (資料格的資料行和資料列) 。</span><span class="sxs-lookup"><span data-stu-id="fbda9-131">**WriteConsoleOutput** treats the source buffer and the destination screen buffer as two-dimensional arrays (columns and rows of character cells).</span></span> <span data-ttu-id="fbda9-132">*LpWriteRegion* 參數所指向的矩形，可指定要在主控台螢幕緩衝區中寫入之區塊的大小與位置。</span><span class="sxs-lookup"><span data-stu-id="fbda9-132">The rectangle pointed to by the *lpWriteRegion* parameter specifies the size and location of the block to be written to in the console screen buffer.</span></span> <span data-ttu-id="fbda9-133">相同大小的矩形位於 *lpBuffer* 陣列中 *dwBufferCoord* 參數座標的左上角儲存格。</span><span class="sxs-lookup"><span data-stu-id="fbda9-133">A rectangle of the same size is located with its upper-left cell at the coordinates of the *dwBufferCoord* parameter in the *lpBuffer* array.</span></span> <span data-ttu-id="fbda9-134">從這個矩形和來源緩衝區矩形交集的資料格中的資料， (其維度是由 *dwBufferSize* 參數指定，) 會寫入至目的地矩形。</span><span class="sxs-lookup"><span data-stu-id="fbda9-134">Data from the cells that are in the intersection of this rectangle and the source buffer rectangle (whose dimensions are specified by the *dwBufferSize* parameter) is written to the destination rectangle.</span></span>

<span data-ttu-id="fbda9-135">目的地矩形中的資料格，其對應的來源位置超出來源緩衝區矩形的界限，因此不會受到寫入作業的影響。</span><span class="sxs-lookup"><span data-stu-id="fbda9-135">Cells in the destination rectangle whose corresponding source location are outside the boundaries of the source buffer rectangle are left unaffected by the write operation.</span></span> <span data-ttu-id="fbda9-136">換句話說，這些是沒有資料可供寫入的儲存格。</span><span class="sxs-lookup"><span data-stu-id="fbda9-136">In other words, these are the cells for which no data is available to be written.</span></span>

<span data-ttu-id="fbda9-137">在 **WriteConsoleOutput** 傳回之前，它會將 *lpWriteRegion* 的成員設定為受寫入操作影響的實際螢幕緩衝區矩形。</span><span class="sxs-lookup"><span data-stu-id="fbda9-137">Before **WriteConsoleOutput** returns, it sets the members of *lpWriteRegion* to the actual screen buffer rectangle affected by the write operation.</span></span> <span data-ttu-id="fbda9-138">這個矩形會反映目的地矩形中的儲存格，而來源緩衝區中有對應的資料格，因為 **WriteConsoleOutput** 會將目的地矩形的維度裁剪到主控台螢幕緩衝區的界限。</span><span class="sxs-lookup"><span data-stu-id="fbda9-138">This rectangle reflects the cells in the destination rectangle for which there existed a corresponding cell in the source buffer, because **WriteConsoleOutput** clips the dimensions of the destination rectangle to the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="fbda9-139">如果 *lpWriteRegion* 所指定的矩形完全落在主控台螢幕緩衝區的界限之外，或對應的矩形完全位於來源緩衝區的界限之外，則不會寫入任何資料。</span><span class="sxs-lookup"><span data-stu-id="fbda9-139">If the rectangle specified by *lpWriteRegion* lies completely outside the boundaries of the console screen buffer, or if the corresponding rectangle is positioned completely outside the boundaries of the source buffer, no data is written.</span></span> <span data-ttu-id="fbda9-140">在此情況下，函式會傳回 *lpWriteRegion* 參數集所指向之結構的成員，讓 **右邊** 的成員小於 **左邊** ，或 **底部** 的成員小於 **頂端** 。</span><span class="sxs-lookup"><span data-stu-id="fbda9-140">In this case, the function returns with the members of the structure pointed to by the *lpWriteRegion* parameter set such that the **Right** member is less than the **Left** , or the **Bottom** member is less than the **Top** .</span></span> <span data-ttu-id="fbda9-141">若要判斷主控台螢幕緩衝區的大小，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="fbda9-141">To determine the size of the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="fbda9-142">**WriteConsoleOutput** 不會影響資料指標的位置。</span><span class="sxs-lookup"><span data-stu-id="fbda9-142">**WriteConsoleOutput** has no effect on the cursor position.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="fbda9-143">此 API 的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機等同于 **[文字格式](console-virtual-terminal-sequences.md#text-formatting)** 和資料 **[指標定位](console-virtual-terminal-sequences.md#cursor-positioning)** 順序。</span><span class="sxs-lookup"><span data-stu-id="fbda9-143">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sequences.</span></span> <span data-ttu-id="fbda9-144">將游標移至要插入的位置，套用所需的格式，並寫出文字。</span><span class="sxs-lookup"><span data-stu-id="fbda9-144">Move the cursor to the location to insert, apply the formatting desired, and write out the text.</span></span> <span data-ttu-id="fbda9-145">建議您針對所有新的和進行中的開發，使用 _虛擬終端機序列_ 。</span><span class="sxs-lookup"><span data-stu-id="fbda9-145">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="fbda9-146">範例</span><span class="sxs-lookup"><span data-stu-id="fbda9-146">Examples</span></span>

<span data-ttu-id="fbda9-147">如需範例，請參閱 [讀取和寫入字元和屬性的區塊](reading-and-writing-blocks-of-characters-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="fbda9-147">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="fbda9-148">規格需求</span><span class="sxs-lookup"><span data-stu-id="fbda9-148">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="fbda9-149">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="fbda9-149">Minimum supported client</span></span> | <span data-ttu-id="fbda9-150">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="fbda9-150">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="fbda9-151">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="fbda9-151">Minimum supported server</span></span> | <span data-ttu-id="fbda9-152">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="fbda9-152">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="fbda9-153">標頭</span><span class="sxs-lookup"><span data-stu-id="fbda9-153">Header</span></span> | <span data-ttu-id="fbda9-154">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="fbda9-154">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="fbda9-155">程式庫</span><span class="sxs-lookup"><span data-stu-id="fbda9-155">Library</span></span> | <span data-ttu-id="fbda9-156">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="fbda9-156">Kernel32.lib</span></span> |
| <span data-ttu-id="fbda9-157">DLL</span><span class="sxs-lookup"><span data-stu-id="fbda9-157">DLL</span></span> | <span data-ttu-id="fbda9-158">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="fbda9-158">Kernel32.dll</span></span> |
| <span data-ttu-id="fbda9-159">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="fbda9-159">Unicode and ANSI names</span></span> | <span data-ttu-id="fbda9-160">**WriteConsoleOutputW** (Unicode) 和 **WriteConsoleOutputA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="fbda9-160">**WriteConsoleOutputW** (Unicode) and **WriteConsoleOutputA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="fbda9-161">請參閱</span><span class="sxs-lookup"><span data-stu-id="fbda9-161">See also</span></span>

[<span data-ttu-id="fbda9-162">主控台功能</span><span class="sxs-lookup"><span data-stu-id="fbda9-162">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="fbda9-163">**字元 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="fbda9-163">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="fbda9-164">**COORD**</span><span class="sxs-lookup"><span data-stu-id="fbda9-164">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="fbda9-165">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="fbda9-165">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="fbda9-166">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="fbda9-166">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="fbda9-167">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="fbda9-167">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="fbda9-168">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="fbda9-168">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="fbda9-169">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="fbda9-169">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="fbda9-170">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="fbda9-170">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="fbda9-171">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="fbda9-171">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="fbda9-172">**小型 \_ 矩形**</span><span class="sxs-lookup"><span data-stu-id="fbda9-172">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="fbda9-173">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="fbda9-173">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="fbda9-174">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="fbda9-174">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

---
title: ReadConsoleOutput 函式
description: 從主控台螢幕緩衝區中的矩形字元資料格區塊讀取字元和色彩屬性資料，並將資料寫入目的地緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/ReadConsoleOutput
- wincon/ReadConsoleOutput
- ReadConsoleOutput
- consoleapi2/ReadConsoleOutputA
- wincon/ReadConsoleOutputA
- ReadConsoleOutputA
- consoleapi2/ReadConsoleOutputW
- wincon/ReadConsoleOutputW
- ReadConsoleOutputW
MS-HAID:
- '\_win32\_readconsoleoutput'
- base.readconsoleoutput
- consoles.readconsoleoutput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: d1391684-6a8f-4b5e-9706-11970a957710
topic_type:
- apiref
api_name:
- ReadConsoleOutput
- ReadConsoleOutputA
- ReadConsoleOutputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 382ed9cd06586ab86097c6efd2f6b8ea92f03eaf
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059474"
---
# <a name="readconsoleoutput-function"></a><span data-ttu-id="ed164-104">ReadConsoleOutput 函式</span><span class="sxs-lookup"><span data-stu-id="ed164-104">ReadConsoleOutput function</span></span>


<span data-ttu-id="ed164-105">從主控台螢幕緩衝區中的矩形字元資料格區塊讀取字元和色彩屬性資料，而函式會將資料寫入目的緩衝區中指定位置的矩形區塊。</span><span class="sxs-lookup"><span data-stu-id="ed164-105">Reads character and color attribute data from a rectangular block of character cells in a console screen buffer, and the function writes the data to a rectangular block at a specified location in the destination buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="ed164-106">語法</span><span class="sxs-lookup"><span data-stu-id="ed164-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsoleOutput(
  _In_    HANDLE      hConsoleOutput,
  _Out_   PCHAR_INFO  lpBuffer,
  _In_    COORD       dwBufferSize,
  _In_    COORD       dwBufferCoord,
  _Inout_ PSMALL_RECT lpReadRegion
);
```

<a name="parameters"></a><span data-ttu-id="ed164-107">參數</span><span class="sxs-lookup"><span data-stu-id="ed164-107">Parameters</span></span>
----------

<span data-ttu-id="ed164-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="ed164-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="ed164-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="ed164-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="ed164-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="ed164-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="ed164-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="ed164-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="ed164-112">*lpBuffer* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="ed164-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="ed164-113">目的地緩衝區的指標，此緩衝區會接收從主控台螢幕緩衝區讀取的資料。</span><span class="sxs-lookup"><span data-stu-id="ed164-113">A pointer to a destination buffer that receives the data read from the console screen buffer.</span></span> <span data-ttu-id="ed164-114">此指標會被視為 [**CHAR \_ 資訊**](char-info-str.md) 結構之二維陣列的來源，其大小是由 *dwBufferSize* 參數所指定。</span><span class="sxs-lookup"><span data-stu-id="ed164-114">This pointer is treated as the origin of a two-dimensional array of [**CHAR\_INFO**](char-info-str.md) structures whose size is specified by the *dwBufferSize* parameter.</span></span>

<span data-ttu-id="ed164-115">*dwBufferSize* \[在\]</span><span class="sxs-lookup"><span data-stu-id="ed164-115">*dwBufferSize* \[in\]</span></span>  
<span data-ttu-id="ed164-116">*LpBuffer*參數的大小，以字元儲存格為限。</span><span class="sxs-lookup"><span data-stu-id="ed164-116">The size of the *lpBuffer* parameter, in character cells.</span></span> <span data-ttu-id="ed164-117">[**COORD**](coord-str.md)結構的**X**成員是資料行的數目;**Y**成員是資料列的數目。</span><span class="sxs-lookup"><span data-stu-id="ed164-117">The **X** member of the [**COORD**](coord-str.md) structure is the number of columns; the **Y** member is the number of rows.</span></span>

<span data-ttu-id="ed164-118">*dwBufferCoord* \[在\]</span><span class="sxs-lookup"><span data-stu-id="ed164-118">*dwBufferCoord* \[in\]</span></span>  
<span data-ttu-id="ed164-119">*LpBuffer*參數中的左上角儲存格座標，可接收從主控台螢幕緩衝區讀取的資料。</span><span class="sxs-lookup"><span data-stu-id="ed164-119">The coordinates of the upper-left cell in the *lpBuffer* parameter that receives the data read from the console screen buffer.</span></span> <span data-ttu-id="ed164-120">[**COORD**](coord-str.md)結構的**X**成員是資料行，而**Y**成員是資料列。</span><span class="sxs-lookup"><span data-stu-id="ed164-120">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="ed164-121">*lpReadRegion* \[in、out\]</span><span class="sxs-lookup"><span data-stu-id="ed164-121">*lpReadRegion* \[in, out\]</span></span>  
<span data-ttu-id="ed164-122">[**小 \_ RECT**](small-rect-str.md)結構的指標。</span><span class="sxs-lookup"><span data-stu-id="ed164-122">A pointer to a [**SMALL\_RECT**](small-rect-str.md) structure.</span></span> <span data-ttu-id="ed164-123">在輸入時，結構成員會指定要讀取函式的主控台螢幕緩衝區矩形左上角和右下角的座標。</span><span class="sxs-lookup"><span data-stu-id="ed164-123">On input, the structure members specify the upper-left and lower-right coordinates of the console screen buffer rectangle from which the function is to read.</span></span> <span data-ttu-id="ed164-124">在輸出時，結構成員會指定所使用的實際矩形。</span><span class="sxs-lookup"><span data-stu-id="ed164-124">On output, the structure members specify the actual rectangle that was used.</span></span>

<a name="return-value"></a><span data-ttu-id="ed164-125">傳回值</span><span class="sxs-lookup"><span data-stu-id="ed164-125">Return value</span></span>
------------

<span data-ttu-id="ed164-126">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="ed164-126">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ed164-127">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="ed164-127">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ed164-128">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="ed164-128">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="ed164-129">備註</span><span class="sxs-lookup"><span data-stu-id="ed164-129">Remarks</span></span>
-------

<span data-ttu-id="ed164-130">**ReadConsoleOutput** 會將主控台畫面緩衝區和目的地緩衝區視為二維陣列 () 的字元資料格的資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="ed164-130">**ReadConsoleOutput** treats the console screen buffer and the destination buffer as two-dimensional arrays (columns and rows of character cells).</span></span> <span data-ttu-id="ed164-131">*LpReadRegion*參數所指向的矩形，可指定要從主控台螢幕緩衝區讀取之區塊的大小與位置。</span><span class="sxs-lookup"><span data-stu-id="ed164-131">The rectangle pointed to by the *lpReadRegion* parameter specifies the size and location of the block to be read from the console screen buffer.</span></span> <span data-ttu-id="ed164-132">相同大小的目的地矩形位於*lpBuffer*陣列中*dwBufferCoord*參數座標的左上角儲存格。</span><span class="sxs-lookup"><span data-stu-id="ed164-132">A destination rectangle of the same size is located with its upper-left cell at the coordinates of the *dwBufferCoord* parameter in the *lpBuffer* array.</span></span> <span data-ttu-id="ed164-133">從主控台螢幕緩衝區來源矩形的儲存格讀取的資料會複製到目的地緩衝區中的對應資料格。</span><span class="sxs-lookup"><span data-stu-id="ed164-133">Data read from the cells in the console screen buffer source rectangle is copied to the corresponding cells in the destination buffer.</span></span> <span data-ttu-id="ed164-134">如果對應的資料格超出目的緩衝區矩形的界限， (其維度是由 *dwBufferSize* 參數) 指定，則不會複製資料。</span><span class="sxs-lookup"><span data-stu-id="ed164-134">If the corresponding cell is outside the boundaries of the destination buffer rectangle (whose dimensions are specified by the *dwBufferSize* parameter), the data is not copied.</span></span>

<span data-ttu-id="ed164-135">目的緩衝區中對應至不在主控台螢幕緩衝區界限內之座標的儲存格會保持不變。</span><span class="sxs-lookup"><span data-stu-id="ed164-135">Cells in the destination buffer corresponding to coordinates that are not within the boundaries of the console screen buffer are left unchanged.</span></span> <span data-ttu-id="ed164-136">換句話說，這些是沒有螢幕緩衝區資料可供讀取的儲存格。</span><span class="sxs-lookup"><span data-stu-id="ed164-136">In other words, these are the cells for which no screen buffer data is available to be read.</span></span>

<span data-ttu-id="ed164-137">在 **ReadConsoleOutput** 傳回之前，它會將 *lpReadRegion* 參數所指向之結構的成員設定為實際的螢幕緩衝區矩形，其儲存格已複製到目的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="ed164-137">Before **ReadConsoleOutput** returns, it sets the members of the structure pointed to by the *lpReadRegion* parameter to the actual screen buffer rectangle whose cells were copied into the destination buffer.</span></span> <span data-ttu-id="ed164-138">這個矩形會反映來源矩形中的儲存格，在目的緩衝區中已有對應的資料格，因為 **ReadConsoleOutput** 會裁剪來源矩形的維度，以符合主控台螢幕緩衝區的界限。</span><span class="sxs-lookup"><span data-stu-id="ed164-138">This rectangle reflects the cells in the source rectangle for which there existed a corresponding cell in the destination buffer, because **ReadConsoleOutput** clips the dimensions of the source rectangle to fit the boundaries of the console screen buffer.</span></span>

<span data-ttu-id="ed164-139">如果 *lpReadRegion* 所指定的矩形完全落在主控台螢幕緩衝區的界限之外，或對應的矩形完全位於目的緩衝區的界限之外，則不會複製任何資料。</span><span class="sxs-lookup"><span data-stu-id="ed164-139">If the rectangle specified by *lpReadRegion* lies completely outside the boundaries of the console screen buffer, or if the corresponding rectangle is positioned completely outside the boundaries of the destination buffer, no data is copied.</span></span> <span data-ttu-id="ed164-140">在此情況下，函式會傳回 *lpReadRegion* 參數集所指向之結構的成員，讓 **右邊** 的成員小於 **左邊**，或 **底部** 的成員小於 **頂端**。</span><span class="sxs-lookup"><span data-stu-id="ed164-140">In this case, the function returns with the members of the structure pointed to by the *lpReadRegion* parameter set such that the **Right** member is less than the **Left**, or the **Bottom** member is less than the **Top**.</span></span> <span data-ttu-id="ed164-141">若要判斷主控台螢幕緩衝區的大小，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="ed164-141">To determine the size of the console screen buffer, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="ed164-142">**ReadConsoleOutput**函式不會影響主控台畫面緩衝區的游標位置。</span><span class="sxs-lookup"><span data-stu-id="ed164-142">The **ReadConsoleOutput** function has no effect on the console screen buffer's cursor position.</span></span> <span data-ttu-id="ed164-143">此函數不會變更控制台螢幕緩衝區的內容。</span><span class="sxs-lookup"><span data-stu-id="ed164-143">The contents of the console screen buffer are not changed by the function.</span></span>

<span data-ttu-id="ed164-144">此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。</span><span class="sxs-lookup"><span data-stu-id="ed164-144">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="ed164-145">主控台的字碼頁一開始預設為系統的 OEM 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="ed164-145">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="ed164-146">若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 或 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函式，或使用 **chcp** 或 **mode con cp select =** 命令。</span><span class="sxs-lookup"><span data-stu-id="ed164-146">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="ed164-147">範例</span><span class="sxs-lookup"><span data-stu-id="ed164-147">Examples</span></span>
--------

<span data-ttu-id="ed164-148">如需範例，請參閱 [讀取和寫入字元和屬性的區塊](reading-and-writing-blocks-of-characters-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="ed164-148">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

<a name="requirements"></a><span data-ttu-id="ed164-149">規格需求</span><span class="sxs-lookup"><span data-stu-id="ed164-149">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="ed164-150">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="ed164-150">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="ed164-151">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="ed164-151">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ed164-152">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="ed164-152">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="ed164-153">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="ed164-153">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ed164-154">標頭</span><span class="sxs-lookup"><span data-stu-id="ed164-154">Header</span></span></p></td>
<td><span data-ttu-id="ed164-155">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="ed164-155">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ed164-156">程式庫</span><span class="sxs-lookup"><span data-stu-id="ed164-156">Library</span></span></p></td>
<td><span data-ttu-id="ed164-157">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="ed164-157">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ed164-158">DLL</span><span class="sxs-lookup"><span data-stu-id="ed164-158">DLL</span></span></p></td>
<td><span data-ttu-id="ed164-159">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ed164-159">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ed164-160">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="ed164-160">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="ed164-161"><strong>ReadConsoleOutputW</strong> (Unicode) 和 <strong>ReadConsoleOutputA</strong> (ANSI) </span><span class="sxs-lookup"><span data-stu-id="ed164-161"><strong>ReadConsoleOutputW</strong> (Unicode) and <strong>ReadConsoleOutputA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="ed164-162"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed164-162"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="ed164-163">主控台功能</span><span class="sxs-lookup"><span data-stu-id="ed164-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ed164-164">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="ed164-164">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="ed164-165">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="ed164-165">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="ed164-166">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="ed164-166">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="ed164-167">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="ed164-167">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="ed164-168">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="ed164-168">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="ed164-169">**小型 \_ 矩形**</span><span class="sxs-lookup"><span data-stu-id="ed164-169">**SMALL\_RECT**</span></span>](small-rect-str.md)

[<span data-ttu-id="ed164-170">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="ed164-170">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="ed164-171">**字元 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="ed164-171">**CHAR\_INFO**</span></span>](char-info-str.md)

[<span data-ttu-id="ed164-172">**COORD**</span><span class="sxs-lookup"><span data-stu-id="ed164-172">**COORD**</span></span>](coord-str.md)

 

 





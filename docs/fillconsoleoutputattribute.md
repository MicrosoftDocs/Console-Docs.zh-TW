---
title: FillConsoleOutputAttribute 函式
description: 針對指定的字元資料格數目，設定從螢幕緩衝區中的指定座標開始的字元屬性。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/FillConsoleOutputAttribute
- wincon/FillConsoleOutputAttribute
- FillConsoleOutputAttribute
MS-HAID:
- '\_win32\_fillconsoleoutputattribute'
- base.fillconsoleoutputattribute
- consoles.fillconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 09440263-71c4-4b7a-8fc6-a2b4fcd677ff
topic_type:
- apiref
api_name:
- FillConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 8b88bfcc264d1370479eef300cea2868142fbb8c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357908"
---
# <a name="fillconsoleoutputattribute-function"></a><span data-ttu-id="1b5b4-104">FillConsoleOutputAttribute 函式</span><span class="sxs-lookup"><span data-stu-id="1b5b4-104">FillConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="1b5b4-105">針對指定的字元資料格數目，設定從螢幕緩衝區中的指定座標開始的字元屬性。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-105">Sets the character attributes for a specified number of character cells, beginning at the specified coordinates in a screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="1b5b4-106">語法</span><span class="sxs-lookup"><span data-stu-id="1b5b4-106">Syntax</span></span>

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="1b5b4-107">參數</span><span class="sxs-lookup"><span data-stu-id="1b5b4-107">Parameters</span></span>

<span data-ttu-id="1b5b4-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="1b5b4-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="1b5b4-109">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="1b5b4-110">控點必須具有 **GENERIC\_WRITE** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="1b5b4-111">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="1b5b4-112">*wAttribute* \[在\]</span><span class="sxs-lookup"><span data-stu-id="1b5b4-112">*wAttribute* \[in\]</span></span>  
<span data-ttu-id="1b5b4-113">寫入主控台螢幕緩衝區時要使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-113">The attributes to use when writing to the console screen buffer.</span></span> <span data-ttu-id="1b5b4-114">如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#character-attributes)。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="1b5b4-115">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="1b5b4-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="1b5b4-116">要設定為指定之色彩屬性的字元儲存格數目。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-116">The number of character cells to be set to the specified color attributes.</span></span>

<span data-ttu-id="1b5b4-117">*dwWriteCoord* \[在\]</span><span class="sxs-lookup"><span data-stu-id="1b5b4-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="1b5b4-118">[**COORD**](coord-str.md)結構，指定要設定其屬性的第一個資料格的字元座標。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell whose attributes are to be set.</span></span>

<span data-ttu-id="1b5b4-119">*lpNumberOfAttrsWritten* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="1b5b4-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="1b5b4-120">變數的指標，此變數會接收實際設定其屬性的字元儲存格數目。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-120">A pointer to a variable that receives the number of character cells whose attributes were actually set.</span></span>

## <a name="return-value"></a><span data-ttu-id="1b5b4-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="1b5b4-121">Return value</span></span>

<span data-ttu-id="1b5b4-122">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1b5b4-123">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1b5b4-124">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-124">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="1b5b4-125">備註</span><span class="sxs-lookup"><span data-stu-id="1b5b4-125">Remarks</span></span>

<span data-ttu-id="1b5b4-126">如果要設定屬性的字元資料格數目延伸超過主控台螢幕緩衝區中指定之資料列的結尾，則會設定下一個資料列的資料格。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-126">If the number of character cells whose attributes are to be set extends beyond the end of the specified row in the console screen buffer, the cells of the next row are set.</span></span> <span data-ttu-id="1b5b4-127">如果要寫入的資料格數目延伸超過主控台螢幕緩衝區的結尾，則資料格會寫入至主控台畫面緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-127">If the number of cells to write to extends beyond the end of the console screen buffer, the cells are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="1b5b4-128">寫入至的位置的字元值不會變更。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-128">The character values at the positions written to are not changed.</span></span>

> [!TIP]
> <span data-ttu-id="1b5b4-129">不建議使用此 API，也不會有對等的特定 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-129">This API is not recommended and does not have a specific **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="1b5b4-130">不支援在可見視窗外填滿區域，而且會保留給終端機的歷程記錄空間。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-130">Filling the region outside the viewable window is not supported and is reserved for the terminal's history space.</span></span> <span data-ttu-id="1b5b4-131">使用新文字或色彩填滿可見區域的動作是透過 **[移動游標](console-virtual-terminal-sequences.md#cursor-positioning)**、 **[設定新屬性](console-virtual-terminal-sequences.md#text-formatting)**，然後撰寫該區域所需的文字，並在填滿填滿的長度時重複字元。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-131">Filling a visible region with new text or color is performed through **[moving the cursor](console-virtual-terminal-sequences.md#cursor-positioning)**, **[setting the new attributes](console-virtual-terminal-sequences.md#text-formatting)**, then writing the desired text for that region, repeating characters if necessary for the length of the fill run.</span></span> <span data-ttu-id="1b5b4-132">您可以接著撰寫所需的文字來填滿矩形區域，以需要額外的資料指標移動。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-132">Additional cursor movement may be required followed by writing the desired text to fill a rectangular region.</span></span> <span data-ttu-id="1b5b4-133">用戶端應用程式應該將自己的記憶體保留在畫面上，而且無法查詢遠端狀態。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-133">The client application is expected to keep its own memory of what is on the screen and is not able to query the remote state.</span></span> <span data-ttu-id="1b5b4-134">如需詳細資訊，請參閱 **[傳統主控台與虛擬終端](classic-vs-vt.md)** 檔。</span><span class="sxs-lookup"><span data-stu-id="1b5b4-134">More information can be found in **[classic console versus virtual terminal](classic-vs-vt.md)** documentation.</span></span>

## <a name="requirements"></a><span data-ttu-id="1b5b4-135">規格需求</span><span class="sxs-lookup"><span data-stu-id="1b5b4-135">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1b5b4-136">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="1b5b4-136">Minimum supported client</span></span> | <span data-ttu-id="1b5b4-137">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="1b5b4-137">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1b5b4-138">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="1b5b4-138">Minimum supported server</span></span> | <span data-ttu-id="1b5b4-139">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="1b5b4-139">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1b5b4-140">標頭</span><span class="sxs-lookup"><span data-stu-id="1b5b4-140">Header</span></span> | <span data-ttu-id="1b5b4-141">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="1b5b4-141">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="1b5b4-142">程式庫</span><span class="sxs-lookup"><span data-stu-id="1b5b4-142">Library</span></span> | <span data-ttu-id="1b5b4-143">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="1b5b4-143">Kernel32.lib</span></span> |
| <span data-ttu-id="1b5b4-144">DLL</span><span class="sxs-lookup"><span data-stu-id="1b5b4-144">DLL</span></span> | <span data-ttu-id="1b5b4-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1b5b4-145">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="1b5b4-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b5b4-146">See also</span></span>

[<span data-ttu-id="1b5b4-147">主控台函式</span><span class="sxs-lookup"><span data-stu-id="1b5b4-147">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1b5b4-148">**COORD**</span><span class="sxs-lookup"><span data-stu-id="1b5b4-148">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="1b5b4-149">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="1b5b4-149">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="1b5b4-150">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="1b5b4-150">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="1b5b4-151">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="1b5b4-151">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

[<span data-ttu-id="1b5b4-152">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="1b5b4-152">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)
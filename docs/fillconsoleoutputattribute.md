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
ms.openlocfilehash: 40eb97e43e406d68ff625db110998ebf69eb26f7
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039066"
---
# <a name="fillconsoleoutputattribute-function"></a><span data-ttu-id="f7ea5-104">FillConsoleOutputAttribute 函式</span><span class="sxs-lookup"><span data-stu-id="f7ea5-104">FillConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="f7ea5-105">針對指定的字元資料格數目，設定從螢幕緩衝區中的指定座標開始的字元屬性。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-105">Sets the character attributes for a specified number of character cells, beginning at the specified coordinates in a screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="f7ea5-106">語法</span><span class="sxs-lookup"><span data-stu-id="f7ea5-106">Syntax</span></span>

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="f7ea5-107">參數</span><span class="sxs-lookup"><span data-stu-id="f7ea5-107">Parameters</span></span>

<span data-ttu-id="f7ea5-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f7ea5-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="f7ea5-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="f7ea5-110">控制碼必須有 **一般 \_ 寫入** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="f7ea5-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="f7ea5-112">*wAttribute* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f7ea5-112">*wAttribute* \[in\]</span></span>  
<span data-ttu-id="f7ea5-113">寫入主控台螢幕緩衝區時要使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-113">The attributes to use when writing to the console screen buffer.</span></span> <span data-ttu-id="f7ea5-114">如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#character-attributes)。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="f7ea5-115">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f7ea5-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="f7ea5-116">要設定為指定之色彩屬性的字元儲存格數目。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-116">The number of character cells to be set to the specified color attributes.</span></span>

<span data-ttu-id="f7ea5-117">*dwWriteCoord* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f7ea5-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="f7ea5-118">[**COORD**](coord-str.md)結構，指定要設定其屬性的第一個資料格的字元座標。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell whose attributes are to be set.</span></span>

<span data-ttu-id="f7ea5-119">*lpNumberOfAttrsWritten* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="f7ea5-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="f7ea5-120">變數的指標，此變數會接收實際設定其屬性的字元儲存格數目。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-120">A pointer to a variable that receives the number of character cells whose attributes were actually set.</span></span>

## <a name="return-value"></a><span data-ttu-id="f7ea5-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="f7ea5-121">Return value</span></span>

<span data-ttu-id="f7ea5-122">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f7ea5-123">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f7ea5-124">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="f7ea5-125">備註</span><span class="sxs-lookup"><span data-stu-id="f7ea5-125">Remarks</span></span>

<span data-ttu-id="f7ea5-126">如果要設定屬性的字元資料格數目延伸超過主控台螢幕緩衝區中指定之資料列的結尾，則會設定下一個資料列的資料格。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-126">If the number of character cells whose attributes are to be set extends beyond the end of the specified row in the console screen buffer, the cells of the next row are set.</span></span> <span data-ttu-id="f7ea5-127">如果要寫入的資料格數目延伸超過主控台螢幕緩衝區的結尾，則資料格會寫入至主控台畫面緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-127">If the number of cells to write to extends beyond the end of the console screen buffer, the cells are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="f7ea5-128">寫入至的位置的字元值不會變更。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-128">The character values at the positions written to are not changed.</span></span>

> [!TIP]
> <span data-ttu-id="f7ea5-129">不建議使用此 API，也不會有對等的特定 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-129">This API is not recommended and does not have a specific **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="f7ea5-130">不支援在可見視窗外填滿區域，而且會保留給終端機的歷程記錄空間。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-130">Filling the region outside the viewable window is not supported and is reserved for the terminal's history space.</span></span> <span data-ttu-id="f7ea5-131">使用新文字或色彩填滿可見區域的動作是透過 **[移動游標](console-virtual-terminal-sequences.md#cursor-positioning)** 、 **[設定新屬性](console-virtual-terminal-sequences.md#text-formatting)** ，然後撰寫該區域所需的文字，並在填滿填滿的長度時重複字元。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-131">Filling a visible region with new text or color is performed through **[moving the cursor](console-virtual-terminal-sequences.md#cursor-positioning)** , **[setting the new attributes](console-virtual-terminal-sequences.md#text-formatting)** , then writing the desired text for that region, repeating characters if necessary for the length of the fill run.</span></span> <span data-ttu-id="f7ea5-132">您可以接著撰寫所需的文字來填滿矩形區域，以需要額外的資料指標移動。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-132">Additional cursor movement may be required followed by writing the desired text to fill a rectangular region.</span></span> <span data-ttu-id="f7ea5-133">用戶端應用程式應該將自己的記憶體保留在畫面上，而且無法查詢遠端狀態。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-133">The client application is expected to keep its own memory of what is on the screen and is not able to query the remote state.</span></span> <span data-ttu-id="f7ea5-134">如需詳細資訊，請參閱 **[傳統主控台與虛擬終端](classic-vs-vt.md)** 檔。</span><span class="sxs-lookup"><span data-stu-id="f7ea5-134">More information can be found in **[classic console versus virtual terminal](classic-vs-vt.md)** documentation.</span></span>

## <a name="requirements"></a><span data-ttu-id="f7ea5-135">規格需求</span><span class="sxs-lookup"><span data-stu-id="f7ea5-135">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="f7ea5-136">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="f7ea5-136">Minimum supported client</span></span> | <span data-ttu-id="f7ea5-137">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="f7ea5-137">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="f7ea5-138">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="f7ea5-138">Minimum supported server</span></span> | <span data-ttu-id="f7ea5-139">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="f7ea5-139">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="f7ea5-140">標頭</span><span class="sxs-lookup"><span data-stu-id="f7ea5-140">Header</span></span> | <span data-ttu-id="f7ea5-141">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="f7ea5-141">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="f7ea5-142">程式庫</span><span class="sxs-lookup"><span data-stu-id="f7ea5-142">Library</span></span> | <span data-ttu-id="f7ea5-143">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="f7ea5-143">Kernel32.lib</span></span> |
| <span data-ttu-id="f7ea5-144">DLL</span><span class="sxs-lookup"><span data-stu-id="f7ea5-144">DLL</span></span> | <span data-ttu-id="f7ea5-145">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f7ea5-145">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="f7ea5-146">請參閱</span><span class="sxs-lookup"><span data-stu-id="f7ea5-146">See also</span></span>

[<span data-ttu-id="f7ea5-147">主控台功能</span><span class="sxs-lookup"><span data-stu-id="f7ea5-147">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f7ea5-148">**COORD**</span><span class="sxs-lookup"><span data-stu-id="f7ea5-148">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="f7ea5-149">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="f7ea5-149">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="f7ea5-150">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="f7ea5-150">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="f7ea5-151">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="f7ea5-151">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

[<span data-ttu-id="f7ea5-152">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="f7ea5-152">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

---
title: FillConsoleOutputCharacter 函式
description: 從指定的座標開始，將字元從主控台螢幕緩衝區寫入指定的次數。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/FillConsoleOutputCharacter
- wincon/FillConsoleOutputCharacter
- FillConsoleOutputCharacter
- consoleapi2/FillConsoleOutputCharacterA
- wincon/FillConsoleOutputCharacterA
- FillConsoleOutputCharacterA
- consoleapi2/FillConsoleOutputCharacterW
- wincon/FillConsoleOutputCharacterW
- FillConsoleOutputCharacterW
MS-HAID:
- '\_win32\_fillconsoleoutputcharacter'
- base.fillconsoleoutputcharacter
- consoles.fillconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 37579cc9-14b3-4fd9-81ed-abaad5c7bd1a
topic_type:
- apiref
api_name:
- FillConsoleOutputCharacter
- FillConsoleOutputCharacterA
- FillConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 95efbcc261943a2986fe6fbb1f3d54aaae1b2d2b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357508"
---
# <a name="fillconsoleoutputcharacter-function"></a><span data-ttu-id="04ff8-104">FillConsoleOutputCharacter 函式</span><span class="sxs-lookup"><span data-stu-id="04ff8-104">FillConsoleOutputCharacter function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="04ff8-105">從指定的座標開始，將字元從主控台螢幕緩衝區寫入指定的次數。</span><span class="sxs-lookup"><span data-stu-id="04ff8-105">Writes a character to the console screen buffer a specified number of times, beginning at the specified coordinates.</span></span>

## <a name="syntax"></a><span data-ttu-id="04ff8-106">語法</span><span class="sxs-lookup"><span data-stu-id="04ff8-106">Syntax</span></span>

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="04ff8-107">參數</span><span class="sxs-lookup"><span data-stu-id="04ff8-107">Parameters</span></span>

<span data-ttu-id="04ff8-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="04ff8-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="04ff8-109">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="04ff8-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="04ff8-110">控點必須具有 **GENERIC\_WRITE** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="04ff8-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="04ff8-111">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="04ff8-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="04ff8-112">*cCharacter* \[在\]</span><span class="sxs-lookup"><span data-stu-id="04ff8-112">*cCharacter* \[in\]</span></span>  
<span data-ttu-id="04ff8-113">要寫入主控台螢幕緩衝區的字元。</span><span class="sxs-lookup"><span data-stu-id="04ff8-113">The character to be written to the console screen buffer.</span></span>

<span data-ttu-id="04ff8-114">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="04ff8-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="04ff8-115">應寫入字元的字元儲存格數目。</span><span class="sxs-lookup"><span data-stu-id="04ff8-115">The number of character cells to which the character should be written.</span></span>

<span data-ttu-id="04ff8-116">*dwWriteCoord* \[在\]</span><span class="sxs-lookup"><span data-stu-id="04ff8-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="04ff8-117">[**COORD**](coord-str.md)結構，指定要寫入字元的第一個資料格的字元座標。</span><span class="sxs-lookup"><span data-stu-id="04ff8-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell to which the character is to be written.</span></span>

<span data-ttu-id="04ff8-118">*lpNumberOfCharsWritten* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="04ff8-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="04ff8-119">變數的指標，此變數會接收實際寫入主控台螢幕緩衝區的字元數。</span><span class="sxs-lookup"><span data-stu-id="04ff8-119">A pointer to a variable that receives the number of characters actually written to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="04ff8-120">傳回值</span><span class="sxs-lookup"><span data-stu-id="04ff8-120">Return value</span></span>

<span data-ttu-id="04ff8-121">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="04ff8-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="04ff8-122">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="04ff8-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="04ff8-123">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="04ff8-123">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="04ff8-124">備註</span><span class="sxs-lookup"><span data-stu-id="04ff8-124">Remarks</span></span>

<span data-ttu-id="04ff8-125">如果要寫入的字元數超出主控台螢幕緩衝區中指定之資料列的結尾，則會將字元寫入至下一個資料列。</span><span class="sxs-lookup"><span data-stu-id="04ff8-125">If the number of characters to write to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="04ff8-126">如果要寫入的字元數超過主控台螢幕緩衝區的結尾，則字元會寫入至主控台畫面緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="04ff8-126">If the number of characters to write to extends beyond the end of the console screen buffer, the characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="04ff8-127">在寫入位置的屬性值不會變更。</span><span class="sxs-lookup"><span data-stu-id="04ff8-127">The attribute values at the positions written are not changed.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="04ff8-128">不建議使用此 API，也不會有對等的特定 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="04ff8-128">This API is not recommended and does not have a specific **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="04ff8-129">不支援在可見視窗外填滿區域，而且會保留給終端機的歷程記錄空間。</span><span class="sxs-lookup"><span data-stu-id="04ff8-129">Filling the region outside the viewable window is not supported and is reserved for the terminal's history space.</span></span> <span data-ttu-id="04ff8-130">使用新文字或色彩填滿可見區域的動作是透過 **[移動游標](console-virtual-terminal-sequences.md#cursor-positioning)**、 **[設定新屬性](console-virtual-terminal-sequences.md#text-formatting)**，然後撰寫該區域所需的文字，並在填滿填滿的長度時重複字元。</span><span class="sxs-lookup"><span data-stu-id="04ff8-130">Filling a visible region with new text or color is performed through **[moving the cursor](console-virtual-terminal-sequences.md#cursor-positioning)**, **[setting the new attributes](console-virtual-terminal-sequences.md#text-formatting)**, then writing the desired text for that region, repeating characters if necessary for the length of the fill run.</span></span> <span data-ttu-id="04ff8-131">您可以接著撰寫所需的文字來填滿矩形區域，以需要額外的資料指標移動。</span><span class="sxs-lookup"><span data-stu-id="04ff8-131">Additional cursor movement may be required followed by writing the desired text to fill a rectangular region.</span></span> <span data-ttu-id="04ff8-132">用戶端應用程式應該將自己的記憶體保留在畫面上，而且無法查詢遠端狀態。</span><span class="sxs-lookup"><span data-stu-id="04ff8-132">The client application is expected to keep its own memory of what is on the screen and is not able to query the remote state.</span></span> <span data-ttu-id="04ff8-133">如需詳細資訊，請參閱 **[傳統主控台與虛擬終端](classic-vs-vt.md)** 檔。</span><span class="sxs-lookup"><span data-stu-id="04ff8-133">More information can be found in **[classic console versus virtual terminal](classic-vs-vt.md)** documentation.</span></span>

## <a name="requirements"></a><span data-ttu-id="04ff8-134">規格需求</span><span class="sxs-lookup"><span data-stu-id="04ff8-134">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="04ff8-135">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="04ff8-135">Minimum supported client</span></span> | <span data-ttu-id="04ff8-136">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="04ff8-136">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="04ff8-137">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="04ff8-137">Minimum supported server</span></span> | <span data-ttu-id="04ff8-138">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="04ff8-138">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="04ff8-139">標頭</span><span class="sxs-lookup"><span data-stu-id="04ff8-139">Header</span></span> | <span data-ttu-id="04ff8-140">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="04ff8-140">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="04ff8-141">程式庫</span><span class="sxs-lookup"><span data-stu-id="04ff8-141">Library</span></span> | <span data-ttu-id="04ff8-142">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="04ff8-142">Kernel32.lib</span></span> |
| <span data-ttu-id="04ff8-143">DLL</span><span class="sxs-lookup"><span data-stu-id="04ff8-143">DLL</span></span> | <span data-ttu-id="04ff8-144">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="04ff8-144">Kernel32.dll</span></span> |
| <span data-ttu-id="04ff8-145">Unicode 與 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="04ff8-145">Unicode and ANSI names</span></span> | <span data-ttu-id="04ff8-146">**FillConsoleOutputCharacterW** (Unicode) 和 **FillConsoleOutputCharacterA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="04ff8-146">**FillConsoleOutputCharacterW** (Unicode) and **FillConsoleOutputCharacterA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="04ff8-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04ff8-147">See also</span></span>

[<span data-ttu-id="04ff8-148">主控台函式</span><span class="sxs-lookup"><span data-stu-id="04ff8-148">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="04ff8-149">**COORD**</span><span class="sxs-lookup"><span data-stu-id="04ff8-149">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="04ff8-150">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="04ff8-150">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="04ff8-151">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="04ff8-151">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="04ff8-152">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="04ff8-152">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="04ff8-153">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="04ff8-153">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="04ff8-154">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="04ff8-154">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
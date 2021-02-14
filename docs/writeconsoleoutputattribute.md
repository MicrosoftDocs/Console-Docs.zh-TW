---
title: WriteConsoleOutputAttribute 函式
description: 從指定的位置開始，將數個字元屬性複製到主控台螢幕緩衝區的連續儲存格。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/WriteConsoleOutputAttribute
- wincon/WriteConsoleOutputAttribute
- WriteConsoleOutputAttribute
MS-HAID:
- '\_win32\_writeconsoleoutputattribute'
- base.writeconsoleoutputattribute
- consoles.writeconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 52a9d6e5-072e-4411-9945-10bd3dd61e25
topic_type:
- apiref
api_name:
- WriteConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d4c940243b8367e2f66923c14ffa90de7c9a384b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357758"
---
# <a name="writeconsoleoutputattribute-function"></a><span data-ttu-id="52617-104">WriteConsoleOutputAttribute 函式</span><span class="sxs-lookup"><span data-stu-id="52617-104">WriteConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="52617-105">從指定的位置開始，將數個字元屬性複製到主控台螢幕緩衝區的連續儲存格。</span><span class="sxs-lookup"><span data-stu-id="52617-105">Copies a number of character attributes to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="52617-106">語法</span><span class="sxs-lookup"><span data-stu-id="52617-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="52617-107">參數</span><span class="sxs-lookup"><span data-stu-id="52617-107">Parameters</span></span>

<span data-ttu-id="52617-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="52617-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="52617-109">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="52617-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="52617-110">控點必須具有 **GENERIC\_WRITE** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="52617-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="52617-111">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="52617-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="52617-112">*lpAttribute* \[在\]</span><span class="sxs-lookup"><span data-stu-id="52617-112">*lpAttribute* \[in\]</span></span>  
<span data-ttu-id="52617-113">要在寫入主控台螢幕緩衝區時使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="52617-113">The attributes to be used when writing to the console screen buffer.</span></span> <span data-ttu-id="52617-114">如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#character-attributes)。</span><span class="sxs-lookup"><span data-stu-id="52617-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="52617-115">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="52617-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="52617-116">要將屬性複製到其中的螢幕緩衝區字元儲存格數目。</span><span class="sxs-lookup"><span data-stu-id="52617-116">The number of screen buffer character cells to which the attributes will be copied.</span></span>

<span data-ttu-id="52617-117">*dwWriteCoord* \[在\]</span><span class="sxs-lookup"><span data-stu-id="52617-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="52617-118">[**COORD**](coord-str.md)結構，指定要將屬性寫入其中的主控台螢幕緩衝區中第一個資料格的字元座標。</span><span class="sxs-lookup"><span data-stu-id="52617-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which the attributes will be written.</span></span>

<span data-ttu-id="52617-119">*lpNumberOfAttrsWritten* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="52617-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="52617-120">變數的指標，此變數會接收實際寫入主控台螢幕緩衝區的屬性數目。</span><span class="sxs-lookup"><span data-stu-id="52617-120">A pointer to a variable that receives the number of attributes actually written to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="52617-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="52617-121">Return value</span></span>

<span data-ttu-id="52617-122">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="52617-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="52617-123">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="52617-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="52617-124">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="52617-124">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="52617-125">備註</span><span class="sxs-lookup"><span data-stu-id="52617-125">Remarks</span></span>

<span data-ttu-id="52617-126">如果要寫入的屬性數目超過主控台螢幕緩衝區中指定之資料列的結尾，則會將屬性寫入至下一個資料列。</span><span class="sxs-lookup"><span data-stu-id="52617-126">If the number of attributes to be written to extends beyond the end of the specified row in the console screen buffer, attributes are written to the next row.</span></span> <span data-ttu-id="52617-127">如果要寫入的屬性數目超過主控台螢幕緩衝區的結尾，則會將屬性寫入至主控台畫面緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="52617-127">If the number of attributes to be written to extends beyond the end of the console screen buffer, the attributes are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="52617-128">寫入至的位置的字元值不會變更。</span><span class="sxs-lookup"><span data-stu-id="52617-128">The character values at the positions written to are not changed.</span></span>

> [!TIP]
> <span data-ttu-id="52617-129">此 API 的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機等同于 **[文字格式](console-virtual-terminal-sequences.md#text-formatting)** 和資料 **[指標定位](console-virtual-terminal-sequences.md#cursor-positioning)** 順序。</span><span class="sxs-lookup"><span data-stu-id="52617-129">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sequences.</span></span> <span data-ttu-id="52617-130">將游標移至要插入的位置，套用所需的格式，並寫出要填滿的文字。</span><span class="sxs-lookup"><span data-stu-id="52617-130">Move the cursor to the location to insert, apply the formatting desired, and write out text to fill.</span></span> <span data-ttu-id="52617-131">沒有任何專案可將色彩套用至區域，也不會發出文字。</span><span class="sxs-lookup"><span data-stu-id="52617-131">There is no equivalent to apply color to an area without also emitting text.</span></span> <span data-ttu-id="52617-132">這項決策刻意讓 Windows 平臺與其他作業系統保持一致，而個別用戶端應用程式應記住自己的繪製狀態以進行進一步的操作。</span><span class="sxs-lookup"><span data-stu-id="52617-132">This decision intentionally aligns the Windows platform with other operating systems where the individual client application is expected to remember its own drawn state for further manipulation.</span></span>

## <a name="requirements"></a><span data-ttu-id="52617-133">規格需求</span><span class="sxs-lookup"><span data-stu-id="52617-133">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="52617-134">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="52617-134">Minimum supported client</span></span> | <span data-ttu-id="52617-135">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="52617-135">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="52617-136">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="52617-136">Minimum supported server</span></span> | <span data-ttu-id="52617-137">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="52617-137">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="52617-138">標頭</span><span class="sxs-lookup"><span data-stu-id="52617-138">Header</span></span> | <span data-ttu-id="52617-139">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="52617-139">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="52617-140">程式庫</span><span class="sxs-lookup"><span data-stu-id="52617-140">Library</span></span> | <span data-ttu-id="52617-141">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="52617-141">Kernel32.lib</span></span> |
| <span data-ttu-id="52617-142">DLL</span><span class="sxs-lookup"><span data-stu-id="52617-142">DLL</span></span> | <span data-ttu-id="52617-143">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="52617-143">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="52617-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="52617-144">See also</span></span>

[<span data-ttu-id="52617-145">主控台函式</span><span class="sxs-lookup"><span data-stu-id="52617-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="52617-146">**COORD**</span><span class="sxs-lookup"><span data-stu-id="52617-146">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="52617-147">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="52617-147">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="52617-148">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="52617-148">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="52617-149">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="52617-149">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="52617-150">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="52617-150">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="52617-151">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="52617-151">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="52617-152">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="52617-152">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
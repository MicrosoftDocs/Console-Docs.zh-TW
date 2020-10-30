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
ms.openlocfilehash: 04c7799cd98479d3b776b1933994b60f5ed9fc9f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039276"
---
# <a name="writeconsoleoutputattribute-function"></a><span data-ttu-id="35049-104">WriteConsoleOutputAttribute 函式</span><span class="sxs-lookup"><span data-stu-id="35049-104">WriteConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="35049-105">從指定的位置開始，將數個字元屬性複製到主控台螢幕緩衝區的連續儲存格。</span><span class="sxs-lookup"><span data-stu-id="35049-105">Copies a number of character attributes to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="35049-106">語法</span><span class="sxs-lookup"><span data-stu-id="35049-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="35049-107">參數</span><span class="sxs-lookup"><span data-stu-id="35049-107">Parameters</span></span>

<span data-ttu-id="35049-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="35049-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="35049-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="35049-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="35049-110">控制碼必須有 **一般 \_ 寫入** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="35049-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="35049-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="35049-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="35049-112">*lpAttribute* \[在\]</span><span class="sxs-lookup"><span data-stu-id="35049-112">*lpAttribute* \[in\]</span></span>  
<span data-ttu-id="35049-113">要在寫入主控台螢幕緩衝區時使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="35049-113">The attributes to be used when writing to the console screen buffer.</span></span> <span data-ttu-id="35049-114">如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#character-attributes)。</span><span class="sxs-lookup"><span data-stu-id="35049-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="35049-115">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="35049-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="35049-116">要將屬性複製到其中的螢幕緩衝區字元儲存格數目。</span><span class="sxs-lookup"><span data-stu-id="35049-116">The number of screen buffer character cells to which the attributes will be copied.</span></span>

<span data-ttu-id="35049-117">*dwWriteCoord* \[在\]</span><span class="sxs-lookup"><span data-stu-id="35049-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="35049-118">[**COORD**](coord-str.md)結構，指定要將屬性寫入其中的主控台螢幕緩衝區中第一個資料格的字元座標。</span><span class="sxs-lookup"><span data-stu-id="35049-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which the attributes will be written.</span></span>

<span data-ttu-id="35049-119">*lpNumberOfAttrsWritten* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="35049-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="35049-120">變數的指標，此變數會接收實際寫入主控台螢幕緩衝區的屬性數目。</span><span class="sxs-lookup"><span data-stu-id="35049-120">A pointer to a variable that receives the number of attributes actually written to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="35049-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="35049-121">Return value</span></span>

<span data-ttu-id="35049-122">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="35049-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="35049-123">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="35049-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="35049-124">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="35049-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="35049-125">備註</span><span class="sxs-lookup"><span data-stu-id="35049-125">Remarks</span></span>

<span data-ttu-id="35049-126">如果要寫入的屬性數目超過主控台螢幕緩衝區中指定之資料列的結尾，則會將屬性寫入至下一個資料列。</span><span class="sxs-lookup"><span data-stu-id="35049-126">If the number of attributes to be written to extends beyond the end of the specified row in the console screen buffer, attributes are written to the next row.</span></span> <span data-ttu-id="35049-127">如果要寫入的屬性數目超過主控台螢幕緩衝區的結尾，則會將屬性寫入至主控台畫面緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="35049-127">If the number of attributes to be written to extends beyond the end of the console screen buffer, the attributes are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="35049-128">寫入至的位置的字元值不會變更。</span><span class="sxs-lookup"><span data-stu-id="35049-128">The character values at the positions written to are not changed.</span></span>

> [!TIP]
> <span data-ttu-id="35049-129">此 API 的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機等同于 **[文字格式](console-virtual-terminal-sequences.md#text-formatting)** 和資料 **[指標定位](console-virtual-terminal-sequences.md#cursor-positioning)** 順序。</span><span class="sxs-lookup"><span data-stu-id="35049-129">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sequences.</span></span> <span data-ttu-id="35049-130">將游標移至要插入的位置，套用所需的格式，並寫出要填滿的文字。</span><span class="sxs-lookup"><span data-stu-id="35049-130">Move the cursor to the location to insert, apply the formatting desired, and write out text to fill.</span></span> <span data-ttu-id="35049-131">沒有任何專案可將色彩套用至區域，也不會發出文字。</span><span class="sxs-lookup"><span data-stu-id="35049-131">There is no equivalent to apply color to an area without also emitting text.</span></span> <span data-ttu-id="35049-132">這項決策刻意讓 Windows 平臺與其他作業系統保持一致，而個別用戶端應用程式應記住自己的繪製狀態以進行進一步的操作。</span><span class="sxs-lookup"><span data-stu-id="35049-132">This decision intentionally aligns the Windows platform with other operating systems where the individual client application is expected to remember its own drawn state for further manipulation.</span></span>

## <a name="requirements"></a><span data-ttu-id="35049-133">規格需求</span><span class="sxs-lookup"><span data-stu-id="35049-133">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="35049-134">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="35049-134">Minimum supported client</span></span> | <span data-ttu-id="35049-135">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="35049-135">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="35049-136">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="35049-136">Minimum supported server</span></span> | <span data-ttu-id="35049-137">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="35049-137">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="35049-138">標頭</span><span class="sxs-lookup"><span data-stu-id="35049-138">Header</span></span> | <span data-ttu-id="35049-139">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="35049-139">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="35049-140">程式庫</span><span class="sxs-lookup"><span data-stu-id="35049-140">Library</span></span> | <span data-ttu-id="35049-141">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="35049-141">Kernel32.lib</span></span> |
| <span data-ttu-id="35049-142">DLL</span><span class="sxs-lookup"><span data-stu-id="35049-142">DLL</span></span> | <span data-ttu-id="35049-143">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="35049-143">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="35049-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="35049-144">See also</span></span>

[<span data-ttu-id="35049-145">主控台功能</span><span class="sxs-lookup"><span data-stu-id="35049-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="35049-146">**COORD**</span><span class="sxs-lookup"><span data-stu-id="35049-146">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="35049-147">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="35049-147">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="35049-148">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="35049-148">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="35049-149">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="35049-149">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="35049-150">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="35049-150">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="35049-151">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="35049-151">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="35049-152">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="35049-152">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

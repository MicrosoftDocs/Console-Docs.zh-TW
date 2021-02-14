---
title: WriteConsoleOutputCharacter 函式
description: 從指定的位置開始，將數個字元複製到主控台螢幕緩衝區的連續儲存格。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/WriteConsoleOutputCharacter
- wincon/WriteConsoleOutputCharacter
- WriteConsoleOutputCharacter
- consoleapi2/WriteConsoleOutputCharacterA
- wincon/WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterA
- consoleapi2/WriteConsoleOutputCharacterW
- wincon/WriteConsoleOutputCharacterW
- WriteConsoleOutputCharacterW
MS-HAID:
- '\_win32\_writeconsoleoutputcharacter'
- base.writeconsoleoutputcharacter
- consoles.writeconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7cc935ea-6b19-4494-b746-259aa7aaa9cc
topic_type:
- apiref
api_name:
- WriteConsoleOutputCharacter
- WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 87d6e8768f55135536b1c0f752cc8f7827c643f1
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100359038"
---
# <a name="writeconsoleoutputcharacter-function"></a><span data-ttu-id="f2205-104">WriteConsoleOutputCharacter 函式</span><span class="sxs-lookup"><span data-stu-id="f2205-104">WriteConsoleOutputCharacter function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="f2205-105">從指定的位置開始，將數個字元複製到主控台螢幕緩衝區的連續儲存格。</span><span class="sxs-lookup"><span data-stu-id="f2205-105">Copies a number of characters to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2205-106">語法</span><span class="sxs-lookup"><span data-stu-id="f2205-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  LPCTSTR lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

## <a name="parameters"></a><span data-ttu-id="f2205-107">參數</span><span class="sxs-lookup"><span data-stu-id="f2205-107">Parameters</span></span>

<span data-ttu-id="f2205-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f2205-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="f2205-109">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="f2205-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="f2205-110">控點必須具有 **GENERIC\_WRITE** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="f2205-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="f2205-111">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="f2205-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="f2205-112">*lpCharacter* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f2205-112">*lpCharacter* \[in\]</span></span>  
<span data-ttu-id="f2205-113">要寫入主控台螢幕緩衝區的字元。</span><span class="sxs-lookup"><span data-stu-id="f2205-113">The characters to be written to the console screen buffer.</span></span>

<span data-ttu-id="f2205-114">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f2205-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="f2205-115">要寫入的字元數。</span><span class="sxs-lookup"><span data-stu-id="f2205-115">The number of characters to be written.</span></span>

<span data-ttu-id="f2205-116">*dwWriteCoord* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f2205-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="f2205-117">[**COORD**](coord-str.md)結構，指定要在其中寫入字元的主控台螢幕緩衝區中第一個資料格的字元座標。</span><span class="sxs-lookup"><span data-stu-id="f2205-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which characters will be written.</span></span>

<span data-ttu-id="f2205-118">*lpNumberOfCharsWritten* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="f2205-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="f2205-119">變數的指標，可接收實際寫入的字元數。</span><span class="sxs-lookup"><span data-stu-id="f2205-119">A pointer to a variable that receives the number of characters actually written.</span></span>

## <a name="return-value"></a><span data-ttu-id="f2205-120">傳回值</span><span class="sxs-lookup"><span data-stu-id="f2205-120">Return value</span></span>

<span data-ttu-id="f2205-121">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="f2205-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f2205-122">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="f2205-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f2205-123">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="f2205-123">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="f2205-124">備註</span><span class="sxs-lookup"><span data-stu-id="f2205-124">Remarks</span></span>

<span data-ttu-id="f2205-125">如果要寫入的字元數超出主控台螢幕緩衝區中指定之資料列的結尾，則會將字元寫入至下一個資料列。</span><span class="sxs-lookup"><span data-stu-id="f2205-125">If the number of characters to be written to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="f2205-126">如果要寫入的字元數超過主控台螢幕緩衝區的結尾，則字元會寫入至主控台畫面緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="f2205-126">If the number of characters to be written to extends beyond the end of the console screen buffer, characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="f2205-127">在寫入至的位置上的屬性值不會變更。</span><span class="sxs-lookup"><span data-stu-id="f2205-127">The attribute values at the positions written to are not changed.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="f2205-128">此 API 的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機等同于 **[文字格式](console-virtual-terminal-sequences.md#text-formatting)** 和資料 **[指標定位](console-virtual-terminal-sequences.md#cursor-positioning)** 順序。</span><span class="sxs-lookup"><span data-stu-id="f2205-128">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sequences.</span></span> <span data-ttu-id="f2205-129">將游標移至要插入的位置，套用所需的格式，並寫出要填滿的文字。</span><span class="sxs-lookup"><span data-stu-id="f2205-129">Move the cursor to the location to insert, apply the formatting desired, and write out text to fill.</span></span> <span data-ttu-id="f2205-130">沒有任何專案會將文字發出至區域，也不會套用使用中的色彩格式。</span><span class="sxs-lookup"><span data-stu-id="f2205-130">There is no equivalent to emit text to an area without also applying the active color formatting.</span></span> <span data-ttu-id="f2205-131">這項決策刻意讓 Windows 平臺與其他作業系統保持一致，而個別用戶端應用程式應記住自己的繪製狀態以進行進一步的操作。</span><span class="sxs-lookup"><span data-stu-id="f2205-131">This decision intentionally aligns the Windows platform with other operating systems where the individual client application is expected to remember its own drawn state for further manipulation.</span></span>

## <a name="requirements"></a><span data-ttu-id="f2205-132">規格需求</span><span class="sxs-lookup"><span data-stu-id="f2205-132">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="f2205-133">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="f2205-133">Minimum supported client</span></span> | <span data-ttu-id="f2205-134">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="f2205-134">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="f2205-135">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="f2205-135">Minimum supported server</span></span> | <span data-ttu-id="f2205-136">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="f2205-136">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="f2205-137">標頭</span><span class="sxs-lookup"><span data-stu-id="f2205-137">Header</span></span> | <span data-ttu-id="f2205-138">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="f2205-138">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="f2205-139">程式庫</span><span class="sxs-lookup"><span data-stu-id="f2205-139">Library</span></span> | <span data-ttu-id="f2205-140">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="f2205-140">Kernel32.lib</span></span> |
| <span data-ttu-id="f2205-141">DLL</span><span class="sxs-lookup"><span data-stu-id="f2205-141">DLL</span></span> | <span data-ttu-id="f2205-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f2205-142">Kernel32.dll</span></span> |
| <span data-ttu-id="f2205-143">Unicode 與 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="f2205-143">Unicode and ANSI names</span></span> | <span data-ttu-id="f2205-144">**WriteConsoleOutputCharacterW** (Unicode) 和 **WriteConsoleOutputCharacterA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="f2205-144">**WriteConsoleOutputCharacterW** (Unicode) and **WriteConsoleOutputCharacterA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="f2205-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2205-145">See also</span></span>

[<span data-ttu-id="f2205-146">主控台函式</span><span class="sxs-lookup"><span data-stu-id="f2205-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f2205-147">**COORD**</span><span class="sxs-lookup"><span data-stu-id="f2205-147">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="f2205-148">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="f2205-148">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="f2205-149">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="f2205-149">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="f2205-150">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="f2205-150">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="f2205-151">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="f2205-151">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="f2205-152">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="f2205-152">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="f2205-153">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="f2205-153">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="f2205-154">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="f2205-154">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="f2205-155">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="f2205-155">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)
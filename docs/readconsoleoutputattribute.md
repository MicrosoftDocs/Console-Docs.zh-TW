---
title: ReadConsoleOutputAttribute 函式
description: 從主控台螢幕緩衝區的連續儲存格（從指定的位置開始）複製指定數目的字元屬性。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/ReadConsoleOutputAttribute
- wincon/ReadConsoleOutputAttribute
- ReadConsoleOutputAttribute
MS-HAID:
- '\_win32\_readconsoleoutputattribute'
- base.readconsoleoutputattribute
- consoles.readconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c3e35779-a487-47f1-8d07-0d5fae99d54a
topic_type:
- apiref
api_name:
- ReadConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: bf140d9f6721196caa5f62a064ed434554067d62
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358689"
---
# <a name="readconsoleoutputattribute-function"></a><span data-ttu-id="968fa-104">ReadConsoleOutputAttribute 函式</span><span class="sxs-lookup"><span data-stu-id="968fa-104">ReadConsoleOutputAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="968fa-105">從主控台螢幕緩衝區的連續儲存格（從指定的位置開始）複製指定數目的字元屬性。</span><span class="sxs-lookup"><span data-stu-id="968fa-105">Copies a specified number of character attributes from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="968fa-106">語法</span><span class="sxs-lookup"><span data-stu-id="968fa-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPWORD  lpAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfAttrsRead
);
```

## <a name="parameters"></a><span data-ttu-id="968fa-107">參數</span><span class="sxs-lookup"><span data-stu-id="968fa-107">Parameters</span></span>

<span data-ttu-id="968fa-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="968fa-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="968fa-109">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="968fa-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="968fa-110">控制代碼必須具有 **GENERIC\_READ** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="968fa-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="968fa-111">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="968fa-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="968fa-112">*lpAttribute* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="968fa-112">*lpAttribute* \[out\]</span></span>  
<span data-ttu-id="968fa-113">緩衝區的指標，此緩衝區會接收主控台螢幕緩衝區所使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="968fa-113">A pointer to a buffer that receives the attributes being used by the console screen buffer.</span></span>

<span data-ttu-id="968fa-114">如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#character-attributes)。</span><span class="sxs-lookup"><span data-stu-id="968fa-114">For more information, see [Character Attributes](console-screen-buffers.md#character-attributes).</span></span>

<span data-ttu-id="968fa-115">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="968fa-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="968fa-116">要從中讀取的螢幕緩衝區字元儲存格數目。</span><span class="sxs-lookup"><span data-stu-id="968fa-116">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="968fa-117">*LpAttribute* 參數所指向的緩衝區大小應該是 `nLength * sizeof(WORD)` 。</span><span class="sxs-lookup"><span data-stu-id="968fa-117">The size of the buffer pointed to by the *lpAttribute* parameter should be `nLength * sizeof(WORD)`.</span></span>

<span data-ttu-id="968fa-118">*dwReadCoord* \[在\]</span><span class="sxs-lookup"><span data-stu-id="968fa-118">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="968fa-119">要從中讀取的主控台螢幕緩衝區中第一個資料格的座標（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="968fa-119">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="968fa-120">[**COORD**](coord-str.md)結構的 **X** 成員是資料行，而 **Y** 成員是資料列。</span><span class="sxs-lookup"><span data-stu-id="968fa-120">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="968fa-121">*lpNumberOfAttrsRead* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="968fa-121">*lpNumberOfAttrsRead* \[out\]</span></span>  
<span data-ttu-id="968fa-122">變數的指標，此變數會接收實際讀取的屬性數目。</span><span class="sxs-lookup"><span data-stu-id="968fa-122">A pointer to a variable that receives the number of attributes actually read.</span></span>

## <a name="return-value"></a><span data-ttu-id="968fa-123">傳回值</span><span class="sxs-lookup"><span data-stu-id="968fa-123">Return value</span></span>

<span data-ttu-id="968fa-124">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="968fa-124">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="968fa-125">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="968fa-125">If the function fails, the return value is zero.</span></span> <span data-ttu-id="968fa-126">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="968fa-126">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="968fa-127">備註</span><span class="sxs-lookup"><span data-stu-id="968fa-127">Remarks</span></span>

<span data-ttu-id="968fa-128">如果要讀取的屬性數目超出指定螢幕緩衝區資料列的結尾，則會從下一個資料列讀取屬性。</span><span class="sxs-lookup"><span data-stu-id="968fa-128">If the number of attributes to be read from extends beyond the end of the specified screen buffer row, attributes are read from the next row.</span></span> <span data-ttu-id="968fa-129">如果要讀取的屬性數目延伸超過主控台螢幕緩衝區的結尾，則會讀取最多至主控台畫面緩衝區結尾的屬性。</span><span class="sxs-lookup"><span data-stu-id="968fa-129">If the number of attributes to be read from extends beyond the end of the console screen buffer, attributes up to the end of the console screen buffer are read.</span></span>

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="requirements"></a><span data-ttu-id="968fa-130">規格需求</span><span class="sxs-lookup"><span data-stu-id="968fa-130">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="968fa-131">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="968fa-131">Minimum supported client</span></span> | <span data-ttu-id="968fa-132">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="968fa-132">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="968fa-133">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="968fa-133">Minimum supported server</span></span> | <span data-ttu-id="968fa-134">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="968fa-134">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="968fa-135">標頭</span><span class="sxs-lookup"><span data-stu-id="968fa-135">Header</span></span> | <span data-ttu-id="968fa-136">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="968fa-136">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="968fa-137">程式庫</span><span class="sxs-lookup"><span data-stu-id="968fa-137">Library</span></span> | <span data-ttu-id="968fa-138">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="968fa-138">Kernel32.lib</span></span> |
| <span data-ttu-id="968fa-139">DLL</span><span class="sxs-lookup"><span data-stu-id="968fa-139">DLL</span></span> | <span data-ttu-id="968fa-140">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="968fa-140">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="968fa-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="968fa-141">See also</span></span>

[<span data-ttu-id="968fa-142">主控台函式</span><span class="sxs-lookup"><span data-stu-id="968fa-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="968fa-143">**COORD**</span><span class="sxs-lookup"><span data-stu-id="968fa-143">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="968fa-144">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="968fa-144">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="968fa-145">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="968fa-145">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="968fa-146">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="968fa-146">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="968fa-147">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="968fa-147">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="968fa-148">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="968fa-148">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="968fa-149">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="968fa-149">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)
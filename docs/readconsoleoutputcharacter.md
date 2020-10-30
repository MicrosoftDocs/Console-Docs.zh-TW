---
title: ReadConsoleOutputCharacter 函式
description: 從主控台螢幕緩衝區的連續資料格複製一些字元，從指定的位置開始。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/ReadConsoleOutputCharacter
- wincon/ReadConsoleOutputCharacter
- ReadConsoleOutputCharacter
- consoleapi2/ReadConsoleOutputCharacterA
- wincon/ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterA
- consoleapi2/ReadConsoleOutputCharacterW
- wincon/ReadConsoleOutputCharacterW
- ReadConsoleOutputCharacterW
MS-HAID:
- '\_win32\_readconsoleoutputcharacter'
- base.readconsoleoutputcharacter
- consoles.readconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f47464a9-6c59-4f15-abd0-be29ab515698
topic_type:
- apiref
api_name:
- ReadConsoleOutputCharacter
- ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: fa70841d5dccf3289807d29c67fab86e3b445279
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037718"
---
# <a name="readconsoleoutputcharacter-function"></a><span data-ttu-id="1209a-104">ReadConsoleOutputCharacter 函式</span><span class="sxs-lookup"><span data-stu-id="1209a-104">ReadConsoleOutputCharacter function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="1209a-105">從主控台螢幕緩衝區的連續資料格複製一些字元，從指定的位置開始。</span><span class="sxs-lookup"><span data-stu-id="1209a-105">Copies a number of characters from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

## <a name="syntax"></a><span data-ttu-id="1209a-106">語法</span><span class="sxs-lookup"><span data-stu-id="1209a-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPTSTR  lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfCharsRead
);
```

## <a name="parameters"></a><span data-ttu-id="1209a-107">參數</span><span class="sxs-lookup"><span data-stu-id="1209a-107">Parameters</span></span>

<span data-ttu-id="1209a-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="1209a-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="1209a-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="1209a-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="1209a-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="1209a-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="1209a-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="1209a-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="1209a-112">*lpCharacter* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="1209a-112">*lpCharacter* \[out\]</span></span>  
<span data-ttu-id="1209a-113">緩衝區的指標，此緩衝區會接收從主控台螢幕緩衝區讀取的字元。</span><span class="sxs-lookup"><span data-stu-id="1209a-113">A pointer to a buffer that receives the characters read from the console screen buffer.</span></span>

<span data-ttu-id="1209a-114">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="1209a-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="1209a-115">要從中讀取的螢幕緩衝區字元儲存格數目。</span><span class="sxs-lookup"><span data-stu-id="1209a-115">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="1209a-116">*LpCharacter* 參數所指向的緩衝區大小應該是 `nLength * sizeof(TCHAR)` 。</span><span class="sxs-lookup"><span data-stu-id="1209a-116">The size of the buffer pointed to by the *lpCharacter* parameter should be `nLength * sizeof(TCHAR)`.</span></span>

<span data-ttu-id="1209a-117">*dwReadCoord* \[在\]</span><span class="sxs-lookup"><span data-stu-id="1209a-117">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="1209a-118">要從中讀取的主控台螢幕緩衝區中第一個資料格的座標（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="1209a-118">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="1209a-119">[**COORD**](coord-str.md)結構的 **X** 成員是資料行，而 **Y** 成員是資料列。</span><span class="sxs-lookup"><span data-stu-id="1209a-119">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="1209a-120">*lpNumberOfCharsRead* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="1209a-120">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="1209a-121">變數的指標，此變數會接收實際讀取的字元數。</span><span class="sxs-lookup"><span data-stu-id="1209a-121">A pointer to a variable that receives the number of characters actually read.</span></span>

## <a name="return-value"></a><span data-ttu-id="1209a-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="1209a-122">Return value</span></span>

<span data-ttu-id="1209a-123">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="1209a-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="1209a-124">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="1209a-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="1209a-125">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="1209a-125">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="1209a-126">備註</span><span class="sxs-lookup"><span data-stu-id="1209a-126">Remarks</span></span>

<span data-ttu-id="1209a-127">如果要讀取的字元數超出指定螢幕緩衝區資料列的結尾，則會從下一個資料列讀取字元。</span><span class="sxs-lookup"><span data-stu-id="1209a-127">If the number of characters to be read from extends beyond the end of the specified screen buffer row, characters are read from the next row.</span></span> <span data-ttu-id="1209a-128">如果要讀取的字元數超過主控台螢幕緩衝區的結尾，則會讀取主控台螢幕緩衝區結尾的字元。</span><span class="sxs-lookup"><span data-stu-id="1209a-128">If the number of characters to be read from extends beyond the end of the console screen buffer, characters up to the end of the console screen buffer are read.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

[!INCLUDE [no-vt-equiv-banner](./includes/no-vt-equiv-banner.md)]

## <a name="requirements"></a><span data-ttu-id="1209a-129">規格需求</span><span class="sxs-lookup"><span data-stu-id="1209a-129">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="1209a-130">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="1209a-130">Minimum supported client</span></span> | <span data-ttu-id="1209a-131">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="1209a-131">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="1209a-132">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="1209a-132">Minimum supported server</span></span> | <span data-ttu-id="1209a-133">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="1209a-133">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="1209a-134">標頭</span><span class="sxs-lookup"><span data-stu-id="1209a-134">Header</span></span> | <span data-ttu-id="1209a-135">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="1209a-135">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="1209a-136">程式庫</span><span class="sxs-lookup"><span data-stu-id="1209a-136">Library</span></span> | <span data-ttu-id="1209a-137">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="1209a-137">Kernel32.lib</span></span> |
| <span data-ttu-id="1209a-138">DLL</span><span class="sxs-lookup"><span data-stu-id="1209a-138">DLL</span></span> | <span data-ttu-id="1209a-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="1209a-139">Kernel32.dll</span></span> |
| <span data-ttu-id="1209a-140">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="1209a-140">Unicode and ANSI names</span></span> | <span data-ttu-id="1209a-141">**ReadConsoleOutputCharacterW** (Unicode) 和 **ReadConsoleOutputCharacterA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="1209a-141">**ReadConsoleOutputCharacterW** (Unicode) and **ReadConsoleOutputCharacterA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="1209a-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="1209a-142">See also</span></span>

[<span data-ttu-id="1209a-143">主控台功能</span><span class="sxs-lookup"><span data-stu-id="1209a-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="1209a-144">**COORD**</span><span class="sxs-lookup"><span data-stu-id="1209a-144">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="1209a-145">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="1209a-145">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="1209a-146">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="1209a-146">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="1209a-147">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="1209a-147">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="1209a-148">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="1209a-148">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="1209a-149">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="1209a-149">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="1209a-150">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="1209a-150">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="1209a-151">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="1209a-151">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="1209a-152">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="1209a-152">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

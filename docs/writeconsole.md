---
title: WriteConsole 函式
description: 從目前的游標位置開始，將字元字串寫入主控台螢幕緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/WriteConsole
- wincon/WriteConsole
- WriteConsole
- consoleapi/WriteConsoleA
- wincon/WriteConsoleA
- WriteConsoleA
- consoleapi/WriteConsoleW
- wincon/WriteConsoleW
- WriteConsoleW
MS-HAID:
- '\_win32\_writeconsole'
- base.writeconsole
- consoles.writeconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1a13d9ef-75a9-49fd-9717-207f18612b59
topic_type:
- apiref
api_name:
- WriteConsole
- WriteConsoleA
- WriteConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.localizationpriority: high
ms.openlocfilehash: 426aa6711e46e0d5cda1eb1b7dab7b2b0b7156d6
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420287"
---
# <a name="writeconsole-function"></a><span data-ttu-id="42983-104">WriteConsole 函式</span><span class="sxs-lookup"><span data-stu-id="42983-104">WriteConsole function</span></span>

<span data-ttu-id="42983-105">從目前的游標位置開始，將字元字串寫入主控台螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="42983-105">Writes a character string to a console screen buffer beginning at the current cursor location.</span></span>

## <a name="syntax"></a><span data-ttu-id="42983-106">語法</span><span class="sxs-lookup"><span data-stu-id="42983-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a><span data-ttu-id="42983-107">參數</span><span class="sxs-lookup"><span data-stu-id="42983-107">Parameters</span></span>

<span data-ttu-id="42983-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="42983-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="42983-109">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="42983-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="42983-110">控點必須具有 **GENERIC\_WRITE** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="42983-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="42983-111">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="42983-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="42983-112">*lpBuffer* \[in\]</span><span class="sxs-lookup"><span data-stu-id="42983-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="42983-113">緩衝區的指標，其中包含要寫入主控台螢幕緩衝區的字元。</span><span class="sxs-lookup"><span data-stu-id="42983-113">A pointer to a buffer that contains characters to be written to the console screen buffer.</span></span> <span data-ttu-id="42983-114">這應該是 `WriteConsoleA` 的 `char` 陣列，或 `WriteConsoleW` 的 `wchar_t` 陣列。</span><span class="sxs-lookup"><span data-stu-id="42983-114">This is expected to be an array of either `char` for `WriteConsoleA` or `wchar_t` for `WriteConsoleW`.</span></span>

<span data-ttu-id="42983-115">*nNumberOfCharsToWrite* \[in\]</span><span class="sxs-lookup"><span data-stu-id="42983-115">*nNumberOfCharsToWrite* \[in\]</span></span>  
<span data-ttu-id="42983-116">要寫入的字元數。</span><span class="sxs-lookup"><span data-stu-id="42983-116">The number of characters to be written.</span></span> <span data-ttu-id="42983-117">如果指定字元數的總大小超過可用的堆積，則函式會因為 **ERROR\_NOT\_ENOUGH\_MEMORY** 而失敗。</span><span class="sxs-lookup"><span data-stu-id="42983-117">If the total size of the specified number of characters exceeds the available heap, the function fails with **ERROR\_NOT\_ENOUGH\_MEMORY**.</span></span>

<span data-ttu-id="42983-118">*lpNumberOfCharsWritten* \[out, optional\]</span><span class="sxs-lookup"><span data-stu-id="42983-118">*lpNumberOfCharsWritten* \[out, optional\]</span></span>  
<span data-ttu-id="42983-119">變數的指標，可接收實際寫入的字元數。</span><span class="sxs-lookup"><span data-stu-id="42983-119">A pointer to a variable that receives the number of characters actually written.</span></span>

<span data-ttu-id="42983-120">*lpReserved* 已保留；必須是 **NULL**。</span><span class="sxs-lookup"><span data-stu-id="42983-120">*lpReserved* Reserved; must be **NULL**.</span></span>

## <a name="return-value"></a><span data-ttu-id="42983-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="42983-121">Return value</span></span>

<span data-ttu-id="42983-122">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="42983-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="42983-123">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="42983-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="42983-124">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="42983-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="42983-125">備註</span><span class="sxs-lookup"><span data-stu-id="42983-125">Remarks</span></span>

<span data-ttu-id="42983-126">**WriteConsole** 函式會在目前游標位置將字元寫入主控台螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="42983-126">The **WriteConsole** function writes characters to the console screen buffer at the current cursor position.</span></span> <span data-ttu-id="42983-127">游標位置會在寫入字元時前進。</span><span class="sxs-lookup"><span data-stu-id="42983-127">The cursor position advances as characters are written.</span></span> <span data-ttu-id="42983-128">[**SetConsoleCursorPosition**](setconsolecursorposition.md) 函式會設定目前的游標位置。</span><span class="sxs-lookup"><span data-stu-id="42983-128">The [**SetConsoleCursorPosition**](setconsolecursorposition.md) function sets the current cursor position.</span></span>

<span data-ttu-id="42983-129">字元是使用與主控台螢幕緩衝區相關聯的前景和背景色彩屬性來撰寫。</span><span class="sxs-lookup"><span data-stu-id="42983-129">Characters are written using the foreground and background color attributes associated with the console screen buffer.</span></span> <span data-ttu-id="42983-130">[**SetConsoleTextAttribute**](setconsoletextattribute.md) 函式會變更這些色彩。</span><span class="sxs-lookup"><span data-stu-id="42983-130">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function changes these colors.</span></span> <span data-ttu-id="42983-131">若要判斷目前的色彩屬性和目前的游標位置，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)。</span><span class="sxs-lookup"><span data-stu-id="42983-131">To determine the current color attributes and the current cursor position, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span>

<span data-ttu-id="42983-132">所有會影響 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 函式行為的輸入模式，在 **WriteConsole** 上具有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="42983-132">All of the input modes that affect the behavior of the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) function have the same effect on **WriteConsole**.</span></span> <span data-ttu-id="42983-133">若要擷取及設定主控台螢幕緩衝區的輸出模式，請使用 [**GetConsoleMode**](getconsolemode.md) 和 [**SetConsoleMode**](setconsolemode.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="42983-133">To retrieve and set the output modes of a console screen buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

<span data-ttu-id="42983-134">如果 **WriteConsole** 搭配會重新導向至檔案的標準控點使用，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="42983-134">**WriteConsole** fails if it is used with a standard handle that is redirected to a file.</span></span> <span data-ttu-id="42983-135">如果應用程式處理可重新導向的多語系輸出，請判斷輸出控點是否為主控台控點 (其中一種方法是呼叫 [**GetConsoleMode**](getconsolemode.md) 函式並檢查其是否成功)。</span><span class="sxs-lookup"><span data-stu-id="42983-135">If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [**GetConsoleMode**](getconsolemode.md) function and check whether it succeeds).</span></span> <span data-ttu-id="42983-136">如果控點是主控台控點，請呼叫 **WriteConsole**。</span><span class="sxs-lookup"><span data-stu-id="42983-136">If the handle is a console handle, call **WriteConsole**.</span></span> <span data-ttu-id="42983-137">如果控點不是主控台控點，系統就會將輸出重新導向，而且您應該呼叫 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 來執行 I/O。</span><span class="sxs-lookup"><span data-stu-id="42983-137">If the handle is not a console handle, the output is redirected and you should call [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) to perform the I/O.</span></span> <span data-ttu-id="42983-138">請務必在 Unicode 純文字檔案前面加上位元組順序標記。</span><span class="sxs-lookup"><span data-stu-id="42983-138">Be sure to prefix a Unicode plain text file with a byte order mark.</span></span> <span data-ttu-id="42983-139">如需詳細資訊，請參閱[使用位元組順序標記](https://msdn.microsoft.com/library/windows/desktop/dd374101)。</span><span class="sxs-lookup"><span data-stu-id="42983-139">For more information, see [Using Byte Order Marks](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span></span>

<span data-ttu-id="42983-140">雖然應用程式可以使用 ANSI 模式的 **WriteConsole** 來寫入 ANSI 字元，但除非已啟用「ANSI 逸出」或「虛擬終端機」序列，否則主控台不提供支援。</span><span class="sxs-lookup"><span data-stu-id="42983-140">Although an application can use **WriteConsole** in ANSI mode to write ANSI characters, consoles do not support "ANSI escape" or "virtual terminal" sequences unless enabled.</span></span> <span data-ttu-id="42983-141">如需詳細資訊和作業系統版本適用性，請參閱 [**主控台虛擬終端機序列**](console-virtual-terminal-sequences.md)。</span><span class="sxs-lookup"><span data-stu-id="42983-141">See [**Console Virtual Terminal Sequences**](console-virtual-terminal-sequences.md) for more information and for operating system version applicability.</span></span>

<span data-ttu-id="42983-142">若未啟用當虛擬終端機逸出序列，主控台函式可以提供對等的功能。</span><span class="sxs-lookup"><span data-stu-id="42983-142">When virtual terminal escape sequences are not enabled, console functions can provide equivalent functionality.</span></span> <span data-ttu-id="42983-143">如需詳細資訊，請參閱 [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)、[**SetConsoleTextAttribute**](setconsoletextattribute.md) 和 [**GetConsoleCursorInfo**](getconsolecursorinfo.md)。</span><span class="sxs-lookup"><span data-stu-id="42983-143">For more information, see [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md), and [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="42983-144">規格需求</span><span class="sxs-lookup"><span data-stu-id="42983-144">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="42983-145">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="42983-145">Minimum supported client</span></span> | <span data-ttu-id="42983-146">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="42983-146">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="42983-147">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="42983-147">Minimum supported server</span></span> | <span data-ttu-id="42983-148">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="42983-148">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="42983-149">標頭</span><span class="sxs-lookup"><span data-stu-id="42983-149">Header</span></span> | <span data-ttu-id="42983-150">ConsoleApi.h (透過 WinCon.h，包括 Windows.h)</span><span class="sxs-lookup"><span data-stu-id="42983-150">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="42983-151">程式庫</span><span class="sxs-lookup"><span data-stu-id="42983-151">Library</span></span> | <span data-ttu-id="42983-152">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="42983-152">Kernel32.lib</span></span> |
| <span data-ttu-id="42983-153">DLL</span><span class="sxs-lookup"><span data-stu-id="42983-153">DLL</span></span> | <span data-ttu-id="42983-154">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="42983-154">Kernel32.dll</span></span> |
| <span data-ttu-id="42983-155">Unicode 與 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="42983-155">Unicode and ANSI names</span></span> | <span data-ttu-id="42983-156">**WriteConsoleW** (Unicode) 和 **WriteConsoleA** (ANSI)</span><span class="sxs-lookup"><span data-stu-id="42983-156">**WriteConsoleW** (Unicode) and **WriteConsoleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="42983-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42983-157">See also</span></span>

[<span data-ttu-id="42983-158">主控台函式</span><span class="sxs-lookup"><span data-stu-id="42983-158">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="42983-159">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="42983-159">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="42983-160">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="42983-160">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="42983-161">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="42983-161">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="42983-162">輸入和輸出方法</span><span class="sxs-lookup"><span data-stu-id="42983-162">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="42983-163">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="42983-163">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="42983-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="42983-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="42983-165">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="42983-165">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="42983-166">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="42983-166">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="42983-167">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="42983-167">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="42983-168">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="42983-168">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

<span data-ttu-id="42983-169">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="42983-169">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span></span>

[<span data-ttu-id="42983-170">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="42983-170">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

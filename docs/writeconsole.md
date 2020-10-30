---
title: WriteConsole 函式
description: 從目前的游標位置開始，將字元字串寫入至主控台畫面緩衝區。
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
ms.openlocfilehash: 9023372cf585e9b3645e7dc0a54e46a665935ad4
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037126"
---
# <a name="writeconsole-function"></a><span data-ttu-id="7439d-104">WriteConsole 函式</span><span class="sxs-lookup"><span data-stu-id="7439d-104">WriteConsole function</span></span>

<span data-ttu-id="7439d-105">從目前的游標位置開始，將字元字串寫入至主控台畫面緩衝區。</span><span class="sxs-lookup"><span data-stu-id="7439d-105">Writes a character string to a console screen buffer beginning at the current cursor location.</span></span>

## <a name="syntax"></a><span data-ttu-id="7439d-106">語法</span><span class="sxs-lookup"><span data-stu-id="7439d-106">Syntax</span></span>

```C
BOOL WINAPI WriteConsole(
  _In_             HANDLE  hConsoleOutput,
  _In_       const VOID    *lpBuffer,
  _In_             DWORD   nNumberOfCharsToWrite,
  _Out_opt_        LPDWORD lpNumberOfCharsWritten,
  _Reserved_       LPVOID  lpReserved
);
```

## <a name="parameters"></a><span data-ttu-id="7439d-107">參數</span><span class="sxs-lookup"><span data-stu-id="7439d-107">Parameters</span></span>

<span data-ttu-id="7439d-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="7439d-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="7439d-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="7439d-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="7439d-110">控制碼必須有 **一般 \_ 寫入** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="7439d-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="7439d-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="7439d-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="7439d-112">*lpBuffer* \[在\]</span><span class="sxs-lookup"><span data-stu-id="7439d-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="7439d-113">包含要寫入主控台螢幕緩衝區之字元的緩衝區指標。</span><span class="sxs-lookup"><span data-stu-id="7439d-113">A pointer to a buffer that contains characters to be written to the console screen buffer.</span></span> <span data-ttu-id="7439d-114">這應該是的 `char` `WriteConsoleA` 或 `wchar_t` 的陣列 `WriteConsoleW` 。</span><span class="sxs-lookup"><span data-stu-id="7439d-114">This is expected to be an array of either `char` for `WriteConsoleA` or `wchar_t` for `WriteConsoleW`.</span></span>

<span data-ttu-id="7439d-115">*nNumberOfCharsToWrite* \[在\]</span><span class="sxs-lookup"><span data-stu-id="7439d-115">*nNumberOfCharsToWrite* \[in\]</span></span>  
<span data-ttu-id="7439d-116">要寫入的字元數。</span><span class="sxs-lookup"><span data-stu-id="7439d-116">The number of characters to be written.</span></span> <span data-ttu-id="7439d-117">如果指定字元數的總大小超過可用的堆積，則函式會失敗，並出現 **錯誤， \_ \_ \_ 記憶體不足** 。</span><span class="sxs-lookup"><span data-stu-id="7439d-117">If the total size of the specified number of characters exceeds the available heap, the function fails with **ERROR\_NOT\_ENOUGH\_MEMORY** .</span></span>

<span data-ttu-id="7439d-118">*lpNumberOfCharsWritten* \[out、optional\]</span><span class="sxs-lookup"><span data-stu-id="7439d-118">*lpNumberOfCharsWritten* \[out, optional\]</span></span>  
<span data-ttu-id="7439d-119">變數的指標，此變數會接收實際寫入的字元數。</span><span class="sxs-lookup"><span data-stu-id="7439d-119">A pointer to a variable that receives the number of characters actually written.</span></span>

<span data-ttu-id="7439d-120">*lpReserved* 保護必須是 **Null** 。</span><span class="sxs-lookup"><span data-stu-id="7439d-120">*lpReserved* Reserved; must be **NULL** .</span></span>

## <a name="return-value"></a><span data-ttu-id="7439d-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="7439d-121">Return value</span></span>

<span data-ttu-id="7439d-122">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="7439d-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="7439d-123">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="7439d-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="7439d-124">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="7439d-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="7439d-125">備註</span><span class="sxs-lookup"><span data-stu-id="7439d-125">Remarks</span></span>

<span data-ttu-id="7439d-126">**WriteConsole** 函式會在目前游標位置的主控台螢幕緩衝區寫入字元。</span><span class="sxs-lookup"><span data-stu-id="7439d-126">The **WriteConsole** function writes characters to the console screen buffer at the current cursor position.</span></span> <span data-ttu-id="7439d-127">資料指標位置會隨著寫入字元而前進。</span><span class="sxs-lookup"><span data-stu-id="7439d-127">The cursor position advances as characters are written.</span></span> <span data-ttu-id="7439d-128">[**SetConsoleCursorPosition**](setconsolecursorposition.md)函式會設定目前的游標位置。</span><span class="sxs-lookup"><span data-stu-id="7439d-128">The [**SetConsoleCursorPosition**](setconsolecursorposition.md) function sets the current cursor position.</span></span>

<span data-ttu-id="7439d-129">字元是使用與主控台螢幕緩衝區相關聯的前景和背景色彩屬性來撰寫。</span><span class="sxs-lookup"><span data-stu-id="7439d-129">Characters are written using the foreground and background color attributes associated with the console screen buffer.</span></span> <span data-ttu-id="7439d-130">[**SetConsoleTextAttribute**](setconsoletextattribute.md)函式會變更這些色彩。</span><span class="sxs-lookup"><span data-stu-id="7439d-130">The [**SetConsoleTextAttribute**](setconsoletextattribute.md) function changes these colors.</span></span> <span data-ttu-id="7439d-131">若要判斷目前的色彩屬性和目前的資料指標位置，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)。</span><span class="sxs-lookup"><span data-stu-id="7439d-131">To determine the current color attributes and the current cursor position, use [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md).</span></span>

<span data-ttu-id="7439d-132">所有影響 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 函式行為的輸入模式在 **WriteConsole** 上都有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="7439d-132">All of the input modes that affect the behavior of the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) function have the same effect on **WriteConsole** .</span></span> <span data-ttu-id="7439d-133">若要取出和設定主控台螢幕緩衝區的輸出模式，請使用 [**GetConsoleMode**](getconsolemode.md) 和 [**SetConsoleMode**](setconsolemode.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="7439d-133">To retrieve and set the output modes of a console screen buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

<span data-ttu-id="7439d-134">如果搭配重新導向至檔案的標準控制碼使用， **WriteConsole** 就會失敗。</span><span class="sxs-lookup"><span data-stu-id="7439d-134">**WriteConsole** fails if it is used with a standard handle that is redirected to a file.</span></span> <span data-ttu-id="7439d-135">如果應用程式處理可重新導向的多語系輸出，請判斷輸出控制碼是否為主控台控制碼 (其中一種方法是呼叫 [**GetConsoleMode**](getconsolemode.md) 函式，並檢查它是否成功) 。</span><span class="sxs-lookup"><span data-stu-id="7439d-135">If an application processes multilingual output that can be redirected, determine whether the output handle is a console handle (one method is to call the [**GetConsoleMode**](getconsolemode.md) function and check whether it succeeds).</span></span> <span data-ttu-id="7439d-136">如果控制碼是主控台控制碼，請呼叫 **WriteConsole** 。</span><span class="sxs-lookup"><span data-stu-id="7439d-136">If the handle is a console handle, call **WriteConsole** .</span></span> <span data-ttu-id="7439d-137">如果控制碼不是主控台控制碼，系統就會將輸出重新導向，而您應該呼叫 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 來執行 i/o。</span><span class="sxs-lookup"><span data-stu-id="7439d-137">If the handle is not a console handle, the output is redirected and you should call [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) to perform the I/O.</span></span> <span data-ttu-id="7439d-138">請務必在 Unicode 純文字檔前面加上位元組順序標記。</span><span class="sxs-lookup"><span data-stu-id="7439d-138">Be sure to prefix a Unicode plain text file with a byte order mark.</span></span> <span data-ttu-id="7439d-139">如需詳細資訊，請參閱 [使用位元組順序標記](https://msdn.microsoft.com/library/windows/desktop/dd374101)。</span><span class="sxs-lookup"><span data-stu-id="7439d-139">For more information, see [Using Byte Order Marks](https://msdn.microsoft.com/library/windows/desktop/dd374101).</span></span>

<span data-ttu-id="7439d-140">雖然應用程式可以使用 ANSI 模式的 **WriteConsole** 來撰寫 ansi 字元，但除非已啟用，否則主控台不支援「ansi escape」或「虛擬終端機」序列。</span><span class="sxs-lookup"><span data-stu-id="7439d-140">Although an application can use **WriteConsole** in ANSI mode to write ANSI characters, consoles do not support "ANSI escape" or "virtual terminal" sequences unless enabled.</span></span> <span data-ttu-id="7439d-141">如需詳細資訊及作業系統版本適用性，請參閱 [**主控台虛擬終端機序列**](console-virtual-terminal-sequences.md) 。</span><span class="sxs-lookup"><span data-stu-id="7439d-141">See [**Console Virtual Terminal Sequences**](console-virtual-terminal-sequences.md) for more information and for operating system version applicability.</span></span>

<span data-ttu-id="7439d-142">當虛擬終端機 escape 序列未啟用時，主控台功能可以提供對等的功能。</span><span class="sxs-lookup"><span data-stu-id="7439d-142">When virtual terminal escape sequences are not enabled, console functions can provide equivalent functionality.</span></span> <span data-ttu-id="7439d-143">如需詳細資訊，請參閱 [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)、 [**SetConsoleTextAttribute**](setconsoletextattribute.md)和 [**GetConsoleCursorInfo**](getconsolecursorinfo.md)。</span><span class="sxs-lookup"><span data-stu-id="7439d-143">For more information, see [**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx), [**SetConsoleTextAttribute**](setconsoletextattribute.md), and [**GetConsoleCursorInfo**](getconsolecursorinfo.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="7439d-144">規格需求</span><span class="sxs-lookup"><span data-stu-id="7439d-144">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="7439d-145">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="7439d-145">Minimum supported client</span></span> | <span data-ttu-id="7439d-146">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="7439d-146">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="7439d-147">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="7439d-147">Minimum supported server</span></span> | <span data-ttu-id="7439d-148">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="7439d-148">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="7439d-149">標頭</span><span class="sxs-lookup"><span data-stu-id="7439d-149">Header</span></span> | <span data-ttu-id="7439d-150">ConsoleApi .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="7439d-150">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="7439d-151">程式庫</span><span class="sxs-lookup"><span data-stu-id="7439d-151">Library</span></span> | <span data-ttu-id="7439d-152">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="7439d-152">Kernel32.lib</span></span> |
| <span data-ttu-id="7439d-153">DLL</span><span class="sxs-lookup"><span data-stu-id="7439d-153">DLL</span></span> | <span data-ttu-id="7439d-154">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7439d-154">Kernel32.dll</span></span> |
| <span data-ttu-id="7439d-155">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="7439d-155">Unicode and ANSI names</span></span> | <span data-ttu-id="7439d-156">**WriteConsoleW** (Unicode) 和 **WriteConsoleA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="7439d-156">**WriteConsoleW** (Unicode) and **WriteConsoleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="7439d-157">請參閱</span><span class="sxs-lookup"><span data-stu-id="7439d-157">See also</span></span>

[<span data-ttu-id="7439d-158">主控台功能</span><span class="sxs-lookup"><span data-stu-id="7439d-158">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="7439d-159">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="7439d-159">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="7439d-160">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="7439d-160">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="7439d-161">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="7439d-161">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="7439d-162">輸入和輸出方法</span><span class="sxs-lookup"><span data-stu-id="7439d-162">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="7439d-163">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="7439d-163">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="7439d-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="7439d-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="7439d-165">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="7439d-165">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="7439d-166">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="7439d-166">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="7439d-167">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="7439d-167">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="7439d-168">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="7439d-168">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

<span data-ttu-id="7439d-169">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span><span class="sxs-lookup"><span data-stu-id="7439d-169">[**SetCursorPos**](https://msdn.microsoft.com/library/windows/desktop/ms648394(v=vs.85).aspx)</span></span>

[<span data-ttu-id="7439d-170">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="7439d-170">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

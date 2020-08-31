---
title: ReadConsole 函式
description: 從主控台輸入緩衝區讀取字元輸入，並將它從緩衝區中移除。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi/ReadConsole
- wincon/ReadConsole
- ReadConsole
- consoleapi/ReadConsoleA
- wincon/ReadConsoleA
- ReadConsoleA
- consoleapi/ReadConsoleW
- wincon/ReadConsoleW
- ReadConsoleW
MS-HAID:
- '\_win32\_readconsole'
- base.readconsole
- consoles.readconsole
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 1aa9ecac-a9b9-4e6d-9206-7a57013de657
topic_type:
- apiref
api_name:
- ReadConsole
- ReadConsoleA
- ReadConsoleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 16287bec8e690e5d70483d6e6055e6badaca40ce
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059058"
---
# <a name="readconsole-function"></a><span data-ttu-id="ca677-104">ReadConsole 函式</span><span class="sxs-lookup"><span data-stu-id="ca677-104">ReadConsole function</span></span>


<span data-ttu-id="ca677-105">從主控台輸入緩衝區讀取字元輸入，並將它從緩衝區中移除。</span><span class="sxs-lookup"><span data-stu-id="ca677-105">Reads character input from the console input buffer and removes it from the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="ca677-106">語法</span><span class="sxs-lookup"><span data-stu-id="ca677-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

<a name="parameters"></a><span data-ttu-id="ca677-107">參數</span><span class="sxs-lookup"><span data-stu-id="ca677-107">Parameters</span></span>
----------

<span data-ttu-id="ca677-108">*hConsoleInput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="ca677-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="ca677-109">主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="ca677-109">A handle to the console input buffer.</span></span> <span data-ttu-id="ca677-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="ca677-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="ca677-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="ca677-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="ca677-112">*lpBuffer* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="ca677-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="ca677-113">緩衝區的指標，此緩衝區會接收從主控台輸入緩衝區讀取的資料。</span><span class="sxs-lookup"><span data-stu-id="ca677-113">A pointer to a buffer that receives the data read from the console input buffer.</span></span>

<span data-ttu-id="ca677-114">*nNumberOfCharsToRead* \[在\]</span><span class="sxs-lookup"><span data-stu-id="ca677-114">*nNumberOfCharsToRead* \[in\]</span></span>  
<span data-ttu-id="ca677-115">要讀取的字元數。</span><span class="sxs-lookup"><span data-stu-id="ca677-115">The number of characters to be read.</span></span> <span data-ttu-id="ca677-116">*LpBuffer*參數所指向的緩衝區大小應該至少是 `nNumberOfCharsToRead * sizeof(TCHAR)` 位元組。</span><span class="sxs-lookup"><span data-stu-id="ca677-116">The size of the buffer pointed to by the *lpBuffer* parameter should be at least `nNumberOfCharsToRead * sizeof(TCHAR)` bytes.</span></span>

<span data-ttu-id="ca677-117">*lpNumberOfCharsRead* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="ca677-117">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="ca677-118">變數的指標，此變數會接收實際讀取的字元數。</span><span class="sxs-lookup"><span data-stu-id="ca677-118">A pointer to a variable that receives the number of characters actually read.</span></span>

<span data-ttu-id="ca677-119">*pInputControl* \[在中，選擇性\]</span><span class="sxs-lookup"><span data-stu-id="ca677-119">*pInputControl* \[in, optional\]</span></span>  
<span data-ttu-id="ca677-120">[**主控台 \_ READCONSOLE \_ 控制項**](console-readconsole-control.md)結構的指標，指定控制字元以表示讀取作業結束。</span><span class="sxs-lookup"><span data-stu-id="ca677-120">A pointer to a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure that specifies a control character to signal the end of the read operation.</span></span> <span data-ttu-id="ca677-121">這個參數可以是 **Null**。</span><span class="sxs-lookup"><span data-stu-id="ca677-121">This parameter can be **NULL**.</span></span>

<span data-ttu-id="ca677-122">此參數預設需要 Unicode 輸入。</span><span class="sxs-lookup"><span data-stu-id="ca677-122">This parameter requires Unicode input by default.</span></span> <span data-ttu-id="ca677-123">若為 ANSI 模式，請將此參數設定為 **Null**。</span><span class="sxs-lookup"><span data-stu-id="ca677-123">For ANSI mode, set this parameter to **NULL**.</span></span>

<a name="return-value"></a><span data-ttu-id="ca677-124">傳回值</span><span class="sxs-lookup"><span data-stu-id="ca677-124">Return value</span></span>
------------

<span data-ttu-id="ca677-125">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="ca677-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="ca677-126">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="ca677-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="ca677-127">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="ca677-127">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="ca677-128">備註</span><span class="sxs-lookup"><span data-stu-id="ca677-128">Remarks</span></span>
-------

<span data-ttu-id="ca677-129">**ReadConsole** 會從主控台的輸入緩衝區讀取鍵盤輸入。</span><span class="sxs-lookup"><span data-stu-id="ca677-129">**ReadConsole** reads keyboard input from a console's input buffer.</span></span> <span data-ttu-id="ca677-130">它的行為類似于 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 函式，不同之處在于它可以讀取 Unicode (寬字元) 或 ANSI 模式。</span><span class="sxs-lookup"><span data-stu-id="ca677-130">It behaves like the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) function, except that it can read in either Unicode (wide-character) or ANSI mode.</span></span> <span data-ttu-id="ca677-131">若要讓應用程式維持一組與這兩種模式相容的一組來源，請使用 **ReadConsole** 而非 **ReadFile**。</span><span class="sxs-lookup"><span data-stu-id="ca677-131">To have applications that maintain a single set of sources compatible with both modes, use **ReadConsole** rather than **ReadFile**.</span></span> <span data-ttu-id="ca677-132">雖然 **ReadConsole** 只能搭配主控台輸入緩衝區控制碼使用，但是 **ReadFile** 可以搭配其他控制碼使用， (例如檔案或管道) 。</span><span class="sxs-lookup"><span data-stu-id="ca677-132">Although **ReadConsole** can only be used with a console input buffer handle, **ReadFile** can be used with other handles (such as files or pipes).</span></span> <span data-ttu-id="ca677-133">如果搭配已重新導向為主控台控制碼以外的標準控制碼使用， **ReadConsole**就會失敗。</span><span class="sxs-lookup"><span data-stu-id="ca677-133">**ReadConsole** fails if used with a standard handle that has been redirected to be something other than a console handle.</span></span>

<span data-ttu-id="ca677-134">所有影響 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 行為的輸入模式在 **ReadConsole**上都有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="ca677-134">All of the input modes that affect the behavior of [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) have the same effect on **ReadConsole**.</span></span> <span data-ttu-id="ca677-135">若要取得和設定主控台輸入緩衝區的輸入模式，請使用 [**GetConsoleMode**](getconsolemode.md) 和 [**SetConsoleMode**](setconsolemode.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="ca677-135">To retrieve and set the input modes of a console input buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

<span data-ttu-id="ca677-136">如果輸入緩衝區包含鍵盤事件以外的輸入事件 (例如滑鼠事件或視窗大小的事件) ，則會捨棄這些事件。</span><span class="sxs-lookup"><span data-stu-id="ca677-136">If the input buffer contains input events other than keyboard events (such as mouse events or window-resizing events), they are discarded.</span></span> <span data-ttu-id="ca677-137">只有使用 [**ReadConsoleInput**](readconsoleinput.md) 函數才能讀取這些事件。</span><span class="sxs-lookup"><span data-stu-id="ca677-137">Those events can only be read by using the [**ReadConsoleInput**](readconsoleinput.md) function.</span></span>

<span data-ttu-id="ca677-138">此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。</span><span class="sxs-lookup"><span data-stu-id="ca677-138">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="ca677-139">主控台的字碼頁一開始預設為系統的 OEM 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="ca677-139">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="ca677-140">若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 或 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函式，或使用 **chcp** 或 **mode con cp select =** 命令。</span><span class="sxs-lookup"><span data-stu-id="ca677-140">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<span data-ttu-id="ca677-141">*PInputControl*參數可以用來從讀取中啟用中繼假喚醒，以回應[**主控台 \_ READCONSOLE \_ 控制**](console-readconsole-control.md)結構中指定的檔案完成控制字元。</span><span class="sxs-lookup"><span data-stu-id="ca677-141">The *pInputControl* parameter can be used to enable intermediate wakeups from the read in response to a file-completion control character specified in a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure.</span></span> <span data-ttu-id="ca677-142">這項功能需要啟用命令延伸模組、標準輸出控制碼是主控台輸出控制碼，而輸入則是 Unicode。</span><span class="sxs-lookup"><span data-stu-id="ca677-142">This feature requires command extensions to be enabled, the standard output handle to be a console output handle, and input to be Unicode.</span></span>

<span data-ttu-id="ca677-143">**Windows Server 2003 和 WINDOWS XP/2000：** 不支援中繼讀取功能。</span><span class="sxs-lookup"><span data-stu-id="ca677-143">**Windows Server 2003 and Windows XP/2000:** The intermediate read feature is not supported.</span></span>

<a name="requirements"></a><span data-ttu-id="ca677-144">規格需求</span><span class="sxs-lookup"><span data-stu-id="ca677-144">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="ca677-145">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="ca677-145">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="ca677-146">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="ca677-146">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ca677-147">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="ca677-147">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="ca677-148">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="ca677-148">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ca677-149">標頭</span><span class="sxs-lookup"><span data-stu-id="ca677-149">Header</span></span></p></td>
<td><span data-ttu-id="ca677-150">ConsoleApi .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="ca677-150">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ca677-151">程式庫</span><span class="sxs-lookup"><span data-stu-id="ca677-151">Library</span></span></p></td>
<td><span data-ttu-id="ca677-152">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="ca677-152">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="ca677-153">DLL</span><span class="sxs-lookup"><span data-stu-id="ca677-153">DLL</span></span></p></td>
<td><span data-ttu-id="ca677-154">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="ca677-154">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="ca677-155">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="ca677-155">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="ca677-156"><strong>ReadConsoleW</strong> (Unicode) 和 <strong>ReadConsoleA</strong> (ANSI) </span><span class="sxs-lookup"><span data-stu-id="ca677-156"><strong>ReadConsoleW</strong> (Unicode) and <strong>ReadConsoleA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="ca677-157"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca677-157"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="ca677-158">主控台功能</span><span class="sxs-lookup"><span data-stu-id="ca677-158">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="ca677-159">**主控台 \_ READCONSOLE \_ 控制項**</span><span class="sxs-lookup"><span data-stu-id="ca677-159">**CONSOLE\_READCONSOLE\_CONTROL**</span></span>](console-readconsole-control.md)

[<span data-ttu-id="ca677-160">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="ca677-160">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="ca677-161">輸入和輸出方法</span><span class="sxs-lookup"><span data-stu-id="ca677-161">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="ca677-162">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="ca677-162">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="ca677-163">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="ca677-163">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="ca677-164">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="ca677-164">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="ca677-165">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="ca677-165">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="ca677-166">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="ca677-166">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="ca677-167">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="ca677-167">**WriteConsole**</span></span>](writeconsole.md)

 

 





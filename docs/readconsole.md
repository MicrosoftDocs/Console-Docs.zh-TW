---
title: ReadConsole 函式
description: 從主控台輸入緩衝區讀取字元輸入，並將它從緩衝區中移除。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
ms.openlocfilehash: 757d770bc7fea543d15678af5f80f15c17dd0e82
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358278"
---
# <a name="readconsole-function"></a><span data-ttu-id="43d32-104">ReadConsole 函式</span><span class="sxs-lookup"><span data-stu-id="43d32-104">ReadConsole function</span></span>

<span data-ttu-id="43d32-105">從主控台輸入緩衝區讀取字元輸入，並將它從緩衝區中移除。</span><span class="sxs-lookup"><span data-stu-id="43d32-105">Reads character input from the console input buffer and removes it from the buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="43d32-106">語法</span><span class="sxs-lookup"><span data-stu-id="43d32-106">Syntax</span></span>

```C
BOOL WINAPI ReadConsole(
  _In_     HANDLE  hConsoleInput,
  _Out_    LPVOID  lpBuffer,
  _In_     DWORD   nNumberOfCharsToRead,
  _Out_    LPDWORD lpNumberOfCharsRead,
  _In_opt_ LPVOID  pInputControl
);
```

## <a name="parameters"></a><span data-ttu-id="43d32-107">參數</span><span class="sxs-lookup"><span data-stu-id="43d32-107">Parameters</span></span>

<span data-ttu-id="43d32-108">*hConsoleInput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="43d32-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="43d32-109">主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="43d32-109">A handle to the console input buffer.</span></span> <span data-ttu-id="43d32-110">控制代碼必須具有 **GENERIC\_READ** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="43d32-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="43d32-111">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="43d32-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="43d32-112">*lpBuffer* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="43d32-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="43d32-113">緩衝區的指標，此緩衝區會接收從主控台輸入緩衝區讀取的資料。</span><span class="sxs-lookup"><span data-stu-id="43d32-113">A pointer to a buffer that receives the data read from the console input buffer.</span></span>

<span data-ttu-id="43d32-114">*nNumberOfCharsToRead* \[在\]</span><span class="sxs-lookup"><span data-stu-id="43d32-114">*nNumberOfCharsToRead* \[in\]</span></span>  
<span data-ttu-id="43d32-115">要讀取的字元數。</span><span class="sxs-lookup"><span data-stu-id="43d32-115">The number of characters to be read.</span></span> <span data-ttu-id="43d32-116">*LpBuffer* 參數所指向的緩衝區大小應該至少是 `nNumberOfCharsToRead * sizeof(TCHAR)` 位元組。</span><span class="sxs-lookup"><span data-stu-id="43d32-116">The size of the buffer pointed to by the *lpBuffer* parameter should be at least `nNumberOfCharsToRead * sizeof(TCHAR)` bytes.</span></span>

<span data-ttu-id="43d32-117">*lpNumberOfCharsRead* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="43d32-117">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="43d32-118">變數的指標，此變數會接收實際讀取的字元數。</span><span class="sxs-lookup"><span data-stu-id="43d32-118">A pointer to a variable that receives the number of characters actually read.</span></span>

<span data-ttu-id="43d32-119">*pInputControl* \[在中，選擇性\]</span><span class="sxs-lookup"><span data-stu-id="43d32-119">*pInputControl* \[in, optional\]</span></span>  
<span data-ttu-id="43d32-120">[**主控台 \_ READCONSOLE \_ 控制項**](console-readconsole-control.md)結構的指標，指定控制字元以表示讀取作業結束。</span><span class="sxs-lookup"><span data-stu-id="43d32-120">A pointer to a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure that specifies a control character to signal the end of the read operation.</span></span> <span data-ttu-id="43d32-121">此參數可以是 **Null**。</span><span class="sxs-lookup"><span data-stu-id="43d32-121">This parameter can be **NULL**.</span></span>

<span data-ttu-id="43d32-122">此參數預設需要 Unicode 輸入。</span><span class="sxs-lookup"><span data-stu-id="43d32-122">This parameter requires Unicode input by default.</span></span> <span data-ttu-id="43d32-123">若為 ANSI 模式，請將此參數設定為 **Null**。</span><span class="sxs-lookup"><span data-stu-id="43d32-123">For ANSI mode, set this parameter to **NULL**.</span></span>

## <a name="return-value"></a><span data-ttu-id="43d32-124">傳回值</span><span class="sxs-lookup"><span data-stu-id="43d32-124">Return value</span></span>

<span data-ttu-id="43d32-125">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="43d32-125">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="43d32-126">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="43d32-126">If the function fails, the return value is zero.</span></span> <span data-ttu-id="43d32-127">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="43d32-127">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="43d32-128">備註</span><span class="sxs-lookup"><span data-stu-id="43d32-128">Remarks</span></span>

<span data-ttu-id="43d32-129">**ReadConsole** 會從主控台的輸入緩衝區讀取鍵盤輸入。</span><span class="sxs-lookup"><span data-stu-id="43d32-129">**ReadConsole** reads keyboard input from a console's input buffer.</span></span> <span data-ttu-id="43d32-130">它的行為類似于 [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) 函式，不同之處在于它可以讀取 Unicode (寬字元) 或 ANSI 模式。</span><span class="sxs-lookup"><span data-stu-id="43d32-130">It behaves like the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) function, except that it can read in either Unicode (wide-character) or ANSI mode.</span></span> <span data-ttu-id="43d32-131">若要讓應用程式維持一組與這兩種模式相容的一組來源，請使用 **ReadConsole** 而非 **ReadFile**。</span><span class="sxs-lookup"><span data-stu-id="43d32-131">To have applications that maintain a single set of sources compatible with both modes, use **ReadConsole** rather than **ReadFile**.</span></span> <span data-ttu-id="43d32-132">雖然 **ReadConsole** 只能搭配主控台輸入緩衝區控制碼使用，但是 **ReadFile** 可以搭配其他控制碼使用， (例如檔案或管道) 。</span><span class="sxs-lookup"><span data-stu-id="43d32-132">Although **ReadConsole** can only be used with a console input buffer handle, **ReadFile** can be used with other handles (such as files or pipes).</span></span> <span data-ttu-id="43d32-133">如果搭配已重新導向為主控台控制碼以外的標準控制碼使用， **ReadConsole** 就會失敗。</span><span class="sxs-lookup"><span data-stu-id="43d32-133">**ReadConsole** fails if used with a standard handle that has been redirected to be something other than a console handle.</span></span>

<span data-ttu-id="43d32-134">所有影響 [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) 行為的輸入模式在 **ReadConsole** 上都有相同的效果。</span><span class="sxs-lookup"><span data-stu-id="43d32-134">All of the input modes that affect the behavior of [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) have the same effect on **ReadConsole**.</span></span> <span data-ttu-id="43d32-135">若要取得和設定主控台輸入緩衝區的輸入模式，請使用 [**GetConsoleMode**](getconsolemode.md) 和 [**SetConsoleMode**](setconsolemode.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="43d32-135">To retrieve and set the input modes of a console input buffer, use the [**GetConsoleMode**](getconsolemode.md) and [**SetConsoleMode**](setconsolemode.md) functions.</span></span>

<span data-ttu-id="43d32-136">如果輸入緩衝區包含鍵盤事件以外的輸入事件 (例如滑鼠事件或視窗大小的事件) ，則會捨棄這些事件。</span><span class="sxs-lookup"><span data-stu-id="43d32-136">If the input buffer contains input events other than keyboard events (such as mouse events or window-resizing events), they are discarded.</span></span> <span data-ttu-id="43d32-137">只有使用 [**ReadConsoleInput**](readconsoleinput.md) 函數才能讀取這些事件。</span><span class="sxs-lookup"><span data-stu-id="43d32-137">Those events can only be read by using the [**ReadConsoleInput**](readconsoleinput.md) function.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

<span data-ttu-id="43d32-138">*PInputControl* 參數可以用來從讀取中啟用中繼假喚醒，以回應 [**主控台 \_ READCONSOLE \_ 控制**](console-readconsole-control.md)結構中指定的檔案完成控制字元。</span><span class="sxs-lookup"><span data-stu-id="43d32-138">The *pInputControl* parameter can be used to enable intermediate wakeups from the read in response to a file-completion control character specified in a [**CONSOLE\_READCONSOLE\_CONTROL**](console-readconsole-control.md) structure.</span></span> <span data-ttu-id="43d32-139">這項功能需要啟用命令延伸模組、標準輸出控制碼是主控台輸出控制碼，而輸入則是 Unicode。</span><span class="sxs-lookup"><span data-stu-id="43d32-139">This feature requires command extensions to be enabled, the standard output handle to be a console output handle, and input to be Unicode.</span></span>

<span data-ttu-id="43d32-140">**Windows Server 2003 和 WINDOWS XP/2000：** 不支援中繼讀取功能。</span><span class="sxs-lookup"><span data-stu-id="43d32-140">**Windows Server 2003 and Windows XP/2000:** The intermediate read feature is not supported.</span></span>

## <a name="requirements"></a><span data-ttu-id="43d32-141">規格需求</span><span class="sxs-lookup"><span data-stu-id="43d32-141">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="43d32-142">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="43d32-142">Minimum supported client</span></span> | <span data-ttu-id="43d32-143">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="43d32-143">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="43d32-144">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="43d32-144">Minimum supported server</span></span> | <span data-ttu-id="43d32-145">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="43d32-145">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="43d32-146">標頭</span><span class="sxs-lookup"><span data-stu-id="43d32-146">Header</span></span> | <span data-ttu-id="43d32-147">ConsoleApi.h (透過 WinCon.h，包括 Windows.h)</span><span class="sxs-lookup"><span data-stu-id="43d32-147">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="43d32-148">程式庫</span><span class="sxs-lookup"><span data-stu-id="43d32-148">Library</span></span> | <span data-ttu-id="43d32-149">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="43d32-149">Kernel32.lib</span></span> |
| <span data-ttu-id="43d32-150">DLL</span><span class="sxs-lookup"><span data-stu-id="43d32-150">DLL</span></span> | <span data-ttu-id="43d32-151">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="43d32-151">Kernel32.dll</span></span> |
| <span data-ttu-id="43d32-152">Unicode 與 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="43d32-152">Unicode and ANSI names</span></span> | <span data-ttu-id="43d32-153">**ReadConsoleW** (Unicode) 和 **ReadConsoleA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="43d32-153">**ReadConsoleW** (Unicode) and **ReadConsoleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="43d32-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43d32-154">See also</span></span>

[<span data-ttu-id="43d32-155">主控台函式</span><span class="sxs-lookup"><span data-stu-id="43d32-155">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="43d32-156">**主控台 \_ READCONSOLE \_ 控制項**</span><span class="sxs-lookup"><span data-stu-id="43d32-156">**CONSOLE\_READCONSOLE\_CONTROL**</span></span>](console-readconsole-control.md)

[<span data-ttu-id="43d32-157">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="43d32-157">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="43d32-158">輸入和輸出方法</span><span class="sxs-lookup"><span data-stu-id="43d32-158">Input and Output Methods</span></span>](input-and-output-methods.md)

[<span data-ttu-id="43d32-159">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="43d32-159">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="43d32-160">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="43d32-160">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="43d32-161">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="43d32-161">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="43d32-162">**SetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="43d32-162">**SetConsoleMode**</span></span>](setconsolemode.md)

[<span data-ttu-id="43d32-163">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="43d32-163">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="43d32-164">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="43d32-164">**WriteConsole**</span></span>](writeconsole.md)
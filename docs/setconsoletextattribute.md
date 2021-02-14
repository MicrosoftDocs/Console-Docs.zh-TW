---
title: SetConsoleTextAttribute 函式
description: 設定 WriteFile 或 WriteConsole 函式寫入主控台螢幕緩衝區的字元屬性，或由 ReadFile 或 ReadConsole 函式回顯的字元屬性。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleTextAttribute
- wincon/SetConsoleTextAttribute
- SetConsoleTextAttribute
MS-HAID:
- '\_win32\_setconsoletextattribute'
- base.setconsoletextattribute
- consoles.setconsoletextattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9fba5bb5-b999-4abd-ab39-7a63d58b8074
topic_type:
- apiref
api_name:
- SetConsoleTextAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: b08f4b0b628f4d20029b81873b4fc25077a11029
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358558"
---
# <a name="setconsoletextattribute-function"></a><span data-ttu-id="e40a8-104">SetConsoleTextAttribute 函式</span><span class="sxs-lookup"><span data-stu-id="e40a8-104">SetConsoleTextAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e40a8-105">設定 [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) 或 [**WriteConsole**](writeconsole.md) 函式寫入主控台螢幕緩衝區的字元屬性，或由 [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) 或 [**ReadConsole**](readconsole.md) 函式回顯的字元屬性。</span><span class="sxs-lookup"><span data-stu-id="e40a8-105">Sets the attributes of characters written to the console screen buffer by the [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) or [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="e40a8-106">此函式會影響在函式呼叫後寫入的文字。</span><span class="sxs-lookup"><span data-stu-id="e40a8-106">This function affects text written after the function call.</span></span>

## <a name="syntax"></a><span data-ttu-id="e40a8-107">語法</span><span class="sxs-lookup"><span data-stu-id="e40a8-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

## <a name="parameters"></a><span data-ttu-id="e40a8-108">參數</span><span class="sxs-lookup"><span data-stu-id="e40a8-108">Parameters</span></span>

<span data-ttu-id="e40a8-109">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e40a8-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="e40a8-110">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="e40a8-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="e40a8-111">控制代碼必須具有 **GENERIC\_READ** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="e40a8-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="e40a8-112">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="e40a8-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="e40a8-113">*wAttributes* \[在\]</span><span class="sxs-lookup"><span data-stu-id="e40a8-113">*wAttributes* \[in\]</span></span>  
<span data-ttu-id="e40a8-114">[字元屬性](console-screen-buffers.md#character-attributes)。</span><span class="sxs-lookup"><span data-stu-id="e40a8-114">The [character attributes](console-screen-buffers.md#character-attributes).</span></span>

## <a name="return-value"></a><span data-ttu-id="e40a8-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="e40a8-115">Return value</span></span>

<span data-ttu-id="e40a8-116">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="e40a8-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e40a8-117">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="e40a8-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e40a8-118">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="e40a8-118">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="e40a8-119">備註</span><span class="sxs-lookup"><span data-stu-id="e40a8-119">Remarks</span></span>

<span data-ttu-id="e40a8-120">若要判斷螢幕緩衝區目前的色彩屬性，請呼叫 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="e40a8-120">To determine the current color attributes of a screen buffer, call the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

> [!TIP]
> <span data-ttu-id="e40a8-121">此 API 具有等同于 **[文字格式設定](console-virtual-terminal-sequences.md#text-formatting)** 順序的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="e40a8-121">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** sequences.</span></span> <span data-ttu-id="e40a8-122">建議您針對所有新的和進行中的開發，使用 _虛擬終端機序列_。</span><span class="sxs-lookup"><span data-stu-id="e40a8-122">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="e40a8-123">範例</span><span class="sxs-lookup"><span data-stu-id="e40a8-123">Examples</span></span>

<span data-ttu-id="e40a8-124">如需範例，請參閱 [使用 High-Level 輸入和輸出函數](using-the-high-level-input-and-output-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="e40a8-124">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="e40a8-125">規格需求</span><span class="sxs-lookup"><span data-stu-id="e40a8-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e40a8-126">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="e40a8-126">Minimum supported client</span></span> | <span data-ttu-id="e40a8-127">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="e40a8-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="e40a8-128">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="e40a8-128">Minimum supported server</span></span> | <span data-ttu-id="e40a8-129">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="e40a8-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="e40a8-130">標頭</span><span class="sxs-lookup"><span data-stu-id="e40a8-130">Header</span></span> | <span data-ttu-id="e40a8-131">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="e40a8-131">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="e40a8-132">程式庫</span><span class="sxs-lookup"><span data-stu-id="e40a8-132">Library</span></span> | <span data-ttu-id="e40a8-133">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="e40a8-133">Kernel32.lib</span></span> |
| <span data-ttu-id="e40a8-134">DLL</span><span class="sxs-lookup"><span data-stu-id="e40a8-134">DLL</span></span> | <span data-ttu-id="e40a8-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e40a8-135">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="e40a8-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e40a8-136">See also</span></span>

[<span data-ttu-id="e40a8-137">主控台函式</span><span class="sxs-lookup"><span data-stu-id="e40a8-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e40a8-138">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="e40a8-138">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="e40a8-139">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="e40a8-139">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="e40a8-140">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="e40a8-140">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="e40a8-141">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="e40a8-141">**ReadFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-readfile)

[<span data-ttu-id="e40a8-142">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="e40a8-142">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="e40a8-143">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="e40a8-143">**WriteFile**</span></span>](/windows/win32/api/fileapi/nf-fileapi-writefile)
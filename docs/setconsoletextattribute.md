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
ms.openlocfilehash: 03925af2668774a36de33bfe6ea5fcdc1b475d5b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039316"
---
# <a name="setconsoletextattribute-function"></a><span data-ttu-id="cd0f2-104">SetConsoleTextAttribute 函式</span><span class="sxs-lookup"><span data-stu-id="cd0f2-104">SetConsoleTextAttribute function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="cd0f2-105">設定 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 或 [**WriteConsole**](writeconsole.md) 函式寫入主控台螢幕緩衝區的字元屬性，或由 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 或 [**ReadConsole**](readconsole.md) 函式回顯的字元屬性。</span><span class="sxs-lookup"><span data-stu-id="cd0f2-105">Sets the attributes of characters written to the console screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="cd0f2-106">此函式會影響在函式呼叫後寫入的文字。</span><span class="sxs-lookup"><span data-stu-id="cd0f2-106">This function affects text written after the function call.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd0f2-107">語法</span><span class="sxs-lookup"><span data-stu-id="cd0f2-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

## <a name="parameters"></a><span data-ttu-id="cd0f2-108">參數</span><span class="sxs-lookup"><span data-stu-id="cd0f2-108">Parameters</span></span>

<span data-ttu-id="cd0f2-109">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="cd0f2-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="cd0f2-110">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="cd0f2-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="cd0f2-111">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="cd0f2-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="cd0f2-112">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="cd0f2-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="cd0f2-113">*wAttributes* \[在\]</span><span class="sxs-lookup"><span data-stu-id="cd0f2-113">*wAttributes* \[in\]</span></span>  
<span data-ttu-id="cd0f2-114">[字元屬性](console-screen-buffers.md#character-attributes)。</span><span class="sxs-lookup"><span data-stu-id="cd0f2-114">The [character attributes](console-screen-buffers.md#character-attributes).</span></span>

## <a name="return-value"></a><span data-ttu-id="cd0f2-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="cd0f2-115">Return value</span></span>

<span data-ttu-id="cd0f2-116">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="cd0f2-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="cd0f2-117">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="cd0f2-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="cd0f2-118">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="cd0f2-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="cd0f2-119">備註</span><span class="sxs-lookup"><span data-stu-id="cd0f2-119">Remarks</span></span>

<span data-ttu-id="cd0f2-120">若要判斷螢幕緩衝區目前的色彩屬性，請呼叫 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="cd0f2-120">To determine the current color attributes of a screen buffer, call the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

> [!TIP]
> <span data-ttu-id="cd0f2-121">此 API 具有等同于 **[文字格式設定](console-virtual-terminal-sequences.md#text-formatting)** 順序的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="cd0f2-121">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[text formatting](console-virtual-terminal-sequences.md#text-formatting)** sequences.</span></span> <span data-ttu-id="cd0f2-122">建議您針對所有新的和進行中的開發，使用 _虛擬終端機序列_ 。</span><span class="sxs-lookup"><span data-stu-id="cd0f2-122">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="cd0f2-123">範例</span><span class="sxs-lookup"><span data-stu-id="cd0f2-123">Examples</span></span>

<span data-ttu-id="cd0f2-124">如需範例，請參閱 [使用 High-Level 輸入和輸出函數](using-the-high-level-input-and-output-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="cd0f2-124">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="cd0f2-125">規格需求</span><span class="sxs-lookup"><span data-stu-id="cd0f2-125">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="cd0f2-126">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="cd0f2-126">Minimum supported client</span></span> | <span data-ttu-id="cd0f2-127">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="cd0f2-127">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="cd0f2-128">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="cd0f2-128">Minimum supported server</span></span> | <span data-ttu-id="cd0f2-129">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="cd0f2-129">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="cd0f2-130">標頭</span><span class="sxs-lookup"><span data-stu-id="cd0f2-130">Header</span></span> | <span data-ttu-id="cd0f2-131">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="cd0f2-131">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="cd0f2-132">程式庫</span><span class="sxs-lookup"><span data-stu-id="cd0f2-132">Library</span></span> | <span data-ttu-id="cd0f2-133">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="cd0f2-133">Kernel32.lib</span></span> |
| <span data-ttu-id="cd0f2-134">DLL</span><span class="sxs-lookup"><span data-stu-id="cd0f2-134">DLL</span></span> | <span data-ttu-id="cd0f2-135">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="cd0f2-135">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="cd0f2-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="cd0f2-136">See also</span></span>

[<span data-ttu-id="cd0f2-137">主控台功能</span><span class="sxs-lookup"><span data-stu-id="cd0f2-137">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="cd0f2-138">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="cd0f2-138">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="cd0f2-139">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="cd0f2-139">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="cd0f2-140">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="cd0f2-140">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="cd0f2-141">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="cd0f2-141">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="cd0f2-142">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="cd0f2-142">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="cd0f2-143">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="cd0f2-143">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

---
title: SetConsoleCursorPosition 函式
description: 請參閱 SetConsoleCursorPosition 函式的參考資訊，此函式會在指定的主控台螢幕緩衝區中設定游標位置。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleCursorPosition
- wincon/SetConsoleCursorPosition
- SetConsoleCursorPosition
MS-HAID:
- '\_win32\_setconsolecursorposition'
- base.setconsolecursorposition
- consoles.setconsolecursorposition
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8e9abada-a64e-429f-8286-ced1169c7104
topic_type:
- apiref
api_name:
- SetConsoleCursorPosition
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: c93fbf4b619b522a95af2b03a49d60ff6f880e7d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039366"
---
# <a name="setconsolecursorposition-function"></a><span data-ttu-id="b6aa1-104">SetConsoleCursorPosition 函式</span><span class="sxs-lookup"><span data-stu-id="b6aa1-104">SetConsoleCursorPosition function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="b6aa1-105">設定指定的主控台螢幕緩衝區中的游標位置。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-105">Sets the cursor position in the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="b6aa1-106">語法</span><span class="sxs-lookup"><span data-stu-id="b6aa1-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCursorPosition(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwCursorPosition
);
```

## <a name="parameters"></a><span data-ttu-id="b6aa1-107">參數</span><span class="sxs-lookup"><span data-stu-id="b6aa1-107">Parameters</span></span>

<span data-ttu-id="b6aa1-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="b6aa1-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="b6aa1-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="b6aa1-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="b6aa1-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="b6aa1-112">*dwCursorPosition* \[在\]</span><span class="sxs-lookup"><span data-stu-id="b6aa1-112">*dwCursorPosition* \[in\]</span></span>  
<span data-ttu-id="b6aa1-113">指定新資料指標位置的 [**COORD**](coord-str.md) 結構（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-113">A [**COORD**](coord-str.md) structure that specifies the new cursor position, in characters.</span></span> <span data-ttu-id="b6aa1-114">座標是螢幕緩衝區字元資料格的資料行和資料列。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-114">The coordinates are the column and row of a screen buffer character cell.</span></span> <span data-ttu-id="b6aa1-115">座標必須在主控台畫面緩衝區的界限內。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-115">The coordinates must be within the boundaries of the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="b6aa1-116">傳回值</span><span class="sxs-lookup"><span data-stu-id="b6aa1-116">Return value</span></span>

<span data-ttu-id="b6aa1-117">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-117">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b6aa1-118">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-118">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b6aa1-119">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-119">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="b6aa1-120">備註</span><span class="sxs-lookup"><span data-stu-id="b6aa1-120">Remarks</span></span>

<span data-ttu-id="b6aa1-121">資料指標位置會決定 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 或 [**WriteConsole**](writeconsole.md) 函數所寫入的字元，或由 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 或 [**ReadConsole**](readconsole.md) 函式所回應的位置。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-121">The cursor position determines where characters written by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function, are displayed.</span></span> <span data-ttu-id="b6aa1-122">若要判斷資料指標目前的位置，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-122">To determine the current position of the cursor, use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<span data-ttu-id="b6aa1-123">如果新的資料指標位置不在主控台畫面緩衝區視窗的界限內，則視窗來源會變更，使游標變成可見。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-123">If the new cursor position is not within the boundaries of the console screen buffer's window, the window origin changes to make the cursor visible.</span></span>

> [!TIP]
> <span data-ttu-id="b6aa1-124">此 API 在 **[簡單資料指標定位](console-virtual-terminal-sequences.md#simple-cursor-positioning)** 和資料 **[指標定位](console-virtual-terminal-sequences.md#cursor-positioning)** 區段中，有相當的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-124">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[simple cursor positioning](console-virtual-terminal-sequences.md#simple-cursor-positioning)** and **[cursor positioning](console-virtual-terminal-sequences.md#cursor-positioning)** sections.</span></span> <span data-ttu-id="b6aa1-125">使用「換行」、「換行」、「倒退鍵」和「索引標籤控制項」序列也可以協助資料指標的定位。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-125">Use of the newline, carriage return, backspace, and tab control sequences can also assist with cursor positioning.</span></span>

## <a name="examples"></a><span data-ttu-id="b6aa1-126">範例</span><span class="sxs-lookup"><span data-stu-id="b6aa1-126">Examples</span></span>

<span data-ttu-id="b6aa1-127">如需範例，請參閱 [使用 High-Level 輸入和輸出函數](using-the-high-level-input-and-output-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="b6aa1-127">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="b6aa1-128">規格需求</span><span class="sxs-lookup"><span data-stu-id="b6aa1-128">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b6aa1-129">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="b6aa1-129">Minimum supported client</span></span> | <span data-ttu-id="b6aa1-130">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="b6aa1-130">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="b6aa1-131">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="b6aa1-131">Minimum supported server</span></span> | <span data-ttu-id="b6aa1-132">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="b6aa1-132">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="b6aa1-133">標頭</span><span class="sxs-lookup"><span data-stu-id="b6aa1-133">Header</span></span> | <span data-ttu-id="b6aa1-134">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="b6aa1-134">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="b6aa1-135">程式庫</span><span class="sxs-lookup"><span data-stu-id="b6aa1-135">Library</span></span> | <span data-ttu-id="b6aa1-136">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="b6aa1-136">Kernel32.lib</span></span> |
| <span data-ttu-id="b6aa1-137">DLL</span><span class="sxs-lookup"><span data-stu-id="b6aa1-137">DLL</span></span> | <span data-ttu-id="b6aa1-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b6aa1-138">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="b6aa1-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="b6aa1-139">See also</span></span>

[<span data-ttu-id="b6aa1-140">主控台功能</span><span class="sxs-lookup"><span data-stu-id="b6aa1-140">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b6aa1-141">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="b6aa1-141">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="b6aa1-142">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="b6aa1-142">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="b6aa1-143">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="b6aa1-143">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="b6aa1-144">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="b6aa1-144">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="b6aa1-145">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="b6aa1-145">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="b6aa1-146">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="b6aa1-146">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

[<span data-ttu-id="b6aa1-147">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="b6aa1-147">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="b6aa1-148">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="b6aa1-148">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

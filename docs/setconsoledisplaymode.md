---
title: SetConsoleDisplayMode 函式
description: 請參閱 SetConsoleDisplayMode 函式的參考資訊，此函式會設定指定的主控台螢幕緩衝區的顯示模式。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/SetConsoleDisplayMode
- wincon/SetConsoleDisplayMode
- SetConsoleDisplayMode
MS-HAID:
- base.setconsoledisplaymode
- consoles.setconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 27437a85-f784-41fc-8279-9fe089b0a744
topic_type:
- apiref
api_name:
- SetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: af61d897269311ccfa9db336083e898f6d75da80
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357698"
---
# <a name="setconsoledisplaymode-function"></a><span data-ttu-id="32f0f-104">SetConsoleDisplayMode 函式</span><span class="sxs-lookup"><span data-stu-id="32f0f-104">SetConsoleDisplayMode function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="32f0f-105">設定指定之主控台螢幕緩衝區的顯示模式。</span><span class="sxs-lookup"><span data-stu-id="32f0f-105">Sets the display mode of the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="32f0f-106">語法</span><span class="sxs-lookup"><span data-stu-id="32f0f-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleDisplayMode(
  _In_      HANDLE hConsoleOutput,
  _In_      DWORD  dwFlags,
  _Out_opt_ PCOORD lpNewScreenBufferDimensions
);
```

## <a name="parameters"></a><span data-ttu-id="32f0f-107">參數</span><span class="sxs-lookup"><span data-stu-id="32f0f-107">Parameters</span></span>

<span data-ttu-id="32f0f-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="32f0f-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="32f0f-109">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="32f0f-109">A handle to the console screen buffer.</span></span>

<span data-ttu-id="32f0f-110">*dwFlags* \[在\]</span><span class="sxs-lookup"><span data-stu-id="32f0f-110">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="32f0f-111">主控台的顯示模式。</span><span class="sxs-lookup"><span data-stu-id="32f0f-111">The display mode of the console.</span></span> <span data-ttu-id="32f0f-112">這個參數可以是下列一或多個值。</span><span class="sxs-lookup"><span data-stu-id="32f0f-112">This parameter can be one or more of the following values.</span></span>

| <span data-ttu-id="32f0f-113">值</span><span class="sxs-lookup"><span data-stu-id="32f0f-113">Value</span></span> | <span data-ttu-id="32f0f-114">意義</span><span class="sxs-lookup"><span data-stu-id="32f0f-114">Meaning</span></span> |
|-|-|
| <span data-ttu-id="32f0f-115">**CONSOLE_FULLSCREEN_MODE** 1</span><span class="sxs-lookup"><span data-stu-id="32f0f-115">**CONSOLE_FULLSCREEN_MODE** 1</span></span> | <span data-ttu-id="32f0f-116">文字會以全螢幕模式顯示。</span><span class="sxs-lookup"><span data-stu-id="32f0f-116">Text is displayed in full-screen mode.</span></span> |
| <span data-ttu-id="32f0f-117">**CONSOLE_WINDOWED_MODE** 2</span><span class="sxs-lookup"><span data-stu-id="32f0f-117">**CONSOLE_WINDOWED_MODE** 2</span></span> | <span data-ttu-id="32f0f-118">文字會顯示在主控台視窗中。</span><span class="sxs-lookup"><span data-stu-id="32f0f-118">Text is displayed in a console window.</span></span> |

<span data-ttu-id="32f0f-119">*lpNewScreenBufferDimensions* \[out、optional\]</span><span class="sxs-lookup"><span data-stu-id="32f0f-119">*lpNewScreenBufferDimensions* \[out, optional\]</span></span>  
<span data-ttu-id="32f0f-120">[**COORD**](coord-str.md)結構的指標，此結構會接收螢幕緩衝區的新維度（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="32f0f-120">A pointer to a [**COORD**](coord-str.md) structure that receives the new dimensions of the screen buffer, in characters.</span></span>

## <a name="return-value"></a><span data-ttu-id="32f0f-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="32f0f-121">Return value</span></span>

<span data-ttu-id="32f0f-122">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="32f0f-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="32f0f-123">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="32f0f-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="32f0f-124">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="32f0f-124">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="32f0f-125">備註</span><span class="sxs-lookup"><span data-stu-id="32f0f-125">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="32f0f-126">規格需求</span><span class="sxs-lookup"><span data-stu-id="32f0f-126">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="32f0f-127">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="32f0f-127">Minimum supported client</span></span> | <span data-ttu-id="32f0f-128">\[僅限 WINDOWS XP desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="32f0f-128">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="32f0f-129">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="32f0f-129">Minimum supported server</span></span> | <span data-ttu-id="32f0f-130">僅限 Windows Server 2003 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="32f0f-130">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="32f0f-131">標頭</span><span class="sxs-lookup"><span data-stu-id="32f0f-131">Header</span></span> | <span data-ttu-id="32f0f-132">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="32f0f-132">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="32f0f-133">程式庫</span><span class="sxs-lookup"><span data-stu-id="32f0f-133">Library</span></span> | <span data-ttu-id="32f0f-134">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="32f0f-134">Kernel32.lib</span></span> |
| <span data-ttu-id="32f0f-135">DLL</span><span class="sxs-lookup"><span data-stu-id="32f0f-135">DLL</span></span> | <span data-ttu-id="32f0f-136">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="32f0f-136">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="32f0f-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32f0f-137">See also</span></span>

[<span data-ttu-id="32f0f-138">主控台函式</span><span class="sxs-lookup"><span data-stu-id="32f0f-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="32f0f-139">主控台模式</span><span class="sxs-lookup"><span data-stu-id="32f0f-139">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="32f0f-140">**GetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="32f0f-140">**GetConsoleDisplayMode**</span></span>](getconsoledisplaymode.md)
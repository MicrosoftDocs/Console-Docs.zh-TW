---
title: GetConsoleDisplayMode 函式
description: 請參閱 GetConsoleDisplayMode 函式的參考資訊，此函數會抓取目前主控台的顯示模式。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetConsoleDisplayMode
- wincon/GetConsoleDisplayMode
- GetConsoleDisplayMode
MS-HAID:
- '\_win32\_getconsoledisplaymode'
- base.getconsoledisplaymode
- consoles.getconsoledisplaymode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e19ff900-a671-41d3-a9c8-9e4507c47eff
topic_type:
- apiref
api_name:
- GetConsoleDisplayMode
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 5b9ec78dc6fe5d7baa1a9af64010fd577f101c47
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358348"
---
# <a name="getconsoledisplaymode-function"></a><span data-ttu-id="e410f-104">GetConsoleDisplayMode 函式</span><span class="sxs-lookup"><span data-stu-id="e410f-104">GetConsoleDisplayMode function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="e410f-105">抓取目前主控台的顯示模式。</span><span class="sxs-lookup"><span data-stu-id="e410f-105">Retrieves the display mode of the current console.</span></span>

## <a name="syntax"></a><span data-ttu-id="e410f-106">語法</span><span class="sxs-lookup"><span data-stu-id="e410f-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleDisplayMode(
  _Out_ LPDWORD lpModeFlags
);
```

## <a name="parameters"></a><span data-ttu-id="e410f-107">參數</span><span class="sxs-lookup"><span data-stu-id="e410f-107">Parameters</span></span>

<span data-ttu-id="e410f-108">*lpModeFlags* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="e410f-108">*lpModeFlags* \[out\]</span></span>  
<span data-ttu-id="e410f-109">主控台的顯示模式。</span><span class="sxs-lookup"><span data-stu-id="e410f-109">The display mode of the console.</span></span> <span data-ttu-id="e410f-110">這個參數可以是下列一或多個值。</span><span class="sxs-lookup"><span data-stu-id="e410f-110">This parameter can be one or more of the following values.</span></span>

| <span data-ttu-id="e410f-111">值</span><span class="sxs-lookup"><span data-stu-id="e410f-111">Value</span></span> | <span data-ttu-id="e410f-112">意義</span><span class="sxs-lookup"><span data-stu-id="e410f-112">Meaning</span></span> |
|-|-|
| <span data-ttu-id="e410f-113">**CONSOLE_FULLSCREEN** 1</span><span class="sxs-lookup"><span data-stu-id="e410f-113">**CONSOLE_FULLSCREEN** 1</span></span> | <span data-ttu-id="e410f-114">全螢幕主控台。</span><span class="sxs-lookup"><span data-stu-id="e410f-114">Full-screen console.</span></span> <span data-ttu-id="e410f-115">當視窗最大化時，主控台便會處於此模式。</span><span class="sxs-lookup"><span data-stu-id="e410f-115">The console is in this mode as soon as the window is maximized.</span></span> <span data-ttu-id="e410f-116">到目前為止，轉換成全螢幕模式仍然可能失敗。</span><span class="sxs-lookup"><span data-stu-id="e410f-116">At this point, the transition to full-screen mode can still fail.</span></span> |
| <span data-ttu-id="e410f-117">**CONSOLE_FULLSCREEN_HARDWARE** 2</span><span class="sxs-lookup"><span data-stu-id="e410f-117">**CONSOLE_FULLSCREEN_HARDWARE** 2</span></span> | <span data-ttu-id="e410f-118">全螢幕主控台會直接與影片硬體通訊。</span><span class="sxs-lookup"><span data-stu-id="e410f-118">Full-screen console communicating directly with the video hardware.</span></span> <span data-ttu-id="e410f-119">主控台處於 **CONSOLE_FULLSCREEN** 模式之後，就會設定此模式，以指出已完成轉換至全螢幕模式。</span><span class="sxs-lookup"><span data-stu-id="e410f-119">This mode is set after the console is in **CONSOLE_FULLSCREEN** mode to indicate that the transition to full-screen mode has completed.</span></span> |

> [!NOTE]
> <span data-ttu-id="e410f-120">在 Windows Vista 中，已將遷移圖形堆疊的轉換成100% 的全螢幕影片硬體模式，並將其轉換成 [WDDM](//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model)。</span><span class="sxs-lookup"><span data-stu-id="e410f-120">The transition to a 100% full screen video hardware mode was removed in Windows Vista with the replatforming of the graphics stack to [WDDM](//windows-hardware/drivers/display/introduction-to-the-windows-vista-and-later-display-driver-model).</span></span> <span data-ttu-id="e410f-121">在較新版本的 Windows 中，產生的最大狀態 **CONSOLE_FULLSCREEN** 代表 frameless 視窗，該視窗會顯示為全螢幕，但無法獨佔控制硬體。</span><span class="sxs-lookup"><span data-stu-id="e410f-121">On later versions of Windows, the maximum resulting state is **CONSOLE_FULLSCREEN** representing a frameless window that appears full screen but isn't in exclusive control of the hardware.</span></span>

## <a name="return-value"></a><span data-ttu-id="e410f-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="e410f-122">Return value</span></span>

<span data-ttu-id="e410f-123">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="e410f-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e410f-124">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="e410f-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e410f-125">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="e410f-125">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="e410f-126">備註</span><span class="sxs-lookup"><span data-stu-id="e410f-126">Remarks</span></span>

<span data-ttu-id="e410f-127">若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0500 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="e410f-127">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="e410f-128">如需詳細資訊，請參閱 [使用 Windows 標頭](/windows/win32/winprog/using-the-windows-headers)。</span><span class="sxs-lookup"><span data-stu-id="e410f-128">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="e410f-129">規格需求</span><span class="sxs-lookup"><span data-stu-id="e410f-129">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="e410f-130">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="e410f-130">Minimum supported client</span></span> | <span data-ttu-id="e410f-131">\[僅限 WINDOWS XP desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="e410f-131">Windows XP \[desktop apps only\]</span></span> |
| <span data-ttu-id="e410f-132">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="e410f-132">Minimum supported server</span></span> | <span data-ttu-id="e410f-133">僅限 Windows Server 2003 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="e410f-133">Windows Server 2003 \[desktop apps only\]</span></span> |
| <span data-ttu-id="e410f-134">標頭</span><span class="sxs-lookup"><span data-stu-id="e410f-134">Header</span></span> | <span data-ttu-id="e410f-135">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="e410f-135">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="e410f-136">程式庫</span><span class="sxs-lookup"><span data-stu-id="e410f-136">Library</span></span> | <span data-ttu-id="e410f-137">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="e410f-137">Kernel32.lib</span></span> |
| <span data-ttu-id="e410f-138">DLL</span><span class="sxs-lookup"><span data-stu-id="e410f-138">DLL</span></span> | <span data-ttu-id="e410f-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e410f-139">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="e410f-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e410f-140">See also</span></span>

[<span data-ttu-id="e410f-141">主控台函式</span><span class="sxs-lookup"><span data-stu-id="e410f-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e410f-142">主控台模式</span><span class="sxs-lookup"><span data-stu-id="e410f-142">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="e410f-143">**SetConsoleDisplayMode**</span><span class="sxs-lookup"><span data-stu-id="e410f-143">**SetConsoleDisplayMode**</span></span>](setconsoledisplaymode.md)
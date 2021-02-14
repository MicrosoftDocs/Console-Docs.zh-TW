---
title: SetConsoleCursorInfo 函式
description: 為指定的主控台螢幕緩衝區設定資料指標的大小和可見度。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleCursorInfo
- wincon/SetConsoleCursorInfo
- SetConsoleCursorInfo
MS-HAID:
- '\_win32\_setconsolecursorinfo'
- base.setconsolecursorinfo
- consoles.setconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c98cbffb-18de-41e8-bba7-5fb46a0c5d25
topic_type:
- apiref
api_name:
- SetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 565ed3bda8bd864fb52aac0106f01cee96eb78ba
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357688"
---
# <a name="setconsolecursorinfo-function"></a><span data-ttu-id="0ed72-104">SetConsoleCursorInfo 函式</span><span class="sxs-lookup"><span data-stu-id="0ed72-104">SetConsoleCursorInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="0ed72-105">為指定的主控台螢幕緩衝區設定資料指標的大小和可見度。</span><span class="sxs-lookup"><span data-stu-id="0ed72-105">Sets the size and visibility of the cursor for the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="0ed72-106">語法</span><span class="sxs-lookup"><span data-stu-id="0ed72-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleCursorInfo(
  _In_       HANDLE              hConsoleOutput,
  _In_ const CONSOLE_CURSOR_INFO *lpConsoleCursorInfo
);
```

## <a name="parameters"></a><span data-ttu-id="0ed72-107">參數</span><span class="sxs-lookup"><span data-stu-id="0ed72-107">Parameters</span></span>

<span data-ttu-id="0ed72-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="0ed72-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="0ed72-109">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="0ed72-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="0ed72-110">控制代碼必須具有 **GENERIC\_READ** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="0ed72-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="0ed72-111">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="0ed72-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="0ed72-112">*lpConsoleCursorInfo* \[在\]</span><span class="sxs-lookup"><span data-stu-id="0ed72-112">*lpConsoleCursorInfo* \[in\]</span></span>  
<span data-ttu-id="0ed72-113">主控台資料指標 [**\_ \_ 資訊**](console-cursor-info-str.md) 結構的指標，此結構會提供主控台螢幕緩衝區之游標的新規格。</span><span class="sxs-lookup"><span data-stu-id="0ed72-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that provides the new specifications for the console screen buffer's cursor.</span></span>

## <a name="return-value"></a><span data-ttu-id="0ed72-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="0ed72-114">Return value</span></span>

<span data-ttu-id="0ed72-115">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="0ed72-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0ed72-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="0ed72-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0ed72-117">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="0ed72-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="0ed72-118">備註</span><span class="sxs-lookup"><span data-stu-id="0ed72-118">Remarks</span></span>

<span data-ttu-id="0ed72-119">當螢幕緩衝區的游標可見時，其外觀可能會有所不同，範圍從完全填滿字元儲存格到顯示為數據格底部的水平線條。</span><span class="sxs-lookup"><span data-stu-id="0ed72-119">When a screen buffer's cursor is visible, its appearance can vary, ranging from completely filling a character cell to showing up as a horizontal line at the bottom of the cell.</span></span> <span data-ttu-id="0ed72-120">[**主控台資料 \_ 指標 \_ 資訊**](console-cursor-info-str.md)結構的 **dwSize** 成員會指定資料指標所填滿的字元資料格百分比。</span><span class="sxs-lookup"><span data-stu-id="0ed72-120">The **dwSize** member of the [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure specifies the percentage of a character cell that is filled by the cursor.</span></span> <span data-ttu-id="0ed72-121">如果這個成員小於1或大於100， **SetConsoleCursorInfo** 就會失敗。</span><span class="sxs-lookup"><span data-stu-id="0ed72-121">If this member is less than 1 or greater than 100, **SetConsoleCursorInfo** fails.</span></span>

> [!TIP]
> <span data-ttu-id="0ed72-122">此 API 在具有和順序的資料 **[指標可見度](console-virtual-terminal-sequences.md#cursor-visibility)** 區段中具有相當的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機 `^[[?25h` `^[[?25l` 。</span><span class="sxs-lookup"><span data-stu-id="0ed72-122">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[cursor visibility](console-virtual-terminal-sequences.md#cursor-visibility)** section with the `^[[?25h` and `^[[?25l` sequences.</span></span> 

## <a name="requirements"></a><span data-ttu-id="0ed72-123">規格需求</span><span class="sxs-lookup"><span data-stu-id="0ed72-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0ed72-124">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="0ed72-124">Minimum supported client</span></span> | <span data-ttu-id="0ed72-125">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="0ed72-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="0ed72-126">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="0ed72-126">Minimum supported server</span></span> | <span data-ttu-id="0ed72-127">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="0ed72-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="0ed72-128">標頭</span><span class="sxs-lookup"><span data-stu-id="0ed72-128">Header</span></span> | <span data-ttu-id="0ed72-129">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="0ed72-129">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="0ed72-130">程式庫</span><span class="sxs-lookup"><span data-stu-id="0ed72-130">Library</span></span> | <span data-ttu-id="0ed72-131">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="0ed72-131">Kernel32.lib</span></span> |
| <span data-ttu-id="0ed72-132">DLL</span><span class="sxs-lookup"><span data-stu-id="0ed72-132">DLL</span></span> | <span data-ttu-id="0ed72-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0ed72-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="0ed72-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ed72-134">See also</span></span>

[<span data-ttu-id="0ed72-135">主控台函式</span><span class="sxs-lookup"><span data-stu-id="0ed72-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0ed72-136">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="0ed72-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="0ed72-137">**主控台資料 \_ 指標 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="0ed72-137">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="0ed72-138">**GetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="0ed72-138">**GetConsoleCursorInfo**</span></span>](getconsolecursorinfo.md)

[<span data-ttu-id="0ed72-139">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="0ed72-139">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)
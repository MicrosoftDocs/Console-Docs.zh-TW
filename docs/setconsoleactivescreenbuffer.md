---
title: SetConsoleActiveScreenBuffer 函式
description: 將指定的螢幕緩衝區設定為目前顯示的主控台螢幕緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleActiveScreenBuffer
- wincon/SetConsoleActiveScreenBuffer
- SetConsoleActiveScreenBuffer
MS-HAID:
- '\_win32\_setconsoleactivescreenbuffer'
- base.setconsoleactivescreenbuffer
- consoles.setconsoleactivescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c026cb94-c8ec-44ee-b432-3870ae3006c2
topic_type:
- apiref
api_name:
- SetConsoleActiveScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 72545409bfff6485a4e454d9a004f7f9fa0161e3
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357748"
---
# <a name="setconsoleactivescreenbuffer-function"></a><span data-ttu-id="b7082-104">SetConsoleActiveScreenBuffer 函式</span><span class="sxs-lookup"><span data-stu-id="b7082-104">SetConsoleActiveScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="b7082-105">將指定的螢幕緩衝區設定為目前顯示的主控台螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b7082-105">Sets the specified screen buffer to be the currently displayed console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="b7082-106">語法</span><span class="sxs-lookup"><span data-stu-id="b7082-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleActiveScreenBuffer(
  _In_ HANDLE hConsoleOutput
);
```

## <a name="parameters"></a><span data-ttu-id="b7082-107">參數</span><span class="sxs-lookup"><span data-stu-id="b7082-107">Parameters</span></span>

<span data-ttu-id="b7082-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b7082-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="b7082-109">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="b7082-109">A handle to the console screen buffer.</span></span>

## <a name="return-value"></a><span data-ttu-id="b7082-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="b7082-110">Return value</span></span>

<span data-ttu-id="b7082-111">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="b7082-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="b7082-112">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="b7082-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="b7082-113">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="b7082-113">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="b7082-114">備註</span><span class="sxs-lookup"><span data-stu-id="b7082-114">Remarks</span></span>

<span data-ttu-id="b7082-115">主控台可以有多個畫面緩衝區。</span><span class="sxs-lookup"><span data-stu-id="b7082-115">A console can have multiple screen buffers.</span></span> <span data-ttu-id="b7082-116">**SetConsoleActiveScreenBuffer** 會決定要顯示哪一個。</span><span class="sxs-lookup"><span data-stu-id="b7082-116">**SetConsoleActiveScreenBuffer** determines which one is displayed.</span></span> <span data-ttu-id="b7082-117">您可以寫入非使用中的螢幕緩衝區，然後使用 **SetConsoleActiveScreenBuffer** 來顯示緩衝區的內容。</span><span class="sxs-lookup"><span data-stu-id="b7082-117">You can write to an inactive screen buffer and then use **SetConsoleActiveScreenBuffer** to display the buffer's contents.</span></span>

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a><span data-ttu-id="b7082-118">範例</span><span class="sxs-lookup"><span data-stu-id="b7082-118">Examples</span></span>

<span data-ttu-id="b7082-119">如需範例，請參閱 [讀取和寫入字元和屬性的區塊](reading-and-writing-blocks-of-characters-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="b7082-119">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="b7082-120">規格需求</span><span class="sxs-lookup"><span data-stu-id="b7082-120">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="b7082-121">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="b7082-121">Minimum supported client</span></span> | <span data-ttu-id="b7082-122">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="b7082-122">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="b7082-123">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="b7082-123">Minimum supported server</span></span> | <span data-ttu-id="b7082-124">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="b7082-124">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="b7082-125">標頭</span><span class="sxs-lookup"><span data-stu-id="b7082-125">Header</span></span> | <span data-ttu-id="b7082-126">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="b7082-126">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="b7082-127">程式庫</span><span class="sxs-lookup"><span data-stu-id="b7082-127">Library</span></span> | <span data-ttu-id="b7082-128">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="b7082-128">Kernel32.lib</span></span> |
| <span data-ttu-id="b7082-129">DLL</span><span class="sxs-lookup"><span data-stu-id="b7082-129">DLL</span></span> | <span data-ttu-id="b7082-130">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="b7082-130">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="b7082-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7082-131">See also</span></span>

[<span data-ttu-id="b7082-132">主控台函式</span><span class="sxs-lookup"><span data-stu-id="b7082-132">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="b7082-133">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="b7082-133">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="b7082-134">**CreateConsoleScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="b7082-134">**CreateConsoleScreenBuffer**</span></span>](createconsolescreenbuffer.md)
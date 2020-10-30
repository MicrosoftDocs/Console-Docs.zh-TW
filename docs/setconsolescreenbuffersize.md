---
title: SetConsoleScreenBufferSize 函式
description: 請參閱 SetConsoleScreenBufferSize 函式的參考資訊，此函式會變更指定之主控台螢幕緩衝區的大小。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleScreenBufferSize
- wincon/SetConsoleScreenBufferSize
- SetConsoleScreenBufferSize
MS-HAID:
- '\_win32\_setconsolescreenbuffersize'
- base.setconsolescreenbuffersize
- consoles.setconsolescreenbuffersize
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 50bf1973-5604-42fe-bbeb-611ddc240bdd
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferSize
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 46c412ccb41ac17a8e7cf327c80d7f8330738d65
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039326"
---
# <a name="setconsolescreenbuffersize-function"></a><span data-ttu-id="733f2-104">SetConsoleScreenBufferSize 函式</span><span class="sxs-lookup"><span data-stu-id="733f2-104">SetConsoleScreenBufferSize function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="733f2-105">變更指定的主控台螢幕緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="733f2-105">Changes the size of the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="733f2-106">語法</span><span class="sxs-lookup"><span data-stu-id="733f2-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleScreenBufferSize(
  _In_ HANDLE hConsoleOutput,
  _In_ COORD  dwSize
);
```

## <a name="parameters"></a><span data-ttu-id="733f2-107">參數</span><span class="sxs-lookup"><span data-stu-id="733f2-107">Parameters</span></span>

<span data-ttu-id="733f2-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="733f2-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="733f2-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="733f2-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="733f2-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="733f2-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="733f2-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="733f2-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="733f2-112">*dwSize* \[在\]</span><span class="sxs-lookup"><span data-stu-id="733f2-112">*dwSize* \[in\]</span></span>  
<span data-ttu-id="733f2-113">[**COORD**](coord-str.md)結構，指定主控台螢幕緩衝區的新大小（以字元資料列和資料行表示）。</span><span class="sxs-lookup"><span data-stu-id="733f2-113">A [**COORD**](coord-str.md) structure that specifies the new size of the console screen buffer, in character rows and columns.</span></span> <span data-ttu-id="733f2-114">指定的寬度和高度不能小於主控台螢幕緩衝區視窗的寬度和高度。</span><span class="sxs-lookup"><span data-stu-id="733f2-114">The specified width and height cannot be less than the width and height of the console screen buffer's window.</span></span> <span data-ttu-id="733f2-115">指定的維度也不能小於系統允許的最小大小。</span><span class="sxs-lookup"><span data-stu-id="733f2-115">The specified dimensions also cannot be less than the minimum size allowed by the system.</span></span> <span data-ttu-id="733f2-116">此最小值取決於使用者) 所選取的主控台 (目前的字型大小，以及 [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385)函式所傳回的 **Sm \_ CXMIN** 和 **sm \_ CYMIN** 值。</span><span class="sxs-lookup"><span data-stu-id="733f2-116">This minimum depends on the current font size for the console (selected by the user) and the **SM\_CXMIN** and **SM\_CYMIN** values returned by the [**GetSystemMetrics**](https://msdn.microsoft.com/library/windows/desktop/ms724385) function.</span></span>

## <a name="return-value"></a><span data-ttu-id="733f2-117">傳回值</span><span class="sxs-lookup"><span data-stu-id="733f2-117">Return value</span></span>

<span data-ttu-id="733f2-118">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="733f2-118">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="733f2-119">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="733f2-119">If the function fails, the return value is zero.</span></span> <span data-ttu-id="733f2-120">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="733f2-120">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="733f2-121">備註</span><span class="sxs-lookup"><span data-stu-id="733f2-121">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="733f2-122">需求</span><span class="sxs-lookup"><span data-stu-id="733f2-122">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="733f2-123">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="733f2-123">Minimum supported client</span></span> | <span data-ttu-id="733f2-124">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="733f2-124">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="733f2-125">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="733f2-125">Minimum supported server</span></span> | <span data-ttu-id="733f2-126">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="733f2-126">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="733f2-127">標頭</span><span class="sxs-lookup"><span data-stu-id="733f2-127">Header</span></span> | <span data-ttu-id="733f2-128">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="733f2-128">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="733f2-129">程式庫</span><span class="sxs-lookup"><span data-stu-id="733f2-129">Library</span></span> | <span data-ttu-id="733f2-130">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="733f2-130">Kernel32.lib</span></span> |
| <span data-ttu-id="733f2-131">DLL</span><span class="sxs-lookup"><span data-stu-id="733f2-131">DLL</span></span> | <span data-ttu-id="733f2-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="733f2-132">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="733f2-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="733f2-133">See also</span></span>

[<span data-ttu-id="733f2-134">主控台功能</span><span class="sxs-lookup"><span data-stu-id="733f2-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="733f2-135">主控台輸入緩衝區</span><span class="sxs-lookup"><span data-stu-id="733f2-135">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="733f2-136">**COORD**</span><span class="sxs-lookup"><span data-stu-id="733f2-136">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="733f2-137">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="733f2-137">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="733f2-138">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="733f2-138">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

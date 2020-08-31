---
title: SetConsoleTextAttribute 函式
description: 設定 WriteFile 或 WriteConsole 函式寫入主控台螢幕緩衝區的字元屬性，或由 ReadFile 或 ReadConsole 函式回顯的字元屬性。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
ms.openlocfilehash: 2242466e4255b0d92c9bb1d1eac5431b59346e7b
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059530"
---
# <a name="setconsoletextattribute-function"></a><span data-ttu-id="07e8c-104">SetConsoleTextAttribute 函式</span><span class="sxs-lookup"><span data-stu-id="07e8c-104">SetConsoleTextAttribute function</span></span>


<span data-ttu-id="07e8c-105">設定 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 或 [**WriteConsole**](writeconsole.md) 函式寫入主控台螢幕緩衝區的字元屬性，或由 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 或 [**ReadConsole**](readconsole.md) 函式回顯的字元屬性。</span><span class="sxs-lookup"><span data-stu-id="07e8c-105">Sets the attributes of characters written to the console screen buffer by the [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md) function, or echoed by the [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) function.</span></span> <span data-ttu-id="07e8c-106">此函式會影響在函式呼叫後寫入的文字。</span><span class="sxs-lookup"><span data-stu-id="07e8c-106">This function affects text written after the function call.</span></span>

<a name="syntax"></a><span data-ttu-id="07e8c-107">語法</span><span class="sxs-lookup"><span data-stu-id="07e8c-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleTextAttribute(
  _In_ HANDLE hConsoleOutput,
  _In_ WORD   wAttributes
);
```

<a name="parameters"></a><span data-ttu-id="07e8c-108">參數</span><span class="sxs-lookup"><span data-stu-id="07e8c-108">Parameters</span></span>
----------

<span data-ttu-id="07e8c-109">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="07e8c-109">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="07e8c-110">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="07e8c-110">A handle to the console screen buffer.</span></span> <span data-ttu-id="07e8c-111">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="07e8c-111">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="07e8c-112">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="07e8c-112">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="07e8c-113">*wAttributes* \[在\]</span><span class="sxs-lookup"><span data-stu-id="07e8c-113">*wAttributes* \[in\]</span></span>  
<span data-ttu-id="07e8c-114">[字元屬性](console-screen-buffers.md#_win32_font_attributes)。</span><span class="sxs-lookup"><span data-stu-id="07e8c-114">The [character attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<a name="return-value"></a><span data-ttu-id="07e8c-115">傳回值</span><span class="sxs-lookup"><span data-stu-id="07e8c-115">Return value</span></span>
------------

<span data-ttu-id="07e8c-116">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="07e8c-116">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="07e8c-117">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="07e8c-117">If the function fails, the return value is zero.</span></span> <span data-ttu-id="07e8c-118">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="07e8c-118">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="07e8c-119">備註</span><span class="sxs-lookup"><span data-stu-id="07e8c-119">Remarks</span></span>
-------

<span data-ttu-id="07e8c-120">若要判斷螢幕緩衝區目前的色彩屬性，請呼叫 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="07e8c-120">To determine the current color attributes of a screen buffer, call the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function.</span></span>

<a name="examples"></a><span data-ttu-id="07e8c-121">範例</span><span class="sxs-lookup"><span data-stu-id="07e8c-121">Examples</span></span>
--------

<span data-ttu-id="07e8c-122">如需範例，請參閱 [使用高階輸入和輸出函數](using-the-high-level-input-and-output-functions.md)。</span><span class="sxs-lookup"><span data-stu-id="07e8c-122">For an example, see [Using the High-Level Input and Output Functions](using-the-high-level-input-and-output-functions.md).</span></span>

<a name="requirements"></a><span data-ttu-id="07e8c-123">規格需求</span><span class="sxs-lookup"><span data-stu-id="07e8c-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="07e8c-124">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="07e8c-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="07e8c-125">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="07e8c-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="07e8c-126">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="07e8c-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="07e8c-127">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="07e8c-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="07e8c-128">標頭</span><span class="sxs-lookup"><span data-stu-id="07e8c-128">Header</span></span></p></td>
<td><span data-ttu-id="07e8c-129">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="07e8c-129">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="07e8c-130">程式庫</span><span class="sxs-lookup"><span data-stu-id="07e8c-130">Library</span></span></p></td>
<td><span data-ttu-id="07e8c-131">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="07e8c-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="07e8c-132">DLL</span><span class="sxs-lookup"><span data-stu-id="07e8c-132">DLL</span></span></p></td>
<td><span data-ttu-id="07e8c-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="07e8c-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="07e8c-134"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="07e8c-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="07e8c-135">主控台功能</span><span class="sxs-lookup"><span data-stu-id="07e8c-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="07e8c-136">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="07e8c-136">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="07e8c-137">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="07e8c-137">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="07e8c-138">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="07e8c-138">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="07e8c-139">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="07e8c-139">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="07e8c-140">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="07e8c-140">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="07e8c-141">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="07e8c-141">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 





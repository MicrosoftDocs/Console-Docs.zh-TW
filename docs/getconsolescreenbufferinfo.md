---
title: GetConsoleScreenBufferInfo 函式
description: 請參閱 GetConsoleScreenBufferInfo 函式的參考資訊，此函式會抓取指定的主控台螢幕緩衝區的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfo
- wincon/GetConsoleScreenBufferInfo
- GetConsoleScreenBufferInfo
ms.assetid: eafe819e-a99a-4ce1-8898-8860444a31af
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 8ced380982705647b7944cee0f72c723c38776c3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059127"
---
# <a name="getconsolescreenbufferinfo-function"></a><span data-ttu-id="9c80a-104">GetConsoleScreenBufferInfo 函式</span><span class="sxs-lookup"><span data-stu-id="9c80a-104">GetConsoleScreenBufferInfo function</span></span>


<span data-ttu-id="9c80a-105">抓取指定的主控台螢幕緩衝區的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9c80a-105">Retrieves information about the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="9c80a-106">語法</span><span class="sxs-lookup"><span data-stu-id="9c80a-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleScreenBufferInfo(
  _In_  HANDLE                      hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFO lpConsoleScreenBufferInfo
);
```

<a name="parameters"></a><span data-ttu-id="9c80a-107">參數</span><span class="sxs-lookup"><span data-stu-id="9c80a-107">Parameters</span></span>
----------

<span data-ttu-id="9c80a-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="9c80a-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="9c80a-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="9c80a-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="9c80a-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="9c80a-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="9c80a-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="9c80a-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="9c80a-112">*lpConsoleScreenBufferInfo* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="9c80a-112">*lpConsoleScreenBufferInfo* \[out\]</span></span>  
<span data-ttu-id="9c80a-113">[\*\*主控台 \_ 螢幕 \_ 緩衝區 \_ \*\*](console-screen-buffer-info-str.md)資訊結構的指標，此結構會接收主控台螢幕緩衝區資訊。</span><span class="sxs-lookup"><span data-stu-id="9c80a-113">A pointer to a [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure that receives the console screen buffer information.</span></span>

<a name="return-value"></a><span data-ttu-id="9c80a-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="9c80a-114">Return value</span></span>
------------

<span data-ttu-id="9c80a-115">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="9c80a-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="9c80a-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="9c80a-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="9c80a-117">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="9c80a-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="9c80a-118">備註</span><span class="sxs-lookup"><span data-stu-id="9c80a-118">Remarks</span></span>
-------

<span data-ttu-id="9c80a-119">您可以修改[**主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊**](console-screen-buffer-info-str.md)結構的**srWindow**成員中所傳回的矩形，然後將其傳遞至[**SetConsoleWindowInfo**](setconsolewindowinfo.md)函式，以在視窗中滾動主控台畫面緩衝區、變更視窗的大小，或兩者。</span><span class="sxs-lookup"><span data-stu-id="9c80a-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="9c80a-120">[**主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊**](console-screen-buffer-info-str.md)結構中傳回的所有座標都是在字元儲存格座標中，其中源 (0、0) 位於主控台螢幕緩衝區的左上角。</span><span class="sxs-lookup"><span data-stu-id="9c80a-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFO**](console-screen-buffer-info-str.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

<a name="examples"></a><span data-ttu-id="9c80a-121">範例</span><span class="sxs-lookup"><span data-stu-id="9c80a-121">Examples</span></span>
--------

<span data-ttu-id="9c80a-122">如需範例，請參閱 [滾動螢幕緩衝區視窗](scrolling-a-screen-buffer-s-window.md)。</span><span class="sxs-lookup"><span data-stu-id="9c80a-122">For an example, see [Scrolling a Screen Buffer's Window](scrolling-a-screen-buffer-s-window.md).</span></span>

<a name="requirements"></a><span data-ttu-id="9c80a-123">規格需求</span><span class="sxs-lookup"><span data-stu-id="9c80a-123">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="9c80a-124">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="9c80a-124">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="9c80a-125">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="9c80a-125">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="9c80a-126">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="9c80a-126">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="9c80a-127">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="9c80a-127">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="9c80a-128">標頭</span><span class="sxs-lookup"><span data-stu-id="9c80a-128">Header</span></span></p></td>
<td><span data-ttu-id="9c80a-129">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="9c80a-129">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="9c80a-130">程式庫</span><span class="sxs-lookup"><span data-stu-id="9c80a-130">Library</span></span></p></td>
<td><span data-ttu-id="9c80a-131">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="9c80a-131">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="9c80a-132">DLL</span><span class="sxs-lookup"><span data-stu-id="9c80a-132">DLL</span></span></p></td>
<td><span data-ttu-id="9c80a-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9c80a-133">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="9c80a-134"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c80a-134"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="9c80a-135">主控台功能</span><span class="sxs-lookup"><span data-stu-id="9c80a-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="9c80a-136">**主控台 \_ 螢幕 \_ 緩衝區 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="9c80a-136">**CONSOLE\_SCREEN\_BUFFER\_INFO**</span></span>](console-screen-buffer-info-str.md)

[<span data-ttu-id="9c80a-137">**GetLargestConsoleWindowSize**</span><span class="sxs-lookup"><span data-stu-id="9c80a-137">**GetLargestConsoleWindowSize**</span></span>](getlargestconsolewindowsize.md)

[<span data-ttu-id="9c80a-138">**SetConsoleCursorPosition**</span><span class="sxs-lookup"><span data-stu-id="9c80a-138">**SetConsoleCursorPosition**</span></span>](setconsolecursorposition.md)

[<span data-ttu-id="9c80a-139">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="9c80a-139">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

[<span data-ttu-id="9c80a-140">**SetConsoleWindowInfo**</span><span class="sxs-lookup"><span data-stu-id="9c80a-140">**SetConsoleWindowInfo**</span></span>](setconsolewindowinfo.md)

[<span data-ttu-id="9c80a-141">視窗和螢幕緩衝區大小</span><span class="sxs-lookup"><span data-stu-id="9c80a-141">Window and Screen Buffer Size</span></span>](window-and-screen-buffer-size.md)

 

 





---
title: GetConsoleScreenBufferInfoEx 函式
description: 抓取指定的主控台螢幕緩衝區的延伸資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/GetConsoleScreenBufferInfoEx
- wincon/GetConsoleScreenBufferInfoEx
- GetConsoleScreenBufferInfoEx
MS-HAID:
- base.getconsolescreenbufferinfoex
- consoles.getconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 60534226-d26f-44e2-a4cc-64811882e308
topic_type:
- apiref
api_name:
- GetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 69cb3c59af1a93cf6af664bbecaf05ef00b64ce8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059143"
---
# <a name="getconsolescreenbufferinfoex-function"></a><span data-ttu-id="31a28-104">GetConsoleScreenBufferInfoEx 函式</span><span class="sxs-lookup"><span data-stu-id="31a28-104">GetConsoleScreenBufferInfoEx function</span></span>


<span data-ttu-id="31a28-105">抓取指定的主控台螢幕緩衝區的延伸資訊。</span><span class="sxs-lookup"><span data-stu-id="31a28-105">Retrieves extended information about the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="31a28-106">語法</span><span class="sxs-lookup"><span data-stu-id="31a28-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleScreenBufferInfoEx(
  _In_  HANDLE                        hConsoleOutput,
  _Out_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

<a name="parameters"></a><span data-ttu-id="31a28-107">參數</span><span class="sxs-lookup"><span data-stu-id="31a28-107">Parameters</span></span>
----------

<span data-ttu-id="31a28-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="31a28-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="31a28-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="31a28-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="31a28-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="31a28-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="31a28-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="31a28-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="31a28-112">*lpConsoleScreenBufferInfoEx* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="31a28-112">*lpConsoleScreenBufferInfoEx* \[out\]</span></span>  
<span data-ttu-id="31a28-113">[**主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX**](console-screen-buffer-infoex.md)結構，此結構會接收要求的主控台畫面緩衝區資訊。</span><span class="sxs-lookup"><span data-stu-id="31a28-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that receives the requested console screen buffer information.</span></span>

<a name="return-value"></a><span data-ttu-id="31a28-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="31a28-114">Return value</span></span>
------------

<span data-ttu-id="31a28-115">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="31a28-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="31a28-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="31a28-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="31a28-117">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="31a28-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="31a28-118">備註</span><span class="sxs-lookup"><span data-stu-id="31a28-118">Remarks</span></span>
-------

<span data-ttu-id="31a28-119">您可以修改[**主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX**](console-screen-buffer-infoex.md)結構的**srWindow**成員中所傳回的矩形，然後將其傳遞至[**SetConsoleWindowInfo**](setconsolewindowinfo.md)函式，以在視窗中滾動主控台畫面緩衝區、變更視窗的大小，或兩者。</span><span class="sxs-lookup"><span data-stu-id="31a28-119">The rectangle returned in the **srWindow** member of the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure can be modified and then passed to the [**SetConsoleWindowInfo**](setconsolewindowinfo.md) function to scroll the console screen buffer in the window, to change the size of the window, or both.</span></span>

<span data-ttu-id="31a28-120">在 [**主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX**](console-screen-buffer-infoex.md) 結構中傳回的所有座標都是在字元儲存格座標中，其中源 (0、0) 位於主控台螢幕緩衝區的左上角。</span><span class="sxs-lookup"><span data-stu-id="31a28-120">All coordinates returned in the [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure are in character-cell coordinates, where the origin (0, 0) is at the upper-left corner of the console screen buffer.</span></span>

<a name="requirements"></a><span data-ttu-id="31a28-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="31a28-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="31a28-122">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="31a28-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="31a28-123">Windows Vista [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="31a28-123">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="31a28-124">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="31a28-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="31a28-125">Windows Server 2008 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="31a28-125">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="31a28-126">標頭</span><span class="sxs-lookup"><span data-stu-id="31a28-126">Header</span></span></p></td>
<td><span data-ttu-id="31a28-127">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="31a28-127">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="31a28-128">程式庫</span><span class="sxs-lookup"><span data-stu-id="31a28-128">Library</span></span></p></td>
<td><span data-ttu-id="31a28-129">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="31a28-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="31a28-130">DLL</span><span class="sxs-lookup"><span data-stu-id="31a28-130">DLL</span></span></p></td>
<td><span data-ttu-id="31a28-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="31a28-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="31a28-132"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="31a28-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="31a28-133">主控台功能</span><span class="sxs-lookup"><span data-stu-id="31a28-133">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="31a28-134">**主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="31a28-134">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="31a28-135">**SetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="31a28-135">**SetConsoleScreenBufferInfoEx**</span></span>](setconsolescreenbufferinfoex.md)

 

 





---
title: SetConsoleScreenBufferInfoEx 函式
description: 將指定之主控台畫面緩衝區的擴充資訊設定為指定的緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/SetConsoleScreenBufferInfoEx
- wincon/SetConsoleScreenBufferInfoEx
- SetConsoleScreenBufferInfoEx
MS-HAID:
- base.setconsolescreenbufferinfoex
- consoles.setconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ff851144-eee9-4410-8fd1-28aa24fc25f1
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 403ce6c3625aacdcc8b2eb498e7df1715d1e6b94
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059522"
---
# <a name="setconsolescreenbufferinfoex-function"></a><span data-ttu-id="cbbe1-104">SetConsoleScreenBufferInfoEx 函式</span><span class="sxs-lookup"><span data-stu-id="cbbe1-104">SetConsoleScreenBufferInfoEx function</span></span>


<span data-ttu-id="cbbe1-105">設定指定的主控台螢幕緩衝區的延伸資訊。</span><span class="sxs-lookup"><span data-stu-id="cbbe1-105">Sets extended information about the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="cbbe1-106">語法</span><span class="sxs-lookup"><span data-stu-id="cbbe1-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleScreenBufferInfoEx(
  _In_ HANDLE                        hConsoleOutput,
  _In_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

<a name="parameters"></a><span data-ttu-id="cbbe1-107">參數</span><span class="sxs-lookup"><span data-stu-id="cbbe1-107">Parameters</span></span>
----------

<span data-ttu-id="cbbe1-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="cbbe1-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="cbbe1-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="cbbe1-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="cbbe1-110">控制碼必須有 **一般 \_ 寫入** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="cbbe1-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="cbbe1-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="cbbe1-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="cbbe1-112">*lpConsoleScreenBufferInfoEx* \[在\]</span><span class="sxs-lookup"><span data-stu-id="cbbe1-112">*lpConsoleScreenBufferInfoEx* \[in\]</span></span>  
<span data-ttu-id="cbbe1-113">[**主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX**](console-screen-buffer-infoex.md)結構，其中包含主控台螢幕緩衝區資訊。</span><span class="sxs-lookup"><span data-stu-id="cbbe1-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that contains the console screen buffer information.</span></span>

<a name="return-value"></a><span data-ttu-id="cbbe1-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="cbbe1-114">Return value</span></span>
------------

<span data-ttu-id="cbbe1-115">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="cbbe1-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="cbbe1-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="cbbe1-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="cbbe1-117">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="cbbe1-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="cbbe1-118">規格需求</span><span class="sxs-lookup"><span data-stu-id="cbbe1-118">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="cbbe1-119">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="cbbe1-119">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="cbbe1-120">Windows Vista [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="cbbe1-120">Windows Vista [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="cbbe1-121">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="cbbe1-121">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="cbbe1-122">Windows Server 2008 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="cbbe1-122">Windows Server 2008 [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="cbbe1-123">標頭</span><span class="sxs-lookup"><span data-stu-id="cbbe1-123">Header</span></span></p></td>
<td><span data-ttu-id="cbbe1-124">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="cbbe1-124">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="cbbe1-125">程式庫</span><span class="sxs-lookup"><span data-stu-id="cbbe1-125">Library</span></span></p></td>
<td><span data-ttu-id="cbbe1-126">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="cbbe1-126">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="cbbe1-127">DLL</span><span class="sxs-lookup"><span data-stu-id="cbbe1-127">DLL</span></span></p></td>
<td><span data-ttu-id="cbbe1-128">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="cbbe1-128">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="cbbe1-129"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbbe1-129"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="cbbe1-130">主控台功能</span><span class="sxs-lookup"><span data-stu-id="cbbe1-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="cbbe1-131">**主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="cbbe1-131">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="cbbe1-132">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="cbbe1-132">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)

 

 





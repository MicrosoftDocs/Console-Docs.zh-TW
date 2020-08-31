---
title: GetConsoleCursorInfo 函式
description: 針對指定的主控台螢幕緩衝區，抓取資料指標的大小和可見度的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/GetConsoleCursorInfo
- wincon/GetConsoleCursorInfo
- GetConsoleCursorInfo
MS-HAID:
- '\_win32\_getconsolecursorinfo'
- base.getconsolecursorinfo
- consoles.getconsolecursorinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6200577d-8d84-46bd-9330-d0b6cbbb3e52
topic_type:
- apiref
api_name:
- GetConsoleCursorInfo
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d87fe0828451615e837c1c6c809a0160f15cf018
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059166"
---
# <a name="getconsolecursorinfo-function"></a><span data-ttu-id="e7a92-104">GetConsoleCursorInfo 函式</span><span class="sxs-lookup"><span data-stu-id="e7a92-104">GetConsoleCursorInfo function</span></span>


<span data-ttu-id="e7a92-105">針對指定的主控台螢幕緩衝區，抓取資料指標的大小和可見度的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e7a92-105">Retrieves information about the size and visibility of the cursor for the specified console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="e7a92-106">語法</span><span class="sxs-lookup"><span data-stu-id="e7a92-106">Syntax</span></span>
------

```C
BOOL WINAPI GetConsoleCursorInfo(
  _In_  HANDLE               hConsoleOutput,
  _Out_ PCONSOLE_CURSOR_INFO lpConsoleCursorInfo
);
```

<a name="parameters"></a><span data-ttu-id="e7a92-107">參數</span><span class="sxs-lookup"><span data-stu-id="e7a92-107">Parameters</span></span>
----------

<span data-ttu-id="e7a92-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="e7a92-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="e7a92-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="e7a92-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="e7a92-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="e7a92-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="e7a92-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="e7a92-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="e7a92-112">*lpConsoleCursorInfo* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="e7a92-112">*lpConsoleCursorInfo* \[out\]</span></span>  
<span data-ttu-id="e7a92-113">主控台資料指標 [\*\* \_ \_ 資訊\*\*](console-cursor-info-str.md) 結構的指標，此結構會接收主控台資料指標的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e7a92-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that receives information about the console's cursor.</span></span>

<a name="return-value"></a><span data-ttu-id="e7a92-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="e7a92-114">Return value</span></span>
------------

<span data-ttu-id="e7a92-115">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="e7a92-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="e7a92-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="e7a92-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="e7a92-117">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="e7a92-117">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="requirements"></a><span data-ttu-id="e7a92-118">規格需求</span><span class="sxs-lookup"><span data-stu-id="e7a92-118">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="e7a92-119">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="e7a92-119">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="e7a92-120">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="e7a92-120">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e7a92-121">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="e7a92-121">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="e7a92-122">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="e7a92-122">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e7a92-123">標頭</span><span class="sxs-lookup"><span data-stu-id="e7a92-123">Header</span></span></p></td>
<td><span data-ttu-id="e7a92-124">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="e7a92-124">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="e7a92-125">程式庫</span><span class="sxs-lookup"><span data-stu-id="e7a92-125">Library</span></span></p></td>
<td><span data-ttu-id="e7a92-126">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="e7a92-126">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="e7a92-127">DLL</span><span class="sxs-lookup"><span data-stu-id="e7a92-127">DLL</span></span></p></td>
<td><span data-ttu-id="e7a92-128">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="e7a92-128">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="e7a92-129"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7a92-129"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="e7a92-130">主控台功能</span><span class="sxs-lookup"><span data-stu-id="e7a92-130">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="e7a92-131">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="e7a92-131">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="e7a92-132">**主控台資料 \_ 指標 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="e7a92-132">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="e7a92-133">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="e7a92-133">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)

 

 





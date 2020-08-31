---
title: GetConsoleCP 函式
description: 抓取與呼叫進程相關聯的主控台所使用的輸入字碼頁。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi/GetConsoleCP
- wincon/GetConsoleCP
- GetConsoleCP
MS-HAID:
- '\_win32\_getconsolecp'
- base.getconsolecp
- consoles.getconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9e0af6d9-0f5c-45b3-a686-22449d26de47
topic_type:
- apiref
api_name:
- GetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: ba0ebfecddf5702e8078197b834931a62658d9dc
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059171"
---
# <a name="getconsolecp-function"></a><span data-ttu-id="d3fbf-104">GetConsoleCP 函式</span><span class="sxs-lookup"><span data-stu-id="d3fbf-104">GetConsoleCP function</span></span>


<span data-ttu-id="d3fbf-105">抓取與呼叫進程相關聯的主控台所使用的輸入字碼頁。</span><span class="sxs-lookup"><span data-stu-id="d3fbf-105">Retrieves the input code page used by the console associated with the calling process.</span></span> <span data-ttu-id="d3fbf-106">主控台會使用其輸入字碼頁面，將鍵盤輸入轉譯成對應的字元值。</span><span class="sxs-lookup"><span data-stu-id="d3fbf-106">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span>

<a name="syntax"></a><span data-ttu-id="d3fbf-107">語法</span><span class="sxs-lookup"><span data-stu-id="d3fbf-107">Syntax</span></span>
------

```C
UINT WINAPI GetConsoleCP(void);
```

<a name="parameters"></a><span data-ttu-id="d3fbf-108">參數</span><span class="sxs-lookup"><span data-stu-id="d3fbf-108">Parameters</span></span>
----------

<span data-ttu-id="d3fbf-109">此函式沒有參數。</span><span class="sxs-lookup"><span data-stu-id="d3fbf-109">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="d3fbf-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="d3fbf-110">Return value</span></span>
------------

<span data-ttu-id="d3fbf-111">傳回值是可識別字碼頁的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d3fbf-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="d3fbf-112">如需識別碼的清單，請參閱 [字碼頁識別碼](https://msdn.microsoft.com/library/windows/desktop/dd317756)。</span><span class="sxs-lookup"><span data-stu-id="d3fbf-112">For a list of identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="d3fbf-113">如果傳回值為零，則函數會失敗。</span><span class="sxs-lookup"><span data-stu-id="d3fbf-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="d3fbf-114">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="d3fbf-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="d3fbf-115">備註</span><span class="sxs-lookup"><span data-stu-id="d3fbf-115">Remarks</span></span>
-------

<span data-ttu-id="d3fbf-116">字碼頁會將256字元碼對應至個別字元。</span><span class="sxs-lookup"><span data-stu-id="d3fbf-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="d3fbf-117">不同的字碼頁包含不同的特殊字元，一般而言是針對語言或語言群組進行自訂。</span><span class="sxs-lookup"><span data-stu-id="d3fbf-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="d3fbf-118">若要取得字碼頁的詳細資訊（包括其名稱），請參閱 [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) 函數。</span><span class="sxs-lookup"><span data-stu-id="d3fbf-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span>

<span data-ttu-id="d3fbf-119">若要設定主控台的輸入字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="d3fbf-119">To set a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) function.</span></span> <span data-ttu-id="d3fbf-120">若要設定及查詢主控台的輸出字碼頁，請使用 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 和 [**GetConsoleOutputCP**](getconsoleoutputcp.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="d3fbf-120">To set and query a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.</span></span>

<a name="requirements"></a><span data-ttu-id="d3fbf-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="d3fbf-121">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="d3fbf-122">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="d3fbf-122">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="d3fbf-123">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="d3fbf-123">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d3fbf-124">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="d3fbf-124">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="d3fbf-125">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="d3fbf-125">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d3fbf-126">標頭</span><span class="sxs-lookup"><span data-stu-id="d3fbf-126">Header</span></span></p></td>
<td><span data-ttu-id="d3fbf-127">ConsoleApi .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="d3fbf-127">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d3fbf-128">程式庫</span><span class="sxs-lookup"><span data-stu-id="d3fbf-128">Library</span></span></p></td>
<td><span data-ttu-id="d3fbf-129">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="d3fbf-129">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d3fbf-130">DLL</span><span class="sxs-lookup"><span data-stu-id="d3fbf-130">DLL</span></span></p></td>
<td><span data-ttu-id="d3fbf-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d3fbf-131">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="d3fbf-132"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3fbf-132"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="d3fbf-133">主控台字碼頁</span><span class="sxs-lookup"><span data-stu-id="d3fbf-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="d3fbf-134">主控台功能</span><span class="sxs-lookup"><span data-stu-id="d3fbf-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d3fbf-135">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="d3fbf-135">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="d3fbf-136">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="d3fbf-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="d3fbf-137">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="d3fbf-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

 

 





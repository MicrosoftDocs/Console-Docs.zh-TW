---
title: GetConsoleTitle 函式
description: 抓取目前主控台視窗之標題的標題和大小。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/GetConsoleTitle
- wincon/GetConsoleTitle
- GetConsoleTitle
- consoleapi2/GetConsoleTitleA
- wincon/GetConsoleTitleA
- GetConsoleTitleA
- consoleapi2/GetConsoleTitleW
- wincon/GetConsoleTitleW
- GetConsoleTitleW
MS-HAID:
- '\_win32\_getconsoletitle'
- base.getconsoletitle
- consoles.getconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c58bba36-9813-4bdc-83bf-30d55f8d7d79
topic_type:
- apiref
api_name:
- GetConsoleTitle
- GetConsoleTitleA
- GetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-Ms-Win-Core-Console-Ansi-L2-1-0.dll
- Kernel32Legacy.dll
api_type:
- DllExport
ms.openlocfilehash: 5b8e78e65e52c3f10be14afa6a122fa12609a2eb
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059119"
---
# <a name="getconsoletitle-function"></a><span data-ttu-id="0cc73-104">GetConsoleTitle 函式</span><span class="sxs-lookup"><span data-stu-id="0cc73-104">GetConsoleTitle function</span></span>


<span data-ttu-id="0cc73-105">抓取目前主控台視窗的標題。</span><span class="sxs-lookup"><span data-stu-id="0cc73-105">Retrieves the title for the current console window.</span></span>

<a name="syntax"></a><span data-ttu-id="0cc73-106">語法</span><span class="sxs-lookup"><span data-stu-id="0cc73-106">Syntax</span></span>
------

```C
DWORD WINAPI GetConsoleTitle(
  _Out_ LPTSTR lpConsoleTitle,
  _In_  DWORD  nSize
);
```

<a name="parameters"></a><span data-ttu-id="0cc73-107">參數</span><span class="sxs-lookup"><span data-stu-id="0cc73-107">Parameters</span></span>
----------

<span data-ttu-id="0cc73-108">*lpConsoleTitle* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="0cc73-108">*lpConsoleTitle* \[out\]</span></span>  
<span data-ttu-id="0cc73-109">緩衝區的指標，此緩衝區會接收包含標題之以 null 結束的字串。</span><span class="sxs-lookup"><span data-stu-id="0cc73-109">A pointer to a buffer that receives a null-terminated string containing the title.</span></span> <span data-ttu-id="0cc73-110">如果緩衝區太小而無法儲存標題，此函式會將標題的任意多個字元儲存為緩衝區中容納的字元，並以 null 結束字元結尾。</span><span class="sxs-lookup"><span data-stu-id="0cc73-110">If the buffer is too small to store the title, the function stores as many characters of the title as will fit in the buffer, ending with a null terminator.</span></span>

<span data-ttu-id="0cc73-111">*nSize* \[在\]</span><span class="sxs-lookup"><span data-stu-id="0cc73-111">*nSize* \[in\]</span></span>  
<span data-ttu-id="0cc73-112">*LpConsoleTitle*參數所指向的緩衝區大小（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="0cc73-112">The size of the buffer pointed to by the *lpConsoleTitle* parameter, in characters.</span></span>

<a name="return-value"></a><span data-ttu-id="0cc73-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="0cc73-113">Return value</span></span>
------------

<span data-ttu-id="0cc73-114">如果函式成功，則傳回值為主控台視窗標題的長度（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="0cc73-114">If the function succeeds, the return value is the length of the console window's title, in characters.</span></span>

<span data-ttu-id="0cc73-115">如果函式失敗，則傳回值為零，而 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) 會傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="0cc73-115">If the function fails, the return value is zero and [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360) returns the error code.</span></span>

<a name="remarks"></a><span data-ttu-id="0cc73-116">備註</span><span class="sxs-lookup"><span data-stu-id="0cc73-116">Remarks</span></span>
-------

<span data-ttu-id="0cc73-117">若要設定主控台視窗的標題，請使用 [**SetConsoleTitle**](setconsoletitle.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="0cc73-117">To set the title for a console window, use the [**SetConsoleTitle**](setconsoletitle.md) function.</span></span> <span data-ttu-id="0cc73-118">若要取出原始的標題字串，請使用 [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="0cc73-118">To retrieve the original title string, use the [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) function.</span></span>

<span data-ttu-id="0cc73-119">此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。</span><span class="sxs-lookup"><span data-stu-id="0cc73-119">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="0cc73-120">主控台的字碼頁一開始預設為系統的 OEM 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="0cc73-120">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="0cc73-121">若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 或 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函式，或使用 **chcp** 或 **mode con cp select =** 命令。</span><span class="sxs-lookup"><span data-stu-id="0cc73-121">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="0cc73-122">範例</span><span class="sxs-lookup"><span data-stu-id="0cc73-122">Examples</span></span>
--------

<span data-ttu-id="0cc73-123">如需範例，請參閱 [**SetConsoleTitle**](setconsoletitle.md)。</span><span class="sxs-lookup"><span data-stu-id="0cc73-123">For an example, see [**SetConsoleTitle**](setconsoletitle.md).</span></span>

<a name="requirements"></a><span data-ttu-id="0cc73-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="0cc73-124">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="0cc73-125">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="0cc73-125">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="0cc73-126">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="0cc73-126">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0cc73-127">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="0cc73-127">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="0cc73-128">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="0cc73-128">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0cc73-129">標頭</span><span class="sxs-lookup"><span data-stu-id="0cc73-129">Header</span></span></p></td>
<td><span data-ttu-id="0cc73-130">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="0cc73-130">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0cc73-131">程式庫</span><span class="sxs-lookup"><span data-stu-id="0cc73-131">Library</span></span></p></td>
<td><span data-ttu-id="0cc73-132">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="0cc73-132">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="0cc73-133">DLL</span><span class="sxs-lookup"><span data-stu-id="0cc73-133">DLL</span></span></p></td>
<td><span data-ttu-id="0cc73-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0cc73-134">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="0cc73-135">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="0cc73-135">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="0cc73-136"><strong>GetConsoleTitleW</strong> (Unicode) 和 <strong>GetConsoleTitleA</strong> (ANSI) </span><span class="sxs-lookup"><span data-stu-id="0cc73-136"><strong>GetConsoleTitleW</strong> (Unicode) and <strong>GetConsoleTitleA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="0cc73-137"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cc73-137"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="0cc73-138">主控台功能</span><span class="sxs-lookup"><span data-stu-id="0cc73-138">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0cc73-139">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="0cc73-139">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="0cc73-140">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="0cc73-140">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="0cc73-141">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="0cc73-141">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="0cc73-142">**SetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="0cc73-142">**SetConsoleTitle**</span></span>](setconsoletitle.md)

 

 





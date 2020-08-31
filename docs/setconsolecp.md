---
title: SetConsoleCP 函式
description: 設定與呼叫進程相關聯的主控台所使用的輸入字碼頁。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/SetConsoleCP
- wincon/SetConsoleCP
- SetConsoleCP
MS-HAID:
- '\_win32\_setconsolecp'
- base.setconsolecp
- consoles.setconsolecp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6a1a9ba5-c792-491d-ae51-979f462dcb53
topic_type:
- apiref
api_name:
- SetConsoleCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: cf7048f9042b6c516c6d8e7a6e0544fdc2ac7533
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059418"
---
# <a name="setconsolecp-function"></a><span data-ttu-id="16de2-104">SetConsoleCP 函式</span><span class="sxs-lookup"><span data-stu-id="16de2-104">SetConsoleCP function</span></span>


<span data-ttu-id="16de2-105">設定與呼叫進程相關聯的主控台所使用的輸入字碼頁。</span><span class="sxs-lookup"><span data-stu-id="16de2-105">Sets the input code page used by the console associated with the calling process.</span></span> <span data-ttu-id="16de2-106">主控台會使用其輸入字碼頁面，將鍵盤輸入轉譯成對應的字元值。</span><span class="sxs-lookup"><span data-stu-id="16de2-106">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span>

<a name="syntax"></a><span data-ttu-id="16de2-107">語法</span><span class="sxs-lookup"><span data-stu-id="16de2-107">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleCP(
  _In_ UINT wCodePageID
);
```

<a name="parameters"></a><span data-ttu-id="16de2-108">參數</span><span class="sxs-lookup"><span data-stu-id="16de2-108">Parameters</span></span>
----------

<span data-ttu-id="16de2-109">*wCodePageID* \[在\]</span><span class="sxs-lookup"><span data-stu-id="16de2-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="16de2-110">要設定的字碼頁識別碼。</span><span class="sxs-lookup"><span data-stu-id="16de2-110">The identifier of the code page to be set.</span></span> <span data-ttu-id="16de2-111">如需詳細資訊，請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="16de2-111">For more information, see Remarks.</span></span>

<a name="return-value"></a><span data-ttu-id="16de2-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="16de2-112">Return value</span></span>
------------

<span data-ttu-id="16de2-113">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="16de2-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="16de2-114">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="16de2-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="16de2-115">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="16de2-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="16de2-116">備註</span><span class="sxs-lookup"><span data-stu-id="16de2-116">Remarks</span></span>
-------

<span data-ttu-id="16de2-117">字碼頁會將256字元碼對應至個別字元。</span><span class="sxs-lookup"><span data-stu-id="16de2-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="16de2-118">不同的字碼頁包含不同的特殊字元，一般而言是針對語言或語言群組進行自訂。</span><span class="sxs-lookup"><span data-stu-id="16de2-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="16de2-119">若要尋找作業系統所安裝或支援的字碼頁，請使用 [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) 函數。</span><span class="sxs-lookup"><span data-stu-id="16de2-119">To find the code pages that are installed or supported by the operating system, use the [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) function.</span></span> <span data-ttu-id="16de2-120">本機電腦上可用的字碼頁識別碼也會儲存在登錄的下列機碼底下：</span><span class="sxs-lookup"><span data-stu-id="16de2-120">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

<span data-ttu-id="16de2-121">**HKEY \_ LOCAL \_ MACHINE \\ SYSTEM \\ CurrentControlSet \\ Control \\ Nls \\ 字碼頁**</span><span class="sxs-lookup"><span data-stu-id="16de2-121">**HKEY\_LOCAL\_MACHINE\\SYSTEM\\CurrentControlSet\\Control\\Nls\\CodePage**</span></span>

<span data-ttu-id="16de2-122">不過，最好使用 [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) 來列舉字碼頁，因為不同版本的 Windows 中的登錄可能不同。</span><span class="sxs-lookup"><span data-stu-id="16de2-122">However, it is better to use [**EnumSystemCodePages**](https://msdn.microsoft.com/library/windows/desktop/dd317825) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>

<span data-ttu-id="16de2-123">若要判斷特定字碼頁是否有效，請使用 [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) 函數。</span><span class="sxs-lookup"><span data-stu-id="16de2-123">To determine whether a particular code page is valid, use the [**IsValidCodePage**](https://msdn.microsoft.com/library/windows/desktop/dd318674) function.</span></span> <span data-ttu-id="16de2-124">若要取得字碼頁的詳細資訊（包括其名稱），請使用 [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) 函數。</span><span class="sxs-lookup"><span data-stu-id="16de2-124">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span> <span data-ttu-id="16de2-125">如需可用字碼頁識別碼的清單，請參閱 [字碼頁識別碼](https://msdn.microsoft.com/library/windows/desktop/dd317756)。</span><span class="sxs-lookup"><span data-stu-id="16de2-125">For a list of available code page identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="16de2-126">若要判斷主控台的目前輸入字碼頁，請使用 [**GetConsoleCP**](getconsolecp.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="16de2-126">To determine a console's current input code page, use the [**GetConsoleCP**](getconsolecp.md) function.</span></span> <span data-ttu-id="16de2-127">若要設定和取出主控台的輸出字碼頁，請使用 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 和 [**GetConsoleOutputCP**](getconsoleoutputcp.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="16de2-127">To set and retrieve a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions.</span></span>

<a name="requirements"></a><span data-ttu-id="16de2-128">規格需求</span><span class="sxs-lookup"><span data-stu-id="16de2-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="16de2-129">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="16de2-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="16de2-130">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="16de2-130">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="16de2-131">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="16de2-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="16de2-132">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="16de2-132">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="16de2-133">標頭</span><span class="sxs-lookup"><span data-stu-id="16de2-133">Header</span></span></p></td>
<td><span data-ttu-id="16de2-134">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="16de2-134">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="16de2-135">程式庫</span><span class="sxs-lookup"><span data-stu-id="16de2-135">Library</span></span></p></td>
<td><span data-ttu-id="16de2-136">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="16de2-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="16de2-137">DLL</span><span class="sxs-lookup"><span data-stu-id="16de2-137">DLL</span></span></p></td>
<td><span data-ttu-id="16de2-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="16de2-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="16de2-139"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="16de2-139"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="16de2-140">主控台字碼頁</span><span class="sxs-lookup"><span data-stu-id="16de2-140">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="16de2-141">主控台功能</span><span class="sxs-lookup"><span data-stu-id="16de2-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="16de2-142">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="16de2-142">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="16de2-143">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="16de2-143">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="16de2-144">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="16de2-144">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

 

 





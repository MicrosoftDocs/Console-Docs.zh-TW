---
title: SetConsoleOutputCP 函式
description: 設定與呼叫進程相關聯的主控台所使用的輸出字碼頁。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleOutputCP
- wincon/SetConsoleOutputCP
- SetConsoleOutputCP
MS-HAID:
- '\_win32\_setconsoleoutputcp'
- base.setconsoleoutputcp
- consoles.setconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 0b41e66b-ca19-4d69-9f39-92da158344ef
topic_type:
- apiref
api_name:
- SetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 85b6ba4d829b86b99138efbdaa14284429d2aa81
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039336"
---
# <a name="setconsoleoutputcp-function"></a><span data-ttu-id="12595-104">SetConsoleOutputCP 函式</span><span class="sxs-lookup"><span data-stu-id="12595-104">SetConsoleOutputCP function</span></span>

<span data-ttu-id="12595-105">設定與呼叫進程相關聯的主控台所使用的輸出字碼頁。</span><span class="sxs-lookup"><span data-stu-id="12595-105">Sets the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="12595-106">主控台會使用其輸出字碼頁，將各種輸出函式所寫入的字元值轉譯為主控台視窗中顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="12595-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="12595-107">語法</span><span class="sxs-lookup"><span data-stu-id="12595-107">Syntax</span></span>

```C
BOOL WINAPI SetConsoleOutputCP(
  _In_ UINT wCodePageID
);
```

## <a name="parameters"></a><span data-ttu-id="12595-108">參數</span><span class="sxs-lookup"><span data-stu-id="12595-108">Parameters</span></span>

<span data-ttu-id="12595-109">*wCodePageID* \[在\]</span><span class="sxs-lookup"><span data-stu-id="12595-109">*wCodePageID* \[in\]</span></span>  
<span data-ttu-id="12595-110">要設定的字碼頁識別碼。</span><span class="sxs-lookup"><span data-stu-id="12595-110">The identifier of the code page to set.</span></span> <span data-ttu-id="12595-111">如需詳細資訊，請參閱＜備註＞。</span><span class="sxs-lookup"><span data-stu-id="12595-111">For more information, see Remarks.</span></span>

## <a name="return-value"></a><span data-ttu-id="12595-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="12595-112">Return value</span></span>

<span data-ttu-id="12595-113">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="12595-113">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="12595-114">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="12595-114">If the function fails, the return value is zero.</span></span> <span data-ttu-id="12595-115">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="12595-115">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="12595-116">備註</span><span class="sxs-lookup"><span data-stu-id="12595-116">Remarks</span></span>

<span data-ttu-id="12595-117">字碼頁會將256字元碼對應至個別字元。</span><span class="sxs-lookup"><span data-stu-id="12595-117">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="12595-118">不同的字碼頁包含不同的特殊字元，一般而言是針對語言或語言群組進行自訂。</span><span class="sxs-lookup"><span data-stu-id="12595-118">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="12595-119">如果目前的字型是固定音調的 Unicode 字型， **SetConsoleOutputCP** 會將字元值的對應變更為字型的字元組，而不是每次呼叫時載入個別的字型。</span><span class="sxs-lookup"><span data-stu-id="12595-119">If the current font is a fixed-pitch Unicode font, **SetConsoleOutputCP** changes the mapping of the character values into the glyph set of the font, rather than loading a separate font each time it is called.</span></span> <span data-ttu-id="12595-120">這會影響在主控台視窗中顯示擴充字元 (ASCII 值大於 127) 的方式。</span><span class="sxs-lookup"><span data-stu-id="12595-120">This affects how extended characters (ASCII value greater than 127) are displayed in a console window.</span></span> <span data-ttu-id="12595-121">但是，如果目前的字型是點陣字型， **SetConsoleOutputCP** 就不會影響擴充字元的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="12595-121">However, if the current font is a raster font, **SetConsoleOutputCP** does not affect how extended characters are displayed.</span></span>

<span data-ttu-id="12595-122">若要尋找作業系統所安裝或支援的字碼頁，請使用 [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) 函數。</span><span class="sxs-lookup"><span data-stu-id="12595-122">To find the code pages that are installed or supported by the operating system, use the [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) function.</span></span> <span data-ttu-id="12595-123">本機電腦上可用的字碼頁識別碼也會儲存在登錄的下列機碼底下：</span><span class="sxs-lookup"><span data-stu-id="12595-123">The identifiers of the code pages available on the local computer are also stored in the registry under the following key:</span></span>

`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`

<span data-ttu-id="12595-124">不過，最好使用 [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) 來列舉字碼頁，因為不同版本的 Windows 中的登錄可能不同。</span><span class="sxs-lookup"><span data-stu-id="12595-124">However, it is better to use [EnumSystemCodePages](https://go.microsoft.com/fwlink/p/?linkid=178051) to enumerate code pages because the registry can differ in different versions of Windows.</span></span>
<span data-ttu-id="12595-125">若要判斷特定字碼頁是否有效，請使用 [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) 函數。</span><span class="sxs-lookup"><span data-stu-id="12595-125">To determine whether a particular code page is valid, use the [IsValidCodePage](https://go.microsoft.com/fwlink/p/?linkid=178053) function.</span></span> <span data-ttu-id="12595-126">若要取得字碼頁的詳細資訊（包括其名稱），請使用 [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) 函數。</span><span class="sxs-lookup"><span data-stu-id="12595-126">To retrieve more information about a code page, including its name, use the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span> <span data-ttu-id="12595-127">如需可用字碼頁識別碼的清單，請參閱 [字碼頁識別碼](https://msdn.microsoft.com/library/windows/desktop/dd317756)。</span><span class="sxs-lookup"><span data-stu-id="12595-127">For a list of available code page identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="12595-128">若要判斷主控台的目前輸出字碼頁，請使用 [**GetConsoleOutputCP**](getconsoleoutputcp.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="12595-128">To determine a console's current output code page, use the [**GetConsoleOutputCP**](getconsoleoutputcp.md) function.</span></span> <span data-ttu-id="12595-129">若要設定和抓取主控台的輸入字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 和 [**GetConsoleCP**](getconsolecp.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="12595-129">To set and retrieve a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="12595-130">規格需求</span><span class="sxs-lookup"><span data-stu-id="12595-130">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="12595-131">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="12595-131">Minimum supported client</span></span> | <span data-ttu-id="12595-132">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="12595-132">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="12595-133">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="12595-133">Minimum supported server</span></span> | <span data-ttu-id="12595-134">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="12595-134">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="12595-135">標頭</span><span class="sxs-lookup"><span data-stu-id="12595-135">Header</span></span> | <span data-ttu-id="12595-136">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="12595-136">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="12595-137">程式庫</span><span class="sxs-lookup"><span data-stu-id="12595-137">Library</span></span> | <span data-ttu-id="12595-138">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="12595-138">Kernel32.lib</span></span> |
| <span data-ttu-id="12595-139">DLL</span><span class="sxs-lookup"><span data-stu-id="12595-139">DLL</span></span> | <span data-ttu-id="12595-140">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="12595-140">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="12595-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="12595-141">See also</span></span>

[<span data-ttu-id="12595-142">主控台字碼頁</span><span class="sxs-lookup"><span data-stu-id="12595-142">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="12595-143">主控台功能</span><span class="sxs-lookup"><span data-stu-id="12595-143">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="12595-144">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="12595-144">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="12595-145">**GetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="12595-145">**GetConsoleOutputCP**</span></span>](getconsoleoutputcp.md)

[<span data-ttu-id="12595-146">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="12595-146">**SetConsoleCP**</span></span>](setconsolecp.md)

---
title: GetConsoleOutputCP 函式
description: 抓取與呼叫進程相關聯的主控台所使用的輸出字碼頁。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi/GetConsoleOutputCP
- wincon/GetConsoleOutputCP
- GetConsoleOutputCP
MS-HAID:
- '\_win32\_getconsoleoutputcp'
- base.getconsoleoutputcp
- consoles.getconsoleoutputcp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c23706c7-ce17-4825-a494-20ca44534d45
topic_type:
- apiref
api_name:
- GetConsoleOutputCP
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: 30276765b35e9179767fa4e82fc40643ee3b2558
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038816"
---
# <a name="getconsoleoutputcp-function"></a><span data-ttu-id="120f3-104">GetConsoleOutputCP 函式</span><span class="sxs-lookup"><span data-stu-id="120f3-104">GetConsoleOutputCP function</span></span>

<span data-ttu-id="120f3-105">抓取與呼叫進程相關聯的主控台所使用的輸出字碼頁。</span><span class="sxs-lookup"><span data-stu-id="120f3-105">Retrieves the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="120f3-106">主控台會使用其輸出字碼頁，將各種輸出函式所寫入的字元值轉譯為主控台視窗中顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="120f3-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="120f3-107">語法</span><span class="sxs-lookup"><span data-stu-id="120f3-107">Syntax</span></span>

```C
UINT WINAPI GetConsoleOutputCP(void);
```

## <a name="parameters"></a><span data-ttu-id="120f3-108">參數</span><span class="sxs-lookup"><span data-stu-id="120f3-108">Parameters</span></span>

<span data-ttu-id="120f3-109">此函式沒有參數。</span><span class="sxs-lookup"><span data-stu-id="120f3-109">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="120f3-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="120f3-110">Return value</span></span>

<span data-ttu-id="120f3-111">傳回值是可識別字碼頁的程式碼。</span><span class="sxs-lookup"><span data-stu-id="120f3-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="120f3-112">如需識別碼的清單，請參閱 [字碼頁識別碼](https://msdn.microsoft.com/library/windows/desktop/dd317756)。</span><span class="sxs-lookup"><span data-stu-id="120f3-112">For a list of identifiers, see [Code Page Identifiers](https://msdn.microsoft.com/library/windows/desktop/dd317756).</span></span>

<span data-ttu-id="120f3-113">如果傳回值為零，則函數會失敗。</span><span class="sxs-lookup"><span data-stu-id="120f3-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="120f3-114">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="120f3-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="120f3-115">備註</span><span class="sxs-lookup"><span data-stu-id="120f3-115">Remarks</span></span>

<span data-ttu-id="120f3-116">字碼頁會將256字元碼對應至個別字元。</span><span class="sxs-lookup"><span data-stu-id="120f3-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="120f3-117">不同的字碼頁包含不同的特殊字元，一般而言是針對語言或語言群組進行自訂。</span><span class="sxs-lookup"><span data-stu-id="120f3-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="120f3-118">若要取得字碼頁的詳細資訊（包括其名稱），請參閱 [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) 函數。</span><span class="sxs-lookup"><span data-stu-id="120f3-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](https://msdn.microsoft.com/library/windows/desktop/dd318081) function.</span></span>

<span data-ttu-id="120f3-119">若要設定主控台的輸出字碼頁，請使用 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="120f3-119">To set a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) function.</span></span> <span data-ttu-id="120f3-120">若要設定及查詢主控台的輸入字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 和 [**GetConsoleCP**](getconsolecp.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="120f3-120">To set and query a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="120f3-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="120f3-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="120f3-122">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="120f3-122">Minimum supported client</span></span> | <span data-ttu-id="120f3-123">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="120f3-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="120f3-124">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="120f3-124">Minimum supported server</span></span> | <span data-ttu-id="120f3-125">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="120f3-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="120f3-126">標頭</span><span class="sxs-lookup"><span data-stu-id="120f3-126">Header</span></span> | <span data-ttu-id="120f3-127">ConsoleApi .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="120f3-127">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="120f3-128">程式庫</span><span class="sxs-lookup"><span data-stu-id="120f3-128">Library</span></span> | <span data-ttu-id="120f3-129">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="120f3-129">Kernel32.lib</span></span> |
| <span data-ttu-id="120f3-130">DLL</span><span class="sxs-lookup"><span data-stu-id="120f3-130">DLL</span></span> | <span data-ttu-id="120f3-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="120f3-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="120f3-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="120f3-132">See also</span></span>

[<span data-ttu-id="120f3-133">主控台字碼頁</span><span class="sxs-lookup"><span data-stu-id="120f3-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="120f3-134">主控台功能</span><span class="sxs-lookup"><span data-stu-id="120f3-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="120f3-135">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="120f3-135">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="120f3-136">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="120f3-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="120f3-137">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="120f3-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

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
ms.openlocfilehash: 858b0de83c7b1c4678e992b5f9d0ca3d4876ba49
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358948"
---
# <a name="getconsoleoutputcp-function"></a><span data-ttu-id="01016-104">GetConsoleOutputCP 函式</span><span class="sxs-lookup"><span data-stu-id="01016-104">GetConsoleOutputCP function</span></span>

<span data-ttu-id="01016-105">抓取與呼叫進程相關聯的主控台所使用的輸出字碼頁。</span><span class="sxs-lookup"><span data-stu-id="01016-105">Retrieves the output code page used by the console associated with the calling process.</span></span> <span data-ttu-id="01016-106">主控台會使用其輸出字碼頁，將各種輸出函式所寫入的字元值轉譯為主控台視窗中顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="01016-106">A console uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="01016-107">語法</span><span class="sxs-lookup"><span data-stu-id="01016-107">Syntax</span></span>

```C
UINT WINAPI GetConsoleOutputCP(void);
```

## <a name="parameters"></a><span data-ttu-id="01016-108">參數</span><span class="sxs-lookup"><span data-stu-id="01016-108">Parameters</span></span>

<span data-ttu-id="01016-109">此函式沒有參數。</span><span class="sxs-lookup"><span data-stu-id="01016-109">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="01016-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="01016-110">Return value</span></span>

<span data-ttu-id="01016-111">傳回值是可識別字碼頁的程式碼。</span><span class="sxs-lookup"><span data-stu-id="01016-111">The return value is a code that identifies the code page.</span></span> <span data-ttu-id="01016-112">如需識別碼的清單，請參閱 [字碼頁識別碼](/windows/win32/intl/code-page-identifiers)。</span><span class="sxs-lookup"><span data-stu-id="01016-112">For a list of identifiers, see [Code Page Identifiers](/windows/win32/intl/code-page-identifiers).</span></span>

<span data-ttu-id="01016-113">如果傳回值為零，則函數會失敗。</span><span class="sxs-lookup"><span data-stu-id="01016-113">If the return value is zero, the function has failed.</span></span> <span data-ttu-id="01016-114">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="01016-114">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="01016-115">備註</span><span class="sxs-lookup"><span data-stu-id="01016-115">Remarks</span></span>

<span data-ttu-id="01016-116">字碼頁會將256字元碼對應至個別字元。</span><span class="sxs-lookup"><span data-stu-id="01016-116">A code page maps 256 character codes to individual characters.</span></span> <span data-ttu-id="01016-117">不同的字碼頁包含不同的特殊字元，一般而言是針對語言或語言群組進行自訂。</span><span class="sxs-lookup"><span data-stu-id="01016-117">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span> <span data-ttu-id="01016-118">若要取得字碼頁的詳細資訊（包括其名稱），請參閱 [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) 函數。</span><span class="sxs-lookup"><span data-stu-id="01016-118">To retrieve more information about a code page, including it's name, see the [**GetCPInfoEx**](/windows/win32/api/winnls/nf-winnls-getcpinfoexa) function.</span></span>

<span data-ttu-id="01016-119">若要設定主控台的輸出字碼頁，請使用 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="01016-119">To set a console's output code page, use the [**SetConsoleOutputCP**](setconsoleoutputcp.md) function.</span></span> <span data-ttu-id="01016-120">若要設定及查詢主控台的輸入字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 和 [**GetConsoleCP**](getconsolecp.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="01016-120">To set and query a console's input code page, use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions.</span></span>

## <a name="requirements"></a><span data-ttu-id="01016-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="01016-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="01016-122">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="01016-122">Minimum supported client</span></span> | <span data-ttu-id="01016-123">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="01016-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="01016-124">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="01016-124">Minimum supported server</span></span> | <span data-ttu-id="01016-125">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="01016-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="01016-126">標頭</span><span class="sxs-lookup"><span data-stu-id="01016-126">Header</span></span> | <span data-ttu-id="01016-127">ConsoleApi.h (透過 WinCon.h，包括 Windows.h)</span><span class="sxs-lookup"><span data-stu-id="01016-127">ConsoleApi.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="01016-128">程式庫</span><span class="sxs-lookup"><span data-stu-id="01016-128">Library</span></span> | <span data-ttu-id="01016-129">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="01016-129">Kernel32.lib</span></span> |
| <span data-ttu-id="01016-130">DLL</span><span class="sxs-lookup"><span data-stu-id="01016-130">DLL</span></span> | <span data-ttu-id="01016-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="01016-131">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="01016-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01016-132">See also</span></span>

[<span data-ttu-id="01016-133">主控台字碼頁</span><span class="sxs-lookup"><span data-stu-id="01016-133">Console Code Pages</span></span>](console-code-pages.md)

[<span data-ttu-id="01016-134">主控台函式</span><span class="sxs-lookup"><span data-stu-id="01016-134">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="01016-135">**GetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="01016-135">**GetConsoleCP**</span></span>](getconsolecp.md)

[<span data-ttu-id="01016-136">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="01016-136">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="01016-137">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="01016-137">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)
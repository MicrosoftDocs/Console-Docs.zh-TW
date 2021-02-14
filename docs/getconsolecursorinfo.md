---
title: GetConsoleCursorInfo 函式
description: 針對指定的主控台螢幕緩衝區，抓取資料指標的大小和可見度的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
ms.openlocfilehash: c920e5dd279a23b07702fa12b80da4245561548f
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358448"
---
# <a name="getconsolecursorinfo-function"></a><span data-ttu-id="d31b9-104">GetConsoleCursorInfo 函式</span><span class="sxs-lookup"><span data-stu-id="d31b9-104">GetConsoleCursorInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="d31b9-105">針對指定的主控台螢幕緩衝區，抓取資料指標的大小和可見度的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d31b9-105">Retrieves information about the size and visibility of the cursor for the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="d31b9-106">語法</span><span class="sxs-lookup"><span data-stu-id="d31b9-106">Syntax</span></span>

```C
BOOL WINAPI GetConsoleCursorInfo(
  _In_  HANDLE               hConsoleOutput,
  _Out_ PCONSOLE_CURSOR_INFO lpConsoleCursorInfo
);
```

## <a name="parameters"></a><span data-ttu-id="d31b9-107">參數</span><span class="sxs-lookup"><span data-stu-id="d31b9-107">Parameters</span></span>

<span data-ttu-id="d31b9-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="d31b9-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="d31b9-109">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="d31b9-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="d31b9-110">控制代碼必須具有 **GENERIC\_READ** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="d31b9-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="d31b9-111">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="d31b9-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="d31b9-112">*lpConsoleCursorInfo* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="d31b9-112">*lpConsoleCursorInfo* \[out\]</span></span>  
<span data-ttu-id="d31b9-113">主控台資料指標 [**\_ \_ 資訊**](console-cursor-info-str.md) 結構的指標，此結構會接收主控台資料指標的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d31b9-113">A pointer to a [**CONSOLE\_CURSOR\_INFO**](console-cursor-info-str.md) structure that receives information about the console's cursor.</span></span>

## <a name="return-value"></a><span data-ttu-id="d31b9-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="d31b9-114">Return value</span></span>

<span data-ttu-id="d31b9-115">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="d31b9-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d31b9-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="d31b9-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d31b9-117">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="d31b9-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="d31b9-118">備註</span><span class="sxs-lookup"><span data-stu-id="d31b9-118">Remarks</span></span>

[!INCLUDE [no-vt-equiv-user-priv](./includes/no-vt-equiv-user-priv.md)]

## <a name="requirements"></a><span data-ttu-id="d31b9-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="d31b9-119">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="d31b9-120">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="d31b9-120">Minimum supported client</span></span> | <span data-ttu-id="d31b9-121">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="d31b9-121">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="d31b9-122">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="d31b9-122">Minimum supported server</span></span> | <span data-ttu-id="d31b9-123">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="d31b9-123">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="d31b9-124">標頭</span><span class="sxs-lookup"><span data-stu-id="d31b9-124">Header</span></span> | <span data-ttu-id="d31b9-125">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="d31b9-125">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="d31b9-126">程式庫</span><span class="sxs-lookup"><span data-stu-id="d31b9-126">Library</span></span> | <span data-ttu-id="d31b9-127">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="d31b9-127">Kernel32.lib</span></span> |
| <span data-ttu-id="d31b9-128">DLL</span><span class="sxs-lookup"><span data-stu-id="d31b9-128">DLL</span></span> | <span data-ttu-id="d31b9-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d31b9-129">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="d31b9-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d31b9-130">See also</span></span>

[<span data-ttu-id="d31b9-131">主控台函式</span><span class="sxs-lookup"><span data-stu-id="d31b9-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d31b9-132">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="d31b9-132">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="d31b9-133">**主控台資料 \_ 指標 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="d31b9-133">**CONSOLE\_CURSOR\_INFO**</span></span>](console-cursor-info-str.md)

[<span data-ttu-id="d31b9-134">**SetConsoleCursorInfo**</span><span class="sxs-lookup"><span data-stu-id="d31b9-134">**SetConsoleCursorInfo**</span></span>](setconsolecursorinfo.md)
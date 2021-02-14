---
title: GetConsoleWindow 函式
description: 抓取與呼叫進程相關聯的主控台所使用的視窗控制碼。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetConsoleWindow
- wincon/GetConsoleWindow
- GetConsoleWindow
MS-HAID:
- '\_win32\_getconsolewindow'
- base.getconsolewindow
- consoles.getconsolewindow
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a5ab0b37-45ac-4413-b6ff-73876556ad38
topic_type:
- apiref
api_name:
- GetConsoleWindow
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: ead8c4216fd0d1beb2a5fa6a6acfe3f4ce20df6f
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358888"
---
# <a name="getconsolewindow-function"></a><span data-ttu-id="3c59c-104">GetConsoleWindow 函式</span><span class="sxs-lookup"><span data-stu-id="3c59c-104">GetConsoleWindow function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="3c59c-105">抓取與呼叫進程相關聯的主控台所使用的視窗控制碼。</span><span class="sxs-lookup"><span data-stu-id="3c59c-105">Retrieves the window handle used by the console associated with the calling process.</span></span>

## <a name="syntax"></a><span data-ttu-id="3c59c-106">語法</span><span class="sxs-lookup"><span data-stu-id="3c59c-106">Syntax</span></span>

```C
HWND WINAPI GetConsoleWindow(void);
```

## <a name="parameters"></a><span data-ttu-id="3c59c-107">參數</span><span class="sxs-lookup"><span data-stu-id="3c59c-107">Parameters</span></span>

<span data-ttu-id="3c59c-108">此函式沒有參數。</span><span class="sxs-lookup"><span data-stu-id="3c59c-108">This function has no parameters.</span></span>

## <a name="return-value"></a><span data-ttu-id="3c59c-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="3c59c-109">Return value</span></span>

<span data-ttu-id="3c59c-110">傳回值是與呼叫進程相關聯的主控台所使用的視窗控制碼，如果沒有這類相關聯的主控台，則為 **Null** 。</span><span class="sxs-lookup"><span data-stu-id="3c59c-110">The return value is a handle to the window used by the console associated with the calling process or **NULL** if there is no such associated console.</span></span>

## <a name="remarks"></a><span data-ttu-id="3c59c-111">備註</span><span class="sxs-lookup"><span data-stu-id="3c59c-111">Remarks</span></span>

<span data-ttu-id="3c59c-112">若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0500 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="3c59c-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="3c59c-113">如需詳細資訊，請參閱 [使用 Windows 標頭](/windows/win32/winprog/using-the-windows-headers)。</span><span class="sxs-lookup"><span data-stu-id="3c59c-113">For more information, see [Using the Windows Headers](/windows/win32/winprog/using-the-windows-headers).</span></span>


[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

<span data-ttu-id="3c59c-114">針對裝載在 [**pseudoconsole**](pseudoconsoles.md) 會話內的應用程式，此函式只會傳回訊息佇列用途的視窗控制碼。</span><span class="sxs-lookup"><span data-stu-id="3c59c-114">For an application that is hosted inside a [**pseudoconsole**](pseudoconsoles.md) session, this function returns a window handle for message queue purposes only.</span></span> <span data-ttu-id="3c59c-115">相關聯的視窗不會在本機顯示，因為 _pseudoconsole_ 會將所有動作序列化至另一個終端機視窗上的顯示位置。</span><span class="sxs-lookup"><span data-stu-id="3c59c-115">The associated window is not displayed locally as the _pseudoconsole_ is serializing all actions to a stream for presentation on another terminal window elsewhere.</span></span>

## <a name="requirements"></a><span data-ttu-id="3c59c-116">規格需求</span><span class="sxs-lookup"><span data-stu-id="3c59c-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="3c59c-117">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="3c59c-117">Minimum supported client</span></span> | <span data-ttu-id="3c59c-118">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="3c59c-118">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="3c59c-119">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="3c59c-119">Minimum supported server</span></span> | <span data-ttu-id="3c59c-120">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="3c59c-120">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="3c59c-121">標頭</span><span class="sxs-lookup"><span data-stu-id="3c59c-121">Header</span></span> | <span data-ttu-id="3c59c-122">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="3c59c-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="3c59c-123">程式庫</span><span class="sxs-lookup"><span data-stu-id="3c59c-123">Library</span></span> | <span data-ttu-id="3c59c-124">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="3c59c-124">Kernel32.lib</span></span> |
| <span data-ttu-id="3c59c-125">DLL</span><span class="sxs-lookup"><span data-stu-id="3c59c-125">DLL</span></span> | <span data-ttu-id="3c59c-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3c59c-126">Kernel32.dll</span></span> |

</table>

## <a name="see-also"></a><span data-ttu-id="3c59c-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c59c-127">See also</span></span>

[<span data-ttu-id="3c59c-128">主控台函式</span><span class="sxs-lookup"><span data-stu-id="3c59c-128">Console Functions</span></span>](console-functions.md)
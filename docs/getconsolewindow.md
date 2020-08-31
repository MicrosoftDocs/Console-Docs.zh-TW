---
title: GetConsoleWindow 函式
description: 抓取與呼叫進程相關聯的主控台所使用的視窗控制碼。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
ms.openlocfilehash: dd356bab4674da0cc090e42911829dee994fa8b1
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059107"
---
# <a name="getconsolewindow-function"></a><span data-ttu-id="9dc53-104">GetConsoleWindow 函式</span><span class="sxs-lookup"><span data-stu-id="9dc53-104">GetConsoleWindow function</span></span>


<span data-ttu-id="9dc53-105">抓取與呼叫進程相關聯的主控台所使用的視窗控制碼。</span><span class="sxs-lookup"><span data-stu-id="9dc53-105">Retrieves the window handle used by the console associated with the calling process.</span></span>

<a name="syntax"></a><span data-ttu-id="9dc53-106">語法</span><span class="sxs-lookup"><span data-stu-id="9dc53-106">Syntax</span></span>
------

```C
HWND WINAPI GetConsoleWindow(void);
```

<a name="parameters"></a><span data-ttu-id="9dc53-107">參數</span><span class="sxs-lookup"><span data-stu-id="9dc53-107">Parameters</span></span>
----------

<span data-ttu-id="9dc53-108">此函式沒有參數。</span><span class="sxs-lookup"><span data-stu-id="9dc53-108">This function has no parameters.</span></span>

<a name="return-value"></a><span data-ttu-id="9dc53-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="9dc53-109">Return value</span></span>
------------

<span data-ttu-id="9dc53-110">傳回值是與呼叫進程相關聯的主控台所使用的視窗控制碼，如果沒有這類相關聯的主控台，則為 **Null** 。</span><span class="sxs-lookup"><span data-stu-id="9dc53-110">The return value is a handle to the window used by the console associated with the calling process or **NULL** if there is no such associated console.</span></span>

<a name="remarks"></a><span data-ttu-id="9dc53-111">備註</span><span class="sxs-lookup"><span data-stu-id="9dc53-111">Remarks</span></span>
-------

<span data-ttu-id="9dc53-112">若要編譯使用此函數的應用程式，請將\*\* \_ WIN32 \_ WINNT\*\*定義為0x0500 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="9dc53-112">To compile an application that uses this function, define **\_WIN32\_WINNT** as 0x0500 or later.</span></span> <span data-ttu-id="9dc53-113">如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。</span><span class="sxs-lookup"><span data-stu-id="9dc53-113">For more information, see [Using the Windows Headers](https://msdn.microsoft.com/library/windows/desktop/aa383745).</span></span>

<a name="requirements"></a><span data-ttu-id="9dc53-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="9dc53-114">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="9dc53-115">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="9dc53-115">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="9dc53-116">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="9dc53-116">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="9dc53-117">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="9dc53-117">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="9dc53-118">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="9dc53-118">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="9dc53-119">標頭</span><span class="sxs-lookup"><span data-stu-id="9dc53-119">Header</span></span></p></td>
<td><span data-ttu-id="9dc53-120">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="9dc53-120">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="9dc53-121">程式庫</span><span class="sxs-lookup"><span data-stu-id="9dc53-121">Library</span></span></p></td>
<td><span data-ttu-id="9dc53-122">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="9dc53-122">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="9dc53-123">DLL</span><span class="sxs-lookup"><span data-stu-id="9dc53-123">DLL</span></span></p></td>
<td><span data-ttu-id="9dc53-124">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9dc53-124">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="9dc53-125"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="9dc53-125"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="9dc53-126">主控台功能</span><span class="sxs-lookup"><span data-stu-id="9dc53-126">Console Functions</span></span>](console-functions.md)

 

 





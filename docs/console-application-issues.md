---
title: 主控台應用程式問題
description: 檢查主控台應用程式問題，例如採用或傳回 OEM 字元集字串的函式，以及採用或傳回 ANSI 字元集字串的函式。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_console\_application\_issues'
- base.console\_application\_issues
- consoles.console\_application\_issues
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a561fbdd-b50d-4687-92d7-735377a7991d
ms.openlocfilehash: a1e49e605d1379984ebff7d1737db5ef96c4ff0f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038456"
---
# <a name="console-application-issues"></a><span data-ttu-id="4ecfa-104">主控台應用程式問題</span><span class="sxs-lookup"><span data-stu-id="4ecfa-104">Console Application Issues</span></span>

<span data-ttu-id="4ecfa-105">8位的主控台功能會使用 OEM 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="4ecfa-105">The 8-bit console functions use the OEM code page.</span></span> <span data-ttu-id="4ecfa-106">所有其他函式預設都會使用 ANSI 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="4ecfa-106">All other functions use the ANSI code page by default.</span></span> <span data-ttu-id="4ecfa-107">這表示，其他函式可能無法正確處理主控台函式所傳回的字串，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="4ecfa-107">This means that strings returned by the console functions may not be processed correctly by the other functions and vice versa.</span></span> <span data-ttu-id="4ecfa-108">例如，如果 **FindFirstFileA** 傳回包含某些擴充 ANSI 字元的字串， **WriteConsoleA** 將不會正確地顯示字串。</span><span class="sxs-lookup"><span data-stu-id="4ecfa-108">For example, if **FindFirstFileA** returns a string that contains certain extended ANSI characters, **WriteConsoleA** will not display the string properly.</span></span>

<span data-ttu-id="4ecfa-109">適用于主控台應用程式的最佳長期解決方案是使用 **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** 。</span><span class="sxs-lookup"><span data-stu-id="4ecfa-109">The best long-term solution for a console application is to use **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** .</span></span> <span data-ttu-id="4ecfa-110">使用 **[SetConsoleCP](setconsolecp.md)** 和 **[SETCONSOLEOUTPUTCP](setconsoleoutputcp.md)** 來 `65001` (`CP_UTF8` utf-8 字碼頁的常數) 之後，主控台將會在 api 的 W 變數或 api 的變異上接受 utf-16 編碼。</span><span class="sxs-lookup"><span data-stu-id="4ecfa-110">The console will accept UTF-16 encoding on the W variant of the APIs or UTF-8 encoding on the A variant of the APIs after using **[SetConsoleCP](setconsolecp.md)** and **[SetConsoleOutputCP](setconsoleoutputcp.md)** to `65001` (`CP_UTF8` constant) for the UTF-8 code page.</span></span>

<span data-ttu-id="4ecfa-111">不使用該解決方案，主控台應用程式應該使用 [可透過 setfileapistooem](https://msdn.microsoft.com/library/windows/desktop/aa365534) 函式。</span><span class="sxs-lookup"><span data-stu-id="4ecfa-111">Barring that solution, a console application should use the [SetFileApisToOEM](https://msdn.microsoft.com/library/windows/desktop/aa365534) function.</span></span> <span data-ttu-id="4ecfa-112">該函式會變更相關的檔案功能，使其產生 OEM 字元集字串，而不是 ANSI 字元集字串。</span><span class="sxs-lookup"><span data-stu-id="4ecfa-112">That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.</span></span>

<span data-ttu-id="4ecfa-113">以下是檔案功能：</span><span class="sxs-lookup"><span data-stu-id="4ecfa-113">The following are file functions:</span></span>

:::row:::
    :::column:::
        [<span data-ttu-id="4ecfa-114">CopyFile</span><span class="sxs-lookup"><span data-stu-id="4ecfa-114">CopyFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363851)  
        [<span data-ttu-id="4ecfa-115">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="4ecfa-115">CreateDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363855)  
        [<span data-ttu-id="4ecfa-116">CreateFile</span><span class="sxs-lookup"><span data-stu-id="4ecfa-116">CreateFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363858)  
        [<span data-ttu-id="4ecfa-117">CreateProcess</span><span class="sxs-lookup"><span data-stu-id="4ecfa-117">CreateProcess</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms682425)  
        [<span data-ttu-id="4ecfa-118">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="4ecfa-118">DeleteFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa363915)  
        [<span data-ttu-id="4ecfa-119">FindFirstFile</span><span class="sxs-lookup"><span data-stu-id="4ecfa-119">FindFirstFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364418)  
        [<span data-ttu-id="4ecfa-120">FindNextFile</span><span class="sxs-lookup"><span data-stu-id="4ecfa-120">FindNextFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364428)  
        [<span data-ttu-id="4ecfa-121">GetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="4ecfa-121">GetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364934)  
        [<span data-ttu-id="4ecfa-122">GetDiskFreeSpace</span><span class="sxs-lookup"><span data-stu-id="4ecfa-122">GetDiskFreeSpace</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364935)  
        [<span data-ttu-id="4ecfa-123">GetDriveType</span><span class="sxs-lookup"><span data-stu-id="4ecfa-123">GetDriveType</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364939)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="4ecfa-124">GetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="4ecfa-124">GetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364944)  
        [<span data-ttu-id="4ecfa-125">>getfullpathname</span><span class="sxs-lookup"><span data-stu-id="4ecfa-125">GetFullPathName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364963)  
        [<span data-ttu-id="4ecfa-126">GetModuleFileName</span><span class="sxs-lookup"><span data-stu-id="4ecfa-126">GetModuleFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683197)  
        [<span data-ttu-id="4ecfa-127">GetModuleHandle</span><span class="sxs-lookup"><span data-stu-id="4ecfa-127">GetModuleHandle</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms683199)  
        [<span data-ttu-id="4ecfa-128">GetSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="4ecfa-128">GetSystemDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724373)  
        [<span data-ttu-id="4ecfa-129">GetTempFileName</span><span class="sxs-lookup"><span data-stu-id="4ecfa-129">GetTempFileName</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364991)  
        [<span data-ttu-id="4ecfa-130">GetTempPath</span><span class="sxs-lookup"><span data-stu-id="4ecfa-130">GetTempPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364992)  
        [<span data-ttu-id="4ecfa-131">GetVolumeInformation</span><span class="sxs-lookup"><span data-stu-id="4ecfa-131">GetVolumeInformation</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa364993)  
        [<span data-ttu-id="4ecfa-132">GetWindowsDirectory</span><span class="sxs-lookup"><span data-stu-id="4ecfa-132">GetWindowsDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724454)  
        [<span data-ttu-id="4ecfa-133">LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="4ecfa-133">LoadLibrary</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684175)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="4ecfa-134">LoadLibraryEx</span><span class="sxs-lookup"><span data-stu-id="4ecfa-134">LoadLibraryEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms684179)  
        [<span data-ttu-id="4ecfa-135">MoveFile</span><span class="sxs-lookup"><span data-stu-id="4ecfa-135">MoveFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365239)  
        [<span data-ttu-id="4ecfa-136">MoveFileEx</span><span class="sxs-lookup"><span data-stu-id="4ecfa-136">MoveFileEx</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365240)  
        [<span data-ttu-id="4ecfa-137">OpenFile</span><span class="sxs-lookup"><span data-stu-id="4ecfa-137">OpenFile</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365430)  
        [<span data-ttu-id="4ecfa-138">RemoveDirectory</span><span class="sxs-lookup"><span data-stu-id="4ecfa-138">RemoveDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365488)  
        [<span data-ttu-id="4ecfa-139">SearchPath</span><span class="sxs-lookup"><span data-stu-id="4ecfa-139">SearchPath</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365527)  
        [<span data-ttu-id="4ecfa-140">>setcurrentdirectory</span><span class="sxs-lookup"><span data-stu-id="4ecfa-140">SetCurrentDirectory</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365530)  
        [<span data-ttu-id="4ecfa-141">SetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="4ecfa-141">SetFileAttributes</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365535)  
    :::column-end:::
:::row-end:::

<span data-ttu-id="4ecfa-142">處理命令列時，主控台應用程式應該以 Unicode 格式取得命令列，並使用相關的字元對 OEM 函式將它轉換為 OEM 表單。</span><span class="sxs-lookup"><span data-stu-id="4ecfa-142">When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions.</span></span> <span data-ttu-id="4ecfa-143">另請注意，該 *argv* 會使用 ANSI 字元集。</span><span class="sxs-lookup"><span data-stu-id="4ecfa-143">Note, also, that *argv* uses the ANSI character set.</span></span>

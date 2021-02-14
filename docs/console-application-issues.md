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
ms.openlocfilehash: e81a2b8f6e3b7ba17a7fd704aac868425c86d52c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358268"
---
# <a name="console-application-issues"></a><span data-ttu-id="d6536-104">主控台應用程式問題</span><span class="sxs-lookup"><span data-stu-id="d6536-104">Console Application Issues</span></span>

<span data-ttu-id="d6536-105">8位的主控台功能會使用 OEM 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="d6536-105">The 8-bit console functions use the OEM code page.</span></span> <span data-ttu-id="d6536-106">所有其他函式預設都會使用 ANSI 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="d6536-106">All other functions use the ANSI code page by default.</span></span> <span data-ttu-id="d6536-107">這表示，其他函式可能無法正確處理主控台函式所傳回的字串，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="d6536-107">This means that strings returned by the console functions may not be processed correctly by the other functions and vice versa.</span></span> <span data-ttu-id="d6536-108">例如，如果 **FindFirstFileA** 傳回包含某些擴充 ANSI 字元的字串， **WriteConsoleA** 將不會正確地顯示字串。</span><span class="sxs-lookup"><span data-stu-id="d6536-108">For example, if **FindFirstFileA** returns a string that contains certain extended ANSI characters, **WriteConsoleA** will not display the string properly.</span></span>

<span data-ttu-id="d6536-109">適用于主控台應用程式的最佳長期解決方案是使用 **[Unicode](/windows/win32/intl/unicode)**。</span><span class="sxs-lookup"><span data-stu-id="d6536-109">The best long-term solution for a console application is to use **[Unicode](/windows/win32/intl/unicode)**.</span></span> <span data-ttu-id="d6536-110">使用 **[SetConsoleCP](setconsolecp.md)** 和 **[SETCONSOLEOUTPUTCP](setconsoleoutputcp.md)** 來 `65001` (`CP_UTF8` utf-8 字碼頁的常數) 之後，主控台將會在 api 的 W 變數或 api 的變異上接受 utf-16 編碼。</span><span class="sxs-lookup"><span data-stu-id="d6536-110">The console will accept UTF-16 encoding on the W variant of the APIs or UTF-8 encoding on the A variant of the APIs after using **[SetConsoleCP](setconsolecp.md)** and **[SetConsoleOutputCP](setconsoleoutputcp.md)** to `65001` (`CP_UTF8` constant) for the UTF-8 code page.</span></span>

<span data-ttu-id="d6536-111">不使用該解決方案，主控台應用程式應該使用 [可透過 setfileapistooem](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) 函式。</span><span class="sxs-lookup"><span data-stu-id="d6536-111">Barring that solution, a console application should use the [SetFileApisToOEM](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) function.</span></span> <span data-ttu-id="d6536-112">該函式會變更相關的檔案功能，使其產生 OEM 字元集字串，而不是 ANSI 字元集字串。</span><span class="sxs-lookup"><span data-stu-id="d6536-112">That function changes relevant file functions so that they produce OEM character set strings rather than ANSI character set strings.</span></span>

<span data-ttu-id="d6536-113">以下是檔案功能：</span><span class="sxs-lookup"><span data-stu-id="d6536-113">The following are file functions:</span></span>

:::row:::
    :::column:::
        [<span data-ttu-id="d6536-114">CopyFile</span><span class="sxs-lookup"><span data-stu-id="d6536-114">CopyFile</span></span>](/windows/win32/api/winbase/nf-winbase-copyfile)  
        [<span data-ttu-id="d6536-115">CreateDirectory</span><span class="sxs-lookup"><span data-stu-id="d6536-115">CreateDirectory</span></span>](/windows/win32/api/fileapi/nf-fileapi-createdirectorya)  
        [<span data-ttu-id="d6536-116">CreateFile</span><span class="sxs-lookup"><span data-stu-id="d6536-116">CreateFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-createfilea)  
        [<span data-ttu-id="d6536-117">CreateProcess</span><span class="sxs-lookup"><span data-stu-id="d6536-117">CreateProcess</span></span>](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)  
        [<span data-ttu-id="d6536-118">DeleteFile</span><span class="sxs-lookup"><span data-stu-id="d6536-118">DeleteFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-deletefilea)  
        [<span data-ttu-id="d6536-119">FindFirstFile</span><span class="sxs-lookup"><span data-stu-id="d6536-119">FindFirstFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-findfirstfilea)  
        [<span data-ttu-id="d6536-120">FindNextFile</span><span class="sxs-lookup"><span data-stu-id="d6536-120">FindNextFile</span></span>](/windows/win32/api/fileapi/nf-fileapi-findnextfilea)  
        [<span data-ttu-id="d6536-121">GetCurrentDirectory</span><span class="sxs-lookup"><span data-stu-id="d6536-121">GetCurrentDirectory</span></span>](/windows/win32/api/winbase/nf-winbase-getcurrentdirectory)  
        [<span data-ttu-id="d6536-122">GetDiskFreeSpace</span><span class="sxs-lookup"><span data-stu-id="d6536-122">GetDiskFreeSpace</span></span>](/windows/win32/api/fileapi/nf-fileapi-getdiskfreespacea)  
        [<span data-ttu-id="d6536-123">GetDriveType</span><span class="sxs-lookup"><span data-stu-id="d6536-123">GetDriveType</span></span>](/windows/win32/api/fileapi/nf-fileapi-getdrivetypea)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="d6536-124">GetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="d6536-124">GetFileAttributes</span></span>](/windows/win32/api/fileapi/nf-fileapi-getfileattributesa)  
        [<span data-ttu-id="d6536-125">>getfullpathname</span><span class="sxs-lookup"><span data-stu-id="d6536-125">GetFullPathName</span></span>](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamea)  
        [<span data-ttu-id="d6536-126">GetModuleFileName</span><span class="sxs-lookup"><span data-stu-id="d6536-126">GetModuleFileName</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamea)  
        [<span data-ttu-id="d6536-127">GetModuleHandle</span><span class="sxs-lookup"><span data-stu-id="d6536-127">GetModuleHandle</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlea)  
        [<span data-ttu-id="d6536-128">GetSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="d6536-128">GetSystemDirectory</span></span>](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemdirectorya)  
        [<span data-ttu-id="d6536-129">GetTempFileName</span><span class="sxs-lookup"><span data-stu-id="d6536-129">GetTempFileName</span></span>](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamea)  
        [<span data-ttu-id="d6536-130">GetTempPath</span><span class="sxs-lookup"><span data-stu-id="d6536-130">GetTempPath</span></span>](/windows/win32/api/fileapi/nf-fileapi-gettemppatha)  
        [<span data-ttu-id="d6536-131">GetVolumeInformation</span><span class="sxs-lookup"><span data-stu-id="d6536-131">GetVolumeInformation</span></span>](/windows/win32/api/fileapi/nf-fileapi-getvolumeinformationa)  
        [<span data-ttu-id="d6536-132">GetWindowsDirectory</span><span class="sxs-lookup"><span data-stu-id="d6536-132">GetWindowsDirectory</span></span>](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getwindowsdirectorya)  
        [<span data-ttu-id="d6536-133">LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="d6536-133">LoadLibrary</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibrarya)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="d6536-134">LoadLibraryEx</span><span class="sxs-lookup"><span data-stu-id="d6536-134">LoadLibraryEx</span></span>](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa)  
        [<span data-ttu-id="d6536-135">MoveFile</span><span class="sxs-lookup"><span data-stu-id="d6536-135">MoveFile</span></span>](/windows/win32/api/winbase/nf-winbase-movefile)  
        [<span data-ttu-id="d6536-136">MoveFileEx</span><span class="sxs-lookup"><span data-stu-id="d6536-136">MoveFileEx</span></span>](/windows/win32/api/winbase/nf-winbase-movefileexa)  
        [<span data-ttu-id="d6536-137">OpenFile</span><span class="sxs-lookup"><span data-stu-id="d6536-137">OpenFile</span></span>](/windows/win32/api/winbase/nf-winbase-openfile)  
        [<span data-ttu-id="d6536-138">RemoveDirectory</span><span class="sxs-lookup"><span data-stu-id="d6536-138">RemoveDirectory</span></span>](/windows/win32/api/fileapi/nf-fileapi-removedirectorya)  
        [<span data-ttu-id="d6536-139">SearchPath</span><span class="sxs-lookup"><span data-stu-id="d6536-139">SearchPath</span></span>](/windows/win32/api/processenv/nf-processenv-searchpatha)  
        [<span data-ttu-id="d6536-140">>setcurrentdirectory</span><span class="sxs-lookup"><span data-stu-id="d6536-140">SetCurrentDirectory</span></span>](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory)  
        [<span data-ttu-id="d6536-141">SetFileAttributes</span><span class="sxs-lookup"><span data-stu-id="d6536-141">SetFileAttributes</span></span>](/windows/win32/api/fileapi/nf-fileapi-setfileattributesa)  
    :::column-end:::
:::row-end:::

<span data-ttu-id="d6536-142">處理命令列時，主控台應用程式應該以 Unicode 格式取得命令列，並使用相關的字元對 OEM 函式將它轉換為 OEM 表單。</span><span class="sxs-lookup"><span data-stu-id="d6536-142">When dealing with command lines, a console application should obtain the command line in Unicode form and convert it to OEM form, using the relevant character-to-OEM functions.</span></span> <span data-ttu-id="d6536-143">另請注意，該 *argv* 會使用 ANSI 字元集。</span><span class="sxs-lookup"><span data-stu-id="d6536-143">Note, also, that *argv* uses the ANSI character set.</span></span>
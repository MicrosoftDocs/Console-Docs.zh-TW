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
# <a name="console-application-issues"></a>主控台應用程式問題

8位的主控台功能會使用 OEM 字碼頁。 所有其他函式預設都會使用 ANSI 字碼頁。 這表示，其他函式可能無法正確處理主控台函式所傳回的字串，反之亦然。 例如，如果 **FindFirstFileA** 傳回包含某些擴充 ANSI 字元的字串， **WriteConsoleA** 將不會正確地顯示字串。

適用于主控台應用程式的最佳長期解決方案是使用 **[Unicode](/windows/win32/intl/unicode)**。 使用 **[SetConsoleCP](setconsolecp.md)** 和 **[SETCONSOLEOUTPUTCP](setconsoleoutputcp.md)** 來 `65001` (`CP_UTF8` utf-8 字碼頁的常數) 之後，主控台將會在 api 的 W 變數或 api 的變異上接受 utf-16 編碼。

不使用該解決方案，主控台應用程式應該使用 [可透過 setfileapistooem](/windows/win32/api/fileapi/nf-fileapi-setfileapistooem) 函式。 該函式會變更相關的檔案功能，使其產生 OEM 字元集字串，而不是 ANSI 字元集字串。

以下是檔案功能：

:::row:::
    :::column:::
        [CopyFile](/windows/win32/api/winbase/nf-winbase-copyfile)  
        [CreateDirectory](/windows/win32/api/fileapi/nf-fileapi-createdirectorya)  
        [CreateFile](/windows/win32/api/fileapi/nf-fileapi-createfilea)  
        [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa)  
        [DeleteFile](/windows/win32/api/fileapi/nf-fileapi-deletefilea)  
        [FindFirstFile](/windows/win32/api/fileapi/nf-fileapi-findfirstfilea)  
        [FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilea)  
        [GetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-getcurrentdirectory)  
        [GetDiskFreeSpace](/windows/win32/api/fileapi/nf-fileapi-getdiskfreespacea)  
        [GetDriveType](/windows/win32/api/fileapi/nf-fileapi-getdrivetypea)  
    :::column-end:::
    :::column:::
        [GetFileAttributes](/windows/win32/api/fileapi/nf-fileapi-getfileattributesa)  
        [>getfullpathname](/windows/win32/api/fileapi/nf-fileapi-getfullpathnamea)  
        [GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamea)  
        [GetModuleHandle](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulehandlea)  
        [GetSystemDirectory](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemdirectorya)  
        [GetTempFileName](/windows/win32/api/fileapi/nf-fileapi-gettempfilenamea)  
        [GetTempPath](/windows/win32/api/fileapi/nf-fileapi-gettemppatha)  
        [GetVolumeInformation](/windows/win32/api/fileapi/nf-fileapi-getvolumeinformationa)  
        [GetWindowsDirectory](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getwindowsdirectorya)  
        [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibrarya)  
    :::column-end:::
    :::column:::
        [LoadLibraryEx](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryexa)  
        [MoveFile](/windows/win32/api/winbase/nf-winbase-movefile)  
        [MoveFileEx](/windows/win32/api/winbase/nf-winbase-movefileexa)  
        [OpenFile](/windows/win32/api/winbase/nf-winbase-openfile)  
        [RemoveDirectory](/windows/win32/api/fileapi/nf-fileapi-removedirectorya)  
        [SearchPath](/windows/win32/api/processenv/nf-processenv-searchpatha)  
        [>setcurrentdirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory)  
        [SetFileAttributes](/windows/win32/api/fileapi/nf-fileapi-setfileattributesa)  
    :::column-end:::
:::row-end:::

處理命令列時，主控台應用程式應該以 Unicode 格式取得命令列，並使用相關的字元對 OEM 函式將它轉換為 OEM 表單。 另請注意，該 *argv* 會使用 ANSI 字元集。
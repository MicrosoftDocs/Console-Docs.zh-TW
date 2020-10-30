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
# <a name="console-application-issues"></a>主控台應用程式問題

8位的主控台功能會使用 OEM 字碼頁。 所有其他函式預設都會使用 ANSI 字碼頁。 這表示，其他函式可能無法正確處理主控台函式所傳回的字串，反之亦然。 例如，如果 **FindFirstFileA** 傳回包含某些擴充 ANSI 字元的字串， **WriteConsoleA** 將不會正確地顯示字串。

適用于主控台應用程式的最佳長期解決方案是使用 **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** 。 使用 **[SetConsoleCP](setconsolecp.md)** 和 **[SETCONSOLEOUTPUTCP](setconsoleoutputcp.md)** 來 `65001` (`CP_UTF8` utf-8 字碼頁的常數) 之後，主控台將會在 api 的 W 變數或 api 的變異上接受 utf-16 編碼。

不使用該解決方案，主控台應用程式應該使用 [可透過 setfileapistooem](https://msdn.microsoft.com/library/windows/desktop/aa365534) 函式。 該函式會變更相關的檔案功能，使其產生 OEM 字元集字串，而不是 ANSI 字元集字串。

以下是檔案功能：

:::row:::
    :::column:::
        [CopyFile](https://msdn.microsoft.com/library/windows/desktop/aa363851)  
        [CreateDirectory](https://msdn.microsoft.com/library/windows/desktop/aa363855)  
        [CreateFile](https://msdn.microsoft.com/library/windows/desktop/aa363858)  
        [CreateProcess](https://msdn.microsoft.com/library/windows/desktop/ms682425)  
        [DeleteFile](https://msdn.microsoft.com/library/windows/desktop/aa363915)  
        [FindFirstFile](https://msdn.microsoft.com/library/windows/desktop/aa364418)  
        [FindNextFile](https://msdn.microsoft.com/library/windows/desktop/aa364428)  
        [GetCurrentDirectory](https://msdn.microsoft.com/library/windows/desktop/aa364934)  
        [GetDiskFreeSpace](https://msdn.microsoft.com/library/windows/desktop/aa364935)  
        [GetDriveType](https://msdn.microsoft.com/library/windows/desktop/aa364939)  
    :::column-end:::
    :::column:::
        [GetFileAttributes](https://msdn.microsoft.com/library/windows/desktop/aa364944)  
        [>getfullpathname](https://msdn.microsoft.com/library/windows/desktop/aa364963)  
        [GetModuleFileName](https://msdn.microsoft.com/library/windows/desktop/ms683197)  
        [GetModuleHandle](https://msdn.microsoft.com/library/windows/desktop/ms683199)  
        [GetSystemDirectory](https://msdn.microsoft.com/library/windows/desktop/ms724373)  
        [GetTempFileName](https://msdn.microsoft.com/library/windows/desktop/aa364991)  
        [GetTempPath](https://msdn.microsoft.com/library/windows/desktop/aa364992)  
        [GetVolumeInformation](https://msdn.microsoft.com/library/windows/desktop/aa364993)  
        [GetWindowsDirectory](https://msdn.microsoft.com/library/windows/desktop/ms724454)  
        [LoadLibrary](https://msdn.microsoft.com/library/windows/desktop/ms684175)  
    :::column-end:::
    :::column:::
        [LoadLibraryEx](https://msdn.microsoft.com/library/windows/desktop/ms684179)  
        [MoveFile](https://msdn.microsoft.com/library/windows/desktop/aa365239)  
        [MoveFileEx](https://msdn.microsoft.com/library/windows/desktop/aa365240)  
        [OpenFile](https://msdn.microsoft.com/library/windows/desktop/aa365430)  
        [RemoveDirectory](https://msdn.microsoft.com/library/windows/desktop/aa365488)  
        [SearchPath](https://msdn.microsoft.com/library/windows/desktop/aa365527)  
        [>setcurrentdirectory](https://msdn.microsoft.com/library/windows/desktop/aa365530)  
        [SetFileAttributes](https://msdn.microsoft.com/library/windows/desktop/aa365535)  
    :::column-end:::
:::row-end:::

處理命令列時，主控台應用程式應該以 Unicode 格式取得命令列，並使用相關的字元對 OEM 函式將它轉換為 OEM 表單。 另請注意，該 *argv* 會使用 ANSI 字元集。

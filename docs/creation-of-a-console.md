---
title: 建立主控台
description: 系統會在啟動主控台程序 (其進入點為主要函式的字元模式程序) 時，建立新的主控台。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_creation\_of\_a\_console'
- base.creation\_of\_a\_console
- consoles.creation\_of\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ec2559-cade-447e-8594-5b824d3d3e81
ms.localizationpriority: high
ms.openlocfilehash: 09de42ced585e4a644fbbcc04211d5cb6037c2af
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420277"
---
# <a name="creation-of-a-console"></a>建立主控台

系統會在啟動主控台程序 (其進入點為 **主要** 函式的字元模式程序) 時，建立新的主控台。 例如，系統會在啟動命令處理器 `cmd.exe` 時，建立新的主控台。 當命令處理器啟動新的主控台程序時，使用者可以指定系統是否要為新的程序建立新的主控台，或其是否要繼承命令處理器的主控台。

程序可以使用下列其中一種方法來建立主控台：

- 圖形使用者介面 (GUI) 或主控台程序可以使用 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 函式搭配 **CREATE\_NEW\_CONSOLE**，以新的主控台建立主控台程序。 (根據預設，主控台程序會繼承其父系的主控台，而且不保證輸入會由其所預期的程序所接收。)
- 目前未連結至主控台的 GUI 或主控台程序可以使用 [**AllocConsole**](allocconsole.md) 函式來建立新的主控台。 (GUI 程序不會在建立時連結至主控台。 使用 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 搭配 **DETACHED\_PROCESS** 建立的主控台程序不會連結至主控台。)

一般而言，若在需要與使用者互動時發生錯誤，程序會使用 [**AllocConsole**](allocconsole.md) 來建立主控台。 例如，GUI 程序可以在發生錯誤而無法使用一般圖形介面時建立主控台，或通常不會與使用者互動的主控台程序可以建立主控台來顯示錯誤。

程序也可以在 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 的呼叫中指定 **CREATE\_NEW\_CONSOLE** 旗標來建立主控台。 此方法會建立子程序可存取但父程序無法存取的新主控台。 個別的主控台可讓父程序和子程序同時與使用者互動，而不會發生衝突。 如果建立主控台程序時未指定此旗標，則兩個程序都會連結至相同的主控台，而且不保證輸入會由正確的程序收到。 應用程式若要避免混淆，可以建立不會繼承輸入緩衝區控制代碼的子程序，或一次只啟用一個子程序來繼承輸入緩衝區控制代碼，並避免父程序在子程序完成之前讀取主控台輸入。

建立新的主控台會產生新的主控台視窗，以及個別的 I/O 畫面緩衝區。 與新主控台相關聯的程序會使用 [**GetStdHandle**](getstdhandle.md) 函式來取得新主控台輸入和畫面緩衝區的控制代碼。 這些控制代碼可讓程序存取主控台。

程序可以在使用 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 時指定 [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) 結構，針對為子程序建立的第一個新主控台 (如果有的話)，該結構的成員會控制其特性。 如果指定 **CREATE\_NEW\_CONSOLE** 旗標，在 **CreateProcess** 的呼叫中指定的 **STARTUPINFO** 結構會影響建立的主控台。 如果子程序後續使用 [**AllocConsole**](allocconsole.md)，其也會影響所建立的主控台。 您可以指定下列主控台特性：

- 新主控台視窗的大小 (以字元資料格表示)
- 新主控台視窗的位置 (以畫面像素座標表示)
- 新主控台畫面緩衝區的大小 (以字元資料格表示)
- 新主控台畫面緩衝區的文字和背景色彩屬性
- 新主控台視窗標題列的顯示名稱

如果未指定 [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) 值，系統會使用預設值。 子程序可以使用 [**GetStartupInfo**](https://msdn.microsoft.com/library/windows/desktop/ms683230) 函式來判斷其 **STARTUPINFO** 結構中的值。

程序無法變更其主控台視窗在畫面上的位置，但是您可以使用下列主控台函式來設定或擷取 [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) 結構中指定的其他屬性。

| 函式 | 說明 |
|-|-|
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) | 擷取視窗大小、畫面緩衝區大小和色彩屬性。 |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md)  | 變更控制台視窗的大小。  |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) | 變更主控台畫面緩衝區的大小。 |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md) | 設定色彩屬性。  |
| [**SetConsoleTitle**](setconsoletitle.md)  | 設定主控台視窗標題。 |
| [**GetConsoleTitle**](getconsoletitle.md)  | 擷取主控台視窗標題。  |

程序可以使用 [**FreeConsole**](freeconsole.md) 函式，將自己從繼承的主控台或由 [**AllocConsole**](allocconsole.md) 所建立的主控台卸離。

程序使用 [**FreeConsole**](freeconsole.md) 從自己的工作階段卸離後 (或者，如果沒有任何連結的工作階段)，可以使用 [**AttachConsole**](attachconsole.md) 函式將本身連結至另一個現有的主控台工作階段。

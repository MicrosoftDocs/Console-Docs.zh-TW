---
title: 建立主控台
description: 系統會在啟動主控台進程時建立新的主控台，其進入點是主要函式的字元模式進程。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_creation\_of\_a\_console'
- base.creation\_of\_a\_console
- consoles.creation\_of\_a\_console
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 84ec2559-cade-447e-8594-5b824d3d3e81
ms.openlocfilehash: b3b4143596035fed6896243043853932ae68233f
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059218"
---
# <a name="creation-of-a-console"></a>建立主控台


系統會在啟動 *主控台進程*時建立新的主控台，其進入點是 **主要** 函式的字元模式進程。 例如，當系統啟動命令處理器時，系統會建立新的主控台。 當命令處理器啟動新的主控台進程時，使用者可以指定系統是否為新的進程建立新的主控台，或是否要繼承命令處理器的主控台。

處理常式可以使用下列其中一種方法來建立主控台：

- GUI 或主控台進程可以搭配使用 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 函式與 **建立 \_ 新的 \_ 主控台** ，以使用新的主控台建立主控台進程。  (根據預設，主控台進程會繼承其父代的主控台，而且不保證會由其預定的進程接收輸入。 ) 
- 目前未連接到主控台的圖形化使用者介面 (GUI) 或主控台進程，可以使用 [**AllocConsole**](allocconsole.md) 函式來建立新的主控台。  (GUI 進程在建立時不會附加至主控台。 主控台進程如果是使用具有卸**離 \_ 進程**的[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)來建立，則不會連接到主控台。 ) 

一般來說，當發生需要與使用者互動的錯誤時，進程會使用 [**AllocConsole**](allocconsole.md) 來建立主控台。 例如，GUI 進程可以在發生錯誤時建立主控台，使其無法使用其一般圖形介面，或者通常不與使用者互動的主控台進程可以建立主控台來顯示錯誤。

進程也可以在對[**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)的呼叫中指定 [**建立 \_ 新的 \_ 主控台**] 旗標，藉以建立主控台。 這個方法會建立可供子進程存取的新主控台，而不是父進程。 個別的主控台可讓父系和子進程與使用者互動，而不會發生衝突。 如果建立主控台進程時未指定此旗標，則這兩個處理常式會附加到相同的主控台，而且不保證正確的程式會收到所需的輸入。 應用程式可以藉由建立不繼承輸入緩衝區控制碼的子進程，或一次只啟用一個子進程來繼承輸入緩衝區控制碼，並防止父進程讀取主控台輸入，直到子系完成為止，藉此防止混淆。

建立新的主控台會產生新的主控台視窗，以及個別的 i/o 螢幕緩衝區。 與新主控台相關聯的進程會使用 [**GetStdHandle**](getstdhandle.md) 函式來取得新主控台之輸入和螢幕緩衝區的控制碼。 這些控點可讓進程存取主控台。

當處理常式使用 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425)時，它可以指定 [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) 結構，其成員可控制第一個新主控台的特性 (如果為子進程建立的任何) 。 如果指定了**建立 \_ 新的 \_ 主控台**旗標，則在對**CreateProcess**的呼叫中指定的**STARTUPINFO**結構會影響主控台所建立的。 如果子進程後續使用 [**AllocConsole**](allocconsole.md)，它也會影響建立的主控台。 您可以指定下列主控台特性：

- 新主控台視窗的大小（以字元儲存格為限）
- 新主控台視窗的位置，以螢幕圖元座標表示
- 新主控台的螢幕緩衝區大小，以字元儲存格為限
- 新主控台螢幕緩衝區的文字和背景色彩屬性
- 新主控台視窗之標題列的顯示名稱

如果未指定 [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) 值，系統會使用預設值。 子進程可以使用 [**GetStartupInfo**](https://msdn.microsoft.com/library/windows/desktop/ms683230) 函數來判斷其 **STARTUPINFO** 結構中的值。

進程無法變更其主控台視窗在螢幕上的位置，但是下列主控台函式可用來設定或抓取 [**STARTUPINFO**](https://msdn.microsoft.com/library/windows/desktop/ms686331) 結構中指定的其他屬性。


| 函式                                                         | 描述                                                          |
|------------------------------------------------------------------|----------------------------------------------------------------------|
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) | 抓取視窗大小、螢幕緩衝區大小和色彩屬性。 |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md)             | 變更控制台視窗的大小。                              |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) | 變更控制台螢幕緩衝區的大小。                       |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md)       | 設定色彩屬性。                                           |
| [**SetConsoleTitle**](setconsoletitle.md)                       | 設定主控台視窗標題。                                       |
| [**GetConsoleTitle**](getconsoletitle.md)                       | 抓取主控台視窗標題。                                  |




進程可以使用 [**FreeConsole**](freeconsole.md) 函式，從繼承的主控台或 [**AllocConsole**](allocconsole.md)所建立的主控台卸離本身。









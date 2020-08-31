---
title: 視窗和螢幕緩衝區大小
description: 螢幕緩衝區的大小是根據字元儲存格以座標方格表示。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_window\_and\_screen\_buffer\_size'
- base.window\_and\_screen\_buffer\_size
- consoles.window\_and\_screen\_buffer\_size
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55246039-31eb-41ca-ad8e-d314cb508644
ms.openlocfilehash: 86a8967eeff35a7a5416273e639ba8bbe5a31ef1
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059534"
---
# <a name="window-and-screen-buffer-size"></a>視窗和螢幕緩衝區大小


螢幕緩衝區的大小是根據字元儲存格以座標方格表示。 寬度是每個資料列中的字元資料格數目，而高度是資料列的數目。 與每個螢幕緩衝區相關聯的視窗，會決定主控台視窗中顯示的主控台螢幕緩衝區矩形部分的大小和位置。 螢幕緩衝區的視窗是藉由指定視窗矩形左上角和右下角儲存格的字元儲存格座標來定義。

螢幕緩衝區可以是任何大小，只受限於可用的記憶體。 螢幕緩衝區視窗的大小不能超過主控台螢幕緩衝區的對應維度或可在螢幕上容納的最大視窗大小（根據目前的字型大小 (由使用者) 獨佔控制）。

[**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)函式會傳回關於螢幕緩衝區和其視窗的下列資訊：

- 目前的主控台螢幕緩衝區大小
- 視窗的目前位置
- 指定目前螢幕緩衝區大小、目前的字型大小和螢幕大小的視窗大小上限

[**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md)函式會根據目前的字型和螢幕大小，傳回主控台視窗的大小上限。 這個大小與 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 所傳回的最大視窗大小不同，因為會忽略主控台螢幕緩衝區大小。

若要變更螢幕緩衝區大小，請使用 [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) 函數。 如果指定大小的任一維度小於主控台視窗的對應維度，則此函式會失敗。

若要變更螢幕緩衝區視窗的大小或位置，請使用 [**SetConsoleWindowInfo**](setconsolewindowinfo.md) 函數。 如果指定的視窗邊角座標超過主控台螢幕緩衝區或畫面的限制，則此函式會失敗。 變更作用中螢幕緩衝區的視窗大小，會變更顯示在畫面上的主控台視窗大小。

進程可以變更其主控台的輸入模式，以啟用視窗輸入，讓程式能夠在使用者變更控制台螢幕緩衝區大小時接收輸入。 如果應用程式啟用視窗輸入，就可以在啟動時使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 來取得視窗和螢幕緩衝區大小。 然後，您可以使用此資訊來決定資料在視窗中的顯示方式。 如果使用者變更控制台螢幕緩衝區大小，則應用程式可以藉由變更資料顯示方式來回應。 例如，如果每個資料列的字元數變更，應用程式可以調整文字在行尾換行的方式。 如果應用程式未啟用視窗輸入，則必須使用繼承的視窗和螢幕緩衝區大小，或在啟動期間將它們設定為所需的大小，並在結束時還原繼承的大小。 如需有關視窗輸入模式的詳細資訊，請參閱 [低層級主控台模式](low-level-console-modes.md)。

 

 





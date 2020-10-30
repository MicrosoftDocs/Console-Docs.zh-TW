---
title: 滾動螢幕緩衝區
description: 描述主控台視窗如何顯示作用中螢幕緩衝區的一部分。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_scrolling\_the\_screen\_buffer'
- base.scrolling\_the\_screen\_buffer
- consoles.scrolling\_the\_screen\_buffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c8404e78-9807-4bed-bc12-25377fa96151
ms.openlocfilehash: 1582b6232461469e10048ed8711c766a6821264f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037596"
---
# <a name="scrolling-the-screen-buffer"></a>滾動螢幕緩衝區

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

主控台視窗會顯示作用中螢幕緩衝區的一部分。 每個螢幕緩衝區都會維護它自己的目前視窗矩形，以指定要在主控台視窗中顯示的左上角和右下角字元資料格的座標。 若要判斷螢幕緩衝區的目前視窗矩形，請使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md)。 建立螢幕緩衝區時，其視窗的左上角位於主控台螢幕緩衝區的左上角，位於 (0，0) 。

視窗矩形可以變更，以顯示主控台螢幕緩衝區的不同部分。 螢幕緩衝區的視窗矩形可能會在下列情況下變更：

- 當呼叫 [**SetConsoleWindowInfo**](setconsolewindowinfo.md) 來指定新的視窗矩形時，會變更視窗矩形的位置，而不變更視窗的大小，藉此滾動主控台畫面緩衝區的視圖。 如需滾動視窗內容的範例，請參閱 [滾動螢幕緩衝區的視窗](scrolling-a-screen-buffer-s-window.md)。

  ![螢幕緩衝區視窗移動大型緩衝區內容](images/cscon-01.png)

- 當使用 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 函式來寫入換行的螢幕緩衝區時，如果已啟用行尾 (EOL) 輸出模式，則視窗矩形會自動移動，因此一律會顯示游標。
- 當 [**SetConsoleCursorPosition**](setconsolecursorposition.md) 函式指定的新資料指標位置超出目前視窗矩形的界限時，視窗矩形會自動移動以顯示游標。
- 當使用者變更控制台視窗的大小，或使用視窗的捲軸時，可以變更現用螢幕緩衝區的視窗矩形。 這項變更不會回報為輸入緩衝區中的視窗大小事件。

在上述每一種情況下，視窗矩形會切換為顯示主控台螢幕緩衝區的不同部分，但是主控台畫面緩衝區的內容會保留在相同的位置。 下列情況可能會導致主控台畫面緩衝區的內容轉移：

- 呼叫 [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 函式時，會從螢幕緩衝區的某個部分將矩形區塊複製到另一個部分。
- 當您使用 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 寫入到已啟用 wrap 輸出模式的螢幕緩衝區時，主控台畫面緩衝區的內容會在遇到主控台畫面緩衝區的結尾時自動滾動。 這項滾動會捨棄主控台畫面緩衝區的頂端列。

[**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 指定移動的主控台螢幕緩衝區矩形，以及要複製矩形的新左上座標。 此函式可將主控台螢幕緩衝區的一部分或整個內容滾動。

下圖顯示的 [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 作業，會將主控台畫面緩衝區的整個內容，由數個數據列滾動。 將會捨棄頂端資料列的內容，並以指定的字元和色彩填滿底部的資料列。

![螢幕緩衝區視窗將內容從上方滾動至捨棄](images/cscon-02.png)

您可以藉由指定選擇性裁剪矩形來限制 [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) 的效果，如此一來，裁剪矩形外的主控台螢幕緩衝區內容就不會變更。 裁剪的效果是建立子視窗 (剪切矩形) 其內容會在不影響主控台螢幕緩衝區其餘部分的情況下滾動。 如需使用 **ScrollConsoleScreenBuffer** 的範例，請參閱 [滾動螢幕緩衝區的內容](scrolling-a-screen-buffer-s-contents.md)。

---
title: 輸入和輸出方法
description: 主控台 i/o 有兩種不同的方法，其選擇取決於應用程式所需的彈性和控制程度。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_input\_and\_output\_methods'
- base.input\_and\_output\_methods
- consoles.input\_and\_output\_methods
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 55a86d5d-d0b1-4d0c-b42f-7342809289ad
ms.openlocfilehash: 29f4ca8f4851c73f79d810f56b57f490995cad04
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059487"
---
# <a name="input-and-output-methods"></a>輸入和輸出方法


主控台 i/o 有兩種不同的方法，其選擇取決於應用程式所需的彈性和控制程度。 高階方法可啟用簡單的字串流 i/o，但它會限制對主控台的輸入和螢幕緩衝區的存取。 低層級的方法需要開發人員撰寫更多程式碼，並在更廣泛的函式中進行選擇，但它也能讓應用程式更有彈性。

應用程式可以使用檔案 i/o 函式、 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 和 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)，以及主控台函式（ [**ReadConsole**](readconsole.md) 和 [**WriteConsole**](writeconsole.md)），以取得可間接存取主控台的輸入和螢幕緩衝區的高階 i/o 功能。 高階輸入函式會篩選和處理主控台輸入緩衝區中的資料，將輸入以字元資料流的形式傳回，並捨棄滑鼠和緩衝區大小的輸入。 同樣地，高階輸出函式會寫入螢幕緩衝區中目前游標位置所顯示的字元資料流。 應用程式會藉由設定主控台的 i/o 模式來控制這些函式的運作方式。

低層級 i/o 函數可讓您直接存取主控台的輸入和螢幕緩衝區，讓應用程式能夠存取滑鼠和緩衝區大小的輸入事件，以及鍵盤事件的延伸資訊。 低層級的輸出函式可讓應用程式讀取或寫入螢幕緩衝區中指定數目的連續字元資料格，或讀取或寫入螢幕緩衝區中指定位置的字元資料格的矩形區塊。 主控台的輸入模式會影響低層級的輸入，方法是讓應用程式判斷滑鼠和緩衝區調整大小事件是否放置於輸入緩衝區中。 主控台的輸出模式不會影響低層級的輸出。

高階層級和低層級 i/o 方法不是互斥的，應用程式可以使用這些函式的任何組合。 不過，應用程式通常會使用一個方法或另一個方法。

下列主題描述主控台模式以及高階和低層級的 i/o 函式。

- [主控台模式](console-modes.md)
- [高層級主控台 i/o](high-level-console-i-o.md)
- [高層級主控台模式](high-level-console-modes.md)
- [高層級主控台輸入和輸出功能](high-level-console-input-and-output-functions.md)
- [低層級主控台 i/o](low-level-console-i-o.md)
- [低層級主控台模式](low-level-console-modes.md)
- [低層級主控台輸入函式](low-level-console-input-functions.md)
- [低層級主控台輸出功能](low-level-console-output-functions.md)

 

 





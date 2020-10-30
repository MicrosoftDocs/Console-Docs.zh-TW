---
title: Low-Level 主控台輸出函式
description: 低層級的主控台輸出函式可讓您直接存取螢幕緩衝區的字元儲存格。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_low\_level\_console\_output\_functions'
- base.low\_level\_console\_output\_functions
- consoles.low\_level\_console\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 94185428-e8c7-4926-93ec-867b8c97b4ca
ms.openlocfilehash: 70782c7bdc6d009be97315d3405cd44e4e7aa866
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038556"
---
# <a name="low-level-console-output-functions"></a>Low-Level 主控台輸出函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

低層級的主控台輸出函式可讓您直接存取螢幕緩衝區的字元儲存格。 一組函式會從主控台螢幕緩衝區中的任何位置開始，讀取或寫入連續的儲存格。 另一組函數會讀取或寫入儲存格的矩形區塊。

下列函式會從指定的資料格開始，讀取或寫入螢幕緩衝區中指定數目的連續字元儲存格。

| 函式 | 描述 |
|-|-|
| [**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md) | 從螢幕緩衝區複製 Unicode 或 ANSI 字元字串。 |
| [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md) | 將 Unicode 或 ANSI 字元字串寫入螢幕緩衝區。 |
| [**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md) | 從螢幕緩衝區複製文字和背景色彩屬性的字串。 |
| [**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md) | 將文字和背景色彩屬性的字串寫入螢幕緩衝區。 |
| [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) | 將單一 Unicode 或 ANSI 字元寫入螢幕緩衝區中指定數目的連續儲存格。 |
| [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) | 將文字和背景色彩屬性組合寫入螢幕緩衝區中指定數目的連續儲存格。 |

針對所有這些函式，當遇到資料列的最後一個資料格時，讀取或寫入至下一個資料列的第一個資料格。 當遇到主控台畫面緩衝區最後一個資料列的結尾時，寫入函式會捨棄所有不成文的字元或屬性，而 read 函數會報告實際寫入的字元數或屬性數目。

下列函式會讀取或寫入螢幕緩衝區中指定位置之字元資料格的矩形區塊。

| 函式 | 描述 |
|-|-|
| [**ReadConsoleOutput**](readconsoleoutput.md) | 將字元和色彩資料從指定的螢幕緩衝區資料格區塊複製到目的緩衝區中的指定區塊。 |
| [**WriteConsoleOutput**](writeconsoleoutput.md) | 從來源緩衝區中的指定區塊，將字元和色彩資料寫入指定的螢幕緩衝區資料格區塊。 |

這些函數會將螢幕緩衝區和來源或目的地緩衝區視為 [**CHAR \_ 資訊**](char-info-str.md) 結構的二維陣列， (包含每個資料格) 的字元和色彩屬性資料。 這些函數會指定來源或目的地緩衝區的寬度和高度（以字元資料格為限），而緩衝區的指標會被視為原始資料格的指標， (0，0) 的二維陣列。 這些函式會使用 [**小型 \_ RECT**](small-rect-str.md) 結構來指定要在主控台螢幕緩衝區中存取的矩形，以及來源或目的地緩衝區中左上方儲存格的座標，決定該緩衝區中對應矩形的位置。

這些函式會自動裁剪指定的螢幕緩衝區矩形，使其符合主控台螢幕緩衝區的界限內。 例如，如果矩形指定的右下座標是 (資料行100、資料列 50) ，而且主控台螢幕緩衝區只是80資料行，則會裁剪座標，使其 (資料行79、資料列 50) 。 同樣地，這個調整的矩形會再次裁剪，以符合來源或目的緩衝區的界限。 指定讀取或寫入之實際矩形的螢幕緩衝區座標。 如需使用這些函數的範例，請參閱 [讀取和寫入字元和屬性的區塊](reading-and-writing-blocks-of-characters-and-attributes.md)。

下圖顯示在從主控台螢幕緩衝區讀取區塊時，以及當區塊複製到目的緩衝區時，發生裁剪的 [**ReadConsoleOutput**](readconsoleoutput.md) 作業。 函數會報告其複製來源的實際螢幕緩衝區矩形。

![具有目的地緩衝區的螢幕緩衝區視窗](images/cscon-03.png)

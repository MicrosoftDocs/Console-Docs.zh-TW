---
ms.openlocfilehash: eaaaa3487e8f2aa95915f6f10724bf4c26784622
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038869"
---
主控台包含輸入緩衝區和一或多個螢幕緩衝區。 主控台緩衝區的模式會決定主控台在輸入或輸出 (i/o) 作業時的行為。 有一組旗標常數用於輸入控制碼，而另一組則是與螢幕緩衝區 (輸出) 控制碼一起使用。 設定一個螢幕緩衝區的輸出模式，並不會影響其他螢幕緩衝區的輸出模式。

「 **啟用 \_ 行 \_ 輸入** 」和「 **啟用 \_ ECHO \_ 輸入** 」模式只會影響使用 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 或 [**ReadConsole**](../readconsole.md) 從主控台的輸入緩衝區讀取的進程。 同樣地， **啟用 \_ 處理的 \_ 輸入** 模式主要會影響 **ReadFile** 和 **ReadConsole** 使用者，不同之處在于它也會決定在輸入緩衝區中是否報告 CTRL + C 輸入 (由 [**ReadConsoleInput**](../readconsoleinput.md) 函式讀取) 或傳遞給應用程式所定義的函式。

[ **啟用 \_ 視窗 \_ 輸入]** 和 [ **啟用 \_ 滑鼠 \_ 輸入** ] 模式會決定是否要在輸入緩衝區中報告與視窗調整大小和滑鼠動作相關的使用者互動。 這些事件可由 [**ReadConsoleInput**](../readconsoleinput.md)讀取，但一律會依 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 和 [**ReadConsole**](../readconsole.md)進行篩選。

在 **\_ \_ \_ EOL \_ 輸出** 模式下 **啟用已處理的 \_ \_ 輸出** 和啟用 WRAP，只會影響使用 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)或 [**ReadConsole**](../readconsole.md)和 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)或 [**WriteConsole**](../writeconsole.md)的進程。

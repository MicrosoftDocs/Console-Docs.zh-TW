---
ms.openlocfilehash: eaaaa3487e8f2aa95915f6f10724bf4c26784622
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "93038869"
---
主控台包含一個輸入緩衝區和一或多個螢幕緩衝區。 主控台緩衝區的模式可決定主控台在輸入或輸出 (I/O) 作業期間的行為。 一組旗標常數用於搭配輸入控點，而另一組則搭配螢幕緩衝區 (輸出) 控點使用。 設定一個螢幕緩衝區的輸出模式並不會影響其他螢幕緩衝區的輸出模式。

**ENABLE\_LINE\_INPUT** 和 **ENABLE\_ECHO\_INPUT** 模式只會影響使用 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 或 [**ReadConsole**](../readconsole.md) 從主控台的輸入緩衝區讀取的程序。 同樣地，**ENABLE\_PROCESSED\_INPUT** 模式主要會影響 **ReadFile** 和 **ReadConsole** 使用者，不同的是，其也會決定是否在輸入緩衝區中報告 CTRL+C 輸入 (將由 [**ReadConsoleInput**](../readconsoleinput.md) 函式讀取)，或傳遞至應用程式所定義的函式。

**ENABLE\_WINDOW\_INPUT** 和 **ENABLE\_MOUSE\_INPUT** 模式可決定是否在輸入緩衝區中報告與視窗大小調整和滑鼠動作有關的使用者互動，或予以捨棄。 這些事件可由 [**ReadConsoleInput**](../readconsoleinput.md)讀取，但一律會依 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 和 [**ReadConsole**](../readconsole.md) 進行篩選。

**ENABLE\_PROCESSED\_OUTPUT** 和 **ENABLE\_WRAP\_AT\_EOL\_OUTPUT** 模式只會影響使用 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 或 [**ReadConsole**](../readconsole.md) 和 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 或 [**WriteConsole**](../writeconsole.md) 的程序。

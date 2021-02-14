---
title: High-Level 主控台輸入和輸出功能
description: ReadFile 和 WriteFile 函式，或 ReadConsole 和 WriteConsole 函式可讓應用程式讀取主控台輸入，並以字串流的形式寫入主控台輸出。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_high\_level\_console\_input\_and\_output\_functions'
- base.high\_level\_console\_input\_and\_output\_functions
- consoles.high\_level\_console\_input\_and\_output\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 086b1bec-85f8-4e31-848d-7cb2d2703a3d
ms.openlocfilehash: 4da8845e4e35170980d306930c182ff6e5fb6cbf
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358298"
---
# <a name="high-level-console-input-and-output-functions"></a>High-Level 主控台輸入和輸出功能

[**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile)和 [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile)函式，或 [**ReadConsole**](readconsole.md)和 [**WriteConsole**](writeconsole.md)函式可讓應用程式讀取主控台輸入，並以字串流的形式寫入主控台輸出。 **ReadConsole** 和 **WriteConsole** 的行為與 **ReadFile** 和 **WriteFile** 的行為完全相同，不同之處在于可以將它們當做寬字元函式使用 (其中 text 引數必須使用 Unicode) 或作為 ANSI 函式 (其中文字引數必須使用 Windows 字元集) 中的字元。 需要維護一組來源以支援 Unicode 或 ANSI 字元集的應用程式應該使用 **ReadConsole** 和 **WriteConsole**。

[**ReadConsole**](readconsole.md) 和 [**WriteConsole**](writeconsole.md) 只能搭配使用主控台控制碼; [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) 和 [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) 可搭配其他控制碼使用， (例如檔案或管道) 。 **ReadConsole** 和 **WriteConsole** 如果搭配已重新導向且不再是主控台控制碼的標準控制碼使用，則會失敗。

若要取得鍵盤輸入，處理常式可以使用 [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) 或 [**ReadConsole**](readconsole.md) 搭配主控台輸入緩衝區的控制碼，也可以使用 **ReadFile** 從檔案或管道讀取輸入（如果已重新導向） `STDIN` 。 這些函式只會傳回可轉譯為 ANSI 或 Unicode 字元的鍵盤事件。 可以傳回的輸入包含控制項按鍵組合。 這些函式不會傳回包含函式按鍵或箭號按鍵的鍵盤事件。 系統會捨棄滑鼠、視窗、焦點或功能表輸入所產生的輸入事件。

如果已啟用行輸入模式 (預設模式) ， [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) 和 [**ReadConsole**](readconsole.md) 在按下 ENTER 鍵之前，不會返回呼叫的應用程式。 如果已停用行輸入模式，在至少有一個字元可用之前，函式不會傳回。 在任一種模式下，都會讀取所有可用的字元，直到沒有其他可用的索引鍵或已讀取指定的字元數為止。 在下一次讀取作業之前，會緩衝處理未讀取的字元。 這些函數會報告實際讀取的字元總數。 如果已啟用 echo 輸入模式，這些函式所讀取的字元會寫入目前游標位置的作用中螢幕緩衝區。

處理常式可以使用 [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) 或 **WriteConsole** 來寫入作用中或非作用中的螢幕緩衝區，或者可以使用 **WriteFile** 來寫入檔案，或在 STDOUT 重新導向時使用管道。 已處理的輸出模式並在 EOL 輸出模式下換行，可控制字元寫入或送至螢幕緩衝區的方式。

由 [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) 或 [**WriteConsole**](writeconsole.md)或由 [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) 或 [**ReadConsole**](readconsole.md)所撰寫的字元，會在目前游標位置的螢幕緩衝區中插入。 寫入每個字元時，游標位置會前進到下一個字元資料格;不過，資料列結尾的行為取決於在 EOL 輸出模式下的主控台畫面緩衝區換行。

有關資料指標位置的進一步詳細資料，可透過 **[虛擬終端機序列](console-virtual-terminal-sequences.md)** 找到，特別是在尋找目前位置的 **[查詢狀態](console-virtual-terminal-sequences.md#query-state)** 類別目錄，以及用來設定目前位置的資料 **[指標定位](console-virtual-terminal-sequences.md#cursor-positioning)** 類別目錄。 或者，應用程式可以使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函式來判斷目前的資料指標位置，以及使用 [**SetConsoleCursorPosition**](setconsolecursorposition.md) 函數來設定資料指標的位置。 不過，建議所有新的和進行中的開發都要有 **虛擬終端機序列** 機制。 如需此決策背後策略的詳細資訊，請參閱 **[傳統功能與虛擬終端](classic-vs-vt.md)** 機和 **[生態系統藍圖](ecosystem-roadmap.md)** 檔。

如需使用高階主控台 i/o 函式的範例，請參閱 [使用 High-Level 輸入和輸出函數](using-the-high-level-input-and-output-functions.md)。
---
title: High-Level 主控台 i/o
description: 高階 i/o 函數提供簡單的方法，從主控台輸入讀取字串流，或將字串流寫入主控台輸出。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_high\_level\_console\_i\_o'
- base.high\_level\_console\_i\_o
- consoles.high\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6d191fee-87bb-4659-8056-910149e591f7
ms.openlocfilehash: 1ab8707fbc801962bbb32f17f7b575343ca530ba
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038676"
---
# <a name="high-level-console-io"></a>High-Level 主控台 i/o

高階 i/o 函數提供簡單的方法，從主控台輸入讀取字串流，或將字串流寫入主控台輸出。 高層級的讀取作業會從主控台的輸入緩衝區取得輸入字元，並將它們儲存在指定的緩衝區中。 高階寫入作業會接受來自指定緩衝區的字元，並將它們寫入目前游標位置的螢幕緩衝區，並在寫入每個字元時，將資料指標前進。

高階 i/o 可讓您選擇 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 和 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 函式，以及 [**ReadConsole**](readconsole.md) 和 [**WriteConsole**](writeconsole.md) 函數。 它們完全相同，但有兩個重要的差異。 主控台函式支援使用 Unicode 字元，或透過每個函式的 A 和 W 變數來設定 ANSI 字元集;檔案 i/o 函式不支援 Unicode，但在 `CP_UTF8` **[SetConsoleCP](setconsolecp.md)** 和 **[SetConsoleOutputCP](setconsoleoutputcp.md)** 函式上使用常數設定的 utf-8 會在使用之前使用。 此外，也可以使用檔案 i/o 功能來存取檔案、管道和串列通訊裝置;主控台功能只能搭配主控台控制碼使用。 如果應用程式依賴可能已重新導向的標準控制碼，則這項差異很重要。

使用其中一組高階函式時，應用程式可以控制用來顯示後續以慣用機制透過 **[虛擬終端機序列](console-virtual-terminal-sequences.md)** 寫入螢幕緩衝區的文字和背景色彩。 應用程式也可以使用會影響高階主控台 i/o 的主控台模式來啟用或停用下列屬性：

- 將鍵盤輸入回應至使用中螢幕緩衝區
- 行輸入，在按下 ENTER 鍵之前，讀取作業不會返回
- 自動處理鍵盤輸入以處理回車、CTRL + C 和其他輸入詳細資料
- 自動處理輸出以處理換行、換行字元、backspaces 和其他輸出詳細資料

如需詳細資訊，請參閱下列主題：

- [主控台模式](console-modes.md)
- [高層級主控台模式](high-level-console-modes.md)
- [高層級主控台輸入和輸出功能](high-level-console-input-and-output-functions.md)
- [傳統 Api 與虛擬終端機序列](classic-vs-vt.md)

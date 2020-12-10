---
title: CTRL+C 和 CTRL+BREAK 訊號
description: CTRL+C 和 CTRL+BREAK 按鍵組合會經由主控台程序接收特殊處理。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_ctrl\_c\_and\_ctrl\_break\_signals'
- base.ctrl\_c\_and\_ctrl\_break\_signals
- consoles.ctrl\_c\_and\_ctrl\_break\_signals
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 5357ed99-920b-47a0-a922-d5faed7bf23e
ms.localizationpriority: high
ms.openlocfilehash: 38cc3486a9e945635147c2e17a4d2f0d197d1d3c
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420187"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a>CTRL+C 和 CTRL+BREAK 訊號

<kbd>CTRL</kbd>+<kbd>C</kbd> 和 <kbd>CTRL</kbd>+<kbd>BREAK</kbd> 按鍵組合會經由主控台程序接收特殊處理。 根據預設，當主控台視窗具有鍵盤焦點時，<kbd>CTRL</kbd>+<kbd>C</kbd> 或 <kbd>CTRL</kbd>+<kbd>BREAK</kbd> 會被視為訊號 (SIGINT 或 SIGBREAK)，而不是鍵盤輸入。 根據預設，這些訊號會傳遞到已連結至主控台的所有主控台程序。 (已中斷連結的程序不受影響。 請參閱 [**建立主控台**](creation-of-a-console.md)。)系統會在每個用戶端程序中建立新執行緒來處理事件。 如果程序正在進行偵錯，執行緒就會引發例外狀況。 偵錯工具可以處理例外狀況，或繼續未處理的例外狀況。

<kbd>CTRL</kbd>+<kbd>BREAK</kbd> 一律會被視為訊號，但是應用程式可以使用兩種方式來變更預設的 <kbd>CTRL</kbd>+<kbd>C</kbd> 行為，以防止呼叫處理常式函式：

- [**SetConsoleMode**](setconsolemode.md) 函式可以停用主控台輸入緩衝區的 **ENABLE\_PROCESSED\_INPUT** 輸入模式，因此會將 CTRL+C 回報為鍵盤輸入，而非訊號。
- 當 [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) 與其參數的 **NULL** and **TRUE** 值一起呼叫時，呼叫程序會忽略 CTRL+C 訊號。 正常的 CTRL+C 處理會使用 **NULL** 和 **FALSE** 值呼叫 **SetConsoleCtrlHandler**，藉此進行還原。 這個忽略或不忽略 CTRL+C 訊號的屬性會由子程序繼承，但是可由任何程序啟用或停用，而不會影響現有的程序。

如需有關如何處理這些訊號 (包括逾時) 的詳細資訊，請參閱 [**處理常式**](handlerroutine.md)回呼文件。

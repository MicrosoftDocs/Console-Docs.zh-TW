---
title: CTRL + C 和 CTRL + BREAK 信號
description: CTRL + C 和 CTRL + BREAK 按鍵組合會接收主控台進程的特殊處理。
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
ms.openlocfilehash: 12a4541d51cb18109caa6d1c15c25479c9e91a7a
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039096"
---
# <a name="ctrlc-and-ctrlbreak-signals"></a>CTRL + C 和 CTRL + BREAK 信號

<kbd>Ctrl</kbd> + <kbd>C</kbd>和<kbd>ctrl</kbd> + <kbd>分隔</kbd>按鍵組合會接收主控台進程的特殊處理。 根據預設，當主控台視窗具有鍵盤焦點時，會將<kbd>ctrl</kbd> + <kbd>C</kbd>或<kbd>ctrl</kbd> + <kbd>BREAK</kbd>視為信號 (SIGINT 或 SIGBREAK) ，而非鍵盤輸入。 根據預設，這些信號會傳遞至所有連接到主控台的主控台處理常式。  (卸離的進程不會受到影響。 請參閱 [**建立主控台**](creation-of-a-console.md)。 ) 系統會在每個用戶端進程中建立新的執行緒，以處理事件。 如果正在調試進程，執行緒就會引發例外狀況。 偵錯工具可以處理例外狀況，或繼續進行未處理的例外狀況。

<kbd>CTRL</kbd> +<kbd>BREAK</kbd>一律會被視為信號，但是應用程式可以透過兩種防止處理函式被呼叫的方式來變更預設的<kbd>CTRL</kbd> + <kbd>C</kbd>行為：

- [**SetConsoleMode**](setconsolemode.md)函式可以停用主控台輸入緩衝區的已 **\_ 處理 \_ 輸入** 輸入模式，因此 CTRL + C 會回報為鍵盤輸入而非信號。
- 當針對其參數使用 **Null** 和 **TRUE** 值呼叫 [**SetConsoleCtrlHandler**](setconsolectrlhandler.md)時，呼叫進程會忽略 CTRL + C 信號。 使用 **Null** 和 **FALSE** 值來呼叫 **SETCONSOLECTRLHANDLER** ，即可還原一般 CTRL + C 處理。 忽略或忽略 CTRL + C 信號的這個屬性會由子進程繼承，但是任何程式都可以啟用或停用它，而不會影響現有的進程。

如需如何處理這些信號的詳細資訊，包括超時，請參閱 [**處理常式常式**](handlerroutine.md) 回呼檔。

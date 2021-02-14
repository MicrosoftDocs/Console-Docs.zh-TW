---
title: Low-Level 主控台輸入函式
description: 低層級的主控台輸入函式緩衝區包含輸入記錄，其中可能包含鍵盤、滑鼠、緩衝區調整大小、焦點和功能表事件的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_low\_level\_console\_input\_functions'
- base.low\_level\_console\_input\_functions
- consoles.low\_level\_console\_input\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 41488614-ca7c-4207-b706-f7776423c7ba
ms.openlocfilehash: fc2969cb266479a0acdde890f4ad3710ca8d7e42
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357818"
---
# <a name="low-level-console-input-functions"></a>Low-Level 主控台輸入函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

低層級的主控台輸入函式緩衝區包含輸入記錄，其中可能包含鍵盤、滑鼠、緩衝區調整大小、焦點和功能表事件的相關資訊。 低層級的函式可直接存取輸入緩衝區，與篩選和處理輸入緩衝區資料的高階函式不同，但會捨棄所有的鍵盤輸入。

有五個低層級的函數可用於存取主控台的輸入緩衝區：

- [**ReadConsoleInput**](readconsoleinput.md)
- [**PeekConsoleInput**](peekconsoleinput.md)
- [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md)
- [**WriteConsoleInput**](writeconsoleinput.md)
- [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md)

[**ReadConsoleInput**](readconsoleinput.md)、 [**PeekConsoleInput**](peekconsoleinput.md)和 [**WriteConsoleInput**](writeconsoleinput.md)函數會使用 [**輸入 \_ 記錄**](input-record-str.md)結構來讀取或寫入輸入緩衝區。

以下是低層級主控台輸入功能的描述。

| 函式 | 描述 |
|-|-|
| [**ReadConsoleInput**](readconsoleinput.md) | 從輸入緩衝區讀取和移除輸入記錄。 除非至少有一個記錄可供讀取，否則函數不會傳回。 然後，所有可用的記錄都會傳送至呼叫進程的緩衝區，直到沒有任何可用的記錄或已讀取指定的記錄數目為止。 未讀取的記錄會保留在輸入緩衝區中，以供下一個讀取作業之用。 此函數會報告已讀取的記錄總數。 如需使用 [**ReadConsoleInput**](readconsoleinput.md)的範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。 |
| [**PeekConsoleInput**](peekconsoleinput.md) | 讀取，而不移除輸入緩衝區中的暫止輸入記錄。 最多可達指定數位的所有可用記錄都會複製到呼叫進程的緩衝區中。 如果沒有可用的記錄，函數會立即傳回。 此函數會報告已讀取的記錄總數。 |
| [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) | 判斷輸入緩衝區中未讀取的輸入記錄數目。 |
| [**WriteConsoleInput**](writeconsoleinput.md) | 將輸入記錄放入緩衝區中任何暫止記錄後方的輸入緩衝區。 視需要，輸入緩衝區會動態成長，以保存所寫入的記錄數目。 若要使用此函式，指定的輸入緩衝區控制碼必須有一般 \_ 寫入存取權限。 |
| [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) | 捨棄輸入緩衝區中的所有未讀取事件。 若要使用此函式，指定的輸入緩衝區控制碼必須有一般 \_ 寫入存取權限。 |

應用程式進程的執行緒可以執行等候作業，等候輸入緩衝區中有可用的輸入。 若要起始等候作業，請在對任何 [等候](/windows/win32/sync/wait-functions)函式的呼叫中指定輸入緩衝區的控制碼。 當一個或多個物件的狀態為已發出信號時，這些函式可能會傳回。 當輸入緩衝區中有未讀取的記錄時，主控台輸入控制碼的狀態就會變成發出信號。 當輸入緩衝區變成空白時，狀態會重設為非信號。 如果沒有可用的輸入，呼叫執行緒會進入有效率的等候狀態，而在等候等候作業的條件時，耗用非常少的處理器時間。
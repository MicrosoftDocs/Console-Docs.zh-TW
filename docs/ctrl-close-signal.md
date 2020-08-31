---
title: CTRL + 關閉信號
description: 當使用者關閉主控台時，系統會產生 CTRL + CLOSE 信號。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_ctrl\_close\_signal'
- base.ctrl\_close\_signal
- consoles.ctrl\_close\_signal
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a327dd55-3250-40ee-b1c4-6ba3b80984a8
ms.openlocfilehash: a44f54e5c73c77155d4aa1d8307375c176463a49
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059214"
---
# <a name="ctrlclose-signal"></a>CTRL + 關閉信號


當使用者關閉主控台時，系統會產生 CTRL + CLOSE 信號。 所有附加至主控台的進程都會收到信號，讓每個處理常式有機會在終止前進行清除。 當進程收到此信號時，處理常式函式在執行任何清除作業之後，可以採取下列其中一個動作：

- 呼叫 [**ExitProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682658) 以終止進程。
- 傳回 **FALSE**。 如果沒有任何已註冊的處理常式函式傳回 **TRUE**，則預設處理常式會終止進程。
- 傳回 **TRUE**。 在此情況下，不會呼叫任何其他處理常式函式，且進程會終止。

 

 





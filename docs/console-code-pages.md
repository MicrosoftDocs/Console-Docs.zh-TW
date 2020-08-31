---
title: 主控台字碼頁
description: 字碼頁是256字元碼與個別字元的對應。 不同的字碼頁包含不同的特殊字元，一般而言是針對語言或語言群組進行自訂。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_console\_code\_pages'
- base.console\_code\_pages
- consoles.console\_code\_pages
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98d56bb1-83d2-40aa-adac-fc2e8beab337
ms.openlocfilehash: cacc4cb1d88a7d2aa01c35e0f0d94b44c393d28c
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059342"
---
# <a name="console-code-pages"></a>主控台字碼頁


*字碼頁*是256字元碼與個別字元的對應。 不同的字碼頁包含不同的特殊字元，一般而言是針對語言或語言群組進行自訂。

與每個主控台相關聯的字碼頁有兩個：一個用於輸入，另一個用於輸出。 主控台會使用其輸入字碼頁面，將鍵盤輸入轉譯成對應的字元值。 它會使用其輸出字碼頁，將各種輸出函式所寫入的字元值轉譯為主控台視窗中顯示的影像。 應用程式可以使用 [**SetConsoleCP**](setconsolecp.md) 和 [**GetConsoleCP**](getconsolecp.md) 函式來設定和取出主控台的輸入字碼頁，以及 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 和 [**GetConsoleOutputCP**](getconsoleoutputcp.md) 函式來設定和取出其輸出字碼頁。

本機電腦上可用的字碼頁識別碼會儲存在登錄中的下列機碼底下。

**HKEY \_ LOCAL \_ MACHINE \\ SYSTEM \\ CurrentControlSet \\ Control \\ Nls \\ 字碼頁**

如需使用登錄功能來判斷可用字碼頁的詳細資訊，請 [**參閱登錄**](https://msdn.microsoft.com/library/windows/desktop/ms724871)。

 

 





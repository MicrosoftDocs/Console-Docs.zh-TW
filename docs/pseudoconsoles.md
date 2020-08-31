---
title: Pseudoconsoles – Windows 桌面
description: Pseudoconsole 是一種概念，用來提供字元模式應用程式的裝載或服務層面。
author: miniksa
ms.author: miniksa
ms.topic: article
ms.prod: console
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api，conpty，pseudoconsole
ms.openlocfilehash: ce2dfb14371e35a738e9c42ba2be8d2bb2758946
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059054"
---
# <a name="pseudoconsoles"></a>Pseudoconsoles

*Pseudoconsole*是一種裝置類型，可讓應用程式成為字元模式應用程式的主機。 

相較于一般的主控台會話，作業系統會代表字元模式應用程式建立裝載視窗，以處理圖形化輸出和使用者輸入。

使用 pseudoconsole 時，並不會建立裝載視窗。 進行 pseudoconsole 的應用程式必須負責顯示圖形化輸出和收集使用者輸入。 或者，您也可以將資訊進一步轉送到另一個應用程式，該應用程式會在鏈中的稍後點負責這些活動。

這項功能的設計是為了讓協力廠商「終端機視窗」應用程式存在於平臺上，或是在另一部電腦上或甚至另一個平臺上，將字元模式活動重新導向至遠端「終端機視窗」會話。

請注意，仍會代表要求 pseudoconsole 的應用程式來建立基礎主控台會話。 [主控台會話](consoles.md)的所有規則仍然適用，包括多個用戶端字元模式應用程式連接到會話的能力。

為了提供與現有 pseudoterminal 功能世界的最大相容性，透過 pseudoconsole 通道提供的資訊一律會以 UTF-8 編碼。 這不會影響附加之用戶端應用程式的字碼頁或編碼。 必要時，會在 pseudoconsole 系統內進行轉譯。

您可以在 [建立 Pseudoconsole 會話](creating-a-pseudoconsole-session.md)中找到開始使用的範例。

如需 pseudoconsoles 的一些額外背景資訊，請參閱公告 blog 文章： windows [命令列： Windows 虛擬主控台簡介 (ConPTY) ](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/)。

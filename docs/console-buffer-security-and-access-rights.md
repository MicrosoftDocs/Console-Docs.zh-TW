---
title: 主控台緩衝區安全性和存取權限
description: Windows 安全性模型可讓您控制主控台輸入緩衝區和主控台螢幕緩衝區的存取。 如需安全性的詳細資訊，請參閱存取控制模型。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_console\_buffer\_security\_and\_access\_rights'
- base.console\_buffer\_security\_and\_access\_rights
- consoles.console\_buffer\_security\_and\_access\_rights
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
ms.openlocfilehash: 63cfdb91f4ab9696ade81c7a15bc62e1c93ab6e3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059350"
---
# <a name="console-buffer-security-and-access-rights"></a>主控台緩衝區安全性和存取權限


Windows 安全性模型可讓您控制主控台輸入緩衝區和主控台螢幕緩衝區的存取。 如需安全性的詳細資訊，請參閱 [存取控制模型](https://msdn.microsoft.com/library/windows/desktop/aa374876)。

當您呼叫[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)或[**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)函式時，可以指定主控台輸入和主控台畫面緩衝區的[安全描述項](https://msdn.microsoft.com/library/windows/desktop/aa379563)。 如果您指定 **Null**，則物件會取得預設安全描述項。 主控台緩衝區之預設安全描述項中的 Acl 來自于建立者的主要或模擬權杖。

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)、 [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)和[**GetStdHandle**](getstdhandle.md)傳回的控制碼具有**一般 \_ 讀取**和**一般 \_ 寫入**存取權限。

有效的存取權限包含**一般 \_ 讀取**和**一般 \_ 寫入**[一般存取權限](https://msdn.microsoft.com/library/windows/desktop/aa446632)。


| 值                            | 意義                                                                                               |
|----------------------------------|-------------------------------------------------------------------------------------------------------|
| **泛型 \_閱讀** (0x80000000L)   | 要求主控台螢幕緩衝區的讀取權限，以便讓進程從緩衝區讀取資料。 |
| **泛型 \_撰寫** (0x40000000L)  | 要求主控台螢幕緩衝區的寫入存取權，讓進程能夠將資料寫入緩衝區。 |











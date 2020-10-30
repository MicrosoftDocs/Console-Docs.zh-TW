---
title: 主控台緩衝區安全性和存取權限
description: Windows 安全性模型可讓您控制主控台輸入緩衝區和主控台螢幕緩衝區的存取。 如需安全性的詳細資訊，請參閱 Access-Control 模型。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_console\_buffer\_security\_and\_access\_rights'
- base.console\_buffer\_security\_and\_access\_rights
- consoles.console\_buffer\_security\_and\_access\_rights
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f9a50063-8fc8-4cd1-8f24-9ae3946d3119
ms.openlocfilehash: dfafdbd59c2b06929c35612d7dcf03b24439eba2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93036976"
---
# <a name="console-buffer-security-and-access-rights"></a>主控台緩衝區安全性和存取權限

Windows 安全性模型可讓您控制主控台輸入緩衝區和主控台螢幕緩衝區的存取。 如需安全性的詳細資訊，請參閱 [存取控制模型](https://msdn.microsoft.com/library/windows/desktop/aa374876)。

## <a name="console-object-security-descriptors"></a>主控台物件安全描述項

當您呼叫 [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)或 [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)函式時，可以指定主控台輸入和主控台畫面緩衝區的 [安全描述項](https://msdn.microsoft.com/library/windows/desktop/aa379563)。 如果您指定 **Null** ，則物件會取得預設安全描述項。 主控台緩衝區之預設安全描述項中的 Acl 來自于建立者的主要或模擬權杖。

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)、 [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)和 [**GetStdHandle**](getstdhandle.md)傳回的控制碼具有 **一般 \_ 讀取** 和 **一般 \_ 寫入** 存取權限。

有效的存取權限包含 **一般 \_ 讀取** 和 **一般 \_ 寫入**[一般存取權限](https://msdn.microsoft.com/library/windows/desktop/aa446632)。

| 值 | 意義 |
|-|-|
| **泛型 \_閱讀** (0x80000000L)   | 要求主控台螢幕緩衝區的讀取權限，以便讓進程從緩衝區讀取資料。 |
| **泛型 \_撰寫** (0x40000000L)  | 要求主控台螢幕緩衝區的寫入存取權，讓進程能夠將資料寫入緩衝區。 |

> [!NOTE]
> 除了上述的安全描述項通常允許的情況下，即使上述的安全描述項正常， **[通用 Windows 平臺主控台應用程式](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)** 和具有較低 **[完整性層級](https://docs.microsoft.com/windows/win32/secauthz/mandatory-integrity-control)** 的主控台應用程式都不會讀取輸出緩衝區和寫入至輸入緩衝區。 如需詳細資料，請參閱下面的 **[錯誤方式討論動詞](#wrong-way-verbs)** 。

## <a name="wrong-way-verbs"></a>Wrong-Way 動詞

即使物件具有明確允許讀取或寫入的安全描述項，還是會拒絕對主控台物件進行某些作業。 這特別關心在較低許可權的內容中執行的命令列應用程式，其會在更寬鬆的內容中共用命令列應用程式所建立的主控台會話。

「錯誤的動詞命令」一詞旨在套用至與其中一個主控台物件的一般流程相反的作業。 具體來說，輸出緩衝區的一般流程是寫入，而輸入緩衝區的一般流程正在讀取。 因此，「錯誤的」是讀取輸出緩衝區或寫入輸入緩衝區。 這些是 **[低層級主控台 I/o 函數](low-level-console-i-o.md)** 檔中所述的函式。

可以找到這兩個案例：

1. **[通用 Windows 平臺主控台應用程式](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)** 。 因為這些是其他通用 Windows 平臺應用程式的 cousin，所以它們會保有與其他應用程式隔離的承諾，並在其作業效果方面提供使用者保證。
1. 任何的主控台應用程式都是以比現有會話更低的 **[完整性層級](https://docs.microsoft.com/windows/win32/secauthz/mandatory-integrity-control)** 來啟動，您可以在 **[CreateProcess 期間使用標籤或權杖操作](https://docs.microsoft.com/previous-versions/dotnet/articles/bb625960(v=msdn.10))** 來完成。

如果偵測到上述任一種情況，主控台會將「錯誤的動詞」旗標套用至命令列應用程式連線，並拒絕對下列 Api 的呼叫，以減少層級之間的通訊介面：

:::row:::
    :::column:::
        [ReadConsoleOutput](readconsoleoutput.md)  
        [ReadConsoleOutputCharacter](readconsoleoutputcharacter.md)  
        [ReadConsoleOutputAttribute](readconsoleoutputattribute.md)  
    :::column-end:::
    :::column:::
        [WriteConsoleInput](writeconsoleinput.md)  
    :::column-end:::
:::row-end:::

拒絕的呼叫會收到 **拒絕存取** 的錯誤碼，與物件上的安全描述項拒絕讀取或寫入權限相同。

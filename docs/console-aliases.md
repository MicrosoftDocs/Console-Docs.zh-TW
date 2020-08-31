---
title: 主控台別名
description: 描述主控台別名，以及如何使用它們將來源字串對應至目標字串。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- base.console\_aliases
- consoles.console\_aliases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8169708b-83da-47ef-94be-eca3ca7d0a5b
ms.openlocfilehash: bce57b152262da06b1950eb3566ca8b67d0bb580
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059355"
---
# <a name="console-aliases"></a>主控台別名


主控台別名是用來將來源字串對應至目標字串。 例如，您可以定義主控台別名，將「測試」對應至「cd \\ a \_ 非常長 \_ 的 \_ 路徑 \\ 測試」。 當您在命令列輸入 "test" 時，主控台子系統會展開別名並執行指定的 cd 命令。

若要定義主控台別名，請使用 Doskey.exe 建立宏，或使用 [**AddConsoleAlias**](addconsolealias.md) 函數。 下列範例會使用 Doskey.exe：

**doskey 測試 = cd \\ **<em> \_ 非常 \_ 長的 \_ 路徑</em>** \\ 測試**

下列 [**AddConsoleAlias**](addconsolealias.md) 呼叫會建立相同的主控台別名：

``` syntax
AddConsoleAlias( TEXT("test"), 
                 TEXT("cd \\<a_very_long_path>\\test"), 
                 TEXT("cmd.exe"));
```

若要使用 Doskey.exe 將參數加入主控台別名宏，請使用批次參數 $1 到 $9。 如需有關可在 Doskey 巨集定義中使用之特殊代碼的詳細資訊，請參閱 TechNet 上的 Doskey.exe 或 [Doskey](https://go.microsoft.com/fwlink/p/?linkid=196265) 的命令列說明。

在相同的主控台視窗中執行之可執行檔的所有實例，都會共用任何定義的主控台別名。 在不同主控台視窗中執行的相同可執行檔的多個實例不會共用主控台別名。 在相同的主控台視窗中執行的不同可執行檔不會共用主控台別名。

若要取得指定之來源字串和可執行檔的目標字串，請使用 [**GetConsoleAlias**](getconsolealias.md) 函數。 若要取得指定之可執行檔的所有別名，請使用 [**GetConsoleAliases**](getconsolealiases.md) 函數。 若要取得已定義主控台別名的所有別名名稱，請使用 [**GetConsoleAliasExes**](getconsolealiasexes.md) 函式。

 

 





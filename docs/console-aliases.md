---
title: 主控台別名
description: 描述主控台別名，以及如何使用它們將來源字串對應至目標字串。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- base.console\_aliases
- consoles.console\_aliases
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 8169708b-83da-47ef-94be-eca3ca7d0a5b
ms.openlocfilehash: 10ee932ba8c09b8e28092d4289b7da64da749b76
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357828"
---
# <a name="console-aliases"></a><span data-ttu-id="1b190-104">主控台別名</span><span class="sxs-lookup"><span data-stu-id="1b190-104">Console Aliases</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="1b190-105">主控台別名是用來將來源字串對應至目標字串。</span><span class="sxs-lookup"><span data-stu-id="1b190-105">Console aliases are used to map source strings to target strings.</span></span> <span data-ttu-id="1b190-106">例如，您可以定義主控台別名，將「測試」對應至「cd \\ a \_ 非常長 \_ 的 \_ 路徑 \\ 測試」。</span><span class="sxs-lookup"><span data-stu-id="1b190-106">For example, you can define a console alias that maps "test" to "cd \\a\_very\_long\_path\\test".</span></span> <span data-ttu-id="1b190-107">當您在命令列輸入 "test" 時，主控台子系統會展開別名並執行指定的 cd 命令。</span><span class="sxs-lookup"><span data-stu-id="1b190-107">When you type "test" at the command line, the console subsystem expands the alias and executes the specified cd command.</span></span>

<span data-ttu-id="1b190-108">若要定義主控台別名，請使用 [**Doskey.exe**](/windows-server/administration/windows-commands/doskey) 建立宏，或使用 [**AddConsoleAlias**](addconsolealias.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="1b190-108">To define a console alias, use [**Doskey.exe**](/windows-server/administration/windows-commands/doskey) to create a macro, or use the [**AddConsoleAlias**](addconsolealias.md) function.</span></span> <span data-ttu-id="1b190-109">下列範例會使用 `Doskey.exe`：</span><span class="sxs-lookup"><span data-stu-id="1b190-109">The following example uses `Doskey.exe`:</span></span>

<span data-ttu-id="1b190-110">**doskey 測試 = cd \\**<em> \_ 非常 \_ 長的 \_ 路徑</em>**\\ 測試**</span><span class="sxs-lookup"><span data-stu-id="1b190-110">**doskey test=cd \\**<em>a\_very\_long\_path</em>**\\test**</span></span>

<span data-ttu-id="1b190-111">下列 [**AddConsoleAlias**](addconsolealias.md) 呼叫會建立相同的主控台別名：</span><span class="sxs-lookup"><span data-stu-id="1b190-111">The following call to [**AddConsoleAlias**](addconsolealias.md) creates the same console alias:</span></span>

``` C
AddConsoleAlias( TEXT("test"),
                 TEXT("cd \\<a_very_long_path>\\test"),
                 TEXT("cmd.exe"));
```

<span data-ttu-id="1b190-112">若要使用將參數加入至主控台別名宏 `Doskey.exe` ，請透過使用批次參數 `$1` `$9` 。</span><span class="sxs-lookup"><span data-stu-id="1b190-112">To add parameters to a console alias macro using `Doskey.exe`, use the batch parameters `$1` through `$9`.</span></span> <span data-ttu-id="1b190-113">如需有關可在 Doskey 巨集定義中使用之特殊代碼的詳細資訊，請參閱 TechNet 上適用于 `Doskey.exe` 或 [doskey](/previous-versions/windows/it-pro/windows-xp/bb490894(v=technet.10)) 的命令列說明。</span><span class="sxs-lookup"><span data-stu-id="1b190-113">For more information on the special codes that can be used in Doskey macro definitions, see the command-line help for `Doskey.exe` or [Doskey](/previous-versions/windows/it-pro/windows-xp/bb490894(v=technet.10)) on TechNet.</span></span>

<span data-ttu-id="1b190-114">在相同的主控台視窗中執行之可執行檔的所有實例，都會共用任何定義的主控台別名。</span><span class="sxs-lookup"><span data-stu-id="1b190-114">All instances of an executable file running in the same console window share any defined console aliases.</span></span> <span data-ttu-id="1b190-115">在不同主控台視窗中執行的相同可執行檔的多個實例不會共用主控台別名。</span><span class="sxs-lookup"><span data-stu-id="1b190-115">Multiple instances of the same executable file running in different console windows do not share console aliases.</span></span> <span data-ttu-id="1b190-116">在相同的主控台視窗中執行的不同可執行檔不會共用主控台別名。</span><span class="sxs-lookup"><span data-stu-id="1b190-116">Different executable files running in the same console window do not share console aliases.</span></span>

<span data-ttu-id="1b190-117">若要取得指定之來源字串和可執行檔的目標字串，請使用 [**GetConsoleAlias**](getconsolealias.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="1b190-117">To retrieve the target string for a specified source string and executable file, use the [**GetConsoleAlias**](getconsolealias.md) function.</span></span> <span data-ttu-id="1b190-118">若要取得指定之可執行檔的所有別名，請使用 [**GetConsoleAliases**](getconsolealiases.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="1b190-118">To retrieve all aliases for a specified executable file, use the [**GetConsoleAliases**](getconsolealiases.md) function.</span></span> <span data-ttu-id="1b190-119">若要取得已定義主控台別名的所有別名名稱，請使用 [**GetConsoleAliasExes**](getconsolealiasexes.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="1b190-119">To retrieve the names of all aliases for which console aliases have been defined, use the [**GetConsoleAliasExes**](getconsolealiasexes.md) function.</span></span>
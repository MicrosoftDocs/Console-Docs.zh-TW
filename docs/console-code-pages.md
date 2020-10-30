---
title: 主控台字碼頁
description: 字碼頁是256字元碼與個別字元的對應。 不同的字碼頁包含不同的特殊字元，一般而言是針對語言或語言群組進行自訂。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_console\_code\_pages'
- base.console\_code\_pages
- consoles.console\_code\_pages
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98d56bb1-83d2-40aa-adac-fc2e8beab337
ms.openlocfilehash: 931e882306c1aaff521b7b78c2b99cf1a5479da1
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039246"
---
# <a name="console-code-pages"></a><span data-ttu-id="f42c0-105">主控台字碼頁</span><span class="sxs-lookup"><span data-stu-id="f42c0-105">Console Code Pages</span></span>

<span data-ttu-id="f42c0-106">*字碼頁* 是256字元碼與個別字元的對應。</span><span class="sxs-lookup"><span data-stu-id="f42c0-106">A *code page* is a mapping of 256 character codes to individual characters.</span></span> <span data-ttu-id="f42c0-107">不同的字碼頁包含不同的特殊字元，一般而言是針對語言或語言群組進行自訂。</span><span class="sxs-lookup"><span data-stu-id="f42c0-107">Different code pages include different special characters, typically customized for a language or a group of languages.</span></span>

<span data-ttu-id="f42c0-108">與每個主控台相關聯的字碼頁有兩個：一個用於輸入，另一個用於輸出。</span><span class="sxs-lookup"><span data-stu-id="f42c0-108">Associated with each console are two code pages: one for input and one for output.</span></span> <span data-ttu-id="f42c0-109">主控台會使用其輸入字碼頁面，將鍵盤輸入轉譯成對應的字元值。</span><span class="sxs-lookup"><span data-stu-id="f42c0-109">A console uses its input code page to translate keyboard input into the corresponding character value.</span></span> <span data-ttu-id="f42c0-110">它會使用其輸出字碼頁，將各種輸出函式所寫入的字元值轉譯為主控台視窗中顯示的影像。</span><span class="sxs-lookup"><span data-stu-id="f42c0-110">It uses its output code page to translate the character values written by the various output functions into the images displayed in the console window.</span></span> <span data-ttu-id="f42c0-111">應用程式可以使用 [**SetConsoleCP**](setconsolecp.md) 和 [**GetConsoleCP**](getconsolecp.md) 函式來設定和取出主控台的輸入字碼頁，以及 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 和 [**GetConsoleOutputCP**](getconsoleoutputcp.md) 函式來設定和取出其輸出字碼頁。</span><span class="sxs-lookup"><span data-stu-id="f42c0-111">An application can use the [**SetConsoleCP**](setconsolecp.md) and [**GetConsoleCP**](getconsolecp.md) functions to set and retrieve a console's input code pages and the [**SetConsoleOutputCP**](setconsoleoutputcp.md) and [**GetConsoleOutputCP**](getconsoleoutputcp.md) functions to set and retrieve its output code pages.</span></span>

<span data-ttu-id="f42c0-112">本機電腦上可用的字碼頁識別碼會儲存在登錄中的下列機碼底下： `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`</span><span class="sxs-lookup"><span data-stu-id="f42c0-112">The identifiers of the code pages available on the local computer are stored in the registry under the following key: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Nls\CodePage`</span></span>

<span data-ttu-id="f42c0-113">如需使用登錄功能來判斷可用字碼頁的詳細資訊，請 [**參閱登錄**](https://msdn.microsoft.com/library/windows/desktop/ms724871)。</span><span class="sxs-lookup"><span data-stu-id="f42c0-113">For information about using the registry functions to determine the available code pages, see [**Registry**](https://msdn.microsoft.com/library/windows/desktop/ms724871).</span></span>

> [!TIP]
> <span data-ttu-id="f42c0-114">建議所有新的和更新的命令列應用程式，以避免字碼頁並使用 **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** 。</span><span class="sxs-lookup"><span data-stu-id="f42c0-114">It is recommended for all new and updated command-line applications to avoid code pages and use **[Unicode](https://docs.microsoft.com/windows/win32/intl/unicode)** .</span></span> <span data-ttu-id="f42c0-115">UTF-16 格式化的文字可以傳送至 *W* 系列的主控台 api。</span><span class="sxs-lookup"><span data-stu-id="f42c0-115">UTF-16 formatted text can be sent to the *W* family of console APIs.</span></span> <span data-ttu-id="f42c0-116">使用 [**SetConsoleCP**](setconsolecp.md)和 [**SetConsoleOutputCP**](setconsoleoutputcp.md)函式確定字碼頁第一次設定為 **[65001 (CP_UTF8)](https://docs.microsoft.com/windows/win32/intl/code-page-identifiers)** 之後，可以將 Utf-8 格式化的文字傳送至 *一* 系列的主控台 api。</span><span class="sxs-lookup"><span data-stu-id="f42c0-116">UTF-8 formatted text can be sent to the *A* family of console APIs after ensuring the code page is first set to **[65001 (CP_UTF8)](https://docs.microsoft.com/windows/win32/intl/code-page-identifiers)** with the [**SetConsoleCP**](setconsolecp.md) and [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions.</span></span>

---
title: High-Level 主控台 i/o
description: 高階 i/o 函數提供簡單的方法，從主控台輸入讀取字串流，或將字串流寫入主控台輸出。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_high\_level\_console\_i\_o'
- base.high\_level\_console\_i\_o
- consoles.high\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6d191fee-87bb-4659-8056-910149e591f7
ms.openlocfilehash: d240a261ea555e0bfa506c96c1aaea9d6a933697
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358691"
---
# <a name="high-level-console-io"></a><span data-ttu-id="b2d02-104">High-Level 主控台 i/o</span><span class="sxs-lookup"><span data-stu-id="b2d02-104">High-Level Console I/O</span></span>

<span data-ttu-id="b2d02-105">高階 i/o 函數提供簡單的方法，從主控台輸入讀取字串流，或將字串流寫入主控台輸出。</span><span class="sxs-lookup"><span data-stu-id="b2d02-105">The high-level I/O functions provide a simple way to read a stream of characters from console input or to write a stream of characters to console output.</span></span> <span data-ttu-id="b2d02-106">高層級的讀取作業會從主控台的輸入緩衝區取得輸入字元，並將它們儲存在指定的緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="b2d02-106">A high-level read operation gets input characters from a console's input buffer and stores them in a specified buffer.</span></span> <span data-ttu-id="b2d02-107">高階寫入作業會接受來自指定緩衝區的字元，並將它們寫入目前游標位置的螢幕緩衝區，並在寫入每個字元時，將資料指標前進。</span><span class="sxs-lookup"><span data-stu-id="b2d02-107">A high-level write operation takes characters from a specified buffer and writes them to a screen buffer at the current cursor location, advancing the cursor as each character is written.</span></span>

<span data-ttu-id="b2d02-108">高階 i/o 可讓您選擇 [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) 和 [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) 函式，以及 [**ReadConsole**](readconsole.md) 和 [**WriteConsole**](writeconsole.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="b2d02-108">High-level I/O gives you a choice between the [**ReadFile**](/windows/win32/api/fileapi/nf-fileapi-readfile) and [**WriteFile**](/windows/win32/api/fileapi/nf-fileapi-writefile) functions and the [**ReadConsole**](readconsole.md) and [**WriteConsole**](writeconsole.md) functions.</span></span> <span data-ttu-id="b2d02-109">它們完全相同，但有兩個重要的差異。</span><span class="sxs-lookup"><span data-stu-id="b2d02-109">They are identical, except for two important differences.</span></span> <span data-ttu-id="b2d02-110">主控台函式支援使用 Unicode 字元，或透過每個函式的 A 和 W 變數來設定 ANSI 字元集;檔案 i/o 函式不支援 Unicode，但在 `CP_UTF8` **[SetConsoleCP](setconsolecp.md)** 和 **[SetConsoleOutputCP](setconsoleoutputcp.md)** 函式上使用常數設定的 utf-8 會在使用之前使用。</span><span class="sxs-lookup"><span data-stu-id="b2d02-110">The console functions support the use of either Unicode characters or the ANSI character set through the A and W variants of each function; the file I/O functions do not support Unicode except for UTF-8 set with the `CP_UTF8` constant on the **[SetConsoleCP](setconsolecp.md)** and **[SetConsoleOutputCP](setconsoleoutputcp.md)** functions prior to use.</span></span> <span data-ttu-id="b2d02-111">此外，也可以使用檔案 i/o 功能來存取檔案、管道和串列通訊裝置;主控台功能只能搭配主控台控制碼使用。</span><span class="sxs-lookup"><span data-stu-id="b2d02-111">Also, the file I/O functions can be used to access files, pipes, and serial communications devices; the console functions can only be used with console handles.</span></span> <span data-ttu-id="b2d02-112">如果應用程式依賴可能已重新導向的標準控制碼，則這項差異很重要。</span><span class="sxs-lookup"><span data-stu-id="b2d02-112">This distinction is important if an application relies on standard handles that may have been redirected.</span></span>

<span data-ttu-id="b2d02-113">使用其中一組高階函式時，應用程式可以控制用來顯示後續以慣用機制透過 **[虛擬終端機序列](console-virtual-terminal-sequences.md)** 寫入螢幕緩衝區的文字和背景色彩。</span><span class="sxs-lookup"><span data-stu-id="b2d02-113">When using either set of high-level functions, an application can control the text and background colors used to display characters subsequently written to a screen buffer with the preferred mechanism being via **[virtual terminal sequences](console-virtual-terminal-sequences.md)**.</span></span> <span data-ttu-id="b2d02-114">應用程式也可以使用會影響高階主控台 i/o 的主控台模式來啟用或停用下列屬性：</span><span class="sxs-lookup"><span data-stu-id="b2d02-114">An application can also use the console modes that affect high-level console I/O to enable or disable the following properties:</span></span>

- <span data-ttu-id="b2d02-115">將鍵盤輸入回應至使用中螢幕緩衝區</span><span class="sxs-lookup"><span data-stu-id="b2d02-115">Echoing of keyboard input to the active screen buffer</span></span>
- <span data-ttu-id="b2d02-116">行輸入，在按下 ENTER 鍵之前，讀取作業不會返回</span><span class="sxs-lookup"><span data-stu-id="b2d02-116">Line input, in which a read operation does not return until the ENTER key is pressed</span></span>
- <span data-ttu-id="b2d02-117">自動處理鍵盤輸入以處理回車、CTRL + C 和其他輸入詳細資料</span><span class="sxs-lookup"><span data-stu-id="b2d02-117">Automatic processing of keyboard input to handle carriage returns, CTRL+C, and other input details</span></span>
- <span data-ttu-id="b2d02-118">自動處理輸出以處理換行、換行字元、backspaces 和其他輸出詳細資料</span><span class="sxs-lookup"><span data-stu-id="b2d02-118">Automatic processing of output to handle line wrapping, carriage returns, backspaces, and other output details</span></span>

<span data-ttu-id="b2d02-119">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="b2d02-119">For more information, see the following topics:</span></span>

- [<span data-ttu-id="b2d02-120">主控台模式</span><span class="sxs-lookup"><span data-stu-id="b2d02-120">Console Modes</span></span>](console-modes.md)
- [<span data-ttu-id="b2d02-121">高層級主控台模式</span><span class="sxs-lookup"><span data-stu-id="b2d02-121">High-Level Console Modes</span></span>](high-level-console-modes.md)
- [<span data-ttu-id="b2d02-122">高層級主控台輸入和輸出功能</span><span class="sxs-lookup"><span data-stu-id="b2d02-122">High-Level Console Input and Output Functions</span></span>](high-level-console-input-and-output-functions.md)
- [<span data-ttu-id="b2d02-123">傳統 Api 與虛擬終端機序列</span><span class="sxs-lookup"><span data-stu-id="b2d02-123">Classic APIs Versus Virtual Terminal Sequences</span></span>](classic-vs-vt.md)
---
title: 關於主控台
description: 主控台提供簡單字元模式應用程式的高階支援，這些應用程式會使用從標準輸入讀取和寫入至標準輸出或標準錯誤的函式，與使用者互動。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: e20fa54434b4121abd3f77ee530945bf9aa590f2
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037526"
---
# <a name="about-character-mode-applications"></a><span data-ttu-id="aecfc-104">關於字元模式應用程式</span><span class="sxs-lookup"><span data-stu-id="aecfc-104">About Character Mode Applications</span></span>

<span data-ttu-id="aecfc-105">字元模式 (或「命令列」 ) 應用程式：</span><span class="sxs-lookup"><span data-stu-id="aecfc-105">Character mode (or "command-line") applications:</span></span>

1. <span data-ttu-id="aecfc-106">\[選擇性地 \] 從標準輸入讀取資料 (stdin) </span><span class="sxs-lookup"><span data-stu-id="aecfc-106">\[Optionally\] Read data from standard input (stdin)</span></span>
2. <span data-ttu-id="aecfc-107">「工作」</span><span class="sxs-lookup"><span data-stu-id="aecfc-107">Do "work"</span></span>
3. <span data-ttu-id="aecfc-108">\[選擇性地 \] 將資料寫入標準輸出 (stdout) 或標準錯誤 (stderr) </span><span class="sxs-lookup"><span data-stu-id="aecfc-108">\[Optionally\] Write data to standard output (stdout) or standard error (stderr)</span></span>

<span data-ttu-id="aecfc-109">字元模式應用程式會透過「主控台」 (或「終端機」 ) 應用程式與終端使用者進行通訊。</span><span class="sxs-lookup"><span data-stu-id="aecfc-109">Character mode applications communicate with the end-user through a "console" (or "terminal") application.</span></span> <span data-ttu-id="aecfc-110">主控台會從鍵盤、滑鼠、觸控畫面、畫筆等來轉換使用者輸入，並將其傳送至字元模式應用程式的 stdin。</span><span class="sxs-lookup"><span data-stu-id="aecfc-110">A console converts user input from keyboard, mouse, touch-screen, pen, etc., and sends it to a character mode application's stdin.</span></span> <span data-ttu-id="aecfc-111">主控台可能也會在使用者的畫面上顯示字元模式應用程式的文字輸出。</span><span class="sxs-lookup"><span data-stu-id="aecfc-111">A console may also display a character mode application's text output on the user's screen.</span></span>

<span data-ttu-id="aecfc-112">在 Windows 中，主控台是內建的，並提供豐富的 API，可讓字元模式應用程式與使用者互動。</span><span class="sxs-lookup"><span data-stu-id="aecfc-112">In Windows, the console is built-in and provides a rich API through which character mode applications can interact with the user.</span></span> <span data-ttu-id="aecfc-113">不過，在最新的時代，主控台小組鼓勵所有的字元模式應用程式，透過傳統 API 呼叫的 [虛擬終端機序列](console-virtual-terminal-sequences.md) 來開發，以獲得 Windows 與其他作業系統之間的最大相容性。</span><span class="sxs-lookup"><span data-stu-id="aecfc-113">However, in the recent era, the console team is encouraging all character mode applications to be developed with [virtual terminal sequences](console-virtual-terminal-sequences.md) over the classic API calls for maximum compatibility between Windows and other operating systems.</span></span> <span data-ttu-id="aecfc-114">有關此轉換的詳細資訊，以及相關的取捨，可在我們的 [傳統 api 與虛擬終端機序列](classic-vs-vt.md)討論中找到。</span><span class="sxs-lookup"><span data-stu-id="aecfc-114">More details on this transition and the trade offs involved can be found in our discussion of [classic APIs versus virtual terminal sequences](classic-vs-vt.md).</span></span>

- [<span data-ttu-id="aecfc-115">機</span><span class="sxs-lookup"><span data-stu-id="aecfc-115">Consoles</span></span>](consoles.md)
- [<span data-ttu-id="aecfc-116">輸入和輸出方法</span><span class="sxs-lookup"><span data-stu-id="aecfc-116">Input and Output Methods</span></span>](input-and-output-methods.md)
- [<span data-ttu-id="aecfc-117">主控台字碼頁</span><span class="sxs-lookup"><span data-stu-id="aecfc-117">Console Code Pages</span></span>](console-code-pages.md)
- [<span data-ttu-id="aecfc-118">主控台控制處理常式</span><span class="sxs-lookup"><span data-stu-id="aecfc-118">Console Control Handlers</span></span>](console-control-handlers.md)
- [<span data-ttu-id="aecfc-119">主控台別名</span><span class="sxs-lookup"><span data-stu-id="aecfc-119">Console Aliases</span></span>](console-aliases.md)
- [<span data-ttu-id="aecfc-120">主控台緩衝區安全性和存取權限</span><span class="sxs-lookup"><span data-stu-id="aecfc-120">Console Buffer Security and Access Rights</span></span>](console-buffer-security-and-access-rights.md)
- [<span data-ttu-id="aecfc-121">主控台應用程式問題</span><span class="sxs-lookup"><span data-stu-id="aecfc-121">Console Application Issues</span></span>](console-application-issues.md)

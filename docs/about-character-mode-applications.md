---
title: 關於主控台
description: 主控台提供簡單字元模式應用程式的高階支援，這些應用程式會使用從標準輸入讀取和寫入至標準輸出或標準錯誤的函式，與使用者互動。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: 0a738c72ec45a68817fae6dbfa9d6b3e45beb53e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059394"
---
# <a name="about-character-mode-applications"></a><span data-ttu-id="d0096-104">關於字元模式應用程式</span><span class="sxs-lookup"><span data-stu-id="d0096-104">About Character Mode Applications</span></span>

<span data-ttu-id="d0096-105">字元模式 (或「命令列」 ) 應用程式：</span><span class="sxs-lookup"><span data-stu-id="d0096-105">Character mode (or "command-line") applications:</span></span>

1. <span data-ttu-id="d0096-106">跟從標準輸入 (stdin) 讀取資料</span><span class="sxs-lookup"><span data-stu-id="d0096-106">[Optionally] Read data from standard input (stdin)</span></span>
2. <span data-ttu-id="d0096-107">「工作」</span><span class="sxs-lookup"><span data-stu-id="d0096-107">Do "work"</span></span>
3. <span data-ttu-id="d0096-108">跟將資料寫入標準輸出 (stdout) 或標準錯誤 (stderr) </span><span class="sxs-lookup"><span data-stu-id="d0096-108">[Optionally] Write data to standard output (stdout) or standard error (stderr)</span></span>

<span data-ttu-id="d0096-109">字元模式應用程式會透過「主控台」 (或「終端機」 ) 應用程式與終端使用者進行通訊。</span><span class="sxs-lookup"><span data-stu-id="d0096-109">Character mode applications communicate with the end-user through a "console" (or "terminal") application.</span></span> <span data-ttu-id="d0096-110">主控台會從鍵盤、滑鼠、觸控畫面、畫筆等來轉換使用者輸入，並將其傳送至字元模式應用程式的 stdin。</span><span class="sxs-lookup"><span data-stu-id="d0096-110">A console converts user input from keyboard, mouse, touch-screen, pen, etc., and sends it to a character mode application's stdin.</span></span> <span data-ttu-id="d0096-111">主控台可能也會在使用者的畫面上顯示字元模式應用程式的文字輸出。</span><span class="sxs-lookup"><span data-stu-id="d0096-111">A console may also display a character mode application's text output on the user's screen.</span></span>

<span data-ttu-id="d0096-112">在 Windows 中，主控台是內建的，並提供豐富的 API，可讓字元模式應用程式與使用者互動。</span><span class="sxs-lookup"><span data-stu-id="d0096-112">In Windows, the console is built-in and provides a rich API through which character mode applications can interact with the user.</span></span>

- [<span data-ttu-id="d0096-113">機</span><span class="sxs-lookup"><span data-stu-id="d0096-113">Consoles</span></span>](consoles.md)
- [<span data-ttu-id="d0096-114">輸入和輸出方法</span><span class="sxs-lookup"><span data-stu-id="d0096-114">Input and Output Methods</span></span>](input-and-output-methods.md)
- [<span data-ttu-id="d0096-115">主控台字碼頁</span><span class="sxs-lookup"><span data-stu-id="d0096-115">Console Code Pages</span></span>](console-code-pages.md)
- [<span data-ttu-id="d0096-116">主控台控制處理常式</span><span class="sxs-lookup"><span data-stu-id="d0096-116">Console Control Handlers</span></span>](console-control-handlers.md)
- [<span data-ttu-id="d0096-117">主控台別名</span><span class="sxs-lookup"><span data-stu-id="d0096-117">Console Aliases</span></span>](console-aliases.md)
- [<span data-ttu-id="d0096-118">主控台緩衝區安全性和存取權限</span><span class="sxs-lookup"><span data-stu-id="d0096-118">Console Buffer Security and Access Rights</span></span>](console-buffer-security-and-access-rights.md)
- [<span data-ttu-id="d0096-119">主控台應用程式問題</span><span class="sxs-lookup"><span data-stu-id="d0096-119">Console Application Issues</span></span>](console-application-issues.md)

 

 





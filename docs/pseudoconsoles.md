---
title: Pseudoconsoles – Windows 桌面
description: Pseudoconsole 是一種概念，用來提供字元模式應用程式的裝載或服務層面。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api，conpty，pseudoconsole
ms.openlocfilehash: 2b2d28065ec4f0e4121decb906e76b34ac1871fc
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039476"
---
# <a name="pseudoconsoles"></a><span data-ttu-id="d756b-104">Pseudoconsoles</span><span class="sxs-lookup"><span data-stu-id="d756b-104">Pseudoconsoles</span></span>

<span data-ttu-id="d756b-105">*Pseudoconsole* 是一種裝置類型，可讓應用程式成為字元模式應用程式的主機。</span><span class="sxs-lookup"><span data-stu-id="d756b-105">A *pseudoconsole* is a device type that allows applications to become the host for character-mode applications.</span></span>

<span data-ttu-id="d756b-106">相較于一般的主控台會話，作業系統會代表字元模式應用程式建立裝載視窗，以處理圖形化輸出和使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="d756b-106">This is in contrast to a typical console session where the operating system will create a hosting window on behalf of the character-mode application to handle graphical output and user input.</span></span>

<span data-ttu-id="d756b-107">使用 pseudoconsole 時，並不會建立裝載視窗。</span><span class="sxs-lookup"><span data-stu-id="d756b-107">With a pseudoconsole, the hosting window is not created.</span></span> <span data-ttu-id="d756b-108">進行 pseudoconsole 的應用程式必須負責顯示圖形化輸出和收集使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="d756b-108">The application that makes the pseudoconsole must become responsible for displaying the graphical output and collecting user input.</span></span> <span data-ttu-id="d756b-109">或者，您也可以將資訊進一步轉送到另一個應用程式，該應用程式會在鏈中的稍後點負責這些活動。</span><span class="sxs-lookup"><span data-stu-id="d756b-109">Alternatively, the information can be relayed further to another application responsible for these activities at a later point in the chain.</span></span>

<span data-ttu-id="d756b-110">這項功能的設計是為了讓協力廠商「終端機視窗」應用程式存在於平臺上，或是在另一部電腦上或甚至另一個平臺上，將字元模式活動重新導向至遠端「終端機視窗」會話。</span><span class="sxs-lookup"><span data-stu-id="d756b-110">This functionality is designed for third-party "terminal window" applications to exist on the platform or for redirection of character-mode activities to a remote "terminal window" session on another machine or even on another platform.</span></span>

<span data-ttu-id="d756b-111">請注意，仍會代表要求 pseudoconsole 的應用程式來建立基礎主控台會話。</span><span class="sxs-lookup"><span data-stu-id="d756b-111">Note that the underlying console session will still be created on behalf of the application requesting the pseudoconsole.</span></span> <span data-ttu-id="d756b-112">[主控台會話](consoles.md)的所有規則仍然適用，包括多個用戶端字元模式應用程式連接到會話的能力。</span><span class="sxs-lookup"><span data-stu-id="d756b-112">All the rules of [console sessions](consoles.md) still apply including the ability for multiple client character-mode applications to connect to the session.</span></span>

<span data-ttu-id="d756b-113">為了提供與現有 pseudoterminal 功能世界的最大相容性，透過 pseudoconsole 通道提供的資訊一律會以 UTF-8 編碼。</span><span class="sxs-lookup"><span data-stu-id="d756b-113">To provide maximum compatibility with the existing world of pseudoterminal functionality, the information provided over the pseudoconsole channel will always be encoded in UTF-8.</span></span> <span data-ttu-id="d756b-114">這不會影響附加之用戶端應用程式的字碼頁或編碼。</span><span class="sxs-lookup"><span data-stu-id="d756b-114">This does not affect the codepage or encoding of the client applications that are attached.</span></span> <span data-ttu-id="d756b-115">必要時，會在 pseudoconsole 系統內進行轉譯。</span><span class="sxs-lookup"><span data-stu-id="d756b-115">Translation will happen inside the pseudoconsole system as necessary.</span></span>

<span data-ttu-id="d756b-116">您可以在 [建立 Pseudoconsole 會話](creating-a-pseudoconsole-session.md)中找到開始使用的範例。</span><span class="sxs-lookup"><span data-stu-id="d756b-116">An example for getting started can be found at [Creating a Pseudoconsole Session](creating-a-pseudoconsole-session.md).</span></span>

<span data-ttu-id="d756b-117">如需 pseudoconsoles 的一些額外背景資訊，請參閱公告 blog 文章： windows [命令列： Windows 虛擬主控台簡介 (ConPTY) ](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/)。</span><span class="sxs-lookup"><span data-stu-id="d756b-117">Some additional background information on pseudoconsoles can be found at the announcement blog post: [Windows Command-Line: Introducing the Windows Pseudo Console (ConPTY)](https://blogs.msdn.microsoft.com/commandline/2018/08/02/windows-command-line-introducing-the-windows-pseudo-console-conpty/).</span></span>

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
# <a name="console-buffer-security-and-access-rights"></a><span data-ttu-id="83f77-105">主控台緩衝區安全性和存取權限</span><span class="sxs-lookup"><span data-stu-id="83f77-105">Console Buffer Security and Access Rights</span></span>

<span data-ttu-id="83f77-106">Windows 安全性模型可讓您控制主控台輸入緩衝區和主控台螢幕緩衝區的存取。</span><span class="sxs-lookup"><span data-stu-id="83f77-106">The Windows security model enables you to control access to console input buffers and console screen buffers.</span></span> <span data-ttu-id="83f77-107">如需安全性的詳細資訊，請參閱 [存取控制模型](https://msdn.microsoft.com/library/windows/desktop/aa374876)。</span><span class="sxs-lookup"><span data-stu-id="83f77-107">For more information about security, see [Access-Control Model](https://msdn.microsoft.com/library/windows/desktop/aa374876).</span></span>

## <a name="console-object-security-descriptors"></a><span data-ttu-id="83f77-108">主控台物件安全描述項</span><span class="sxs-lookup"><span data-stu-id="83f77-108">Console Object Security Descriptors</span></span>

<span data-ttu-id="83f77-109">當您呼叫 [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)或 [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)函式時，可以指定主控台輸入和主控台畫面緩衝區的 [安全描述項](https://msdn.microsoft.com/library/windows/desktop/aa379563)。</span><span class="sxs-lookup"><span data-stu-id="83f77-109">You can specify a [security descriptor](https://msdn.microsoft.com/library/windows/desktop/aa379563) for the console input and console screen buffers when you call the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) or [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) function.</span></span> <span data-ttu-id="83f77-110">如果您指定 **Null** ，則物件會取得預設安全描述項。</span><span class="sxs-lookup"><span data-stu-id="83f77-110">If you specify **NULL** , the object gets a default security descriptor.</span></span> <span data-ttu-id="83f77-111">主控台緩衝區之預設安全描述項中的 Acl 來自于建立者的主要或模擬權杖。</span><span class="sxs-lookup"><span data-stu-id="83f77-111">The ACLs in the default security descriptor for a console buffer come from the primary or impersonation token of the creator.</span></span>

<span data-ttu-id="83f77-112">[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)、 [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)和 [**GetStdHandle**](getstdhandle.md)傳回的控制碼具有 **一般 \_ 讀取** 和 **一般 \_ 寫入** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="83f77-112">The handles returned by [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md), and [**GetStdHandle**](getstdhandle.md) have the **GENERIC\_READ** and **GENERIC\_WRITE** access rights.</span></span>

<span data-ttu-id="83f77-113">有效的存取權限包含 **一般 \_ 讀取** 和 **一般 \_ 寫入**[一般存取權限](https://msdn.microsoft.com/library/windows/desktop/aa446632)。</span><span class="sxs-lookup"><span data-stu-id="83f77-113">The valid access rights include the **GENERIC\_READ** and **GENERIC\_WRITE** [generic access rights](https://msdn.microsoft.com/library/windows/desktop/aa446632).</span></span>

| <span data-ttu-id="83f77-114">值</span><span class="sxs-lookup"><span data-stu-id="83f77-114">Value</span></span> | <span data-ttu-id="83f77-115">意義</span><span class="sxs-lookup"><span data-stu-id="83f77-115">Meaning</span></span> |
|-|-|
| <span data-ttu-id="83f77-116">**泛型 \_閱讀** (0x80000000L) </span><span class="sxs-lookup"><span data-stu-id="83f77-116">**GENERIC\_READ** (0x80000000L)</span></span>  | <span data-ttu-id="83f77-117">要求主控台螢幕緩衝區的讀取權限，以便讓進程從緩衝區讀取資料。</span><span class="sxs-lookup"><span data-stu-id="83f77-117">Requests read access to the console screen buffer, enabling the process to read data from the buffer.</span></span> |
| <span data-ttu-id="83f77-118">**泛型 \_撰寫** (0x40000000L) </span><span class="sxs-lookup"><span data-stu-id="83f77-118">**GENERIC\_WRITE** (0x40000000L)</span></span> | <span data-ttu-id="83f77-119">要求主控台螢幕緩衝區的寫入存取權，讓進程能夠將資料寫入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="83f77-119">Requests write access to the console screen buffer, enabling the process to write data to the buffer.</span></span> |

> [!NOTE]
> <span data-ttu-id="83f77-120">除了上述的安全描述項通常允許的情況下，即使上述的安全描述項正常， **[通用 Windows 平臺主控台應用程式](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)** 和具有較低 **[完整性層級](https://docs.microsoft.com/windows/win32/secauthz/mandatory-integrity-control)** 的主控台應用程式都不會讀取輸出緩衝區和寫入至輸入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="83f77-120">**[Universal Windows Platform console apps](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)** and those with a lower **[integrity level](https://docs.microsoft.com/windows/win32/secauthz/mandatory-integrity-control)** than the attached console will be prohibited from both reading the output buffer and writing to the input buffer even if the security descriptors above would normally permit it.</span></span> <span data-ttu-id="83f77-121">如需詳細資料，請參閱下面的 **[錯誤方式討論動詞](#wrong-way-verbs)** 。</span><span class="sxs-lookup"><span data-stu-id="83f77-121">Please see the **[Wrong Way Verbs](#wrong-way-verbs)** discussion below for more details.</span></span>

## <a name="wrong-way-verbs"></a><span data-ttu-id="83f77-122">Wrong-Way 動詞</span><span class="sxs-lookup"><span data-stu-id="83f77-122">Wrong-Way Verbs</span></span>

<span data-ttu-id="83f77-123">即使物件具有明確允許讀取或寫入的安全描述項，還是會拒絕對主控台物件進行某些作業。</span><span class="sxs-lookup"><span data-stu-id="83f77-123">Some operations to the console objects will be denied even if the object has a security descriptor that is stated to specifically permit reading or writing.</span></span> <span data-ttu-id="83f77-124">這特別關心在較低許可權的內容中執行的命令列應用程式，其會在更寬鬆的內容中共用命令列應用程式所建立的主控台會話。</span><span class="sxs-lookup"><span data-stu-id="83f77-124">This specifically concerns command-line applications running in a reduced-privilege context that are sharing a console session that was created by a command-line application in a more permissive context.</span></span>

<span data-ttu-id="83f77-125">「錯誤的動詞命令」一詞旨在套用至與其中一個主控台物件的一般流程相反的作業。</span><span class="sxs-lookup"><span data-stu-id="83f77-125">The term "wrong-way verbs" is intended to apply to the operation that is the converse of the normal flow for one of the console objects.</span></span> <span data-ttu-id="83f77-126">具體來說，輸出緩衝區的一般流程是寫入，而輸入緩衝區的一般流程正在讀取。</span><span class="sxs-lookup"><span data-stu-id="83f77-126">Specifically, the normal flow for the output buffer is writing and the normal flow for the input buffer is reading.</span></span> <span data-ttu-id="83f77-127">因此，「錯誤的」是讀取輸出緩衝區或寫入輸入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="83f77-127">The "wrong-way" would therefore be the reading of the output buffer or the writing of the input buffer.</span></span> <span data-ttu-id="83f77-128">這些是 **[低層級主控台 I/o 函數](low-level-console-i-o.md)** 檔中所述的函式。</span><span class="sxs-lookup"><span data-stu-id="83f77-128">These are functions that are described in the **[Low-Level Console I/O Functions](low-level-console-i-o.md)** documentation.</span></span>

<span data-ttu-id="83f77-129">可以找到這兩個案例：</span><span class="sxs-lookup"><span data-stu-id="83f77-129">The two scenarios where this can be found are:</span></span>

1. <span data-ttu-id="83f77-130">**[通用 Windows 平臺主控台應用程式](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)** 。</span><span class="sxs-lookup"><span data-stu-id="83f77-130">**[Universal Windows Platform console apps](https://docs.microsoft.com/windows/uwp/launch-resume/console-uwp)** .</span></span> <span data-ttu-id="83f77-131">因為這些是其他通用 Windows 平臺應用程式的 cousin，所以它們會保有與其他應用程式隔離的承諾，並在其作業效果方面提供使用者保證。</span><span class="sxs-lookup"><span data-stu-id="83f77-131">As these are cousins of other Universal Windows Platform applications, they hold a promise that they are isolated from other applications and provide user guarantees around the effects of their operation.</span></span>
1. <span data-ttu-id="83f77-132">任何的主控台應用程式都是以比現有會話更低的 **[完整性層級](https://docs.microsoft.com/windows/win32/secauthz/mandatory-integrity-control)** 來啟動，您可以在 **[CreateProcess 期間使用標籤或權杖操作](https://docs.microsoft.com/previous-versions/dotnet/articles/bb625960(v=msdn.10))** 來完成。</span><span class="sxs-lookup"><span data-stu-id="83f77-132">Any console application intentionally launched with a lower **[integrity level](https://docs.microsoft.com/windows/win32/secauthz/mandatory-integrity-control)** than the existing session which can be accomplished with **[labeling or token manipulation during CreateProcess](https://docs.microsoft.com/previous-versions/dotnet/articles/bb625960(v=msdn.10))** .</span></span>

<span data-ttu-id="83f77-133">如果偵測到上述任一種情況，主控台會將「錯誤的動詞」旗標套用至命令列應用程式連線，並拒絕對下列 Api 的呼叫，以減少層級之間的通訊介面：</span><span class="sxs-lookup"><span data-stu-id="83f77-133">If either of these scenarios is detected, the console will apply the "wrong-way verbs" flag to the command-line application connection and reject calls to the following APIs to reduce the surface of communication between the levels:</span></span>

:::row:::
    :::column:::
        [<span data-ttu-id="83f77-134">ReadConsoleOutput</span><span class="sxs-lookup"><span data-stu-id="83f77-134">ReadConsoleOutput</span></span>](readconsoleoutput.md)  
        [<span data-ttu-id="83f77-135">ReadConsoleOutputCharacter</span><span class="sxs-lookup"><span data-stu-id="83f77-135">ReadConsoleOutputCharacter</span></span>](readconsoleoutputcharacter.md)  
        [<span data-ttu-id="83f77-136">ReadConsoleOutputAttribute</span><span class="sxs-lookup"><span data-stu-id="83f77-136">ReadConsoleOutputAttribute</span></span>](readconsoleoutputattribute.md)  
    :::column-end:::
    :::column:::
        [<span data-ttu-id="83f77-137">WriteConsoleInput</span><span class="sxs-lookup"><span data-stu-id="83f77-137">WriteConsoleInput</span></span>](writeconsoleinput.md)  
    :::column-end:::
:::row-end:::

<span data-ttu-id="83f77-138">拒絕的呼叫會收到 **拒絕存取** 的錯誤碼，與物件上的安全描述項拒絕讀取或寫入權限相同。</span><span class="sxs-lookup"><span data-stu-id="83f77-138">Rejected calls will receive an **access denied** error code, the same as if the read or write permission were denied by the security descriptors on the object.</span></span>

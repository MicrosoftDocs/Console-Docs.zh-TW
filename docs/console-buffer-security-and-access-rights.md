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
# <a name="console-buffer-security-and-access-rights"></a><span data-ttu-id="88330-105">主控台緩衝區安全性和存取權限</span><span class="sxs-lookup"><span data-stu-id="88330-105">Console Buffer Security and Access Rights</span></span>


<span data-ttu-id="88330-106">Windows 安全性模型可讓您控制主控台輸入緩衝區和主控台螢幕緩衝區的存取。</span><span class="sxs-lookup"><span data-stu-id="88330-106">The Windows security model enables you to control access to console input buffers and console screen buffers.</span></span> <span data-ttu-id="88330-107">如需安全性的詳細資訊，請參閱 [存取控制模型](https://msdn.microsoft.com/library/windows/desktop/aa374876)。</span><span class="sxs-lookup"><span data-stu-id="88330-107">For more information about security, see [Access-Control Model](https://msdn.microsoft.com/library/windows/desktop/aa374876).</span></span>

<span data-ttu-id="88330-108">當您呼叫[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)或[**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)函式時，可以指定主控台輸入和主控台畫面緩衝區的[安全描述項](https://msdn.microsoft.com/library/windows/desktop/aa379563)。</span><span class="sxs-lookup"><span data-stu-id="88330-108">You can specify a [security descriptor](https://msdn.microsoft.com/library/windows/desktop/aa379563) for the console input and console screen buffers when you call the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) or [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) function.</span></span> <span data-ttu-id="88330-109">如果您指定 **Null**，則物件會取得預設安全描述項。</span><span class="sxs-lookup"><span data-stu-id="88330-109">If you specify **NULL**, the object gets a default security descriptor.</span></span> <span data-ttu-id="88330-110">主控台緩衝區之預設安全描述項中的 Acl 來自于建立者的主要或模擬權杖。</span><span class="sxs-lookup"><span data-stu-id="88330-110">The ACLs in the default security descriptor for a console buffer come from the primary or impersonation token of the creator.</span></span>

<span data-ttu-id="88330-111">[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)、 [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)和[**GetStdHandle**](getstdhandle.md)傳回的控制碼具有**一般 \_ 讀取**和**一般 \_ 寫入**存取權限。</span><span class="sxs-lookup"><span data-stu-id="88330-111">The handles returned by [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858), [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md), and [**GetStdHandle**](getstdhandle.md) have the **GENERIC\_READ** and **GENERIC\_WRITE** access rights.</span></span>

<span data-ttu-id="88330-112">有效的存取權限包含**一般 \_ 讀取**和**一般 \_ 寫入**[一般存取權限](https://msdn.microsoft.com/library/windows/desktop/aa446632)。</span><span class="sxs-lookup"><span data-stu-id="88330-112">The valid access rights include the **GENERIC\_READ** and **GENERIC\_WRITE** [generic access rights](https://msdn.microsoft.com/library/windows/desktop/aa446632).</span></span>


| <span data-ttu-id="88330-113">值</span><span class="sxs-lookup"><span data-stu-id="88330-113">Value</span></span>                            | <span data-ttu-id="88330-114">意義</span><span class="sxs-lookup"><span data-stu-id="88330-114">Meaning</span></span>                                                                                               |
|----------------------------------|-------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="88330-115">**泛型 \_閱讀** (0x80000000L) </span><span class="sxs-lookup"><span data-stu-id="88330-115">**GENERIC\_READ** (0x80000000L)</span></span>  | <span data-ttu-id="88330-116">要求主控台螢幕緩衝區的讀取權限，以便讓進程從緩衝區讀取資料。</span><span class="sxs-lookup"><span data-stu-id="88330-116">Requests read access to the console screen buffer, enabling the process to read data from the buffer.</span></span> |
| <span data-ttu-id="88330-117">**泛型 \_撰寫** (0x40000000L) </span><span class="sxs-lookup"><span data-stu-id="88330-117">**GENERIC\_WRITE** (0x40000000L)</span></span> | <span data-ttu-id="88330-118">要求主控台螢幕緩衝區的寫入存取權，讓進程能夠將資料寫入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="88330-118">Requests write access to the console screen buffer, enabling the process to write data to the buffer.</span></span> |











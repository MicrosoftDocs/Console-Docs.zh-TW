---
title: CTRL + 關閉信號
description: 當使用者關閉主控台時，系統會產生 CTRL + CLOSE 信號。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_ctrl\_close\_signal'
- base.ctrl\_close\_signal
- consoles.ctrl\_close\_signal
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a327dd55-3250-40ee-b1c4-6ba3b80984a8
ms.openlocfilehash: be237eac7649ad76615aea341a555a8a7af6445c
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357888"
---
# <a name="ctrlclose-signal"></a><span data-ttu-id="4b61b-104">CTRL + 關閉信號</span><span class="sxs-lookup"><span data-stu-id="4b61b-104">CTRL+CLOSE Signal</span></span>

<span data-ttu-id="4b61b-105">當使用者關閉主控台時，系統會產生 CTRL + CLOSE 信號。</span><span class="sxs-lookup"><span data-stu-id="4b61b-105">The system generates a CTRL+CLOSE signal when the user closes a console.</span></span> <span data-ttu-id="4b61b-106">所有附加至主控台的進程都會收到信號，讓每個處理常式有機會在終止前進行清除。</span><span class="sxs-lookup"><span data-stu-id="4b61b-106">All processes attached to the console receive the signal, giving each process an opportunity to clean up before termination.</span></span> <span data-ttu-id="4b61b-107">當進程收到此信號時，處理常式函式在執行任何清除作業之後，可以採取下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="4b61b-107">When a process receives this signal, the handler function can take one of the following actions after performing any cleanup operations:</span></span>

- <span data-ttu-id="4b61b-108">呼叫 [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) 以終止進程。</span><span class="sxs-lookup"><span data-stu-id="4b61b-108">Call [**ExitProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) to terminate the process.</span></span>
- <span data-ttu-id="4b61b-109">傳回 **FALSE**。</span><span class="sxs-lookup"><span data-stu-id="4b61b-109">Return **FALSE**.</span></span> <span data-ttu-id="4b61b-110">如果沒有任何已註冊的處理常式函式傳回 **TRUE**，則預設處理常式會終止進程。</span><span class="sxs-lookup"><span data-stu-id="4b61b-110">If none of the registered handler functions returns **TRUE**, the default handler terminates the process.</span></span>
- <span data-ttu-id="4b61b-111">傳回 **TRUE**。</span><span class="sxs-lookup"><span data-stu-id="4b61b-111">Return **TRUE**.</span></span> <span data-ttu-id="4b61b-112">在此情況下，不會呼叫任何其他處理常式函式，且進程會終止。</span><span class="sxs-lookup"><span data-stu-id="4b61b-112">In this case, no other handler functions are called and the process terminates.</span></span>
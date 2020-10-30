---
ms.openlocfilehash: 16b504d04a19d10e57d618ab380d8d2091c9c906
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037719"
---
> [!TIP]
> <span data-ttu-id="1b268-101">不建議使用此 API，也不會有對等的 **[虛擬終端](../console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="1b268-101">This API is not recommended and does not have a **[virtual terminal](../console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="1b268-102">這項決策刻意讓 Windows 平臺與其他作業系統保持一致，而個別用戶端應用程式應記住自己的繪製狀態以進行進一步的操作。</span><span class="sxs-lookup"><span data-stu-id="1b268-102">This decision intentionally aligns the Windows platform with other operating systems where the individual client application is expected to remember its own drawn state for further manipulation.</span></span> <span data-ttu-id="1b268-103">使用此 API 時，透過跨平臺公用程式和傳輸（如 SSH）的應用程式遠端執行可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="1b268-103">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

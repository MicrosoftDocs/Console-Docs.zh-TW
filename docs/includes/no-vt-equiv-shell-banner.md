---
ms.openlocfilehash: 572d988660f53b2a504800f4fef3dce46d16b61b
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037549"
---
> [!TIP]
> <span data-ttu-id="3ca8d-101">不建議使用此 API，也不會有對等的 **[虛擬終端](../console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="3ca8d-101">This API is not recommended and does not have a **[virtual terminal](../console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="3ca8d-102">這項決策刻意讓 Windows 平臺與其他作業系統保持一致，也就是做為 shell 或解譯器的個別用戶端應用程式應維持自己的使用者便利功能，例如行讀和操作行為，包括別名和命令歷程記錄。</span><span class="sxs-lookup"><span data-stu-id="3ca8d-102">This decision intentionally aligns the Windows platform with other operating systems where the individual client application acting as a shell or interpreter is expected to maintain its own user-convenience functionality like line reading and manipulation behavior including aliases and command history.</span></span> <span data-ttu-id="3ca8d-103">使用此 API 時，透過跨平臺公用程式和傳輸（如 SSH）的應用程式遠端執行可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="3ca8d-103">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

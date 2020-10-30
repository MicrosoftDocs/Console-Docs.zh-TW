---
ms.openlocfilehash: ef8a068fe6edd2a7d2013c930c238235326b8c1d
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039129"
---
> [!TIP]
> <span data-ttu-id="af26c-101">不建議使用此 API，但它在 **[替代螢幕緩衝區](../console-virtual-terminal-sequences.md#alternate-screen-buffer)** 順序中有相當接近的 **[虛擬終端](../console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="af26c-101">This API is not recommended but it does have an approximate **[virtual terminal](../console-virtual-terminal-sequences.md)** equivalent in the **[alternate screen buffer](../console-virtual-terminal-sequences.md#alternate-screen-buffer)** sequence.</span></span> <span data-ttu-id="af26c-102">設定 _替代螢幕緩衝區_ 可為應用程式提供個別、隔離的空間，以在其會話執行時間的過程中進行繪製，同時保留應用程式的啟動程式所顯示的內容。</span><span class="sxs-lookup"><span data-stu-id="af26c-102">Setting the _alternate screen buffer_ can provide an application with a separate, isolated space for drawing over the course of its session runtime while preserving the content that was displayed by the application's invoker.</span></span> <span data-ttu-id="af26c-103">這會維護在進程結束時進行簡單還原的繪圖資訊。</span><span class="sxs-lookup"><span data-stu-id="af26c-103">This maintains that drawing information for simple restoration on process exit.</span></span>

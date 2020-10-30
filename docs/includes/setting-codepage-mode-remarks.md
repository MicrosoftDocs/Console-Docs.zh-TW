---
ms.openlocfilehash: 2e5222bba5878d98c6f703b8aa25dfd1a22197db
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037028"
---
<span data-ttu-id="f126e-101">此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。</span><span class="sxs-lookup"><span data-stu-id="f126e-101">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="f126e-102">主控台的字碼頁一開始預設為系統的 OEM 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="f126e-102">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="f126e-103">若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](../setconsolecp.md) 或 [**SetConsoleOutputCP**](../setconsoleoutputcp.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="f126e-103">To change the console's code page, use the [**SetConsoleCP**](../setconsolecp.md) or [**SetConsoleOutputCP**](../setconsoleoutputcp.md) functions.</span></span> <span data-ttu-id="f126e-104">舊版取用者也可以使用 **chcp** 或 **mode con cp select =** 命令，但不建議用於新的開發。</span><span class="sxs-lookup"><span data-stu-id="f126e-104">Legacy consumers may also use the **chcp** or **mode con cp select=** commands, but it is not recommended for new development.</span></span>
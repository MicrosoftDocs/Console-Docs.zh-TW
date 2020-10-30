---
ms.openlocfilehash: 2e5222bba5878d98c6f703b8aa25dfd1a22197db
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037028"
---
此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。 主控台的字碼頁一開始預設為系統的 OEM 字碼頁。 若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](../setconsolecp.md) 或 [**SetConsoleOutputCP**](../setconsoleoutputcp.md) 函數。 舊版取用者也可以使用 **chcp** 或 **mode con cp select =** 命令，但不建議用於新的開發。
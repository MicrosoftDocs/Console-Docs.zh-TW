---
ms.openlocfilehash: 2e5222bba5878d98c6f703b8aa25dfd1a22197db
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "93037028"
---
此函式會從主控台的目前字碼頁使用 Unicode 字元或 8 位元字元。 主控台的字碼頁一開始會預設為系統的 OEM 字碼頁。 若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](../setconsolecp.md) 或 [**SetConsoleOutputCP**](../setconsoleoutputcp.md) 函式。 舊版取用者也可以使用 **chcp** 或 **mode con cp select=** 命令，但不建議用於新的開發。
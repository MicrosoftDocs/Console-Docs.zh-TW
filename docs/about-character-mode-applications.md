---
title: 關於主控台
description: 主控台提供簡單字元模式應用程式的高階支援，這些應用程式會使用從標準輸入讀取和寫入至標準輸出或標準錯誤的函式，與使用者互動。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_about\_character\_mode\_applications'
- base.about\_character\_mode\_applications
- consoles.about\_character\_mode\_applications
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 39204f0e-b0b8-4f92-af8e-e146ac06c454
ms.openlocfilehash: 0a738c72ec45a68817fae6dbfa9d6b3e45beb53e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059394"
---
# <a name="about-character-mode-applications"></a>關於字元模式應用程式

字元模式 (或「命令列」 ) 應用程式：

1. 跟從標準輸入 (stdin) 讀取資料
2. 「工作」
3. 跟將資料寫入標準輸出 (stdout) 或標準錯誤 (stderr) 

字元模式應用程式會透過「主控台」 (或「終端機」 ) 應用程式與終端使用者進行通訊。 主控台會從鍵盤、滑鼠、觸控畫面、畫筆等來轉換使用者輸入，並將其傳送至字元模式應用程式的 stdin。 主控台可能也會在使用者的畫面上顯示字元模式應用程式的文字輸出。

在 Windows 中，主控台是內建的，並提供豐富的 API，可讓字元模式應用程式與使用者互動。

- [機](consoles.md)
- [輸入和輸出方法](input-and-output-methods.md)
- [主控台字碼頁](console-code-pages.md)
- [主控台控制處理常式](console-control-handlers.md)
- [主控台別名](console-aliases.md)
- [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)
- [主控台應用程式問題](console-application-issues.md)

 

 





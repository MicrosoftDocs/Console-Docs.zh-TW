---
title: 主控台控制代碼
description: 主控台程序會使用控制代碼來存取其主控台的輸入和畫面緩衝區，包括 GetStdHandle、CreateFile 或 CreateConsoleScreenBuffer 函式。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_console\_handles'
- base.console\_handles
- consoles.console\_handles
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: dc723046-b3e9-418a-b386-79be411e5ac8
ms.localizationpriority: high
ms.openlocfilehash: acc7d65e15451fc2804dc1782644c1ccbaa30e28
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420237"
---
# <a name="console-handles"></a>主控台控制代碼

主控台程序會使用控制代碼來存取其主控台的輸入和畫面緩衝區。 程序可以使用 [**GetStdHandle**](getstdhandle.md)、[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)，或 [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) 函式來開啟其中一個控制代碼。

[**GetStdHandle**](getstdhandle.md) 函式提供一種機制，可用來擷取與程序相關聯的標準輸入 (`STDIN`)、標準輸出 (`STDOUT`) 和標準錯誤 (`STDERR`) 控制代碼。 系統會在建立主控台期間建立這些控制代碼。 一開始，`STDIN` 是主控台輸入緩衝區的控制代碼，而 `STDOUT` 和 `STDERR` 是主控台作用中畫面緩衝區的控制代碼。 不過，[**SetStdHandle**](setstdhandle.md) 函式可以藉由變更與 `STDIN`、`STDOUT` 或 `STDERR` 相關聯的控制代碼，來重新導向標準控制代碼。 因為父系的標準控制代碼會由任何子程序繼承，所以後續對 **GetStdHandle**  發出的呼叫都會傳回重新導向的控制代碼。 因此，**GetStdHandle** 傳回的控制代碼可能會參考主控台 I/O 以外的項目。 例如，在建立子程序之前，父程序可以使用 **SetStdHandle** 將管道控制代碼設定為子程序繼承的 `STDIN` 控制代碼。 當子程序呼叫 **GetStdHandle** 時，即可取得管道控制代碼。 這表示父程序可以控制子程序的標準控制代碼。 **GetStdHandle** 傳回的控制代碼都具有 `GENERIC_READ | GENERIC_WRITE` 存取權 (除非已使用 **SetStdHandle** 將標準控制代碼設定為具有較低的存取權)。

[**GetStdHandle**](getstdhandle.md) 所傳回的控制代碼值不是 0、1 和 2，因此 Stdio.h 中的標準預先定義資料流常數 (`STDIN`、`STDOUT` 和 `STDERR`) 不能用在需要主控台控制代碼的函式中。

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) 函式可讓程序取得其主控台輸入緩衝區和作用中畫面緩衝區的控制代碼，即使 `STDIN` 和 `STDOUT` 已經重新導向也一樣。 若要開啟主控台輸入緩衝區的控制代碼，請在對 **CreateFile** 發出的呼叫中指定 `CONIN$` 值。 在對 **CreateFile** 發出的呼叫中指定 `CONOUT$` 值，可開啟主控台作用中畫面緩衝區的控制代碼。 **CreateFile** 可讓您指定所傳回控制代碼的讀取/寫入存取權。

[**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) 函式會建立新的畫面緩衝區，並傳回控制代碼。 此控制代碼可用於任何接受主控台輸出控制代碼的函式。 若要讓新的畫面緩衝區開始作用 (顯示)，則必須在呼叫 [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) 函式時指定其控制代碼。 請注意，變更作用中畫面緩衝區不會影響 [**GetStdHandle**](getstdhandle.md) 所傳回的控制代碼。 同樣地，使用 [**SetStdHandle**](setstdhandle.md) 變更 `STDOUT` 控制代碼，並不會影響作用中的畫面緩衝區。

當任何主控台函式需要主控台輸入緩衝區的控制代碼或主控台畫面緩衝區的控制代碼時，您都可以使用 [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) 和 [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) 所傳回的主控台控制代碼。 如果主控台函式尚未重新導向為參考主控台 I/O 以外的項目，主控台函式也可使用 [**GetStdHandle**](getstdhandle.md) 所傳回的控制代碼。 不過，如果已將標準控制代碼重新導向為參考檔案或管道，則只有 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 和 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 函式可以使用控制代碼。 [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype) 可以協助您判斷控制代碼所參考的裝置類型。 主控台控制代碼會顯示為 `FILE_TYPE_CHAR`。

程序可以使用 [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) 函式建立重複的主控台控制代碼，但其存取權或繼承性可以與原本控制代碼不同。 不過，請注意，程序建立的重複主控台控制代碼僅能供自己使用。 這與其他控制代碼類型 (例如檔案、管道或 Mutex 物件) 不同，**DuplicateHandle** 可以建立對不同程序有效的副本。
主控台的存取權必須在 [建立](creation-of-a-console.md)其他程序期間共用，或是由其他程序透過 [**AttachConsole**](attachconsole.md) 機制來要求。

若要關閉主控台控制代碼，程序可以使用 [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) 函式。

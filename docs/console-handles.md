---
title: 主控台控制代碼
description: 主控台進程會使用控制碼來存取其主控台的輸入和螢幕緩衝區，包括 GetStdHandle、CreateFile 或 CreateConsoleScreenBuffer 函數。
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
ms.openlocfilehash: 29d25e83281c7c98c74ae4a0da03eea06dbf0077
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039226"
---
# <a name="console-handles"></a>主控台控制代碼

主控台進程會使用控制碼來存取其主控台的輸入和螢幕緩衝區。 處理常式可以使用 [**GetStdHandle**](getstdhandle.md)、 [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)或 [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) 函數來開啟這些控制碼的其中一個。

[**GetStdHandle**](getstdhandle.md)函式會提供一種機制，用來抓取標準輸入 (`STDIN`) 、標準輸出 (`STDOUT`) ，以及 `STDERR` 與處理常式相關聯的標準錯誤 () 控制碼。 在主控台建立期間，系統會建立這些控制碼。 一開始， `STDIN` 是主控台輸入緩衝區的控制碼，而且 `STDOUT` `STDERR` 是主控台的作用中螢幕緩衝區的控制碼。 不過， [**SetStdHandle**](setstdhandle.md) 函數可以藉由變更與、或相關聯的控制碼，來重新導向標準控制碼 `STDIN` `STDOUT` `STDERR` 。 由於父系的標準控制碼會由任何子進程繼承，因此對 **GetStdHandle** 的後續呼叫會傳回重新導向的控制碼。 因此， **GetStdHandle** 所傳回的控制碼可能會參考主控台 i/o 以外的內容。 例如，在建立子進程之前，父進程可以使用 **SetStdHandle** 將管道控制碼設定為 `STDIN` 子進程繼承的控制碼。 當子進程呼叫 **GetStdHandle** 時，它會取得管道控制碼。 這表示父進程可以控制子進程的標準控制碼。 **GetStdHandle** 所傳回的控制碼具有 `GENERIC_READ | GENERIC_WRITE` 存取權，除非使用 **SetStdHandle** 來設定標準控制碼的存取權較少。

[**GetStdHandle**](getstdhandle.md)傳回的控制碼值不是0、1和2，因此在 `STDIN` `STDOUT` 需要主控台控制碼的函式中， `STDERR` 不能使用 stdio.h 中的標準預先定義資料流程常數 (、和) 。

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)函式可讓進程取得其主控台輸入緩衝區和作用中螢幕緩衝區的控制碼，即使 `STDIN` 和已重新 `STDOUT` 導向。 若要開啟主控台輸入緩衝區的控制碼，請 `CONIN$` 在 **CreateFile** 的呼叫中指定值。 `CONOUT$`在 **CreateFile** 的呼叫中指定值，以開啟主控台的作用中螢幕緩衝區的控制碼。 **CreateFile** 可讓您指定所傳回之控制碼的讀取/寫入存取權。

[**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)函式會建立新的螢幕緩衝區，並傳回控制碼。 這個控制碼可用於接受主控台輸出之控制碼的任何函式。 在 [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) 函式的呼叫中指定其控制碼之前，新的螢幕緩衝區不會 (顯示) 。 請注意，變更主動螢幕緩衝區並不會影響 [**GetStdHandle**](getstdhandle.md)所傳回的控制碼。 同樣地，使用 [**SetStdHandle**](setstdhandle.md) 來變更 `STDOUT` 控制碼並不會影響使用中的螢幕緩衝區。

[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)和 [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md)所傳回的主控台控制碼，可用於需要主控台輸入緩衝區或主控台螢幕緩衝區控制碼的任何主控台功能。 如果 [**GetStdHandle**](getstdhandle.md) 傳回的控制碼未被重新導向來參考主控台 i/o 以外的內容，則可供主控台函式使用。 但是，如果標準控制碼已重新導向為參考檔案或管道，則控制碼只能由 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 和 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 函式使用。 [**GetFileType**](https://docs.microsoft.com/windows/win32/api/fileapi/nf-fileapi-getfiletype) 可協助判斷控制碼所參考的裝置類型。 主控台控制碼會顯示為 `FILE_TYPE_CHAR` 。

進程可以使用 [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) 函式來建立重複的主控台控制碼，該控制碼具有不同的存取或可從原始控制碼取得的繼承性。 不過，請注意，處理常式可以建立重複的主控台控制碼，只供自己使用。 這與其他控制碼類型不同 (例如檔案、管道或 mutex 物件) ， **DuplicateHandle** 可以針對不同的進程建立有效的重複項。
您必須在 [建立](creation-of-a-console.md) 其他進程期間共用主控台的存取權，或透過 [**AttachConsole**](attachconsole.md) 機制來要求其他進程的存取權。

若要關閉主控台控制碼，處理常式可以使用 [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) 函式。

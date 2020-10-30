---
title: 主控台功能
description: 描述用來存取主控台的所有功能的完整清單。
author: miniksa
ms.author: miniksa
ms.topic: hub-page
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_console\_functions'
- base.console\_functions
- consoles.console\_functions
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2a0e5dcc-be48-42ab-a05a-96f68d012a67
ms.openlocfilehash: 0ee2dde2c14a3d827aa2bc5e14f3cc65cf5fdc0f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039236"
---
# <a name="console-functions"></a>主控台功能

以下是用來存取主控台的函式。

| 函式 | 描述 |
|-|-|
| [**AddConsoleAlias**](addconsolealias.md) | 定義指定之可執行檔的主控台別名。 |
| [**AllocConsole**](allocconsole.md) | 配置呼叫進程的新主控台。 |
| [**AttachConsole**](attachconsole.md) | 將呼叫進程附加至指定進程的主控台。 |
| [**ClosePseudoConsole**](closepseudoconsole.md) | 從給定的控制碼關閉 pseudoconsole。 |
| [**CreatePseudoConsole**](createpseudoconsole.md) | 配置呼叫進程的新 pseudoconsole。 |
| [**CreateConsoleScreenBuffer**](createconsolescreenbuffer.md) | 建立主控台螢幕緩衝區。 |
| [**FillConsoleOutputAttribute**](fillconsoleoutputattribute.md) | 為指定的字元儲存格數目設定文字和背景色彩屬性。 |
| [**FillConsoleOutputCharacter**](fillconsoleoutputcharacter.md) | 將字元寫入主控台螢幕緩衝區指定的次數。 |
| [**FlushConsoleInputBuffer**](flushconsoleinputbuffer.md) | 清空主控台輸入緩衝區。 |
| [**FreeConsole**](freeconsole.md) | 從其主控台卸離呼叫進程。 |
| [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) | 將指定的信號傳送至主控台進程群組，該群組會共用與呼叫進程相關聯的主控台。 |
| [**GetConsoleAlias**](getconsolealias.md) | 針對指定的可執行檔，抓取指定的別名。 |
| [**GetConsoleAliases**](getconsolealiases.md) | 針對指定的可執行檔，抓取所有已定義的主控台別名。 |
| [**GetConsoleAliasesLength**](getconsolealiaseslength.md) | 傳回為指定的可執行檔儲存所有主控台別名所需的緩衝區大小（以位元組為單位）。 |
| [**GetConsoleAliasExes**](getconsolealiasexes.md) | 使用定義的主控台別名，抓取所有可執行檔的名稱。 |
| [**GetConsoleAliasExesLength**](getconsolealiasexeslength.md) | 傳回所需的緩衝區大小（以位元組為單位），以儲存所有已定義主控台別名之可執行檔的名稱。 |
| [**GetConsoleCP**](getconsolecp.md) | 抓取與呼叫進程相關聯的主控台所使用的輸入字碼頁。 |
| [**GetConsoleCursorInfo**](getconsolecursorinfo.md) | 針對指定的主控台螢幕緩衝區，抓取資料指標的大小和可見度的相關資訊。 |
| [**GetConsoleDisplayMode**](getconsoledisplaymode.md) | 抓取目前主控台的顯示模式。 |
| [**GetConsoleFontSize**](getconsolefontsize.md) | 抓取指定的主控台螢幕緩衝區所使用的字型大小。 |
| [**GetConsoleHistoryInfo**](getconsolehistoryinfo.md) | 抓取呼叫進程主控台的歷程記錄設定。 |
| [**GetConsoleMode**](getconsolemode.md) | 抓取主控台之輸入緩衝區的目前輸入模式，或主控台螢幕緩衝區目前的輸出模式。 |
| [**GetConsoleOriginalTitle**](getconsoleoriginaltitle.md) | 抓取目前主控台視窗的原始標題。 |
| [**GetConsoleOutputCP**](getconsoleoutputcp.md) | 抓取與呼叫進程相關聯的主控台所使用的輸出字碼頁。 |
| [**GetConsoleProcessList**](getconsoleprocesslist.md) | 抓取附加至目前主控台的進程清單。 |
| [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) | 抓取指定的主控台螢幕緩衝區的相關資訊。 |
| [**GetConsoleScreenBufferInfoEx**](getconsolescreenbufferinfoex.md) | 抓取指定的主控台螢幕緩衝區的延伸資訊。 |
| [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md) | 抓取目前主控台選取專案的相關資訊。 |
| [**GetConsoleTitle**](getconsoletitle.md) | 抓取目前主控台視窗的標題。 |
| [**GetConsoleWindow**](getconsolewindow.md) | 抓取與呼叫進程相關聯的主控台所使用的視窗控制碼。 |
| [**GetCurrentConsoleFont**](getcurrentconsolefont.md) | 抓取目前主控台字型的相關資訊。 |
| [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) | 抓取有關目前主控台字型的延伸資訊。 |
| [**GetLargestConsoleWindowSize**](getlargestconsolewindowsize.md) | 抓取最大可能主控台視窗的大小。 |
| [**GetNumberOfConsoleInputEvents**](getnumberofconsoleinputevents.md) | 抓取主控台輸入緩衝區中未讀取的輸入記錄數目。 |
| [**GetNumberOfConsoleMouseButtons**](getnumberofconsolemousebuttons.md) | 抓取目前主控台使用之滑鼠上的按鈕數目。 |
| [**GetStdHandle**](getstdhandle.md) | 抓取標準輸入、標準輸出或標準錯誤裝置的控制碼。 |
| [**HandlerRoutine**](handlerroutine.md) | 搭配 [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) 函數使用的應用程式定義函數。 |
| [**PeekConsoleInput**](peekconsoleinput.md) | 從指定的主控台輸入緩衝區讀取資料，而不將它從緩衝區中移除。 |
| [**ReadConsole**](readconsole.md) | 從主控台輸入緩衝區讀取字元輸入，並將它從緩衝區中移除。 |
| [**ReadConsoleInput**](readconsoleinput.md) | 從主控台輸入緩衝區讀取資料，並將其從緩衝區中移除。 |
| [**ReadConsoleOutput**](readconsoleoutput.md) | 從主控台螢幕緩衝區中的字元資料格的矩形區塊讀取字元和色彩屬性資料。 |
| [**ReadConsoleOutputAttribute**](readconsoleoutputattribute.md) | 從主控台螢幕緩衝區的連續儲存格複製指定數目的前景和背景色彩屬性。 |
| [**ReadConsoleOutputCharacter**](readconsoleoutputcharacter.md) | 從主控台螢幕緩衝區的連續儲存格複製一些字元。 |
| [**ResizePseudoConsole**](resizepseudoconsole.md) | 將 pseudoconsole 的內部緩衝區大小調整為指定的大小。 |
| [**ScrollConsoleScreenBuffer**](scrollconsolescreenbuffer.md) | 移動螢幕緩衝區中的資料區塊。 |
| [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) | 將指定的螢幕緩衝區設定為目前顯示的主控台螢幕緩衝區。 |
| [**SetConsoleCP**](setconsolecp.md) | 設定與呼叫進程相關聯的主控台所使用的輸入字碼頁。 |
| [**SetConsoleCtrlHandler**](setconsolectrlhandler.md) | 從呼叫進程的處理常式函式清單中，加入或移除應用程式定義的 [**HandlerRoutine**](handlerroutine.md) 。 |
| [**SetConsoleCursorInfo**](setconsolecursorinfo.md) | 為指定的主控台螢幕緩衝區設定資料指標的大小和可見度。 |
| [**SetConsoleCursorPosition**](setconsolecursorposition.md) | 設定指定的主控台螢幕緩衝區中的游標位置。 |
| [**SetConsoleDisplayMode**](setconsoledisplaymode.md) | 設定指定之主控台螢幕緩衝區的顯示模式。 |
| [**SetConsoleHistoryInfo**](setconsolehistoryinfo.md) | 設定呼叫進程主控台的歷程記錄設定。 |
| [**SetConsoleMode**](setconsolemode.md) | 設定主控台之輸入緩衝區的輸入模式或主控台螢幕緩衝區的輸出模式。 |
| [**SetConsoleOutputCP**](setconsoleoutputcp.md) | 設定與呼叫進程相關聯的主控台所使用的輸出字碼頁。 |
| [**SetConsoleScreenBufferInfoEx**](setconsolescreenbufferinfoex.md) | 設定指定的主控台螢幕緩衝區的延伸資訊。 |
| [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) | 變更指定的主控台螢幕緩衝區大小。 |
| [**SetConsoleTextAttribute**](setconsoletextattribute.md) | 設定寫入主控台螢幕緩衝區之字元的前景 (文字) 和背景色彩屬性。 |
| [**SetConsoleTitle**](setconsoletitle.md) | 設定目前主控台視窗的標題。 |
| [**SetConsoleWindowInfo**](setconsolewindowinfo.md) | 設定主控台螢幕緩衝區視窗的目前大小和位置。 |
| [**SetCurrentConsoleFontEx**](setcurrentconsolefontex.md) | 設定目前主控台字型的延伸資訊。 |
| [**SetStdHandle**](setstdhandle.md) | 設定標準輸入、標準輸出或標準錯誤裝置的控制碼。 |
| [**WriteConsole**](writeconsole.md) | 從目前的游標位置開始，將字元字串寫入至主控台畫面緩衝區。 |
| [**WriteConsoleInput**](writeconsoleinput.md) | 將資料直接寫入主控台輸入緩衝區。 |
| [**WriteConsoleOutput**](writeconsoleoutput.md) | 將字元和色彩屬性資料寫入主控台螢幕緩衝區中指定之字元資料格的矩形區塊。 |
| [**WriteConsoleOutputAttribute**](writeconsoleoutputattribute.md) | 將一些前景和背景色彩屬性複製到主控台螢幕緩衝區的連續儲存格。 |
| [**WriteConsoleOutputCharacter**](writeconsoleoutputcharacter.md) | 將一些字元複製到主控台螢幕緩衝區的連續儲存格。 |

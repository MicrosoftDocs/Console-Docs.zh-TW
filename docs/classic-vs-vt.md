---
title: 傳統主控台 API 與虛擬終端機順序
description: 說明傳統 Win32 主控台 API 介面與虛擬終端機序列 (有時也稱為逸出序列) 概念之間的對比，以撰寫命令列應用程式。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 終端機, 虛擬終端機, 逸出序列, vt, vt100, 主控台 api
ms.prod: console
ms.localizationpriority: high
ms.openlocfilehash: 541300b50521909b22ceaccb595f1945fbfc7e6d
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420177"
---
# <a name="classic-console-apis-versus-virtual-terminal-sequences"></a>傳統主控台 API 與虛擬終端機順序

我們建議是以 **虛擬終端機序列** 取代傳統 **Windows 主控台 API**。 本文將概述這兩者之間的差異，並討論我們建議的原因。

## <a name="definitions"></a>定義

傳統 **[Windows 主控台 API](console-functions.md)** 介面已定義為 `kernel32.dll` 中的 C 語言功能介面系列，其名稱包含 "Console"。

**[虛擬終端機序列](console-virtual-terminal-sequences.md)** 已定義為內嵌在標準輸入和標準輸出資料流中的命令語言。 虛擬終端機序列會使用不可列印的逸出字元，對與一般可列印文字交錯的命令進行訊號處理。

## <a name="history"></a>歷程記錄

**Windows 主控台** 提供廣泛的 API 介面，以供用戶端命令列應用程式控管輸出顯示緩衝區和使用者輸入緩衝區。 不過，其他非 Windows 平台從未對其命令列環境提供此種特定 API 驅動方法，而選擇改為使用內嵌在標準輸入和標準輸出資料流中的虛擬終端機序列。 *(曾有一段時間，Microsoft 透過稱為 ANSI.SYS 的驅動程式，在舊版 DOS 和 Windows 中支援此行為。)*

相反地，**虛擬終端機序列** (採用各種方言) 會驅動所有其他平台的命令列環境作業。 這些序列是由多家廠商植入 [ECMA 標準](https://www.ecma-international.org/publications/standards/Ecma-048.htm)和擴充功能系列中，可往回追溯至 Digital Equipment Corporation 和 Tektronix 終端機，一直到更現代化和常見的軟體終端機，例如 [xterm](https://invisible-island.net/xterm/)。 虛擬終端機序列網域內有許多擴充功能存在，而且有些序列比其他序列受到更廣泛的支援，但請放心，世界已將此標準化為命令列體驗的命令語言，而且幾乎每個終端機和命令列用戶端應用程式都支援已知的子集。

## <a name="cross-platform-support"></a>跨平台支援

**虛擬終端機序列** 會以原生方式跨平台支援，讓終端機應用程式和命令列公用程式能輕鬆地在不同的作業系統 (Windows 除外) 版本之間進行移植。

相反地，只有 Windows 支援 **Windows 主控台 API**。 當您嘗試從在平台之間移植命令列公用程式時，必須在 Windows 與虛擬終端機之間撰寫廣大配接器或轉譯程式庫，反之亦然。

### <a name="remote-access"></a>遠端存取

**虛擬終端機序列** 保有遠端存取的主要優點。 其不需執行額外的工作來傳輸或執行遠端程序呼叫，而是透過設定標準遠端命令列連線所需的功能。 只要透過管道、通訊端、檔案、序列埠或任何其他裝置連接輸出和輸入傳輸通道 (或單一雙向通道)，就足以將應用程式陳述這些序列所需的所有資訊完全送到遠端主機。

相反地，**Windows 主控台 API** 只有在本機電腦上可供存取，而在遠端進行的所有工作都需要建立整個遠端呼叫和傳輸介面層，不只是簡單的通道。

### <a name="separation-of-concerns"></a>關注點分離

有些 **Windows 主控台 API** 會提供對輸入和輸出緩衝區的低層級存取，或適用於互動式命令列的便捷功能。 這可能包括在主控台子系統和主機環境中以程式設計方式撰寫的別名和命令歷程記錄，而不是在命令列用戶端應用程式本身內撰寫。

相反地，**其他平台** 讓記住應用程式和便利功能的目前狀態成為命令列公用程式或 Shell 本身的責任。

**Windows 主控台** 在主控台主機和 API 中處理這項責任的方式，可讓您更快速且更輕鬆地使用這些功能來撰寫命令列應用程式，進而消除記得描繪狀態或處理編輯便利功能的責任。 不過，由於實作和可用性方面的變化，這讓您幾乎無法在不同平台、版本或案例中，從遠端連線這些活動。 這種處理責任的方式也會讓這些 Windows 命令列應用程式的最終互動式體驗完全相依於主控台主機的實作、優先順序和發行週期。

例如，只有在命令列應用程式處理編輯顧慮本身時，才可以使用進階行編輯功能，例如語法醒目提示和複雜的選取。 主控台絕對無法像用戶端應用程式一樣，以概括的方式完全理解這些案例。

相反地，其他平台會使用 **虛擬終端機序列**，透過可重複使用的用戶端程式庫 (例如 [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 和 [ncurses](https://invisible-island.net/ncurses/ncurses.html)) 來處理這些活動和虛擬終端機通訊本身。 最終終端機只負責顯示資訊和透過該雙向通道接收輸入。

### <a name="wrong-way-verbs"></a>錯誤的動詞命令

透過 **Windows 主控台**，可以在輸入和輸出資料流上，以反自然的方向執行某些動作。 這可讓 Windows 命令列應用程式避免管理自有緩衝區的疑慮。 也可讓 Windows 命令列應用程式執行進階作業，例如，代表使用者模擬/插入輸入，或讀回已寫入的部分歷程記錄。

雖然這可讓 Windows 應用程式在單一電腦上的特定使用者內容中運作，但是若使用於某些案例，也會提供一個媒介來跨越安全性和權限層級或網域。 這類案例包括在同一部電腦上的不同內容之間運作，或是將內容跨越至另一個電腦或環境。

其他使用 **虛擬終端機序列** 的平台則不允許此活動。 我們建議從傳統 Windows 主控台轉換到虛擬終端機序列的意圖，就是基於互通性和安全性理由來趨近此策略。

### <a name="direct-window-access"></a>直接視窗存取

**Windows 主控台 API 介面** 會提供主控視窗的精確視窗控點。 這可讓命令列公用程式藉由進入針對視窗控點所允許的各種 Win32 API 來執行進階視窗作業。 這些 Win32 API 可以控管視窗狀態、框架、圖示或視窗的其他相關屬性。

相反地，在具有 **虛擬終端機序列** 的其他平台上，有一小組可針對視窗執行的命令。 這些命令可執行像是變更視窗大小或所顯示標題之類的作業，但必須在相同的頻帶中以及與資料流其餘部分相同的控制下完成。

隨著 Windows 演變，視窗控點的安全性控制和限制也隨之增加。 此外，在任何特定使用者介面元素上，應用程式可定址視窗控點的性質和存在已演進，尤其是對裝置外型規格和平台的支援增加。 這可讓命令列應用程式的直接視窗存取變得脆弱，因為平台和體驗都進化。

### <a name="unicode"></a>Unicode

UTF-8 是幾乎所有新式平台上 Unicode 資料接受的編碼，因為其在可攜性、儲存體大小和處理時間之間達到適當的平衡。 不過，Windows 在過去選擇 UTF-16 作為 Unicode 資料的主要編碼。 Windows 中的 UTF-8 支援一直增加，使用這些 Unicode 格式並不會妨礙其他編碼的使用。

**Windows 主控台** 平台已支援並將持續支援所有現有的字碼頁和編碼。 使用 UTF-16 以達到跨 Windows 版本的最大相容性，並在必要時以 UTF-8 執行演算轉譯。 主控台系統正在增加 UTF-8 的支援。

不需透過所有主控台 API 的 _W_ 變體來進行其他設定，便可利用主控台中的 UTF-16 支援，而對於透過與其他 Microsoft 和 Windows 平台功能和產品的 `wchar_t` 和 _W_ 變體通訊而已經精通 UTF-16 的應用程式而言，UTF-16 支援是比較合適的選擇。

透過 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 和 [**SetConsoleCP**](setconsolecp.md) 方法將字碼頁設定為 `65001` 或 `CP_UTF8` 之後，即可透過主控台 API 的 _A_ 變體，對主控台控點利用主控台中的 UTF-8 支援。 只有在電腦尚未在 [控制台] 的 [地區] 區段中針對非 Unicode 應用程式的設定選擇 [使用 Unicode UTF-8 作為全球語言支援] 時，才需要預先設定字碼頁。

>[!NOTE]
> 從現在開始，透過 [**WriteConsole**](writeconsole.md) 和 [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 方法在標準輸出資料流上完全支援 UTF-8。 輸入資料流的支援會隨著輸入模式而有所不同，並且會隨著時間繼續改善。 值得注意的是，輸入上的預設 **[「修正」](high-level-console-modes.md)** 模式尚未完全支援 UTF-8。 在 GitHub 上的 [**microsoft/terminal#7777**](https://github.com/microsoft/terminal/issues/7777) 可找到此工作的目前狀態。 因應措施是使用可以演算法方式轉譯的 UTF-16，透過 [**ReadConsoleW**](readconsole.md) 或 [**ReadConsoleInputW**](readconsoleinput.md) 來讀取輸入，直到解決懸而未決的問題為止。

## <a name="recommendations"></a>建議

對於在 Windows 上進行的所有全新和持續開發，**建議使用虛擬終端機序列** 作為與終端機互動的方式。 這會將 Windows 命令列用戶端應用程式與其他所有平台上的應用程式設計樣式匯聚在一起。

### <a name="exceptions-for-using-windows-console-apis"></a>使用 Windows 主控台 API 的例外狀況

建立初始環境時，仍然需要 **有限的 Windows 主控台 API 子集**。 在程序、訊號、裝置和編碼處理方面，Windows 平台仍然與其他平台有所不同：

- 程序的標準控點仍會使用 **[GetStdHandle](getstdhandle.md)** 和 **[SetStdHandle](setstdhandle.md)** 進行控制。

- 在要加入虛擬終端機序列支援的控點上，將會使用 **[GetConsoleMode](getconsolemode.md)** 和 **[SetConsoleMode](setconsolemode.md)** 來處理主控台模式的設定。

- 字碼頁或 UTF-8 支援的宣告會利用 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 和 [**SetConsoleCP**](setconsolecp.md) 方法進行。

- [**AllocConsole**](allocconsole.md)、[**AttachConsole**](attachconsole.md) 和 [**FreeConsole**](freeconsole.md) 可能需要某種程度的整體程序管理，才能加入或離開主控台裝置工作階段。

- [**SetConsoleCtrlHandler**](setconsolectrlhandler.md)、[**HandlerRoutine**](handlerroutine.md) 和 [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) 會繼續進行訊號和訊號處理。

- 可以透過 [**WriteConsole**](writeconsole.md) 和 [**ReadConsole**](readconsole.md) 進行與主控台裝置控點的通訊。 也可透過以下形式的程式設計語言執行階段來進行：- C 執行階段 (CRT)：**printf**、**scanf**、**putc**、**getc** 之類的[資料流 I/O](https://docs.microsoft.com/cpp/c-runtime-library/stream-i-o)，或[其他層級的 I/O 函式](https://docs.microsoft.com/cpp/c-runtime-library/input-and-output)。
        - C++ 標準程式庫 (STL)：[iostream](https://docs.microsoft.com/cpp/standard-library/iostream)，例如 **cout** 和 **cin**。
        - .NET 執行階段：[System.Console](https://docs.microsoft.com/dotnet/api/system.console)，例如 **Console.WriteLine**。

- 必須留意視窗大小變更的應用程式，仍然需要使用 [**ReadConsoleInput**](readconsoleinput.md) 來接收與重要事件交錯的變更，因為 **ReadConsole** 會獨自捨棄這些變更。

- 尋找視窗大小仍必須使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 執行，以便應用程式嘗試描繪資料行、格線或填滿顯示。 視窗和緩衝區大小會在 [pseudoconsole](pseudoconsoles.md) 工作階段中比對。

## <a name="future-planning-and-pseudoconsole"></a>未來規劃和 Pseudoconsole

不打算從平排中移除 Windows 主控台 API。

相反地，Windows 主控台主機已提供 **[pseudoconsole](pseudoconsoles.md)** 技術，可將現有的 Windows 命令列應用程式呼叫轉譯為虛擬終端機序列，並從遠端或跨越平台將其轉送至另一個主控環境。

這種轉譯並不完美。 需要主控台主機視窗，才能維護 Windows 對使用者所顯示的模擬環境。 接著，將此模擬環境的複本投射到 **pseudoconsole** 主機。 所有 Windows 主控台 API 呼叫都是在模擬環境中運作，以滿足舊版命令列用戶端應用程式的需求。 只有效果會傳播到最終主機。

命令列應用程式很渴望跨平台的完全相容性，以及在 Windows 和其他平台上完整支援所有的新功能和案例，因此建議移至虛擬終端機序列，並調整命令列應用程式的架構以符合所有平台。

如需命令列應用程式的此種 Windows 轉換詳細資訊，請參閱我們的[生態系統藍圖](ecosystem-roadmap.md)。

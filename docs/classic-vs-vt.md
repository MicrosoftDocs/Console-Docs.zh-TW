---
title: 傳統主控台 Api 與虛擬終端機序列
description: 描述傳統 Win32 主控台 API 介面和虛擬終端機序列（有時也稱為 escape 序列）之間的對比，以撰寫命令列應用程式。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台、終端機、虛擬終端機、escape 序列、vt、vt100、主控台 api
ms.prod: console
ms.openlocfilehash: 0fdd39cab5b8f6ca5cc1602c8e68ec7f2a2303ad
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039578"
---
# <a name="classic-console-apis-versus-virtual-terminal-sequences"></a>傳統主控台 Api 與虛擬終端機序列

我們的建議是將傳統 **Windows 主控台 API** 取代為 **虛擬終端機序列** 。 本文將概述兩者之間的差異，並討論建議的原因。

## <a name="definitions"></a>定義

傳統 **[Windows 主控台 API](console-functions.md)** 介面定義為 `kernel32.dll` 名稱中具有 "Console" 的 C 語言功能介面系列。

**[虛擬終端機序列](console-virtual-terminal-sequences.md)** 定義為內嵌在標準輸入和標準輸出資料流程中的命令語言。 虛擬終端機序列使用不可列印的 escape 字元，以使用正常可列印文字來進行交叉信號的命令。

## <a name="history"></a>歷程記錄

**Windows 主控台** 針對用戶端命令列應用程式提供廣泛的 API 介面，以操作輸出顯示緩衝區和使用者輸入緩衝區。 不過，其他非 Windows 平臺從未對其命令列環境將這個特定的 API 導向方法，改為使用內嵌在標準輸入和標準輸出串流內的虛擬終端機序列。 *(一段時間，Microsoft 會透過稱為 ANSI.SYS 的驅動程式，在舊版 DOS 和 Windows 中支援此行為。 )*

相較之下， **虛擬終端機序列** (于各種方言中，) 為所有其他平臺的命令列環境作業驅動。 這些序列是以 [ECMA 標準](https://www.ecma-international.org/publications/standards/Ecma-048.htm) 和一系列的延伸模組為基礎，由許多廠商向數位設備公司和 Tektronix 終端機，再到更新式和常見的軟體終端，例如 [xterm](https://invisible-island.net/xterm/)。 虛擬終端機序列網域內有許多擴充功能，而且有些序列比其他序列更廣泛支援，但您可以放心地將其標準化為命令列體驗的命令語言，這是幾乎每個終端機和命令列用戶端應用程式都支援的知名子集。

## <a name="cross-platform-support"></a>跨平臺支援

跨平臺原生支援 **虛擬終端機序列** ，讓終端機應用程式和命令列公用程式輕鬆地在版本和作業系統的變化之間可移植，但 Windows 除外。

相較之下，windows **主控台 api** 只有在 windows 上才受到支援。 當您嘗試從某個平臺或另一個平臺移植命令列公用程式時，必須在 Windows 與虛擬終端機之間撰寫延伸的介面卡或轉譯程式庫，反之亦然。

### <a name="remote-access"></a>遠端存取

**虛擬終端機序列** 擁有遠端存取的主要優點。 在設定標準遠端命令列連線所需的設定下，不需要額外的工作來傳輸或執行遠端程序呼叫。 只要將輸出和輸入傳輸通道 (或單一雙向通道) 透過管道、通訊端、檔案、序列埠或任何其他裝置來連接，就足以將應用程式對遠端主機說出這些順序所需的所有資訊全部完整地攜帶起來。

相反地， **Windows 主控台 api** 只能在本機電腦上存取，而遠端這些 api 需要建立整個遠端呼叫和傳輸介面層，但只限于簡單的通道。

### <a name="separation-of-concerns"></a>關注點分離

某些 **Windows 主控台 api** 提供對輸入和輸出緩衝區的低層級存取，或互動式命令列的便利性函數。 這可能包括以程式設計方式在主控台子系統和主機環境內進行程式設計的別名和命令歷程記錄，而不是在命令列用戶端應用程式本身內。

相反地， **其他平臺** 則會將應用程式目前狀態的記憶體，和命令列公用程式或 shell 本身的責任提供給便利性功能。

在主控台主機和 API 中處理此責任的 **Windows 主控台** 可讓您更快速且更輕鬆地撰寫具有這些功能的命令列應用程式，而不需記住繪製狀態或處理編輯便利性功能的責任。 不過，這讓您幾乎無法在不同的平臺、版本或案例之間，從遠端連線這些活動，因為這種方式可讓您在執行和可用性方面有所變化。 這種處理責任的方式也能讓這些 Windows 命令列應用程式的最終互動式體驗完全相依于主控台主機的執行、優先順序和發行週期。

例如，只有在命令列應用程式自行處理編輯考慮時，才可以使用先進的行編輯功能，例如語法醒目提示和複雜的選取專案。 主控台從來沒有足夠的內容，可以完全瞭解這些案例，就像用戶端應用程式一樣。

相反地，其他平臺會使用 **虛擬終端機序列** ，透過可重複使用的用戶端程式庫（例如 [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 和 [ncurses](https://invisible-island.net/ncurses/ncurses.html)）來處理這些活動和虛擬終端機通訊本身。 最後的終端機會只負責顯示資訊，並透過該雙向通道接收輸入。

### <a name="wrong-way-verbs"></a>Wrong-Way 動詞

利用 **Windows 主控台** ，可以在輸入和輸出資料流程上，以相反的自然方向來執行某些動作。 這可讓 Windows 命令列應用程式避免管理自己的緩衝區。 它也可讓 Windows 命令列應用程式執行先進的作業，例如代表使用者模擬/插入輸入，或讀回部分寫入的歷程記錄。

雖然這可讓 Windows 應用程式在單一電腦上的特定使用者內容中運作，但是在某些情況下使用時，也會提供一種向量來跨安全性和許可權層級或網域。 這類案例包括在同一部電腦上的內容之間進行操作，或在不同的內容之間進行作業。

使用 **虛擬終端順序** 的其他平臺不允許此活動。 從傳統 Windows 主控台轉換至虛擬終端機序列的建議目的是要將此策略與互通性和安全性原因融合在一起。

### <a name="direct-window-access"></a>直接視窗存取

**Windows 主控台 API 介面** 可為裝載視窗提供精確的視窗控制碼。 這可讓命令列公用程式藉由達到視窗控制碼所允許的廣泛 Win32 Api 來執行 advanced window 作業。 這些 Win32 Api 可以操作視窗狀態、框架、圖示或視窗的其他屬性。

相反地，在具有 **虛擬終端順序** 的其他平臺上，會有一組較窄的命令可針對視窗執行。 這些命令可以執行一些動作，例如變更視窗大小或顯示的標題，但必須在相同的頻外完成，並在與資料流程其餘部分相同的控制項下執行。

隨著 Windows 發展，視窗控制碼的安全性控制和限制也已增加。 此外，在任何特定的使用者介面專案上，應用程式可定址的視窗控制碼的本質和存在都已演進，特別是隨著裝置外型規格和平臺的增加支援。 如此一來，當平臺和經驗演進時，直接視窗存取命令列應用程式就會變得脆弱。

### <a name="unicode"></a>Unicode

UTF-8 是幾乎所有新式平臺上的 Unicode 資料所接受的編碼方式，因為它會在可攜性、儲存體大小和處理時間之間取得適當的平衡。 不過，Windows 過去選擇 UTF-16 作為 Unicode 資料的主要編碼方式。 UTF-8 的支援會在 Windows 中增加，使用這些 Unicode 格式並不會妨礙其他編碼的使用。

**Windows 主控台** 平臺已受到支援，並將繼續支援所有現有的字碼頁和編碼。 使用 UTF-16 以取得跨 Windows 版本的最大相容性，並視需要使用 UTF-8 執行演算法轉譯。 主控台系統正在增加對 UTF-8 的支援。

主控台中的 UTF-16 支援可透過所有主控台 Api 的 _W_ 變體來利用，而不需要額外的設定，而且對於已精通在 utf-16 中的應用程式而言，是更有可能的選擇，因為它會與 `wchar_t` 其他 Microsoft 和 Windows 平臺功能和產品的和 _W_ 變體進行通訊。

您可以視情況將字碼頁設定為 _A_ `65001` 或 `CP_UTF8` [**SetConsoleOutputCP**](setconsoleoutputcp.md)和 [**SetConsoleCP**](setconsolecp.md)方法之後，在主控台控制碼上利用主控台 api 的 utf-8 支援。 只有當電腦尚未在主控台的 [區域] 區段中，針對非 Unicode 應用程式的設定選擇 [使用 Unicode UTF-8 來提供全球語言支援] 時，才需要預先設定字碼頁。

>[!NOTE]
> 目前，在標準輸出資料流程上，使用 [**WriteConsole**](writeconsole.md) 和 [**WRITEFILE**](https://msdn.microsoft.com/library/windows/desktop/aa365747) 方法的 utf-8 完全受到支援。 輸入資料流程的支援會因輸入模式而異，而且會隨著時間持續改善。 值得注意的是，輸入的預設「 **[處理後](high-level-console-modes.md)** 」模式並不完全支援 utf-8。 您可以在 GitHub 上的 [**microsoft/terminal # 7777**](https://github.com/microsoft/terminal/issues/7777) 找到此工作的目前狀態。 解決方法是使用演算法可翻譯的 UTF-16，透過 [**ReadConsoleW**](readconsole.md) 或 [**ReadConsoleInputW**](readconsoleinput.md) 讀取輸入，直到未解決的問題解決為止。

## <a name="recommendations"></a>建議

針對 Windows 上的所有新開發和持續進行中的開發， **建議將虛擬終端機序列** 作為與終端機互動的方式。 這會將 Windows 命令列用戶端應用程式與所有其他平臺上的應用程式設計樣式融合在一起。

### <a name="exceptions-for-using-windows-console-apis"></a>使用 Windows 主控台 Api 的例外狀況

建立初始環境 **仍需要有限的 Windows 主控台 api 子集** 。 Windows 平臺在處理、信號、裝置及編碼處理方面仍有不同之處：

- 進程的標準控制碼仍會使用 **[GetStdHandle](getstdhandle.md)** 和 **[SetStdHandle](setstdhandle.md)** 來控制。

- 在加入宣告虛擬終端機序列支援的控制碼上設定主控台模式時，將會使用 **[GetConsoleMode](getconsolemode.md)** 和 **[SetConsoleMode](setconsolemode.md)** 來處理。

- 程式字碼頁或 UTF-8 支援的宣告會使用 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 和 [**SetConsoleCP**](setconsolecp.md) 方法進行。

- [**AllocConsole**](allocconsole.md)、 [**AttachConsole**](attachconsole.md)和 [**FreeConsole**](freeconsole.md)可能需要某種程度的整體進程管理，才能加入或離開主控台裝置會話。

- 使用 [**SetConsoleCtrlHandler**](setconsolectrlhandler.md)、 [**HandlerRoutine**](handlerroutine.md)和 [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md)時，會繼續進行信號和信號處理。

- 您可以使用 [**WriteConsole**](writeconsole.md) 和 [**ReadConsole**](readconsole.md)來執行與主控台裝置控制碼的通訊。 您也可以透過程式設計語言執行時間，利用：-C 執行時間 (CRT) ： [資料流程 i/o](https://docs.microsoft.com/cpp/c-runtime-library/stream-i-o) （例如 **printf** 、 **scanf** 、 **putc** 、 **getc** 或 [其他層級的 i/o 函數](https://docs.microsoft.com/cpp/c-runtime-library/input-and-output)）來利用這些程式設計語言執行時間。
        -C + + 標準程式庫 (STL) ： [iostream](https://docs.microsoft.com/cpp/standard-library/iostream) ，例如 **cout** 和 **cin** 。
        -.NET 執行時間： Console 等 [系統主控台](https://docs.microsoft.com/dotnet/api/system.console) **。**

- 必須留意視窗大小變更的應用程式仍然需要使用 [**ReadConsoleInput**](readconsoleinput.md) 來接收它們交錯的金鑰事件，因為 **ReadConsole** 單獨會捨棄它們。

- 如果應用程式嘗試繪製資料行、格線或填滿顯示，則仍必須使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 來尋找視窗大小。 [Pseudoconsole](pseudoconsoles.md)會話中的視窗和緩衝區大小將會相符。

## <a name="future-planning-and-pseudoconsole"></a>未來規劃和 pseudoconsole

沒有計劃從平臺移除 Windows 主控台 Api。

相反地，Windows 主控台主機提供了 **[pseudoconsole](pseudoconsoles.md)** 技術，可將現有的 Windows 命令列應用程式呼叫轉譯為虛擬終端機序列，並將其從遠端或跨平臺轉送到另一個裝載環境。

這項轉譯並不完美。 它需要主控台主機視窗，以維護 Windows 對使用者顯示的模擬環境。 然後，它會將此模擬環境的複本投射至 **pseudoconsole** 主機。 所有 Windows 主控台 API 呼叫都是在模擬環境內運作，以滿足舊版命令列用戶端應用程式的需求。 只有效果會傳播到最終的主機上。

因此，命令列應用程式會 desiring 跨平臺的完整相容性，以及在 Windows 和其他地方完全支援所有新功能和案例，因此建議移至虛擬終端機序列，並調整命令列應用程式的架構，以配合所有平臺。

有關命令列應用程式之 Windows 轉換的詳細資訊，可以在我們的 [生態系統藍圖](ecosystem-roadmap.md)中找到。

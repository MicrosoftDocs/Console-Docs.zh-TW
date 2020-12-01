---
title: Windows 主控台和終端生態系統藍圖
description: 提供 Windows 主控台主機、主控台 Api、主控台子系統和終端機產品之間與方案之間互動的高階觀點。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台、終端機、虛擬終端機、主控台主機、命令列、子系統、藍圖、生態系統
ms.prod: console
ms.localizationpriority: high
ms.openlocfilehash: e5d28a06789f230943d70a49e7c89642b17fdb5c
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2020
ms.locfileid: "96420257"
---
# <a name="windows-console-and-terminal-ecosystem-roadmap"></a>Windows 主控台和終端生態系統藍圖

本檔是 Windows 主控台和 Windows 終端機產品的高階藍圖。 它涵蓋：


- Windows 主控台和 Windows 終端機如何融入 Windows 和其他作業系統上的命令列應用程式生態系統。

- 產品、功能和策略的歷程記錄和未來藍圖，這些都是建立平臺的一部分，也是針對此平臺建立。

Microsoft 目前的主控台/終端時代的重點，是要直接為 Windows 平臺上的開發人員提供頂級的終端機體驗，並[推出](classic-vs-vt.md)傳統的 Windows 主控台 api，使用[pseudoconsole](pseudoconsoles.md)取代[虛擬終端機序列](console-virtual-terminal-sequences.md)。 **[Windows 終端機](/terminal/get-started)** 將這項轉換展示為頂級體驗、邀請開發人員群體中的 [開放原始](https://github.com/microsoft/terminal) 碼共同作業、支援完整的用戶端命令列和終端機裝載應用程式混合和比對，以及將 Windows 生態系統與所有其他平臺整合。

## <a name="definitions"></a>定義

建議您先熟悉此空間中所使用之常見術語的 [定義](definitions.md) ，再繼續進行。 常見術語包括： [命令列 (或主控台) 應用程式](definitions.md#command-line-applications)、 [標準處理 `STDIN` (`STDOUT` 、 `STDERR`) ](definitions.md#standard-handles)、 [TTY 和 PTY 裝置](definitions.md#ttypty)、 [用戶端和伺服器](definitions.md#clients-and-servers)、 [主控台子系統](definitions.md#console-subsystem)、 [主控台主機](definitions.md#console-host)、 [pseudoconsole](definitions.md#pseudoconsole)和 [終端](definitions.md#terminal)機。

## <a name="architecture"></a>架構

系統的一般架構分為四個部分：用戶端、裝置、伺服器和終端機。

![從用戶端到裝置到終端機的命令列通訊流程圖來源至目的地](images/command-line-communication.png)

### <a name="client"></a>Client

用戶端是一種命令列應用程式，它會使用以文字為基礎的介面，讓使用者 (輸入命令，而不是以滑鼠為基礎的使用者介面) ，傳回結果的文字標記法。 在 Windows 上，主控台 API 會提供用戶端與裝置之間的通訊層。  (這也可以是具有裝置控制 Api) 的標準主控台控制碼。

### <a name="device"></a>裝置

裝置是兩個進程、用戶端和伺服器之間的中繼訊息處理通訊層。 在 Windows 中，這是主控台驅動程式。 在其他平臺上，它是 TTY 或 PTY 裝置。 如果整個交易是純文字或包含 [虛擬終端順序](console-virtual-terminal-sequences.md)，而不是 [Windows 主控台 api](console-functions.md)，則可以使用其他裝置（如檔案、管道和通訊端）作為通道。

### <a name="server"></a>伺服器

伺服器會從用戶端解釋要求的 API 呼叫或訊息。 在處於傳統操作模式的 Windows 上，伺服器也會建立使用者介面，以便將輸出呈現到畫面。 伺服器會另外收集輸入，以便透過驅動程式將回應訊息傳回至用戶端，例如在相同模組中配套的終端機。 使用 [pseudoconsole](pseudoconsoles.md) 模式時，它會改為將 [虛擬終端機序列](console-virtual-terminal-sequences.md) 中的這項資訊呈現至附加的終端機。

### <a name="terminal"></a>終端

終端機是最後一層，為使用者提供圖形化顯示和互動服務。 它負責捕獲輸入，並將其編碼為 [虛擬終端機序列](console-virtual-terminal-sequences.md)，最後會到達用戶端 `STDIN` 。 它也會接收和解碼從用戶端在螢幕上呈現的 *虛擬終端* 機序列 `STDOUT` 。

#### <a name="further-connections"></a>進一步連接

作為補充項，可以藉由將服務多個角色的應用程式連結到其中一個端點，來執行進一步的連接。 例如，SSH 會話有兩個角色：它是在一個裝置上執行的命令列應用程式的 **終端** 機，但它會將所有收到的資訊轉送到另一個裝置上的 **用戶端** 角色。 此連結可以無限期地跨裝置和內容進行，以提供廣泛的案例彈性。

在非 Windows 平臺上， **伺服器** 和 **終端** 機角色是單一單位，因為 API 集合與 [虛擬終端機序列](console-virtual-terminal-sequences.md)之間不需要轉譯相容性層。

## <a name="microsoft-products"></a>Microsoft 產品

所有 Microsoft Windows 命令列產品現在都可在 GitHub 的開放原始碼存放庫（ [microsoft/terminal](https://github.com/microsoft/terminal)）中使用。

### <a name="windows-console-host"></a>Windows 主控台主機

這是命令列應用程式的傳統 Windows 使用者介面。 它會處理從任何附加的命令列應用程式呼叫的所有主控台 API 服務。 Windows 主控台也會代表這些應用程式，處理 (GUI) 標記法的圖形化使用者介面。 它會在系統目錄中找到 `conhost.exe` ，或 `openconsole.exe` 在其開放原始碼表單中找到。 它隨附于 Windows 作業系統。 您也可以在從開放原始碼存放庫中建立的其他 Microsoft 產品中找到此資訊，以取得最新的 [pseudoconsole](pseudoconsoles.md) 基礎結構執行。 根據上述定義，它會以傳統的伺服器和終端機角色，或透過慣用 _pseudoconsole_ 基礎結構的僅限伺服器角色運作。

### <a name="windows-terminal"></a>Windows 終端機

這是命令列應用程式的新 Windows 介面。 Windows 終端機可作為使用 [pseudoconsole](pseudoconsoles.md) 來分隔 API 服務與以文字為基礎之應用程式介面間的疑慮的第一方範例，與所有非 Windows 平臺很類似。


Windows 終端機是適用于 Windows 的旗艦文字模式使用者介面。 它會示範生態系統的功能，並促使 Windows 開發與其他平臺統一。 Windows 終端機也是如何建立強大且複雜的現代化應用程式，以跨越 Windows Api 和架構的歷程記錄和範圍的範例。 根據上述定義，此產品會以終端機角色運作。

## <a name="major-historical-milestones"></a>主要歷程記錄里程碑

主控台子系統的主要歷程記錄里程碑會在2014之前分成「執行」，然後在 Windows 10 的時代形成命令列的更新焦點時，移至自2014之後所執行的工作總覽。

### <a name="initial-implementation"></a>初始執行

**\[ 1989 年-1990 年代）** 初始的主控台主機系統已實作為 WINDOWS 作業系統內 DOS 環境的模擬。 其程式碼與 [命令提示](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd)字元纏結併合作， `cmd.exe` 這是該 DOS 環境的標記法。 主控台主機系統程式碼會透過命令提示字元解譯器/shell 來共用責任和許可權。 它也提供其他命令列公用程式的基底層級服務，以類似 CMD 的方式來執行服務。

### <a name="dbcs-for-cjk"></a>適用于 CJK 的 DBCS

**\[ 1997-1999 \]** 到目前為止，已引進 [DBCS](https://docs.microsoft.com/windows/win32/intl/double-byte-character-sets)支援 ( 「雙位元組字元集」 ) ，以支援 CJK (中文、日文和韓文) 市場。 這項工作會在主控台內提供許多撰寫和讀取方法的分叉，以提供「西方」版本來處理單一位元組字元以及「東部」版本的替代標記法，其中需要兩個位元組才能代表龐大的字元陣列。 此分叉包括將主控台環境中的儲存格展開表示為1或2個儲存格，其中1個儲存格的範圍 (高度高於寬度) ，而2個儲存格為寬、全形，或為一般中文、日文和韓文表意文字可以加入的正方形。

### <a name="securityisolation"></a>安全性/隔離

**\[ 2005-2009 \]** 在關鍵系統程式內執行的主控台子系統體驗，將各種 `csrss.exe` 不同存取層級的各種用戶端應用程式連接到單一超級關鍵和特殊許可權的程式，特別危險。 在這個時代，主控台子系統已分割成用戶端、驅動程式和伺服器應用程式。 每個應用程式都可以在自己的內容中執行，以降低每個應用程式的職責和許可權。 這項隔離會提高系統的一般健全狀況，因為主控台子系統中的任何失敗都會不再影響其他重要的進程功能。

### <a name="user-experience-improvements"></a>使用者經驗改進

**\[ 2014-2016 \]** 經過很長一段時間，通常是由組織中的各種小組集中維護主控台子系統，以開發人員為焦點的團隊，並在主控台中提供改進功能。 這段期間的改進包括：直線選取、平滑視窗調整大小、reflowing 文字、複製和貼上、高 DPI 支援，以及專注于 Unicode，包括在 "西歐" 和 "東部" 儲存體與資料流程操作演算法之間進行分割的聚合。

### <a name="virtual-terminal-client"></a>虛擬終端用戶端

**\[ 2015-2017 \]** 在 [Windows 子系統 Linux 版](https://docs.microsoft.com/windows/wsl/)抵達的情況下，Microsoft 致力於改善 [Windows 上的 Docker](https://docs.microsoft.com/dotnet/architecture/microservices/container-docker-introduction/docker-defined)體驗，並採用 [OpenSSH](https://docs.microsoft.com/windows-server/administration/openssh/openssh_overview)作為頂級命令列遠端執行技術，將 [虛擬終端機序列](console-virtual-terminal-sequences.md)的初始執行導入到主控台主機中。 這可讓現有的主控台作為終端機，直接附加到其各自環境中的那些 Linux 原生應用程式，將圖形和文字屬性轉譯為顯示，並以適當的方言傳回使用者輸入。

### <a name="virtual-terminal-server"></a>虛擬終端機伺服器

**\[ 2018 \]** 過去二十年來，收件匣主控台主機的協力廠商替代方案是為了提供額外的開發人員生產力，並在豐富的自訂和索引標籤式介面中強調。 這些應用程式仍然需要執行和隱藏主控台主機視窗。 它們會附加為次要「用戶端」應用程式，以在主要命令列用戶端應用程式運作時，抓取輪詢迴圈中的緩衝區資訊。 他們的目標是做為終端機，就像是在其他平臺上，但在沒有可更換終端機的 Windows 環境中。

在這段時間內，已引進 [pseudoconsole](pseudoconsoles.md) 基礎結構。 Pseudoconsole 允許任何應用程式在非互動模式中啟動主控台主機，並成為使用者的最終終端介面。 這項工作的主要限制是 Windows 的持續相容性承諾，可針對不確定的未來服務所有已發佈的 [Windows 主控台 api](console-functions.md) ，同時提供取代的伺服器裝載介面，以符合所有其他平臺上的預期： [虛擬終端機序列](console-virtual-terminal-sequences.md)。 如此一來，這項工作會執行用戶端階段的鏡像映射： _pseudoconsole_ 專案會在螢幕上顯示的內容，做為委派主機的 _虛擬終端機順序_ ，並將回復轉譯為用戶端應用程式取用的 Windows 格式輸入序列。

## <a name="roadmap-for-the-future"></a>未來的藍圖

### <a name="terminal-applications"></a>終端機應用程式

**\[ 2019-現在 \]** 這是主控台子系統的開放原始碼時代，著重于新的 Windows 終端機。 在5月2019的 Microsoft Build 會議期間宣佈，Windows 終端機完全在 [microsoft/Terminal](https://github.com/microsoft/terminal)的 GitHub 上。 在 [pseudoconsole](pseudoconsoles.md) 的精簡平臺上建立 Windows 終端機應用程式將會是此時代的重點，直接在 Windows 平臺上為開發人員帶來頂級的終端機體驗。

**[Windows 終端機](/terminal/get-started)** 不只是展示平臺，包括 [WinUI](/apps/winui/) 介面技術、 [MSIX](/msix/) 封裝模型，以及 [c + +/WinRT](/uwp/cpp-and-winrt-apis/) 元件架構，也能作為平臺本身的驗證。 Windows 終端機正在推動 Windows 組織在必要時開啟及發展應用程式平臺，以繼續提升開發人員的生產力。 Windows 終端機一組獨特的 power 使用者和開發人員需求，可推動這些市場真正需要的 Windows 平臺需求。

在 Windows 作業系統中，這包括從預設位置 [淘汰傳統主控台主機使用者介面](./classic-vs-vt.md) ，以促進 [Windows 終端機](/terminal/get-started)、 [ConPTY](https://devblogs.microsoft.com/commandline/windows-command-line-introducing-the-windows-pseudo-console-conpty/)和 [虛擬終端機序列](console-virtual-terminal-sequences.md)。

最後，這個時代打算提供預設體驗的完整選擇，無論是 Windows 終端機產品或任何替代終端。

### <a name="client-support-library"></a>用戶端支援程式庫

**\[ 未來 \]** 在用戶端提供 [虛擬終端機序列](console-virtual-terminal-sequences.md)的支援和檔，強烈建議 windows 命令列公用程式開發人員先透過傳統 Windows api 使用虛擬終端機序列，以獲得整合生態系統與所有平臺的優點。 不過，有一個重要的部分是，其他平臺有各式各樣的用戶端協助程式程式庫，可處理像是 [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 和圖形顯示的輸入，例如 [ncurses](https://invisible-island.net/ncurses/ncurses.html)。 這個特定的未來藍圖元素表示探索生態系統所提供的內容，以及如何透過傳統主控台 API，加速在 Windows 命令列應用程式中採用虛擬終端機序列。

### <a name="sequence-passthrough"></a>序列傳遞

**\[ 未來 \]** 虛擬終端用戶端和伺服器的執行組合，可讓用戶端命令列和終端機裝載應用程式完全混合和比對。 這種組合可以說傳統的 [Windows 主控台 api](console-functions.md) 或 [虛擬終端機序列](console-virtual-terminal-sequences.md)，但是將這項功能轉譯為傳統相容的 windows 方法，然後再回到更通用的虛擬終端機方法，會產生額外的成本。

一旦市場充分採用 _虛擬終端機序列_ 和 Windows 上的 utf-8，就可以選擇性地停用主控台主機的轉換/解讀作業。 然後，主控台主機會變成簡單的 API 呼叫服務程式，並透過 [pseudoconsole](pseudoconsoles.md)從裝置呼叫轉送至主機應用程式。 這項變更將可提升效能，並最大化可在用戶端應用程式與終端機之間說出的序列方言。 透過這項變更，將會啟用更多的互動性案例，並 *(最後)* 讓 Windows 世界與命令列應用程式空間中所有其他平臺的系列保持一致。

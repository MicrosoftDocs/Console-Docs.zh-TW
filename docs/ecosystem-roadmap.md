---
title: Windows 主控台和終端生態系統藍圖
description: 提供 Windows 主控台主機、主控台 API、主控台子系統和終端機產品之間互動和計畫的整體觀點。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 終端機, 虛擬終端機, 主控台主機, 命令列, 子系統, 藍圖, 生態系統
ms.prod: console
ms.localizationpriority: high
ms.openlocfilehash: e5d28a06789f230943d70a49e7c89642b17fdb5c
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96420257"
---
# <a name="windows-console-and-terminal-ecosystem-roadmap"></a>Windows 主控台和終端生態系統藍圖

本文件是 Windows 主控台和 Windows 終端機產品的整體藍圖。 內容包括：


- Windows 主控台和 Windows 終端機如何適應 Windows 和其他作業系統上的命令列應用程式生態系統。

- 產品、功能和策略的歷程記錄和未來藍圖，都是建置平台的一部分，也是專為此平台打造的。

Microsoft 目前的主控台/終端機時代重點是，在 Windows 平台上直接為開發人員帶來一流的終端機體驗，以及[淘汰](classic-vs-vt.md)傳統 Windows 主控台 API，並以利用 [pseudoconsole](pseudoconsoles.md)的[虛擬終端機序列](console-virtual-terminal-sequences.md)進行取代。 **[Windows 終端機](/terminal/get-started)** 會展示轉換為一流體驗、從開發人員社群邀請[開放原始碼共同作業](https://github.com/microsoft/terminal)、支援用戶端命令列和終端機主控應用程式的完整混合和比對，以及整合 Windows 生態系統與所有其他平台。

## <a name="definitions"></a>定義

在繼續之前，建議您先熟悉此空間中常用術語的[定義](definitions.md)。 常見術語包括：[命令列 (或主控台) 應用程式](definitions.md#command-line-applications)、[標準控點 (`STDIN`、`STDOUT`、`STDERR`)](definitions.md#standard-handles)、[TTY 和 PTY 裝置](definitions.md#ttypty)、[用戶端和伺服器](definitions.md#clients-and-servers)、[主控台子系統](definitions.md#console-subsystem)、[主控台主機](definitions.md#console-host)、[pseudoconsole](definitions.md#pseudoconsole) 和[終端機](definitions.md#terminal)。

## <a name="architecture"></a>架構

系統的一般架構分為四個部分：用戶端、裝置、伺服器和終端機。

![命令列通訊流程圖：來源至目的地 (執行自用戶端到裝置到伺服器到終端機)](images/command-line-communication.png)

### <a name="client"></a>用戶端

用戶端是一種使用文字型介面的命令列應用程式，可讓使用者輸入命令 (而不是滑鼠型使用者介面)，並傳回結果的文字呈現。 在 Windows 上，主控台 API 會在用戶端與裝置之間提供通訊層。 (這也可以是使用裝置控制 API 的標準主控台控點)。

### <a name="device"></a>裝置

裝置是介於兩個程序 (用戶端與伺服器) 之間的中繼訊息處理通訊層。 在 Windows 上，這是主控台驅動程式。 在其他平台上，則是 TTY 或 PTY 裝置。 如果整個交易為純文字或包含[虛擬終端機序列](console-virtual-terminal-sequences.md)，而不是使用 [Windows 主控台 API](console-functions.md)，則檔案、管道和通訊端之類的其他裝置可作為此通訊通道。

### <a name="server"></a>伺服器

伺服器會從用戶端解讀要求的 API 呼叫或訊息。 在傳統作業模式的 Windows 上，伺服器也會建立使用者介面，以將輸出呈現至螢幕。 伺服器會另外收集輸入，以透過驅動程式 (例如在相同模組中搭售的終端機) 將回應訊息傳回給用戶端。 使用 [pseudoconsole](pseudoconsoles.md) 模式，其只是用來向連結的終端機呈現[虛擬終端機序列](console-virtual-terminal-sequences.md)中此資訊的翻譯工具。

### <a name="terminal"></a>終端

終端機是為使用者提供圖形化顯示和互動服務的最後一層。 其負責擷取輸入並將其編碼為[虛擬終端機序列](console-virtual-terminal-sequences.md)，這最終會到達用戶端的 `STDIN`。 此外，也會接收和解碼其從用戶端的 `STDOUT` 接收回來的虛擬終端機序列，以在螢幕上呈現。

#### <a name="further-connections"></a>進一步連線

追加功能：將扮演多個角色的應用程式鏈結到其中一個端點，即可執行進一步連線。 例如，SSH 工作階段有兩個角色：這是在某個裝置上執行之命令列應用程式的 **終端機**，但是會將所有收到的資訊轉送給另一個裝置上的 **用戶端** 角色。 此鏈結可以會在不同裝置和內容之間無限期地發生，以提供廣泛的案例彈性。

在非 Windows 平台上，**伺服器** 和 **終端機** 角色都是單一單位，因為 API 集與[虛擬終端機序列](console-virtual-terminal-sequences.md)之間不需要轉譯相容性層。

## <a name="microsoft-products"></a>Microsoft 產品

您現在可以在 GitHub 上的開放原始碼存放庫 ([microsoft/terminal](https://github.com/microsoft/terminal)) 中找到所有 Microsoft Windows 命令列產品。

### <a name="windows-console-host"></a>Windows 主控台主機

這是命令列應用程式的傳統 Windows 使用者介面。 可處理從任何已連結命令列應用程式呼叫的所有主控台 API 服務。 Windows 主控台也會代表所有應用程式來處理圖形化使用者介面 (GUI) 呈現。 在系統目錄中可找到 `conhost.exe`，或在其開放原始碼表單中找到的 `openconsole.exe`。 其隨附於 Windows 作業系統。 在從開放原始碼存放庫建置的其他 Microsoft 產品中也可以找到，以供取得 [pseudoconsole](pseudoconsoles.md) 基礎結構的最新實作。 根據上述定義，其會透過慣用的 pseudoconsole 基礎結構，以傳統上兼具伺服器和終端機的角色或僅限伺服器的角色運作。

### <a name="windows-terminal"></a>Windows 終端機

這是命令列應用程式的新 Windows 介面。 Windows 終端機可作為以下情況的第一方範例：使用 [pseudoconsole](pseudoconsoles.md) 來區分 API 服務與文字型應用程式介面之間的顧慮，非常類似所有非 Windows 平台。


Windows 終端機是適用於 Windows 的旗艦型文字模式使用者介面。 其會示範生態系統的功能，並將 Windows 開發推向與其他平台整合。 Windows 終端機也是如何建置功能強大且複雜新式應用程式的範例，此種應用程式橫越 Windows API 和架構的歷史和全程。 根據上述定義，此產品會以終端機角色運作。

## <a name="major-historical-milestones"></a>過去主要的里程碑

主控台子系統過去主要的里程碑細分為 2014 年前實作，然後移到自 2014 年起的工作概觀，而當時命令列上更新的焦點是在 Windows 10 年代中形成。

### <a name="initial-implementation"></a>初始實作

**\[1989-1990 年代]** 初始主控台主機系統已實作為 Windows 作業系統中 DOS 環境的模擬。 其程式碼會與[命令提示字元](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd)(`cmd.exe`) 糾結在一起並協同合作，這是該 DOS 環境的表示法。 主控台主機系統程式碼會與命令提示字元解譯器/shell 一起分擔責任和權限。 其也會提供服務的基底層級，讓其他命令列公用程式以類似 CMD 的方式執行服務。

### <a name="dbcs-for-cjk"></a>適用於 CJK 的 DBCS

**\[1997-1999\]** 這段時間，引進了 [DBCS](https://docs.microsoft.com/windows/win32/intl/double-byte-character-sets) 支援 (「雙位元組字元集」) 來支援 CJK (中文、日文和韓文) 市場。 此種努力導致在主控台內許多寫入和讀取方法的分歧，以提供「西方」版本來處理單一位元組字元，以及「東方」版本的替代表示法，其中需要兩個位元組來代表龐大的字元陣列。 此分歧包括將主控台環境中儲存格的呈現展開為 1 或 2 個儲存格，其中 1 個儲存格是窄的 (高度大於寬度)，2 個儲存格則是寬的、全形，或者是可在其銘寫典型中文、日文和韓文表意文字的方形。

### <a name="securityisolation"></a>安全性/隔離

**\[2005-2009\]** 透過在關鍵系統程序 (`csrss.exe`) 內執行的主控台子系統體驗，將各種不同存取層級的各式用戶端應用程式連線到單一超級關鍵和具特殊權限的程序，特別危險。 在此年代中，主控台子系統已分割成用戶端、驅動程式和伺服器應用程式。 每個應用程式都可以在自己的內容中執行，進而降低各自的責任和權限。 此種隔離提升了系統的一般穩固性，因為主控台子系統中的任何失敗不會再影響其他關鍵程序功能。

### <a name="user-experience-improvements"></a>使用者經驗改進

**\[2014-2016\]** 經過一段很長的時間，由組織內各種小組分散維護主控台子系統之後，以開發人員為主的新小組形成了，負責推動主控台的改進。 這段期間的改進包括：行選取、平滑視窗大小調整、自動重排文字、複製和貼上、高 DPI 支援，以及著重於 Unicode，包括「西方」與「東方」儲存體和資料流操作演算法分裂的匯聚。

### <a name="virtual-terminal-client"></a>虛擬終端機用戶端

**\[2015-2017\]** 隨著 [Windows 子系統 Linux 版](https://docs.microsoft.com/windows/wsl/)的到來，Microsoft 致力於改善 [Windows 上的 Docker](https://docs.microsoft.com/dotnet/architecture/microservices/container-docker-introduction/docker-defined) 體驗，並採用 [OpenSSH](https://docs.microsoft.com/windows-server/administration/openssh/openssh_overview) 作為首要命令列遠端執行技術，而主控台主機引進了[虛擬終端機序列](console-virtual-terminal-sequences.md)的初始實作。 這可讓現有主控台充當終端機，直接連結到其各自環境中的 Linux 原生應用程式，將圖形化和文字屬性轉譯至顯示器，並以適當的方言傳回使用者輸入。

### <a name="virtual-terminal-server"></a>虛擬終端機伺服器

**\[2018\]** 過去二十年來，建立了收件匣主控台主機的第三方替代方案，以提供額外的開發人員生產力，其醒目地置於豐富的自訂項目和索引標籤式介面的中間。 這些應用程式仍然需要執行和隱藏主控台主機視窗。 其會連結為次要的「用戶端」應用程式，以在主要命令列用戶端應用程式運作時，消除輪詢迴圈中的緩衝區資訊。 其目標是要成為終端機，如同在其他平台上，但是在 Windows 世界中，終端機不是可更換的。

在這段時間內，引進了 [pseudoconsole](pseudoconsoles.md) 基礎結構。 Pseudoconsole 允許任何應用程式以非互動式模式啟動主控台主機，並成為使用者的最終終端機介面。 此種作法的主要限制是 Windows 未來為所有已發佈的 [Windows 主控台 API](console-functions.md) 提供無限期服務的持續相容性承諾，同時提供符合所有其他平台上期望的替代伺服器主控介面：[虛擬終端機序列](console-virtual-terminal-sequences.md)。 因此，此種作法執行了用戶端階段的鏡映影像：pseudoconsole 會將畫面上會顯示的內容投射為委派主機的「虛擬終端機序列」，並將回覆轉譯為用戶端應用程式使用量的 Windows 格式輸入序列。

## <a name="roadmap-for-the-future"></a>未來的藍圖

### <a name="terminal-applications"></a>終端機應用程式

**\[2019-現在\]** 這是主控台子系統的開放原始碼時代，著重於新的 Windows 終端機。 2019 年 5 月的 Microsoft Build 會議期間宣佈，Windows 終端機完全放在 GitHub 的 [Microsoft/Terminal](https://github.com/microsoft/terminal) 上。 在 [pseudoconsole](pseudoconsoles.md) 的精簡平台上建置 Windows 終端機應用程式，將成為這個時代的焦點，並在 Windows 平台上直接為開發人員帶來一流的終端機體驗。

**[Windows 終端機](/terminal/get-started)** 不僅要展示平台 (包括 [WinUI](/apps/winui/) 介面技術、[MSIX](/msix/) 封裝模型，以及 [C++/WinRT](/uwp/cpp-and-winrt-apis/) 元件架構)，還要成為平台本身的驗證。 Windows 終端機會促使 Windows 組織開啟應用程式平台並視需要改進，以繼續提升開發人員的生產力。 Windows 終端機獨特的進階使用者和開發人員需求推動了現代化 Windows 平台需求，以滿足這些市場對於 Windows 的真正需求。

在 Windows 作業系統中，這包括從預設位置中[淘汰傳統主控台主機使用者介面](./classic-vs-vt.md)，改為支持 [Windows 終端機](/terminal/get-started)、[ConPTY](https://devblogs.microsoft.com/commandline/windows-command-line-introducing-the-windows-pseudo-console-conpty/)和[虛擬終端機序列](console-virtual-terminal-sequences.md)。

最後，不管是 Windows 終端機產品還是任何替代終端機，這個時代都想要提供完全自選的預設體驗。

### <a name="client-support-library"></a>用戶端支援程式庫

**\[未來\]** 有了用戶端的[虛擬終端機序列](console-virtual-terminal-sequences.md)支援和文件，強烈鼓勵 Windows 命令列公用程式開發人員先透過傳統 Windows API 使用虛擬終端機序列，以獲得整合生態系統與所有平台的優點。 不過，遺漏了一個重要的部分，那就是其他平台都有一系列廣泛的用戶端協助程式程式庫，可供處理 [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) 之類的輸入和 [ncurses](https://invisible-island.net/ncurses/ncurses.html) 之類的圖形化顯示。 這個特定的未來藍圖元素代表探索生態系統所提供的內容，以及如何透過傳統主控台 API，加速在 Windows 命令列應用程式中採用虛擬終端機序列。

### <a name="sequence-passthrough"></a>序列傳遞

**\[未來\]** 虛擬終端機用戶端與伺服器實作的組合，可讓用戶端命令列和終端機主控應用程式完全混搭。 此種組合對傳統 [Windows 主控台 API](console-functions.md) 或[虛擬終端機序列](console-virtual-terminal-sequences.md)都有吸引力，不過，將此轉譯成傳統相容的 Windows 方法，然後再回到更通用的虛擬終端機方法，會產生額外負荷成本。

一旦市場充分採用 Windows 上的虛擬終端機序列和 UTF-8，就可以選擇性地停用主控台主機的轉換/轉譯作業。 主控台主機接著會變成簡單的 API 呼叫服務工具，並透過 [pseudoconsole](pseudoconsoles.md) 從裝置呼叫轉送至主控應用程式。 這項變更將會提升效能，並充分發揮可在用戶端應用程式與終端機之間傳達的序列方言。 透過這項變更會達成其他互動性案例，而 (最終) 讓 Windows 世界與命令列應用程式空間中的所有其他平台系列保持一致。

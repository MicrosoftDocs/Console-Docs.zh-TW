---
title: 舊版主控台模式– Windows 桌面
description: 舊版主控台模式是一種相容性工具，可協助執行可能無法與 Windows 10 主控台主機搭配運作的命令列應用程式
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api, 相容性
ms.openlocfilehash: eeddfd00ffa8c3ad9d99583b89e4b3be7959f445
ms.sourcegitcommit: 508e93bc83b4bca6ce678f88ab081d66b95d605c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "93037706"
---
# <a name="legacy-console-mode"></a>舊版主控台模式

舊版主控台模式是一種相容性工具，其設計訴求是要協助 Windows 10 上的舊版命令列工具使用者。 對於在預設 Windows 10 主控台體驗中未顯示或正常運作的任何命令列工具，此模式提供了粗略的解決方案，讓系統逐步退回舊版的主控台主控體驗。

## <a name="using-legacy-console-mode"></a>使用舊版主控台模式

若要使用舊版主控台模式，請先開啟任何主控台主控視窗。 啟動其中一個命令解譯器 [CMD](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd) 或 [PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell)，通常可完成此動作。

以滑鼠右鍵按一下應用程式標題列，然後選擇 `Properties` 功能表選項。 選擇第一個索引標籤 `Options`。 然後勾選頁面底部描述 `Use legacy console` 的方塊。 按下 `OK` 按鈕加以套用。

返回相同的屬性工作表功能表並取消選取該方塊，然後按下 `OK`，即可還原此設定。

> [!NOTE]
>此設定會全面套用至所有在喜好設定變更後啟動的工作階段。 已開啟的工作階段將不會變更。

## <a name="differences-between-modes"></a>模式間的差異

主控台主機小組致力於縮小主控台的舊版和目前模式之間的差異，以確保盡可能有較多客戶可執行最新版本。 如果您遇到的問題需要您使用此處未記載的舊版主控台，請在 [microsoft/terminal](https://github.com/microsoft/terminal/) GitHub 存放庫上或透過[意見反應中樞](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app)連絡小組，以取得協助。

### <a name="16-bit-applications-on-32-bit-windows"></a>32 位元 Windows 上的 16 位元應用程式

32 位元 Windows 上的某些 16 位元應用程式會使用稱為 [NTVDM](https://docs.microsoft.com/windows/compatibility/ntvdm-and-16-bit-app-support) 的虛擬機器技術進行操作。 這些應用程式通常會使用圖形化螢幕緩衝模式搭配主控台主控環境進行操作。 只有舊版主控台體驗支援這些圖形化緩衝模式，以及啟動這些應用程式所需的其他主控台 API 支援。 當其中一個這類應用程式啟動時，系統會自動選取舊版主控台環境。

### <a name="ime-embedding"></a>IME 內嵌

舊版主控台主機會藉由在畫面底部保留一行作為建議，將 IME 的建議部分內嵌在主控視窗中。 目前的主控台主機環境會改為將此活動委派給 IME 子系統，以在主控台主機上方顯示包含建議的重疊視窗。 在不可能重疊視窗的環境中 (例如特定遠端工具)，可能需要舊版的主控台主機。

### <a name="api-differences"></a>API 差異

舊版和目前版本之間的主要已知差異在於 UTF-8 的實作。 舊版主機具有極為基本且通常不正確的 UTF-8 支援 ([字碼頁 65001](https://docs.microsoft.com/windows/win32/intl/code-pages))。 目前的主控台主機包含 Windows 10 的各版累加式改良，可改善這項支援。 嘗試依賴從舊版主控台預測 UTF-8「已知不正確」解譯的應用程式，將發現自己會在改善支援時收到不同的答案。

透過 API 經歷的其他差異應該回報至 [microsoft/terminal GitHub 存放庫](https://github.com/microsoft/terminal/)或透過[意見反應中樞](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app)回報，以進行分級和可能的補救。

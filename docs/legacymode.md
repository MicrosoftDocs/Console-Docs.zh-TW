---
title: 舊版主控台模式-Windows 桌面
description: 舊版主控台模式是一種相容性工具，可協助您執行可能無法搭配 Windows 10 主控台主機運作的命令列應用程式。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api，相容性
ms.openlocfilehash: eeddfd00ffa8c3ad9d99583b89e4b3be7959f445
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037706"
---
# <a name="legacy-console-mode"></a>舊版主控台模式

舊版主控台模式是一種相容性工具，其設計目的是要協助 Windows 10 上舊版命令列工具的使用者。 針對未在預設 Windows 10 主控台體驗中顯示或正常運作的任何命令列工具，此模式提供了粗略的解決方案，可將系統逐步執行至舊版主控台裝載體驗。

## <a name="using-legacy-console-mode"></a>使用舊版主控台模式

若要使用舊版主控台模式，請先開啟任何主控台裝載視窗。 這通常是藉由啟動其中一個命令直譯器 [CMD](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd) 或 [PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell)來完成。

在應用程式標題列上按一下滑鼠右鍵，然後選擇 `Properties` 功能表選項。 選擇 [第一個] 索引標籤 `Options` 。 然後，勾選描述的頁面底部的方塊 `Use legacy console` 。 按下 `OK` 按鈕以套用。

您可以返回相同的屬性工作表功能表，並取消核取該方塊，然後按下，來還原此設定 `OK` 。

> [!NOTE]
>這項設定會全域套用至在變更喜好設定之後啟動的所有會話。 已開啟的會話將不會變更。

## <a name="differences-between-modes"></a>模式之間的差異

主控台主機小組致力於將舊版和目前的主控台模式之間的差異降至最低，以確保盡可能有許多客戶可以執行最新版本。 如果您遇到要求您使用此處未記載之舊版主控台的問題，請洽詢 [microsoft/終端](https://github.com/microsoft/terminal/) 機 GitHub 存放庫上的小組，或透過 [意見反應中樞](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) 取得協助。

### <a name="16-bit-applications-on-32-bit-windows"></a>32位 Windows 上的16位應用程式

32位 Windows 上的一些16位應用程式會使用虛擬機器技術來操作，稱為 [NTVDM](https://docs.microsoft.com/windows/compatibility/ntvdm-and-16-bit-app-support)。 這些應用程式通常會使用圖形化螢幕緩衝模式搭配主控台裝載環境來操作。 只有舊版主控台體驗支援這些圖形緩衝模式，以及支援這些應用程式所需的其他主控台 API 支援。 當其中一個應用程式啟動時，系統會自動選取舊版主控台環境。

### <a name="ime-embedding"></a>輸入法嵌入

舊版主控台主機會在螢幕底部保留一行，以將輸入法的建議部分內嵌在主控視窗內，以取得建議。 目前的主控台主機環境會改為將此活動委派給 IME 子系統，以在主控台主機上方顯示有建議的重迭視窗。 在無法覆迭視窗的環境中 (像是) 某些遠端處理工具一樣，可能需要舊版主控台主機。

### <a name="api-differences"></a>API 差異

Legacy 和 current 之間的主要已知差異在於 UTF-8 的執行。 舊版主機在使用 [字碼頁 65001](https://docs.microsoft.com/windows/win32/intl/code-pages)時，對 utf-8 的支援非常基本且通常不正確。 目前的主控台主機包含 Windows 10 的累加式改良版，以改善這項支援。 嘗試依賴從舊版主控台預測 UTF-8 的「已知不正確」解讀的應用程式，將會在支援改善時，發現自己收到不同的答案。

您應該向 [microsoft/終端機 GitHub 存放庫](https://github.com/microsoft/terminal/) 或透過 [意見反應中樞](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) 回報 api 的其他差異，以進行分級和可能的補救。

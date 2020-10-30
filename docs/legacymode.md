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
# <a name="legacy-console-mode"></a><span data-ttu-id="0d5d2-104">舊版主控台模式</span><span class="sxs-lookup"><span data-stu-id="0d5d2-104">Legacy Console mode</span></span>

<span data-ttu-id="0d5d2-105">舊版主控台模式是一種相容性工具，其設計目的是要協助 Windows 10 上舊版命令列工具的使用者。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-105">Legacy Console mode is a compatibility tool designed to help users of older command-line tools on Windows 10.</span></span> <span data-ttu-id="0d5d2-106">針對未在預設 Windows 10 主控台體驗中顯示或正常運作的任何命令列工具，此模式提供了粗略的解決方案，可將系統逐步執行至舊版主控台裝載體驗。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-106">For any command-line tool that is not displaying or operating correctly in the default Windows 10 console experience, this mode provides a coarse-grained solution to stepping the system back to an older version of the console hosting experience.</span></span>

## <a name="using-legacy-console-mode"></a><span data-ttu-id="0d5d2-107">使用舊版主控台模式</span><span class="sxs-lookup"><span data-stu-id="0d5d2-107">Using Legacy Console Mode</span></span>

<span data-ttu-id="0d5d2-108">若要使用舊版主控台模式，請先開啟任何主控台裝載視窗。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-108">To use Legacy Console mode, first open any console hosting window.</span></span> <span data-ttu-id="0d5d2-109">這通常是藉由啟動其中一個命令直譯器 [CMD](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd) 或 [PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell)來完成。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-109">This is typically done by launching one of the command interpreters [CMD](https://docs.microsoft.com/windows-server/administration/windows-commands/cmd) or [PowerShell](https://docs.microsoft.com/powershell/scripting/install/installing-windows-powershell).</span></span>

<span data-ttu-id="0d5d2-110">在應用程式標題列上按一下滑鼠右鍵，然後選擇 `Properties` 功能表選項。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-110">Right-click on the application title bar and choose the `Properties` menu option.</span></span> <span data-ttu-id="0d5d2-111">選擇 [第一個] 索引標籤 `Options` 。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-111">Choose the first tab, `Options`.</span></span> <span data-ttu-id="0d5d2-112">然後，勾選描述的頁面底部的方塊 `Use legacy console` 。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-112">Then check the box at the bottom of the page describing `Use legacy console`.</span></span> <span data-ttu-id="0d5d2-113">按下 `OK` 按鈕以套用。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-113">Press the `OK` button to apply.</span></span>

<span data-ttu-id="0d5d2-114">您可以返回相同的屬性工作表功能表，並取消核取該方塊，然後按下，來還原此設定 `OK` 。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-114">The setting can be reverted by returning to the same property sheet menu and unchecking the box then pressing `OK`.</span></span>

> [!NOTE]
><span data-ttu-id="0d5d2-115">這項設定會全域套用至在變更喜好設定之後啟動的所有會話。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-115">This setting is globally applied to all sessions that start after the preference is changed.</span></span> <span data-ttu-id="0d5d2-116">已開啟的會話將不會變更。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-116">Sessions that are already open will not be changed.</span></span>

## <a name="differences-between-modes"></a><span data-ttu-id="0d5d2-117">模式之間的差異</span><span class="sxs-lookup"><span data-stu-id="0d5d2-117">Differences between modes</span></span>

<span data-ttu-id="0d5d2-118">主控台主機小組致力於將舊版和目前的主控台模式之間的差異降至最低，以確保盡可能有許多客戶可以執行最新版本。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-118">The Console Host team strives to minimize differences between the Legacy and current modes of the console to ensure that as many customers as possible can run the most up-to-date version.</span></span> <span data-ttu-id="0d5d2-119">如果您遇到要求您使用此處未記載之舊版主控台的問題，請洽詢 [microsoft/終端](https://github.com/microsoft/terminal/) 機 GitHub 存放庫上的小組，或透過 [意見反應中樞](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) 取得協助。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-119">If you experience an issue that requires you to use the legacy console that is not documented here, please contact the team on the [microsoft/terminal](https://github.com/microsoft/terminal/) GitHub repository or via the [Feedback Hub](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) for assistance.</span></span>

### <a name="16-bit-applications-on-32-bit-windows"></a><span data-ttu-id="0d5d2-120">32位 Windows 上的16位應用程式</span><span class="sxs-lookup"><span data-stu-id="0d5d2-120">16-bit applications on 32-bit Windows</span></span>

<span data-ttu-id="0d5d2-121">32位 Windows 上的一些16位應用程式會使用虛擬機器技術來操作，稱為 [NTVDM](https://docs.microsoft.com/windows/compatibility/ntvdm-and-16-bit-app-support)。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-121">Some 16-bit applications on 32-bit Windows use a virtual machine technology to operate called [NTVDM](https://docs.microsoft.com/windows/compatibility/ntvdm-and-16-bit-app-support).</span></span> <span data-ttu-id="0d5d2-122">這些應用程式通常會使用圖形化螢幕緩衝模式搭配主控台裝載環境來操作。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-122">Often these applications use a graphical screen buffering mode in conjunction with the console hosting environment to operate.</span></span> <span data-ttu-id="0d5d2-123">只有舊版主控台體驗支援這些圖形緩衝模式，以及支援這些應用程式所需的其他主控台 API 支援。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-123">Only the legacy console experience supports these graphical buffering modes and the additional console API support required to power these applications.</span></span> <span data-ttu-id="0d5d2-124">當其中一個應用程式啟動時，系統會自動選取舊版主控台環境。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-124">The system will automatically select the legacy console environment when one of these applications is launched.</span></span>

### <a name="ime-embedding"></a><span data-ttu-id="0d5d2-125">輸入法嵌入</span><span class="sxs-lookup"><span data-stu-id="0d5d2-125">IME Embedding</span></span>

<span data-ttu-id="0d5d2-126">舊版主控台主機會在螢幕底部保留一行，以將輸入法的建議部分內嵌在主控視窗內，以取得建議。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-126">The legacy Console Host embedded the suggestion portion of the IME inside the hosting window by reserving a line at the bottom of the screen for suggestions.</span></span> <span data-ttu-id="0d5d2-127">目前的主控台主機環境會改為將此活動委派給 IME 子系統，以在主控台主機上方顯示有建議的重迭視窗。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-127">The current Console Host environment instead delegates this activity to the IME subsystem to display an overlay window above the console host with suggestions.</span></span> <span data-ttu-id="0d5d2-128">在無法覆迭視窗的環境中 (像是) 某些遠端處理工具一樣，可能需要舊版主控台主機。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-128">In an environment where overlay windows are not possible (like with certain remoting tools), the legacy console host may be required.</span></span>

### <a name="api-differences"></a><span data-ttu-id="0d5d2-129">API 差異</span><span class="sxs-lookup"><span data-stu-id="0d5d2-129">API Differences</span></span>

<span data-ttu-id="0d5d2-130">Legacy 和 current 之間的主要已知差異在於 UTF-8 的執行。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-130">The major known difference between legacy and current is the implementation of UTF-8.</span></span> <span data-ttu-id="0d5d2-131">舊版主機在使用 [字碼頁 65001](https://docs.microsoft.com/windows/win32/intl/code-pages)時，對 utf-8 的支援非常基本且通常不正確。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-131">The legacy host has extremely rudimentary and often incorrect support of UTF-8 with [code page 65001](https://docs.microsoft.com/windows/win32/intl/code-pages).</span></span> <span data-ttu-id="0d5d2-132">目前的主控台主機包含 Windows 10 的累加式改良版，以改善這項支援。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-132">The current console host contains incremental improvements release-over-release of Windows 10 to improve this support.</span></span> <span data-ttu-id="0d5d2-133">嘗試依賴從舊版主控台預測 UTF-8 的「已知不正確」解讀的應用程式，將會在支援改善時，發現自己收到不同的答案。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-133">Applications that are attempting to rely on predicting "known incorrect" interpretations of UTF-8 from the legacy console will find themselves receiving different answers as support is improved.</span></span>

<span data-ttu-id="0d5d2-134">您應該向 [microsoft/終端機 GitHub 存放庫](https://github.com/microsoft/terminal/) 或透過 [意見反應中樞](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) 回報 api 的其他差異，以進行分級和可能的補救。</span><span class="sxs-lookup"><span data-stu-id="0d5d2-134">Other differences experienced with APIs should be reported to the [microsoft/terminal GitHub repository](https://github.com/microsoft/terminal/) or via the [Feedback Hub](https://docs.microsoft.com/windows-insider/feedback-hub/feedback-hub-app) for triage and possible remediation.</span></span>

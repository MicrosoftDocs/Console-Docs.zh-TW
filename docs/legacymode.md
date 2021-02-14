---
title: 舊版主控台模式– Windows 桌面
description: 舊版主控台模式是一種相容性工具，可協助執行可能無法與 Windows 10 主控台主機搭配運作的命令列應用程式
author: miniksa
ms.author: miniksa
ms.topic: conceptual
ms.prod: console
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api, 相容性
ms.openlocfilehash: e3b5876131ff30f5b0baebddc842ab3366c02786
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357788"
---
# <a name="legacy-console-mode"></a><span data-ttu-id="3fea2-104">舊版主控台模式</span><span class="sxs-lookup"><span data-stu-id="3fea2-104">Legacy Console mode</span></span>

<span data-ttu-id="3fea2-105">舊版主控台模式是一種相容性工具，其設計訴求是要協助 Windows 10 上的舊版命令列工具使用者。</span><span class="sxs-lookup"><span data-stu-id="3fea2-105">Legacy Console mode is a compatibility tool designed to help users of older command-line tools on Windows 10.</span></span> <span data-ttu-id="3fea2-106">對於在預設 Windows 10 主控台體驗中未顯示或正常運作的任何命令列工具，此模式提供了粗略的解決方案，讓系統逐步退回舊版的主控台主控體驗。</span><span class="sxs-lookup"><span data-stu-id="3fea2-106">For any command-line tool that is not displaying or operating correctly in the default Windows 10 console experience, this mode provides a coarse-grained solution to stepping the system back to an older version of the console hosting experience.</span></span>

## <a name="using-legacy-console-mode"></a><span data-ttu-id="3fea2-107">使用舊版主控台模式</span><span class="sxs-lookup"><span data-stu-id="3fea2-107">Using Legacy Console Mode</span></span>

<span data-ttu-id="3fea2-108">若要使用舊版主控台模式，請先開啟任何主控台主控視窗。</span><span class="sxs-lookup"><span data-stu-id="3fea2-108">To use Legacy Console mode, first open any console hosting window.</span></span> <span data-ttu-id="3fea2-109">啟動其中一個命令解譯器 [CMD](/windows-server/administration/windows-commands/cmd) 或 [PowerShell](/powershell/scripting/install/installing-windows-powershell)，通常可完成此動作。</span><span class="sxs-lookup"><span data-stu-id="3fea2-109">This is typically done by launching one of the command interpreters [CMD](/windows-server/administration/windows-commands/cmd) or [PowerShell](/powershell/scripting/install/installing-windows-powershell).</span></span>

<span data-ttu-id="3fea2-110">以滑鼠右鍵按一下應用程式標題列，然後選擇 `Properties` 功能表選項。</span><span class="sxs-lookup"><span data-stu-id="3fea2-110">Right-click on the application title bar and choose the `Properties` menu option.</span></span> <span data-ttu-id="3fea2-111">選擇第一個索引標籤 `Options`。</span><span class="sxs-lookup"><span data-stu-id="3fea2-111">Choose the first tab, `Options`.</span></span> <span data-ttu-id="3fea2-112">然後勾選頁面底部描述 `Use legacy console` 的方塊。</span><span class="sxs-lookup"><span data-stu-id="3fea2-112">Then check the box at the bottom of the page describing `Use legacy console`.</span></span> <span data-ttu-id="3fea2-113">按下 `OK` 按鈕加以套用。</span><span class="sxs-lookup"><span data-stu-id="3fea2-113">Press the `OK` button to apply.</span></span>

<span data-ttu-id="3fea2-114">返回相同的屬性工作表功能表並取消選取該方塊，然後按下 `OK`，即可還原此設定。</span><span class="sxs-lookup"><span data-stu-id="3fea2-114">The setting can be reverted by returning to the same property sheet menu and unchecking the box then pressing `OK`.</span></span>

> [!NOTE]
><span data-ttu-id="3fea2-115">此設定會全面套用至所有在喜好設定變更後啟動的工作階段。</span><span class="sxs-lookup"><span data-stu-id="3fea2-115">This setting is globally applied to all sessions that start after the preference is changed.</span></span> <span data-ttu-id="3fea2-116">已開啟的工作階段將不會變更。</span><span class="sxs-lookup"><span data-stu-id="3fea2-116">Sessions that are already open will not be changed.</span></span>

## <a name="differences-between-modes"></a><span data-ttu-id="3fea2-117">模式間的差異</span><span class="sxs-lookup"><span data-stu-id="3fea2-117">Differences between modes</span></span>

<span data-ttu-id="3fea2-118">主控台主機小組致力於縮小主控台的舊版和目前模式之間的差異，以確保盡可能有較多客戶可執行最新版本。</span><span class="sxs-lookup"><span data-stu-id="3fea2-118">The Console Host team strives to minimize differences between the Legacy and current modes of the console to ensure that as many customers as possible can run the most up-to-date version.</span></span> <span data-ttu-id="3fea2-119">如果您遇到的問題需要您使用此處未記載的舊版主控台，請在 [microsoft/terminal](https://github.com/microsoft/terminal/) GitHub 存放庫上或透過[意見反應中樞](/windows-insider/feedback-hub/feedback-hub-app)連絡小組，以取得協助。</span><span class="sxs-lookup"><span data-stu-id="3fea2-119">If you experience an issue that requires you to use the legacy console that is not documented here, please contact the team on the [microsoft/terminal](https://github.com/microsoft/terminal/) GitHub repository or via the [Feedback Hub](/windows-insider/feedback-hub/feedback-hub-app) for assistance.</span></span>

### <a name="16-bit-applications-on-32-bit-windows"></a><span data-ttu-id="3fea2-120">32 位元 Windows 上的 16 位元應用程式</span><span class="sxs-lookup"><span data-stu-id="3fea2-120">16-bit applications on 32-bit Windows</span></span>

<span data-ttu-id="3fea2-121">32 位元 Windows 上的某些 16 位元應用程式會使用稱為 [NTVDM](/windows/compatibility/ntvdm-and-16-bit-app-support) 的虛擬機器技術進行操作。</span><span class="sxs-lookup"><span data-stu-id="3fea2-121">Some 16-bit applications on 32-bit Windows use a virtual machine technology to operate called [NTVDM](/windows/compatibility/ntvdm-and-16-bit-app-support).</span></span> <span data-ttu-id="3fea2-122">這些應用程式通常會使用圖形化螢幕緩衝模式搭配主控台主控環境進行操作。</span><span class="sxs-lookup"><span data-stu-id="3fea2-122">Often these applications use a graphical screen buffering mode in conjunction with the console hosting environment to operate.</span></span> <span data-ttu-id="3fea2-123">只有舊版主控台體驗支援這些圖形化緩衝模式，以及啟動這些應用程式所需的其他主控台 API 支援。</span><span class="sxs-lookup"><span data-stu-id="3fea2-123">Only the legacy console experience supports these graphical buffering modes and the additional console API support required to power these applications.</span></span> <span data-ttu-id="3fea2-124">當其中一個這類應用程式啟動時，系統會自動選取舊版主控台環境。</span><span class="sxs-lookup"><span data-stu-id="3fea2-124">The system will automatically select the legacy console environment when one of these applications is launched.</span></span>

### <a name="ime-embedding"></a><span data-ttu-id="3fea2-125">IME 內嵌</span><span class="sxs-lookup"><span data-stu-id="3fea2-125">IME Embedding</span></span>

<span data-ttu-id="3fea2-126">舊版主控台主機會藉由在畫面底部保留一行作為建議，將 IME 的建議部分內嵌在主控視窗中。</span><span class="sxs-lookup"><span data-stu-id="3fea2-126">The legacy Console Host embedded the suggestion portion of the IME inside the hosting window by reserving a line at the bottom of the screen for suggestions.</span></span> <span data-ttu-id="3fea2-127">目前的主控台主機環境會改為將此活動委派給 IME 子系統，以在主控台主機上方顯示包含建議的重疊視窗。</span><span class="sxs-lookup"><span data-stu-id="3fea2-127">The current Console Host environment instead delegates this activity to the IME subsystem to display an overlay window above the console host with suggestions.</span></span> <span data-ttu-id="3fea2-128">在不可能重疊視窗的環境中 (例如特定遠端工具)，可能需要舊版的主控台主機。</span><span class="sxs-lookup"><span data-stu-id="3fea2-128">In an environment where overlay windows are not possible (like with certain remoting tools), the legacy console host may be required.</span></span>

### <a name="api-differences"></a><span data-ttu-id="3fea2-129">API 差異</span><span class="sxs-lookup"><span data-stu-id="3fea2-129">API Differences</span></span>

<span data-ttu-id="3fea2-130">舊版和目前版本之間的主要已知差異在於 UTF-8 的實作。</span><span class="sxs-lookup"><span data-stu-id="3fea2-130">The major known difference between legacy and current is the implementation of UTF-8.</span></span> <span data-ttu-id="3fea2-131">舊版主機具有極為基本且通常不正確的 UTF-8 支援 ([字碼頁 65001](/windows/win32/intl/code-pages))。</span><span class="sxs-lookup"><span data-stu-id="3fea2-131">The legacy host has extremely rudimentary and often incorrect support of UTF-8 with [code page 65001](/windows/win32/intl/code-pages).</span></span> <span data-ttu-id="3fea2-132">目前的主控台主機包含 Windows 10 的各版累加式改良，可改善這項支援。</span><span class="sxs-lookup"><span data-stu-id="3fea2-132">The current console host contains incremental improvements release-over-release of Windows 10 to improve this support.</span></span> <span data-ttu-id="3fea2-133">嘗試依賴從舊版主控台預測 UTF-8「已知不正確」解譯的應用程式，將發現自己會在改善支援時收到不同的答案。</span><span class="sxs-lookup"><span data-stu-id="3fea2-133">Applications that are attempting to rely on predicting "known incorrect" interpretations of UTF-8 from the legacy console will find themselves receiving different answers as support is improved.</span></span>

<span data-ttu-id="3fea2-134">透過 API 經歷的其他差異應該回報至 [microsoft/terminal GitHub 存放庫](https://github.com/microsoft/terminal/)或透過[意見反應中樞](/windows-insider/feedback-hub/feedback-hub-app)回報，以進行分級和可能的補救。</span><span class="sxs-lookup"><span data-stu-id="3fea2-134">Other differences experienced with APIs should be reported to the [microsoft/terminal GitHub repository](https://github.com/microsoft/terminal/) or via the [Feedback Hub](/windows-insider/feedback-hub/feedback-hub-app) for triage and possible remediation.</span></span>
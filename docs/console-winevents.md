---
title: 主控台 WinEvents
description: 下列事件常數用於 WinEventProc 回呼函數的事件參數。 如需詳細資訊，請參閱 WinEvents。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- winuser/EVENT_CONSOLE_CARET
- winuser/EVENT_CONSOLE_END_APPLICATION
- winuser/EVENT_CONSOLE_LAYOUT
- winuser/EVENT_CONSOLE_START_APPLICATION
- winuser/EVENT_CONSOLE_UPDATE_REGION
- winuser/EVENT_CONSOLE_UPDATE_SCROLL
- winuser/EVENT_CONSOLE_UPDATE_SIMPLE
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
MS-HAID:
- '\_win32\_console\_winevents'
- base.console\_winevents
- consoles.console\_winevents
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: b7078b2d-5508-4e42-bac2-34b70f1856e2
topic_type:
- apiref
api_name:
- EVENT_CONSOLE_CARET
- EVENT_CONSOLE_END_APPLICATION
- EVENT_CONSOLE_LAYOUT
- EVENT_CONSOLE_START_APPLICATION
- EVENT_CONSOLE_UPDATE_REGION
- EVENT_CONSOLE_UPDATE_SCROLL
- EVENT_CONSOLE_UPDATE_SIMPLE
api_location:
- Winuser.h
api_type:
- HeaderDef
ms.openlocfilehash: 2cd48537ef79f09024a55b32a98e2aa85fe76f62
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358048"
---
# <a name="console-winevents"></a><span data-ttu-id="5df41-105">主控台 WinEvents</span><span class="sxs-lookup"><span data-stu-id="5df41-105">Console WinEvents</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5df41-106">WinEvents 是舊版 **[Microsoft Active Accessibility](/windows/win32/winauto/microsoft-active-accessibility)** framework 的一部分。</span><span class="sxs-lookup"><span data-stu-id="5df41-106">WinEvents are part of the legacy **[Microsoft Active Accessibility](/windows/win32/winauto/microsoft-active-accessibility)** framework.</span></span> <span data-ttu-id="5df41-107">強烈建議您不要使用這些事件進行開發， **[消費者介面自動化](/windows/win32/winauto/entry-uiauto-win32)** 以提供更健全且完整的介面套件，讓協助工具和自動化應用程式與主控台互動。</span><span class="sxs-lookup"><span data-stu-id="5df41-107">Development using these events is strongly discouraged in favor of the **[Microsoft UI Automation](/windows/win32/winauto/entry-uiauto-win32)** framework which provides a more robust and comprehensive suite of interfaces for accessibility and automation applications to interact with the console.</span></span> 

> [!WARNING]
> <span data-ttu-id="5df41-108">註冊這些事件是一項全域活動，會大幅影響系統上執行之所有命令列應用程式的效能，包括服務和背景公用程式。</span><span class="sxs-lookup"><span data-stu-id="5df41-108">Registering for these events is a global activity and will significantly impact performance of all command-line applications running on a system at the same time, including services and background utilities.</span></span> <span data-ttu-id="5df41-109">**Microsoft 消費者介面自動化** framework 是特定的主控台會話，克服這項限制。</span><span class="sxs-lookup"><span data-stu-id="5df41-109">The **Microsoft UI Automation** framework is console session specific and overcomes this limitation.</span></span>

<span data-ttu-id="5df41-110">下列事件常數用於 [*WinEventProc*](/windows/win32/api/winuser/nc-winuser-wineventproc)回呼函數的 *事件* 參數。</span><span class="sxs-lookup"><span data-stu-id="5df41-110">The following event constants are used in the *event* parameter of the [*WinEventProc*](/windows/win32/api/winuser/nc-winuser-wineventproc) callback function.</span></span> <span data-ttu-id="5df41-111">如需詳細資訊，請參閱 [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889)。</span><span class="sxs-lookup"><span data-stu-id="5df41-111">For more information, see [WinEvents](https://msdn.microsoft.com/library/windows/desktop/dd373889).</span></span>

| <span data-ttu-id="5df41-112">常數/值</span><span class="sxs-lookup"><span data-stu-id="5df41-112">Constant/value</span></span> | <span data-ttu-id="5df41-113">Description</span><span class="sxs-lookup"><span data-stu-id="5df41-113">Description</span></span> |
|-|-|
| <span data-ttu-id="5df41-114">**EVENT_CONSOLE_CARET** 0x4001</span><span class="sxs-lookup"><span data-stu-id="5df41-114">**EVENT_CONSOLE_CARET** 0x4001</span></span> | <span data-ttu-id="5df41-115">主控台插入號已移動。</span><span class="sxs-lookup"><span data-stu-id="5df41-115">The console caret has moved.</span></span> <span data-ttu-id="5df41-116">*IdObject* 參數是下列其中一個或多個值： **CONSOLE_CARET_SELECTION** 或 **CONSOLE_CARET_VISIBLE**。</span><span class="sxs-lookup"><span data-stu-id="5df41-116">The *idObject* parameter is one or more of the following values: **CONSOLE_CARET_SELECTION** or **CONSOLE_CARET_VISIBLE**.</span></span> <span data-ttu-id="5df41-117">*IdChild* 參數是一種 **[COORD](coord-str.md)** 結構，可指定資料指標的目前位置。</span><span class="sxs-lookup"><span data-stu-id="5df41-117">The *idChild* parameter is a **[COORD](coord-str.md)** structure that specifies the cursor's current position.</span></span> |
| <span data-ttu-id="5df41-118">**EVENT_CONSOLE_END_APPLICATION** 0x4007</span><span class="sxs-lookup"><span data-stu-id="5df41-118">**EVENT_CONSOLE_END_APPLICATION** 0x4007</span></span> | <span data-ttu-id="5df41-119">主控台進程已結束。</span><span class="sxs-lookup"><span data-stu-id="5df41-119">A console process has exited.</span></span> <span data-ttu-id="5df41-120">*IdObject* 參數包含終止進程的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="5df41-120">The *idObject* parameter contains the process identifier of the terminated process.</span></span> |
| <span data-ttu-id="5df41-121">**EVENT_CONSOLE_LAYOUT** 0x4005</span><span class="sxs-lookup"><span data-stu-id="5df41-121">**EVENT_CONSOLE_LAYOUT** 0x4005</span></span> | <span data-ttu-id="5df41-122">主控台版面配置已變更。</span><span class="sxs-lookup"><span data-stu-id="5df41-122">The console layout has changed.</span></span> |
| <span data-ttu-id="5df41-123">**EVENT_CONSOLE_START_APPLICATION** 0x4006</span><span class="sxs-lookup"><span data-stu-id="5df41-123">**EVENT_CONSOLE_START_APPLICATION** 0x4006</span></span> | <span data-ttu-id="5df41-124">新的主控台進程已啟動。</span><span class="sxs-lookup"><span data-stu-id="5df41-124">A new console process has started.</span></span> <span data-ttu-id="5df41-125">*IdObject* 參數包含新建立之進程的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="5df41-125">The *idObject* parameter contains the process identifier of the newly created process.</span></span> <span data-ttu-id="5df41-126">如果應用程式是16位的應用程式，則會 **CONSOLE_APPLICATION_16BIT** *idChild* 參數，而 *idObject* 是與主控台相關聯之 NTVDM 會話的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="5df41-126">If the application is a 16-bit application, the *idChild* parameter is **CONSOLE_APPLICATION_16BIT** and *idObject* is the process identifier of the NTVDM session associated with the console.</span></span> |
|<span data-ttu-id="5df41-127">**EVENT_CONSOLE_UPDATE_REGION** 0x4002</span><span class="sxs-lookup"><span data-stu-id="5df41-127">**EVENT_CONSOLE_UPDATE_REGION** 0x4002</span></span> | <span data-ttu-id="5df41-128">有一個以上的字元已經變更。</span><span class="sxs-lookup"><span data-stu-id="5df41-128">More than one character has changed.</span></span> <span data-ttu-id="5df41-129">*IdObject* 參數是指定變更區域開頭的 **[COORD](coord-str.md)** 結構。</span><span class="sxs-lookup"><span data-stu-id="5df41-129">The  *idObject* parameter is a **[COORD](coord-str.md)** structure that specifies the start of the changed region.</span></span> <span data-ttu-id="5df41-130">*IdChild* 參數是指定已變更區域結尾的 **COORD** 結構。</span><span class="sxs-lookup"><span data-stu-id="5df41-130">The *idChild* parameter is a **COORD** structure that specifies the end of the changed region.</span></span> |
|<span data-ttu-id="5df41-131">**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004</span><span class="sxs-lookup"><span data-stu-id="5df41-131">**EVENT_CONSOLE_UPDATE_SCROLL** 0x4004</span></span> | <span data-ttu-id="5df41-132">主控台已滾動。</span><span class="sxs-lookup"><span data-stu-id="5df41-132">The console has scrolled.</span></span> <span data-ttu-id="5df41-133">*IdObject* 參數是主控台滾動的水準距離。</span><span class="sxs-lookup"><span data-stu-id="5df41-133">The *idObject* parameter is the horizontal distance the console has scrolled.</span></span> <span data-ttu-id="5df41-134">*IdChild* 參數是主控台滾動的垂直距離。</span><span class="sxs-lookup"><span data-stu-id="5df41-134">The *idChild* parameter is the vertical distance the console has scrolled.</span></span> |
|<span data-ttu-id="5df41-135">**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003</span><span class="sxs-lookup"><span data-stu-id="5df41-135">**EVENT_CONSOLE_UPDATE_SIMPLE** 0x4003</span></span> | <span data-ttu-id="5df41-136">單一字元已經變更。</span><span class="sxs-lookup"><span data-stu-id="5df41-136">A single character has changed.</span></span> <span data-ttu-id="5df41-137">*IdObject* 參數是指定已變更之字元的 **[COORD](coord-str.md)** 結構。</span><span class="sxs-lookup"><span data-stu-id="5df41-137">The *idObject* parameter is a **[COORD](coord-str.md)** structure that specifies the character that has changed.</span></span> <span data-ttu-id="5df41-138">*IdChild* 參數會指定低字組中的字元和高位字中的 **[字元屬性](console-screen-buffers.md#character-attributes)**。</span><span class="sxs-lookup"><span data-stu-id="5df41-138">The *idChild* parameter specifies the character in the low word and the **[character attributes](console-screen-buffers.md#character-attributes)** in the high word.</span></span> |

## <a name="requirements"></a><span data-ttu-id="5df41-139">規格需求</span><span class="sxs-lookup"><span data-stu-id="5df41-139">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="5df41-140">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="5df41-140">Minimum supported client</span></span> | <span data-ttu-id="5df41-141">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="5df41-141">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="5df41-142">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="5df41-142">Minimum supported server</span></span> | <span data-ttu-id="5df41-143">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="5df41-143">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="5df41-144">標頭</span><span class="sxs-lookup"><span data-stu-id="5df41-144">Header</span></span> | <span data-ttu-id="5df41-145">Winuser。h</span><span class="sxs-lookup"><span data-stu-id="5df41-145">Winuser.h</span></span> |
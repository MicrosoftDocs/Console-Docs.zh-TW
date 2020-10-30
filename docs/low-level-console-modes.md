---
title: Low-Level 主控台模式
description: 主控台輸入緩衝區中報告的輸入事件種類，取決於主控台的滑鼠和視窗輸入模式。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_low\_level\_console\_modes'
- base.low\_level\_console\_modes
- consoles.low\_level\_console\_modes
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 41bfdc51-27cb-4d5e-898c-507ffc8789b9
ms.openlocfilehash: acd68e9679f209349f3e0db6989ca905815525a9
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039536"
---
# <a name="low-level-console-modes"></a><span data-ttu-id="39395-104">Low-Level 主控台模式</span><span class="sxs-lookup"><span data-stu-id="39395-104">Low-Level Console Modes</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="39395-105">主控台輸入緩衝區中報告的輸入事件種類，取決於主控台的滑鼠和視窗輸入模式。</span><span class="sxs-lookup"><span data-stu-id="39395-105">The types of input events reported in a console's input buffer depend on the console's mouse and window input modes.</span></span> <span data-ttu-id="39395-106">主控台的已處理輸入模式會決定系統如何處理 CTRL + C 按鍵組合。</span><span class="sxs-lookup"><span data-stu-id="39395-106">The console's processed input mode determines how the system handles the CTRL+C key combination.</span></span> <span data-ttu-id="39395-107">若要設定或抓取主控台的輸入模式狀態，應用程式可以在 [**SetConsoleMode**](setconsolemode.md) 或 [**GetConsoleMode**](getconsolemode.md) 函式的呼叫中指定主控台輸入緩衝區控制碼。</span><span class="sxs-lookup"><span data-stu-id="39395-107">To set or retrieve the state of a console's input modes, an application can specify a console input buffer handle in a call to the [**SetConsoleMode**](setconsolemode.md) or [**GetConsoleMode**](getconsolemode.md) function.</span></span> <span data-ttu-id="39395-108">主控台輸入控制碼會使用下列模式。</span><span class="sxs-lookup"><span data-stu-id="39395-108">The following modes are used with console input handles.</span></span>

| <span data-ttu-id="39395-109">[模式]</span><span class="sxs-lookup"><span data-stu-id="39395-109">Mode</span></span> | <span data-ttu-id="39395-110">描述</span><span class="sxs-lookup"><span data-stu-id="39395-110">Description</span></span> |
|-|-|
| <span data-ttu-id="39395-111">**啟用 \_ 滑鼠 \_ 輸入**</span><span class="sxs-lookup"><span data-stu-id="39395-111">**ENABLE\_MOUSE\_INPUT**</span></span>     | <span data-ttu-id="39395-112">控制是否要在輸入緩衝區中報告滑鼠事件。</span><span class="sxs-lookup"><span data-stu-id="39395-112">Controls whether mouse events are reported in the input buffer.</span></span> <span data-ttu-id="39395-113">依預設，會啟用滑鼠輸入並停用視窗輸入。</span><span class="sxs-lookup"><span data-stu-id="39395-113">By default, mouse input is enabled and window input is disabled.</span></span> <span data-ttu-id="39395-114">變更其中一個模式只會影響在設定模式之後所發生的輸入;輸入緩衝區中的暫止滑鼠或視窗事件不會排清。</span><span class="sxs-lookup"><span data-stu-id="39395-114">Changing either of these modes affects only input that occurs after the mode is set; pending mouse or window events in the input buffer are not flushed.</span></span> <span data-ttu-id="39395-115">無論滑鼠模式為何，都會顯示滑鼠指標。</span><span class="sxs-lookup"><span data-stu-id="39395-115">The mouse pointer is displayed regardless of the mouse mode.</span></span>                                                |
| <span data-ttu-id="39395-116">**啟用 \_ 視窗 \_ 輸入**</span><span class="sxs-lookup"><span data-stu-id="39395-116">**ENABLE\_WINDOW\_INPUT**</span></span>    | <span data-ttu-id="39395-117">控制是否在輸入緩衝區中報告緩衝區調整大小的事件。</span><span class="sxs-lookup"><span data-stu-id="39395-117">Controls whether buffer-resizing events are reported in the input buffer.</span></span> <span data-ttu-id="39395-118">依預設，會啟用滑鼠輸入並停用視窗輸入。</span><span class="sxs-lookup"><span data-stu-id="39395-118">By default, mouse input is enabled and window input is disabled.</span></span> <span data-ttu-id="39395-119">變更其中一個模式只會影響在設定模式之後所發生的輸入;輸入緩衝區中的暫止滑鼠或視窗事件不會排清。</span><span class="sxs-lookup"><span data-stu-id="39395-119">Changing either of these modes affects only input that occurs after the mode is set; pending mouse or window events in the input buffer are not flushed.</span></span> <span data-ttu-id="39395-120">無論滑鼠模式為何，都會顯示滑鼠指標。</span><span class="sxs-lookup"><span data-stu-id="39395-120">The mouse pointer is displayed regardless of the mouse mode.</span></span>                                      |
| <span data-ttu-id="39395-121">**啟用已 \_ 處理的 \_ 輸入**</span><span class="sxs-lookup"><span data-stu-id="39395-121">**ENABLE\_PROCESSED\_INPUT**</span></span> | <span data-ttu-id="39395-122">使用高階主控台 i/o 函數控制應用程式的輸入處理。</span><span class="sxs-lookup"><span data-stu-id="39395-122">Controls the processing of input for applications using the high-level console I/O functions.</span></span> <span data-ttu-id="39395-123">但是，如果已啟用已處理的輸入模式，則主控台的輸入緩衝區中不會報告 CTRL + C 按鍵組合。</span><span class="sxs-lookup"><span data-stu-id="39395-123">However, if processed input mode is enabled, the CTRL+C key combination is not reported in the console's input buffer.</span></span> <span data-ttu-id="39395-124">相反地，它會傳遞給適當的控制項處理常式函式。</span><span class="sxs-lookup"><span data-stu-id="39395-124">Instead, it is passed on to the appropriate control handler function.</span></span> <span data-ttu-id="39395-125">如需控制處理常式的詳細資訊，請參閱 [主控台控制項處理常式](console-control-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="39395-125">For more information about control handlers, see [Console Control Handlers](console-control-handlers.md).</span></span> |

<span data-ttu-id="39395-126">螢幕緩衝區的輸出模式不會影響低層級輸出函數的行為。</span><span class="sxs-lookup"><span data-stu-id="39395-126">The output modes of a screen buffer do not affect the behavior of the low-level output functions.</span></span>

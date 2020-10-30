---
title: 主控台處理群組
description: 當進程使用 CreateProcess 函式來建立新的主控台進程時，它可以指定 [建立 \_ 新的 \_ 進程群組] 旗標， \_ 讓新的進程成為主控台進程群組的根進程。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_console\_process\_groups'
- base.console\_process\_groups
- consoles.console\_process\_groups
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6cfe5b4b-d677-4747-bbf2-c7243db2346e
ms.openlocfilehash: 26a1b0b9001f64ea2dc7465fa298b1383f30aa61
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038446"
---
# <a name="console-process-groups"></a><span data-ttu-id="c42c7-104">主控台處理群組</span><span class="sxs-lookup"><span data-stu-id="c42c7-104">Console Process Groups</span></span>

<span data-ttu-id="c42c7-105">當進程使用 [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) 函式來建立新的主控台進程時，它可以指定 [ **建立 \_ 新的 \_ 進程 \_ 群組** ] 旗標，讓新的進程成為主控台進程群組的根進程。</span><span class="sxs-lookup"><span data-stu-id="c42c7-105">When a process uses the [**CreateProcess**](https://msdn.microsoft.com/library/windows/desktop/ms682425) function to create a new console process, it can specify the **CREATE\_NEW\_PROCESS\_GROUP** flag to make the new process the root process of a console process group.</span></span> <span data-ttu-id="c42c7-106">進程群組包含根進程下階的所有進程。</span><span class="sxs-lookup"><span data-stu-id="c42c7-106">The process group includes all processes that are descendants of the root process.</span></span>

<span data-ttu-id="c42c7-107">進程可以使用 [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) 函式，將 Ctrl + C 或 CTRL + BREAK 信號傳送到主控台進程群組中的所有進程。</span><span class="sxs-lookup"><span data-stu-id="c42c7-107">A process can use the [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) function to send a CTRL+C or CTRL+BREAK signal to all processes in a console process group.</span></span> <span data-ttu-id="c42c7-108">只有當群組中附加到與呼叫 **GenerateConsoleCtrlEvent** 進程相同之主控台的進程時，才會收到信號。</span><span class="sxs-lookup"><span data-stu-id="c42c7-108">The signal is only received by those processes in the group that are attached to the same console as the process that called **GenerateConsoleCtrlEvent** .</span></span>

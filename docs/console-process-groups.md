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
ms.openlocfilehash: 8df877eca9a52ef9072685c673461723dda78a0b
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358098"
---
# <a name="console-process-groups"></a>主控台處理群組

當進程使用 [**CreateProcess**](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessa) 函式來建立新的主控台進程時，它可以指定 [ **建立 \_ 新的 \_ 進程 \_ 群組** ] 旗標，讓新的進程成為主控台進程群組的根進程。 進程群組包含根進程下階的所有進程。

進程可以使用 [**GenerateConsoleCtrlEvent**](generateconsolectrlevent.md) 函式，將 Ctrl + C 或 CTRL + BREAK 信號傳送到主控台進程群組中的所有進程。 只有當群組中附加到與呼叫 **GenerateConsoleCtrlEvent** 進程相同之主控台的進程時，才會收到信號。
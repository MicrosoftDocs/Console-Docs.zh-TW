---
title: 主控台選取
description: 協助工具應用程式需要在主控台中選取使用者的相關資訊。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_console\_selection'
- base.console\_selection
- consoles.console\_selection
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 2f631e1b-d502-45b7-9c15-34c01e913738
ms.openlocfilehash: afc2d0a7615381b394df7f496aaf1b2a6002d04f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039156"
---
# <a name="console-selection"></a>主控台選取

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

協助工具應用程式需要在主控台中選取使用者的相關資訊。 若要取出目前的主控台選取專案，請呼叫 [**GetConsoleSelectionInfo**](getconsoleselectioninfo.md) 函式。 [**主控台 \_ 選取 \_ 資訊**](console-selection-info-str.md)結構包含選取專案的相關資訊，例如錨點、座標和狀態。

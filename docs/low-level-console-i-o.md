---
title: Low-Level 主控台 i/o
description: 低層級主控台 i/o 函數可讓您直接存取主控台的輸入和螢幕緩衝區，藉以擴充應用程式對主控台 i/o 的控制。
author: miniksa
ms.author: miniksa
ms.topic: conceptual
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
MS-HAID:
- '\_win32\_low\_level\_console\_i\_o'
- base.low\_level\_console\_i\_o
- consoles.low\_level\_console\_i\_o
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: c874aff4-6129-4dbc-8949-24d46382d81c
ms.openlocfilehash: b4ec834e44f7ff291466cfe1714442bc17ca7aca
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039546"
---
# <a name="low-level-console-io"></a><span data-ttu-id="0e801-104">Low-Level 主控台 i/o</span><span class="sxs-lookup"><span data-stu-id="0e801-104">Low-Level Console I/O</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="0e801-105">低層級主控台 i/o 函數可讓您直接存取主控台的輸入和螢幕緩衝區，藉以擴充應用程式對主控台 i/o 的控制。</span><span class="sxs-lookup"><span data-stu-id="0e801-105">The low-level console I/O functions expand an application's control over console I/O by enabling direct access to a console's input and screen buffers.</span></span> <span data-ttu-id="0e801-106">這些函數可讓應用程式執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="0e801-106">These functions enable an application to perform the following tasks:</span></span>

- <span data-ttu-id="0e801-107">接收關於滑鼠和緩衝區調整大小事件的輸入</span><span class="sxs-lookup"><span data-stu-id="0e801-107">Receive input about mouse and buffer-resizing events</span></span>
- <span data-ttu-id="0e801-108">接收鍵盤輸入事件的擴充資訊</span><span class="sxs-lookup"><span data-stu-id="0e801-108">Receive extended information about keyboard input events</span></span>
- <span data-ttu-id="0e801-109">將輸入記錄寫入輸入緩衝區</span><span class="sxs-lookup"><span data-stu-id="0e801-109">Write input records to the input buffer</span></span>
- <span data-ttu-id="0e801-110">讀取輸入記錄而不從輸入緩衝區移除</span><span class="sxs-lookup"><span data-stu-id="0e801-110">Read input records without removing them from the input buffer</span></span>
- <span data-ttu-id="0e801-111">判斷輸入緩衝區中的暫止事件數目</span><span class="sxs-lookup"><span data-stu-id="0e801-111">Determine the number of pending events in the input buffer</span></span>
- <span data-ttu-id="0e801-112">清除輸入緩衝區</span><span class="sxs-lookup"><span data-stu-id="0e801-112">Flush the input buffer</span></span>
- <span data-ttu-id="0e801-113">在螢幕緩衝區中的指定位置，讀取及寫入 Unicode 或 ANSI 字元的字串</span><span class="sxs-lookup"><span data-stu-id="0e801-113">Read and write strings of Unicode or ANSI characters at a specified location in a screen buffer</span></span>
- <span data-ttu-id="0e801-114">在指定的螢幕緩衝區位置讀取和寫入文字和背景色彩屬性的字串</span><span class="sxs-lookup"><span data-stu-id="0e801-114">Read and write strings of text and background color attributes at a specified screen buffer location</span></span>
- <span data-ttu-id="0e801-115">在指定的螢幕緩衝區位置讀取和寫入字元和色彩資料的矩形區塊</span><span class="sxs-lookup"><span data-stu-id="0e801-115">Read and write rectangular blocks of character and color data at a specified screen buffer location</span></span>
- <span data-ttu-id="0e801-116">從指定的螢幕緩衝區位置開始，將單一 Unicode 或 ANSI 字元（或文字和背景色彩屬性組合）寫入指定數目的連續儲存格</span><span class="sxs-lookup"><span data-stu-id="0e801-116">Write a single Unicode or ANSI character, or a text and background color attribute combination, to a specified number of consecutive cells beginning at a specified screen buffer location</span></span>

<span data-ttu-id="0e801-117">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="0e801-117">For more information, see the following topics:</span></span>

- [<span data-ttu-id="0e801-118">主控台模式</span><span class="sxs-lookup"><span data-stu-id="0e801-118">Console Modes</span></span>](console-modes.md)
- [<span data-ttu-id="0e801-119">低層級主控台模式</span><span class="sxs-lookup"><span data-stu-id="0e801-119">Low-Level Console Modes</span></span>](low-level-console-modes.md)
- [<span data-ttu-id="0e801-120">低層級主控台輸入函式</span><span class="sxs-lookup"><span data-stu-id="0e801-120">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)
- [<span data-ttu-id="0e801-121">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="0e801-121">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

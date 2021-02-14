---
title: SetConsoleScreenBufferInfoEx 函式
description: 將指定之主控台畫面緩衝區的擴充資訊設定為指定的緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleScreenBufferInfoEx
- wincon/SetConsoleScreenBufferInfoEx
- SetConsoleScreenBufferInfoEx
MS-HAID:
- base.setconsolescreenbufferinfoex
- consoles.setconsolescreenbufferinfoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ff851144-eee9-4410-8fd1-28aa24fc25f1
topic_type:
- apiref
api_name:
- SetConsoleScreenBufferInfoEx
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 677df94d6397c1515ad96757788c9a044b6ed87e
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100358648"
---
# <a name="setconsolescreenbufferinfoex-function"></a><span data-ttu-id="0d81a-104">SetConsoleScreenBufferInfoEx 函式</span><span class="sxs-lookup"><span data-stu-id="0d81a-104">SetConsoleScreenBufferInfoEx function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="0d81a-105">設定指定的主控台螢幕緩衝區的延伸資訊。</span><span class="sxs-lookup"><span data-stu-id="0d81a-105">Sets extended information about the specified console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="0d81a-106">語法</span><span class="sxs-lookup"><span data-stu-id="0d81a-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleScreenBufferInfoEx(
  _In_ HANDLE                        hConsoleOutput,
  _In_ PCONSOLE_SCREEN_BUFFER_INFOEX lpConsoleScreenBufferInfoEx
);
```

## <a name="parameters"></a><span data-ttu-id="0d81a-107">參數</span><span class="sxs-lookup"><span data-stu-id="0d81a-107">Parameters</span></span>

<span data-ttu-id="0d81a-108">*hConsoleOutput* \[in\]</span><span class="sxs-lookup"><span data-stu-id="0d81a-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="0d81a-109">主控台螢幕緩衝區的控點。</span><span class="sxs-lookup"><span data-stu-id="0d81a-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="0d81a-110">控點必須具有 **GENERIC\_WRITE** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="0d81a-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="0d81a-111">如需詳細資訊，請參閱[主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="0d81a-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="0d81a-112">*lpConsoleScreenBufferInfoEx* \[在\]</span><span class="sxs-lookup"><span data-stu-id="0d81a-112">*lpConsoleScreenBufferInfoEx* \[in\]</span></span>  
<span data-ttu-id="0d81a-113">[**主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX**](console-screen-buffer-infoex.md)結構，其中包含主控台螢幕緩衝區資訊。</span><span class="sxs-lookup"><span data-stu-id="0d81a-113">A [**CONSOLE\_SCREEN\_BUFFER\_INFOEX**](console-screen-buffer-infoex.md) structure that contains the console screen buffer information.</span></span>

## <a name="return-value"></a><span data-ttu-id="0d81a-114">傳回值</span><span class="sxs-lookup"><span data-stu-id="0d81a-114">Return value</span></span>

<span data-ttu-id="0d81a-115">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="0d81a-115">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="0d81a-116">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="0d81a-116">If the function fails, the return value is zero.</span></span> <span data-ttu-id="0d81a-117">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="0d81a-117">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="0d81a-118">備註</span><span class="sxs-lookup"><span data-stu-id="0d81a-118">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="0d81a-119">此 API 具有對等的部分 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="0d81a-119">This API has a partial **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="0d81a-120">資料 **[指標定位緩衝區](console-virtual-terminal-sequences.md#cursor-positioning)** 和 **[文字屬性](console-virtual-terminal-sequences.md#text-formatting)** 具有特定的順序對應。</span><span class="sxs-lookup"><span data-stu-id="0d81a-120">**[Cursor positioning buffer](console-virtual-terminal-sequences.md#cursor-positioning)** and **[text attributes](console-virtual-terminal-sequences.md#text-formatting)** have specific sequence equivalents.</span></span> <span data-ttu-id="0d81a-121">Color 資料表無法設定，但是 **[擴充色彩](console-virtual-terminal-sequences.md#extended-colors)** 的可用範圍，通常是透過主控台函式所提供的 **[功能](console-functions.md)**。</span><span class="sxs-lookup"><span data-stu-id="0d81a-121">The color table is not configurable, but **[extended colors](console-virtual-terminal-sequences.md#extended-colors)** are available beyond what is normally available through **[console functions](console-functions.md)**.</span></span> <span data-ttu-id="0d81a-122">Popup 屬性沒有對等專案，因為快顯功能表是 **虛擬終端** 機世界中命令列用戶端應用程式的責任。</span><span class="sxs-lookup"><span data-stu-id="0d81a-122">Popup attributes have no equivalent as popup menus are the responsibility of the command-line client application in the **virtual terminal** world.</span></span> <span data-ttu-id="0d81a-123">最後，視窗和全螢幕狀態的大小會被視為 **虛擬終端** 機世界中使用者所擁有的許可權，而且沒有對等的順序。</span><span class="sxs-lookup"><span data-stu-id="0d81a-123">Finally, the size of the window and the full screen status are considered privileges owned by the user in the **virtual terminal** world and have no equivalent sequence.</span></span>

## <a name="requirements"></a><span data-ttu-id="0d81a-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="0d81a-124">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="0d81a-125">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="0d81a-125">Minimum supported client</span></span> | <span data-ttu-id="0d81a-126">\[僅限 Windows Vista 桌面應用程式\]</span><span class="sxs-lookup"><span data-stu-id="0d81a-126">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="0d81a-127">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="0d81a-127">Minimum supported server</span></span> | <span data-ttu-id="0d81a-128">僅限 Windows Server 2008 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="0d81a-128">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="0d81a-129">標頭</span><span class="sxs-lookup"><span data-stu-id="0d81a-129">Header</span></span> | <span data-ttu-id="0d81a-130">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="0d81a-130">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="0d81a-131">程式庫</span><span class="sxs-lookup"><span data-stu-id="0d81a-131">Library</span></span> | <span data-ttu-id="0d81a-132">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="0d81a-132">Kernel32.lib</span></span> |
| <span data-ttu-id="0d81a-133">DLL</span><span class="sxs-lookup"><span data-stu-id="0d81a-133">DLL</span></span> | <span data-ttu-id="0d81a-134">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="0d81a-134">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="0d81a-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d81a-135">See also</span></span>

[<span data-ttu-id="0d81a-136">主控台函式</span><span class="sxs-lookup"><span data-stu-id="0d81a-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="0d81a-137">**主控台 \_ 螢幕 \_ 緩衝區 \_ INFOEX**</span><span class="sxs-lookup"><span data-stu-id="0d81a-137">**CONSOLE\_SCREEN\_BUFFER\_INFOEX**</span></span>](console-screen-buffer-infoex.md)

[<span data-ttu-id="0d81a-138">**GetConsoleScreenBufferInfoEx**</span><span class="sxs-lookup"><span data-stu-id="0d81a-138">**GetConsoleScreenBufferInfoEx**</span></span>](getconsolescreenbufferinfoex.md)
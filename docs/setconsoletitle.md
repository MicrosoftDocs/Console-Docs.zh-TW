---
title: SetConsoleTitle 函式
description: 請參閱 SetConsoleTitle 函式的參考資訊，此函數會設定目前主控台視窗的標題。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/SetConsoleTitle
- wincon/SetConsoleTitle
- SetConsoleTitle
- consoleapi2/SetConsoleTitleA
- wincon/SetConsoleTitleA
- SetConsoleTitleA
- consoleapi2/SetConsoleTitleW
- wincon/SetConsoleTitleW
- SetConsoleTitleW
MS-HAID:
- '\_win32\_setconsoletitle'
- base.setconsoletitle
- consoles.setconsoletitle
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f1db449b-0dd0-4d61-bb79-b7da9a5168f4
topic_type:
- apiref
api_name:
- SetConsoleTitle
- SetConsoleTitleA
- SetConsoleTitleW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: fa4f79925af870f3d345f384dab52ff4b98c182c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037029"
---
# <a name="setconsoletitle-function"></a><span data-ttu-id="544bf-104">SetConsoleTitle 函式</span><span class="sxs-lookup"><span data-stu-id="544bf-104">SetConsoleTitle function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="544bf-105">設定目前主控台視窗的標題。</span><span class="sxs-lookup"><span data-stu-id="544bf-105">Sets the title for the current console window.</span></span>

## <a name="syntax"></a><span data-ttu-id="544bf-106">語法</span><span class="sxs-lookup"><span data-stu-id="544bf-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleTitle(
  _In_ LPCTSTR lpConsoleTitle
);
```

## <a name="parameters"></a><span data-ttu-id="544bf-107">參數</span><span class="sxs-lookup"><span data-stu-id="544bf-107">Parameters</span></span>

<span data-ttu-id="544bf-108">*lpConsoleTitle* \[在\]</span><span class="sxs-lookup"><span data-stu-id="544bf-108">*lpConsoleTitle* \[in\]</span></span>  
<span data-ttu-id="544bf-109">要在主控台視窗的標題列中顯示的字串。</span><span class="sxs-lookup"><span data-stu-id="544bf-109">The string to be displayed in the title bar of the console window.</span></span> <span data-ttu-id="544bf-110">總大小必須小於64K。</span><span class="sxs-lookup"><span data-stu-id="544bf-110">The total size must be less than 64K.</span></span>

## <a name="return-value"></a><span data-ttu-id="544bf-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="544bf-111">Return value</span></span>

<span data-ttu-id="544bf-112">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="544bf-112">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="544bf-113">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="544bf-113">If the function fails, the return value is zero.</span></span> <span data-ttu-id="544bf-114">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="544bf-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="544bf-115">備註</span><span class="sxs-lookup"><span data-stu-id="544bf-115">Remarks</span></span>

<span data-ttu-id="544bf-116">當進程結束時，系統會還原原始的主控台標題。</span><span class="sxs-lookup"><span data-stu-id="544bf-116">When the process terminates, the system restores the original console title.</span></span>

[!INCLUDE [setting-codepage-mode-remarks](./includes/setting-codepage-mode-remarks.md)]

> [!TIP]
> <span data-ttu-id="544bf-117">此 API 在 **[視窗標題](console-virtual-terminal-sequences.md#window-title)** 序列中有對等的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="544bf-117">This API has a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent in the **[window title](console-virtual-terminal-sequences.md#window-title)** sequences.</span></span> <span data-ttu-id="544bf-118">建議您針對所有新的和進行中的開發，使用 _虛擬終端機序列_ 。</span><span class="sxs-lookup"><span data-stu-id="544bf-118">_Virtual terminal sequences_ are recommended for all new and ongoing development.</span></span>

## <a name="examples"></a><span data-ttu-id="544bf-119">範例</span><span class="sxs-lookup"><span data-stu-id="544bf-119">Examples</span></span>

<span data-ttu-id="544bf-120">下列範例示範如何取出和修改主控台標題。</span><span class="sxs-lookup"><span data-stu-id="544bf-120">The following example shows how to retrieve and modify the console title.</span></span>

```C
#include <windows.h>
#include <tchar.h>
#include <conio.h>
#include <strsafe.h>

int main( void )
{
   TCHAR szOldTitle[MAX_PATH];
   TCHAR szNewTitle[MAX_PATH];

   // Save current console title.

   if( GetConsoleTitle(szOldTitle, MAX_PATH) )
   {
      // Build new console title string.

      StringCchPrintf(szNewTitle, MAX_PATH, TEXT("TEST: %s"), szOldTitle);

      // Set console title to new title
      if( !SetConsoleTitle(szNewTitle) )
      {
         _tprintf(TEXT("SetConsoleTitle failed (%d)\n"), GetLastError());
         return 1;
      }
      else
      {
         _tprintf(TEXT("SetConsoleTitle succeeded.\n"));
      }
   }
   return 0;
}
```

## <a name="requirements"></a><span data-ttu-id="544bf-121">規格需求</span><span class="sxs-lookup"><span data-stu-id="544bf-121">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="544bf-122">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="544bf-122">Minimum supported client</span></span> | <span data-ttu-id="544bf-123">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="544bf-123">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="544bf-124">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="544bf-124">Minimum supported server</span></span> | <span data-ttu-id="544bf-125">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="544bf-125">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="544bf-126">標頭</span><span class="sxs-lookup"><span data-stu-id="544bf-126">Header</span></span> | <span data-ttu-id="544bf-127">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="544bf-127">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="544bf-128">程式庫</span><span class="sxs-lookup"><span data-stu-id="544bf-128">Library</span></span> | <span data-ttu-id="544bf-129">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="544bf-129">Kernel32.lib</span></span> |
| <span data-ttu-id="544bf-130">DLL</span><span class="sxs-lookup"><span data-stu-id="544bf-130">DLL</span></span> | <span data-ttu-id="544bf-131">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="544bf-131">Kernel32.dll</span></span> |
| <span data-ttu-id="544bf-132">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="544bf-132">Unicode and ANSI names</span></span> | <span data-ttu-id="544bf-133">**SetConsoleTitleW** (Unicode) 和 **SetConsoleTitleA** (ANSI) </span><span class="sxs-lookup"><span data-stu-id="544bf-133">**SetConsoleTitleW** (Unicode) and **SetConsoleTitleA** (ANSI)</span></span> |

## <a name="see-also"></a><span data-ttu-id="544bf-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="544bf-134">See also</span></span>

[<span data-ttu-id="544bf-135">主控台功能</span><span class="sxs-lookup"><span data-stu-id="544bf-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="544bf-136">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="544bf-136">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="544bf-137">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="544bf-137">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="544bf-138">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="544bf-138">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="544bf-139">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="544bf-139">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

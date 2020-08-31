---
title: SetConsoleTitle 函式
description: 請參閱 SetConsoleTitle 函式的參考資訊，此函數會設定目前主控台視窗的標題。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
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
ms.openlocfilehash: e1789243fd5c184221dd53038d8ec87c9b010749
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059514"
---
# <a name="setconsoletitle-function"></a><span data-ttu-id="76436-104">SetConsoleTitle 函式</span><span class="sxs-lookup"><span data-stu-id="76436-104">SetConsoleTitle function</span></span>


<span data-ttu-id="76436-105">設定目前主控台視窗的標題。</span><span class="sxs-lookup"><span data-stu-id="76436-105">Sets the title for the current console window.</span></span>

<a name="syntax"></a><span data-ttu-id="76436-106">語法</span><span class="sxs-lookup"><span data-stu-id="76436-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleTitle(
  _In_ LPCTSTR lpConsoleTitle
);
```

<a name="parameters"></a><span data-ttu-id="76436-107">參數</span><span class="sxs-lookup"><span data-stu-id="76436-107">Parameters</span></span>
----------

<span data-ttu-id="76436-108">*lpConsoleTitle* \[在\]</span><span class="sxs-lookup"><span data-stu-id="76436-108">*lpConsoleTitle* \[in\]</span></span>  
<span data-ttu-id="76436-109">要在主控台視窗的標題列中顯示的字串。</span><span class="sxs-lookup"><span data-stu-id="76436-109">The string to be displayed in the title bar of the console window.</span></span> <span data-ttu-id="76436-110">總大小必須小於64K。</span><span class="sxs-lookup"><span data-stu-id="76436-110">The total size must be less than 64K.</span></span>

<a name="return-value"></a><span data-ttu-id="76436-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="76436-111">Return value</span></span>
------------

<span data-ttu-id="76436-112">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="76436-112">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="76436-113">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="76436-113">If the function fails, the return value is zero.</span></span> <span data-ttu-id="76436-114">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="76436-114">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="76436-115">備註</span><span class="sxs-lookup"><span data-stu-id="76436-115">Remarks</span></span>
-------

<span data-ttu-id="76436-116">當進程結束時，系統會還原原始的主控台標題。</span><span class="sxs-lookup"><span data-stu-id="76436-116">When the process terminates, the system restores the original console title.</span></span>

<span data-ttu-id="76436-117">此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。</span><span class="sxs-lookup"><span data-stu-id="76436-117">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="76436-118">主控台的字碼頁一開始預設為系統的 OEM 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="76436-118">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="76436-119">若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 或 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函式，或使用 **chcp** 或 **mode con cp select =** 命令。</span><span class="sxs-lookup"><span data-stu-id="76436-119">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="examples"></a><span data-ttu-id="76436-120">範例</span><span class="sxs-lookup"><span data-stu-id="76436-120">Examples</span></span>
--------

<span data-ttu-id="76436-121">下列範例示範如何取出和修改主控台標題。</span><span class="sxs-lookup"><span data-stu-id="76436-121">The following example shows how to retrieve and modify the console title.</span></span>

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

<a name="requirements"></a><span data-ttu-id="76436-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="76436-122">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="76436-123">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="76436-123">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="76436-124">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="76436-124">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="76436-125">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="76436-125">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="76436-126">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="76436-126">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="76436-127">標頭</span><span class="sxs-lookup"><span data-stu-id="76436-127">Header</span></span></p></td>
<td><span data-ttu-id="76436-128">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="76436-128">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="76436-129">程式庫</span><span class="sxs-lookup"><span data-stu-id="76436-129">Library</span></span></p></td>
<td><span data-ttu-id="76436-130">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="76436-130">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="76436-131">DLL</span><span class="sxs-lookup"><span data-stu-id="76436-131">DLL</span></span></p></td>
<td><span data-ttu-id="76436-132">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="76436-132">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="76436-133">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="76436-133">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="76436-134"><strong>SetConsoleTitleW</strong> (Unicode) 和 <strong>SetConsoleTitleA</strong> (ANSI) </span><span class="sxs-lookup"><span data-stu-id="76436-134"><strong>SetConsoleTitleW</strong> (Unicode) and <strong>SetConsoleTitleA</strong> (ANSI)</span></span></p></td>
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="76436-135"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="76436-135"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="76436-136">主控台功能</span><span class="sxs-lookup"><span data-stu-id="76436-136">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="76436-137">**GetConsoleOriginalTitle**</span><span class="sxs-lookup"><span data-stu-id="76436-137">**GetConsoleOriginalTitle**</span></span>](getconsoleoriginaltitle.md)

[<span data-ttu-id="76436-138">**GetConsoleTitle**</span><span class="sxs-lookup"><span data-stu-id="76436-138">**GetConsoleTitle**</span></span>](getconsoletitle.md)

[<span data-ttu-id="76436-139">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="76436-139">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="76436-140">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="76436-140">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

 

 





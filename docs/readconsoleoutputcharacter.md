---
title: ReadConsoleOutputCharacter 函式
description: 從主控台螢幕緩衝區的連續資料格複製一些字元，從指定的位置開始。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/ReadConsoleOutputCharacter
- wincon/ReadConsoleOutputCharacter
- ReadConsoleOutputCharacter
- consoleapi2/ReadConsoleOutputCharacterA
- wincon/ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterA
- consoleapi2/ReadConsoleOutputCharacterW
- wincon/ReadConsoleOutputCharacterW
- ReadConsoleOutputCharacterW
MS-HAID:
- '\_win32\_readconsoleoutputcharacter'
- base.readconsoleoutputcharacter
- consoles.readconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: f47464a9-6c59-4f15-abd0-be29ab515698
topic_type:
- apiref
api_name:
- ReadConsoleOutputCharacter
- ReadConsoleOutputCharacterA
- ReadConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 8f761d10951e6df77a54fd075c29379657204a99
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059451"
---
# <a name="readconsoleoutputcharacter-function"></a><span data-ttu-id="459a5-104">ReadConsoleOutputCharacter 函式</span><span class="sxs-lookup"><span data-stu-id="459a5-104">ReadConsoleOutputCharacter function</span></span>


<span data-ttu-id="459a5-105">從主控台螢幕緩衝區的連續資料格複製一些字元，從指定的位置開始。</span><span class="sxs-lookup"><span data-stu-id="459a5-105">Copies a number of characters from consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="459a5-106">語法</span><span class="sxs-lookup"><span data-stu-id="459a5-106">Syntax</span></span>
------

```C
BOOL WINAPI ReadConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _Out_ LPTSTR  lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwReadCoord,
  _Out_ LPDWORD lpNumberOfCharsRead
);
```

<a name="parameters"></a><span data-ttu-id="459a5-107">參數</span><span class="sxs-lookup"><span data-stu-id="459a5-107">Parameters</span></span>
----------

<span data-ttu-id="459a5-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="459a5-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="459a5-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="459a5-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="459a5-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="459a5-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="459a5-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="459a5-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="459a5-112">*lpCharacter* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="459a5-112">*lpCharacter* \[out\]</span></span>  
<span data-ttu-id="459a5-113">緩衝區的指標，此緩衝區會接收從主控台螢幕緩衝區讀取的字元。</span><span class="sxs-lookup"><span data-stu-id="459a5-113">A pointer to a buffer that receives the characters read from the console screen buffer.</span></span>

<span data-ttu-id="459a5-114">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="459a5-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="459a5-115">要從中讀取的螢幕緩衝區字元儲存格數目。</span><span class="sxs-lookup"><span data-stu-id="459a5-115">The number of screen buffer character cells from which to read.</span></span> <span data-ttu-id="459a5-116">*LpCharacter*參數所指向的緩衝區大小應該是 `nLength * sizeof(TCHAR)` 。</span><span class="sxs-lookup"><span data-stu-id="459a5-116">The size of the buffer pointed to by the *lpCharacter* parameter should be `nLength * sizeof(TCHAR)`.</span></span>

<span data-ttu-id="459a5-117">*dwReadCoord* \[在\]</span><span class="sxs-lookup"><span data-stu-id="459a5-117">*dwReadCoord* \[in\]</span></span>  
<span data-ttu-id="459a5-118">要從中讀取的主控台螢幕緩衝區中第一個資料格的座標（以字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="459a5-118">The coordinates of the first cell in the console screen buffer from which to read, in characters.</span></span> <span data-ttu-id="459a5-119">[**COORD**](coord-str.md)結構的**X**成員是資料行，而**Y**成員是資料列。</span><span class="sxs-lookup"><span data-stu-id="459a5-119">The **X** member of the [**COORD**](coord-str.md) structure is the column, and the **Y** member is the row.</span></span>

<span data-ttu-id="459a5-120">*lpNumberOfCharsRead* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="459a5-120">*lpNumberOfCharsRead* \[out\]</span></span>  
<span data-ttu-id="459a5-121">變數的指標，此變數會接收實際讀取的字元數。</span><span class="sxs-lookup"><span data-stu-id="459a5-121">A pointer to a variable that receives the number of characters actually read.</span></span>

<a name="return-value"></a><span data-ttu-id="459a5-122">傳回值</span><span class="sxs-lookup"><span data-stu-id="459a5-122">Return value</span></span>
------------

<span data-ttu-id="459a5-123">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="459a5-123">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="459a5-124">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="459a5-124">If the function fails, the return value is zero.</span></span> <span data-ttu-id="459a5-125">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="459a5-125">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="459a5-126">備註</span><span class="sxs-lookup"><span data-stu-id="459a5-126">Remarks</span></span>
-------

<span data-ttu-id="459a5-127">如果要讀取的字元數超出指定螢幕緩衝區資料列的結尾，則會從下一個資料列讀取字元。</span><span class="sxs-lookup"><span data-stu-id="459a5-127">If the number of characters to be read from extends beyond the end of the specified screen buffer row, characters are read from the next row.</span></span> <span data-ttu-id="459a5-128">如果要讀取的字元數超過主控台螢幕緩衝區的結尾，則會讀取主控台螢幕緩衝區結尾的字元。</span><span class="sxs-lookup"><span data-stu-id="459a5-128">If the number of characters to be read from extends beyond the end of the console screen buffer, characters up to the end of the console screen buffer are read.</span></span>

<span data-ttu-id="459a5-129">此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。</span><span class="sxs-lookup"><span data-stu-id="459a5-129">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="459a5-130">主控台的字碼頁一開始預設為系統的 OEM 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="459a5-130">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="459a5-131">若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 或 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函式，或使用 **chcp** 或 **mode con cp select =** 命令。</span><span class="sxs-lookup"><span data-stu-id="459a5-131">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="459a5-132">規格需求</span><span class="sxs-lookup"><span data-stu-id="459a5-132">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="459a5-133">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="459a5-133">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="459a5-134">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="459a5-134">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="459a5-135">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="459a5-135">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="459a5-136">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="459a5-136">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="459a5-137">標頭</span><span class="sxs-lookup"><span data-stu-id="459a5-137">Header</span></span></p></td>
<td><span data-ttu-id="459a5-138">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="459a5-138">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="459a5-139">程式庫</span><span class="sxs-lookup"><span data-stu-id="459a5-139">Library</span></span></p></td>
<td><span data-ttu-id="459a5-140">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="459a5-140">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="459a5-141">DLL</span><span class="sxs-lookup"><span data-stu-id="459a5-141">DLL</span></span></p></td>
<td><span data-ttu-id="459a5-142">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="459a5-142">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="459a5-143">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="459a5-143">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="459a5-144"><strong>ReadConsoleOutputCharacterW</strong> (Unicode) 和 <strong>ReadConsoleOutputCharacterA</strong> (ANSI) </span><span class="sxs-lookup"><span data-stu-id="459a5-144"><strong>ReadConsoleOutputCharacterW</strong> (Unicode) and <strong>ReadConsoleOutputCharacterA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="459a5-145"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="459a5-145"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="459a5-146">主控台功能</span><span class="sxs-lookup"><span data-stu-id="459a5-146">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="459a5-147">**COORD**</span><span class="sxs-lookup"><span data-stu-id="459a5-147">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="459a5-148">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="459a5-148">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="459a5-149">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="459a5-149">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="459a5-150">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="459a5-150">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="459a5-151">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="459a5-151">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="459a5-152">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="459a5-152">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="459a5-153">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="459a5-153">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="459a5-154">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="459a5-154">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

[<span data-ttu-id="459a5-155">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="459a5-155">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 





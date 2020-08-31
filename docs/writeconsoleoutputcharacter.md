---
title: WriteConsoleOutputCharacter 函式
description: 從指定的位置開始，將數個字元複製到主控台螢幕緩衝區的連續儲存格。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/WriteConsoleOutputCharacter
- wincon/WriteConsoleOutputCharacter
- WriteConsoleOutputCharacter
- consoleapi2/WriteConsoleOutputCharacterA
- wincon/WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterA
- consoleapi2/WriteConsoleOutputCharacterW
- wincon/WriteConsoleOutputCharacterW
- WriteConsoleOutputCharacterW
MS-HAID:
- '\_win32\_writeconsoleoutputcharacter'
- base.writeconsoleoutputcharacter
- consoles.writeconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 7cc935ea-6b19-4494-b746-259aa7aaa9cc
topic_type:
- apiref
api_name:
- WriteConsoleOutputCharacter
- WriteConsoleOutputCharacterA
- WriteConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: bc313abbcb28016968355cc405e0cc2de3d36cb0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059506"
---
# <a name="writeconsoleoutputcharacter-function"></a><span data-ttu-id="68dec-104">WriteConsoleOutputCharacter 函式</span><span class="sxs-lookup"><span data-stu-id="68dec-104">WriteConsoleOutputCharacter function</span></span>


<span data-ttu-id="68dec-105">從指定的位置開始，將數個字元複製到主控台螢幕緩衝區的連續儲存格。</span><span class="sxs-lookup"><span data-stu-id="68dec-105">Copies a number of characters to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="68dec-106">語法</span><span class="sxs-lookup"><span data-stu-id="68dec-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  LPCTSTR lpCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

<a name="parameters"></a><span data-ttu-id="68dec-107">參數</span><span class="sxs-lookup"><span data-stu-id="68dec-107">Parameters</span></span>
----------

<span data-ttu-id="68dec-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="68dec-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="68dec-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="68dec-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="68dec-110">控制碼必須有 **一般 \_ 寫入** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="68dec-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="68dec-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="68dec-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="68dec-112">*lpCharacter* \[在\]</span><span class="sxs-lookup"><span data-stu-id="68dec-112">*lpCharacter* \[in\]</span></span>  
<span data-ttu-id="68dec-113">要寫入主控台螢幕緩衝區的字元。</span><span class="sxs-lookup"><span data-stu-id="68dec-113">The characters to be written to the console screen buffer.</span></span>

<span data-ttu-id="68dec-114">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="68dec-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="68dec-115">要寫入的字元數。</span><span class="sxs-lookup"><span data-stu-id="68dec-115">The number of characters to be written.</span></span>

<span data-ttu-id="68dec-116">*dwWriteCoord* \[在\]</span><span class="sxs-lookup"><span data-stu-id="68dec-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="68dec-117">[**COORD**](coord-str.md)結構，指定要在其中寫入字元的主控台螢幕緩衝區中第一個資料格的字元座標。</span><span class="sxs-lookup"><span data-stu-id="68dec-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which characters will be written.</span></span>

<span data-ttu-id="68dec-118">*lpNumberOfCharsWritten* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="68dec-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="68dec-119">變數的指標，此變數會接收實際寫入的字元數。</span><span class="sxs-lookup"><span data-stu-id="68dec-119">A pointer to a variable that receives the number of characters actually written.</span></span>

<a name="return-value"></a><span data-ttu-id="68dec-120">傳回值</span><span class="sxs-lookup"><span data-stu-id="68dec-120">Return value</span></span>
------------

<span data-ttu-id="68dec-121">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="68dec-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="68dec-122">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="68dec-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="68dec-123">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="68dec-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="68dec-124">備註</span><span class="sxs-lookup"><span data-stu-id="68dec-124">Remarks</span></span>
-------

<span data-ttu-id="68dec-125">如果要寫入的字元數超出主控台螢幕緩衝區中指定之資料列的結尾，則會將字元寫入至下一個資料列。</span><span class="sxs-lookup"><span data-stu-id="68dec-125">If the number of characters to be written to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="68dec-126">如果要寫入的字元數超過主控台螢幕緩衝區的結尾，則字元會寫入至主控台畫面緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="68dec-126">If the number of characters to be written to extends beyond the end of the console screen buffer, characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="68dec-127">在寫入至的位置上的屬性值不會變更。</span><span class="sxs-lookup"><span data-stu-id="68dec-127">The attribute values at the positions written to are not changed.</span></span>

<span data-ttu-id="68dec-128">此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。</span><span class="sxs-lookup"><span data-stu-id="68dec-128">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="68dec-129">主控台的字碼頁一開始預設為系統的 OEM 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="68dec-129">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="68dec-130">若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 或 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函式，或使用 **chcp** 或 **mode con cp select =** 命令。</span><span class="sxs-lookup"><span data-stu-id="68dec-130">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="68dec-131">規格需求</span><span class="sxs-lookup"><span data-stu-id="68dec-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="68dec-132">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="68dec-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="68dec-133">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="68dec-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="68dec-134">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="68dec-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="68dec-135">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="68dec-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="68dec-136">標頭</span><span class="sxs-lookup"><span data-stu-id="68dec-136">Header</span></span></p></td>
<td><span data-ttu-id="68dec-137">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="68dec-137">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="68dec-138">程式庫</span><span class="sxs-lookup"><span data-stu-id="68dec-138">Library</span></span></p></td>
<td><span data-ttu-id="68dec-139">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="68dec-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="68dec-140">DLL</span><span class="sxs-lookup"><span data-stu-id="68dec-140">DLL</span></span></p></td>
<td><span data-ttu-id="68dec-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="68dec-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="68dec-142">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="68dec-142">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="68dec-143"><strong>WriteConsoleOutputCharacterW</strong> (Unicode) 和 <strong>WriteConsoleOutputCharacterA</strong> (ANSI) </span><span class="sxs-lookup"><span data-stu-id="68dec-143"><strong>WriteConsoleOutputCharacterW</strong> (Unicode) and <strong>WriteConsoleOutputCharacterA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="68dec-144"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="68dec-144"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="68dec-145">主控台功能</span><span class="sxs-lookup"><span data-stu-id="68dec-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="68dec-146">**COORD**</span><span class="sxs-lookup"><span data-stu-id="68dec-146">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="68dec-147">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="68dec-147">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="68dec-148">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="68dec-148">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="68dec-149">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="68dec-149">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="68dec-150">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="68dec-150">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="68dec-151">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="68dec-151">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="68dec-152">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="68dec-152">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="68dec-153">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="68dec-153">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="68dec-154">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="68dec-154">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

 

 





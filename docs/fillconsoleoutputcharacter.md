---
title: FillConsoleOutputCharacter 函式
description: 從指定的座標開始，將字元從主控台螢幕緩衝區寫入指定的次數。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/FillConsoleOutputCharacter
- wincon/FillConsoleOutputCharacter
- FillConsoleOutputCharacter
- consoleapi2/FillConsoleOutputCharacterA
- wincon/FillConsoleOutputCharacterA
- FillConsoleOutputCharacterA
- consoleapi2/FillConsoleOutputCharacterW
- wincon/FillConsoleOutputCharacterW
- FillConsoleOutputCharacterW
MS-HAID:
- '\_win32\_fillconsoleoutputcharacter'
- base.fillconsoleoutputcharacter
- consoles.fillconsoleoutputcharacter
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 37579cc9-14b3-4fd9-81ed-abaad5c7bd1a
topic_type:
- apiref
api_name:
- FillConsoleOutputCharacter
- FillConsoleOutputCharacterA
- FillConsoleOutputCharacterW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: d11e0ef196f9923f1478e17faacd41b43a0511eb
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059211"
---
# <a name="fillconsoleoutputcharacter-function"></a><span data-ttu-id="d6bb3-104">FillConsoleOutputCharacter 函式</span><span class="sxs-lookup"><span data-stu-id="d6bb3-104">FillConsoleOutputCharacter function</span></span>


<span data-ttu-id="d6bb3-105">從指定的座標開始，將字元從主控台螢幕緩衝區寫入指定的次數。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-105">Writes a character to the console screen buffer a specified number of times, beginning at the specified coordinates.</span></span>

<a name="syntax"></a><span data-ttu-id="d6bb3-106">語法</span><span class="sxs-lookup"><span data-stu-id="d6bb3-106">Syntax</span></span>
------

```C
BOOL WINAPI FillConsoleOutputCharacter(
  _In_  HANDLE  hConsoleOutput,
  _In_  TCHAR   cCharacter,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfCharsWritten
);
```

<a name="parameters"></a><span data-ttu-id="d6bb3-107">參數</span><span class="sxs-lookup"><span data-stu-id="d6bb3-107">Parameters</span></span>
----------

<span data-ttu-id="d6bb3-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="d6bb3-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="d6bb3-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="d6bb3-110">控制碼必須有 **一般 \_ 寫入** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="d6bb3-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="d6bb3-112">*cCharacter* \[在\]</span><span class="sxs-lookup"><span data-stu-id="d6bb3-112">*cCharacter* \[in\]</span></span>  
<span data-ttu-id="d6bb3-113">要寫入主控台螢幕緩衝區的字元。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-113">The character to be written to the console screen buffer.</span></span>

<span data-ttu-id="d6bb3-114">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="d6bb3-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="d6bb3-115">應寫入字元的字元儲存格數目。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-115">The number of character cells to which the character should be written.</span></span>

<span data-ttu-id="d6bb3-116">*dwWriteCoord* \[在\]</span><span class="sxs-lookup"><span data-stu-id="d6bb3-116">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="d6bb3-117">[**COORD**](coord-str.md)結構，指定要寫入字元的第一個資料格的字元座標。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-117">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell to which the character is to be written.</span></span>

<span data-ttu-id="d6bb3-118">*lpNumberOfCharsWritten* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="d6bb3-118">*lpNumberOfCharsWritten* \[out\]</span></span>  
<span data-ttu-id="d6bb3-119">變數的指標，此變數會接收實際寫入主控台螢幕緩衝區的字元數。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-119">A pointer to a variable that receives the number of characters actually written to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="d6bb3-120">傳回值</span><span class="sxs-lookup"><span data-stu-id="d6bb3-120">Return value</span></span>
------------

<span data-ttu-id="d6bb3-121">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-121">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="d6bb3-122">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-122">If the function fails, the return value is zero.</span></span> <span data-ttu-id="d6bb3-123">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-123">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="d6bb3-124">備註</span><span class="sxs-lookup"><span data-stu-id="d6bb3-124">Remarks</span></span>
-------

<span data-ttu-id="d6bb3-125">如果要寫入的字元數超出主控台螢幕緩衝區中指定之資料列的結尾，則會將字元寫入至下一個資料列。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-125">If the number of characters to write to extends beyond the end of the specified row in the console screen buffer, characters are written to the next row.</span></span> <span data-ttu-id="d6bb3-126">如果要寫入的字元數超過主控台螢幕緩衝區的結尾，則字元會寫入至主控台畫面緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-126">If the number of characters to write to extends beyond the end of the console screen buffer, the characters are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="d6bb3-127">在寫入位置的屬性值不會變更。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-127">The attribute values at the positions written are not changed.</span></span>

<span data-ttu-id="d6bb3-128">此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-128">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="d6bb3-129">主控台的字碼頁一開始預設為系統的 OEM 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-129">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="d6bb3-130">若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 或 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函式，或使用 **chcp** 或 **mode con cp select =** 命令。</span><span class="sxs-lookup"><span data-stu-id="d6bb3-130">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="d6bb3-131">規格需求</span><span class="sxs-lookup"><span data-stu-id="d6bb3-131">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="d6bb3-132">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="d6bb3-132">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="d6bb3-133">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="d6bb3-133">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d6bb3-134">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="d6bb3-134">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="d6bb3-135">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="d6bb3-135">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d6bb3-136">標頭</span><span class="sxs-lookup"><span data-stu-id="d6bb3-136">Header</span></span></p></td>
<td><span data-ttu-id="d6bb3-137">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="d6bb3-137">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d6bb3-138">程式庫</span><span class="sxs-lookup"><span data-stu-id="d6bb3-138">Library</span></span></p></td>
<td><span data-ttu-id="d6bb3-139">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="d6bb3-139">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="d6bb3-140">DLL</span><span class="sxs-lookup"><span data-stu-id="d6bb3-140">DLL</span></span></p></td>
<td><span data-ttu-id="d6bb3-141">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="d6bb3-141">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="d6bb3-142">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="d6bb3-142">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="d6bb3-143"><strong>FillConsoleOutputCharacterW</strong> (Unicode) 和 <strong>FillConsoleOutputCharacterA</strong> (ANSI) </span><span class="sxs-lookup"><span data-stu-id="d6bb3-143"><strong>FillConsoleOutputCharacterW</strong> (Unicode) and <strong>FillConsoleOutputCharacterA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="d6bb3-144"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6bb3-144"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="d6bb3-145">主控台功能</span><span class="sxs-lookup"><span data-stu-id="d6bb3-145">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="d6bb3-146">**COORD**</span><span class="sxs-lookup"><span data-stu-id="d6bb3-146">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="d6bb3-147">**FillConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="d6bb3-147">**FillConsoleOutputAttribute**</span></span>](fillconsoleoutputattribute.md)

[<span data-ttu-id="d6bb3-148">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="d6bb3-148">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="d6bb3-149">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="d6bb3-149">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="d6bb3-150">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="d6bb3-150">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="d6bb3-151">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="d6bb3-151">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 





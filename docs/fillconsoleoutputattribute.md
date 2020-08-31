---
title: FillConsoleOutputAttribute 函式
description: 針對指定的字元資料格數目，設定從螢幕緩衝區中的指定座標開始的字元屬性。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/FillConsoleOutputAttribute
- wincon/FillConsoleOutputAttribute
- FillConsoleOutputAttribute
MS-HAID:
- '\_win32\_fillconsoleoutputattribute'
- base.fillconsoleoutputattribute
- consoles.fillconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 09440263-71c4-4b7a-8fc6-a2b4fcd677ff
topic_type:
- apiref
api_name:
- FillConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 4b3df3a9922655835979136a33628e2be0663f4e
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059210"
---
# <a name="fillconsoleoutputattribute-function"></a><span data-ttu-id="7c59f-104">FillConsoleOutputAttribute 函式</span><span class="sxs-lookup"><span data-stu-id="7c59f-104">FillConsoleOutputAttribute function</span></span>


<span data-ttu-id="7c59f-105">針對指定的字元資料格數目，設定從螢幕緩衝區中的指定座標開始的字元屬性。</span><span class="sxs-lookup"><span data-stu-id="7c59f-105">Sets the character attributes for a specified number of character cells, beginning at the specified coordinates in a screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="7c59f-106">語法</span><span class="sxs-lookup"><span data-stu-id="7c59f-106">Syntax</span></span>
------

```C
BOOL WINAPI FillConsoleOutputAttribute(
  _In_  HANDLE  hConsoleOutput,
  _In_  WORD    wAttribute,
  _In_  DWORD   nLength,
  _In_  COORD   dwWriteCoord,
  _Out_ LPDWORD lpNumberOfAttrsWritten
);
```

<a name="parameters"></a><span data-ttu-id="7c59f-107">參數</span><span class="sxs-lookup"><span data-stu-id="7c59f-107">Parameters</span></span>
----------

<span data-ttu-id="7c59f-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="7c59f-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="7c59f-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="7c59f-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="7c59f-110">控制碼必須有 **一般 \_ 寫入** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="7c59f-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="7c59f-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="7c59f-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="7c59f-112">*wAttribute* \[在\]</span><span class="sxs-lookup"><span data-stu-id="7c59f-112">*wAttribute* \[in\]</span></span>  
<span data-ttu-id="7c59f-113">寫入主控台螢幕緩衝區時要使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="7c59f-113">The attributes to use when writing to the console screen buffer.</span></span> <span data-ttu-id="7c59f-114">如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#_win32_font_attributes)。</span><span class="sxs-lookup"><span data-stu-id="7c59f-114">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="7c59f-115">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="7c59f-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="7c59f-116">要設定為指定之色彩屬性的字元儲存格數目。</span><span class="sxs-lookup"><span data-stu-id="7c59f-116">The number of character cells to be set to the specified color attributes.</span></span>

<span data-ttu-id="7c59f-117">*dwWriteCoord* \[在\]</span><span class="sxs-lookup"><span data-stu-id="7c59f-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="7c59f-118">[**COORD**](coord-str.md)結構，指定要設定其屬性的第一個資料格的字元座標。</span><span class="sxs-lookup"><span data-stu-id="7c59f-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell whose attributes are to be set.</span></span>

<span data-ttu-id="7c59f-119">*lpNumberOfAttrsWritten* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="7c59f-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="7c59f-120">變數的指標，此變數會接收實際設定其屬性的字元儲存格數目。</span><span class="sxs-lookup"><span data-stu-id="7c59f-120">A pointer to a variable that receives the number of character cells whose attributes were actually set.</span></span>

<a name="return-value"></a><span data-ttu-id="7c59f-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="7c59f-121">Return value</span></span>
------------

<span data-ttu-id="7c59f-122">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="7c59f-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="7c59f-123">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="7c59f-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="7c59f-124">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="7c59f-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="7c59f-125">備註</span><span class="sxs-lookup"><span data-stu-id="7c59f-125">Remarks</span></span>
-------

<span data-ttu-id="7c59f-126">如果要設定屬性的字元資料格數目延伸超過主控台螢幕緩衝區中指定之資料列的結尾，則會設定下一個資料列的資料格。</span><span class="sxs-lookup"><span data-stu-id="7c59f-126">If the number of character cells whose attributes are to be set extends beyond the end of the specified row in the console screen buffer, the cells of the next row are set.</span></span> <span data-ttu-id="7c59f-127">如果要寫入的資料格數目延伸超過主控台螢幕緩衝區的結尾，則資料格會寫入至主控台畫面緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="7c59f-127">If the number of cells to write to extends beyond the end of the console screen buffer, the cells are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="7c59f-128">寫入至的位置的字元值不會變更。</span><span class="sxs-lookup"><span data-stu-id="7c59f-128">The character values at the positions written to are not changed.</span></span>

<a name="requirements"></a><span data-ttu-id="7c59f-129">規格需求</span><span class="sxs-lookup"><span data-stu-id="7c59f-129">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="7c59f-130">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="7c59f-130">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="7c59f-131">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="7c59f-131">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7c59f-132">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="7c59f-132">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="7c59f-133">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="7c59f-133">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7c59f-134">標頭</span><span class="sxs-lookup"><span data-stu-id="7c59f-134">Header</span></span></p></td>
<td><span data-ttu-id="7c59f-135">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="7c59f-135">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="7c59f-136">程式庫</span><span class="sxs-lookup"><span data-stu-id="7c59f-136">Library</span></span></p></td>
<td><span data-ttu-id="7c59f-137">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="7c59f-137">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="7c59f-138">DLL</span><span class="sxs-lookup"><span data-stu-id="7c59f-138">DLL</span></span></p></td>
<td><span data-ttu-id="7c59f-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="7c59f-139">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="7c59f-140"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c59f-140"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="7c59f-141">主控台功能</span><span class="sxs-lookup"><span data-stu-id="7c59f-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="7c59f-142">**COORD**</span><span class="sxs-lookup"><span data-stu-id="7c59f-142">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="7c59f-143">**FillConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="7c59f-143">**FillConsoleOutputCharacter**</span></span>](fillconsoleoutputcharacter.md)

[<span data-ttu-id="7c59f-144">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="7c59f-144">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="7c59f-145">**SetConsoleTextAttribute**</span><span class="sxs-lookup"><span data-stu-id="7c59f-145">**SetConsoleTextAttribute**</span></span>](setconsoletextattribute.md)

[<span data-ttu-id="7c59f-146">**WriteConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="7c59f-146">**WriteConsoleOutputAttribute**</span></span>](writeconsoleoutputattribute.md)

 

 





---
title: WriteConsoleOutputAttribute 函式
description: 從指定的位置開始，將數個字元屬性複製到主控台螢幕緩衝區的連續儲存格。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/WriteConsoleOutputAttribute
- wincon/WriteConsoleOutputAttribute
- WriteConsoleOutputAttribute
MS-HAID:
- '\_win32\_writeconsoleoutputattribute'
- base.writeconsoleoutputattribute
- consoles.writeconsoleoutputattribute
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 52a9d6e5-072e-4411-9945-10bd3dd61e25
topic_type:
- apiref
api_name:
- WriteConsoleOutputAttribute
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: e7c684b2f450713eaa78730676a0148e9b090c79
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059510"
---
# <a name="writeconsoleoutputattribute-function"></a><span data-ttu-id="a1e81-104">WriteConsoleOutputAttribute 函式</span><span class="sxs-lookup"><span data-stu-id="a1e81-104">WriteConsoleOutputAttribute function</span></span>


<span data-ttu-id="a1e81-105">從指定的位置開始，將數個字元屬性複製到主控台螢幕緩衝區的連續儲存格。</span><span class="sxs-lookup"><span data-stu-id="a1e81-105">Copies a number of character attributes to consecutive cells of a console screen buffer, beginning at a specified location.</span></span>

<a name="syntax"></a><span data-ttu-id="a1e81-106">語法</span><span class="sxs-lookup"><span data-stu-id="a1e81-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleOutputAttribute(
  _In_        HANDLE  hConsoleOutput,
  _In_  const WORD    *lpAttribute,
  _In_        DWORD   nLength,
  _In_        COORD   dwWriteCoord,
  _Out_       LPDWORD lpNumberOfAttrsWritten
);
```

<a name="parameters"></a><span data-ttu-id="a1e81-107">參數</span><span class="sxs-lookup"><span data-stu-id="a1e81-107">Parameters</span></span>
----------

<span data-ttu-id="a1e81-108">*hConsoleOutput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="a1e81-108">*hConsoleOutput* \[in\]</span></span>  
<span data-ttu-id="a1e81-109">主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="a1e81-109">A handle to the console screen buffer.</span></span> <span data-ttu-id="a1e81-110">控制碼必須有 **一般 \_ 寫入** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="a1e81-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="a1e81-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="a1e81-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="a1e81-112">*lpAttribute* \[在\]</span><span class="sxs-lookup"><span data-stu-id="a1e81-112">*lpAttribute* \[in\]</span></span>  
<span data-ttu-id="a1e81-113">要在寫入主控台螢幕緩衝區時使用的屬性。</span><span class="sxs-lookup"><span data-stu-id="a1e81-113">The attributes to be used when writing to the console screen buffer.</span></span> <span data-ttu-id="a1e81-114">如需詳細資訊，請參閱 [字元屬性](console-screen-buffers.md#_win32_font_attributes)。</span><span class="sxs-lookup"><span data-stu-id="a1e81-114">For more information, see [Character Attributes](console-screen-buffers.md#_win32_font_attributes).</span></span>

<span data-ttu-id="a1e81-115">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="a1e81-115">*nLength* \[in\]</span></span>  
<span data-ttu-id="a1e81-116">要將屬性複製到其中的螢幕緩衝區字元儲存格數目。</span><span class="sxs-lookup"><span data-stu-id="a1e81-116">The number of screen buffer character cells to which the attributes will be copied.</span></span>

<span data-ttu-id="a1e81-117">*dwWriteCoord* \[在\]</span><span class="sxs-lookup"><span data-stu-id="a1e81-117">*dwWriteCoord* \[in\]</span></span>  
<span data-ttu-id="a1e81-118">[**COORD**](coord-str.md)結構，指定要將屬性寫入其中的主控台螢幕緩衝區中第一個資料格的字元座標。</span><span class="sxs-lookup"><span data-stu-id="a1e81-118">A [**COORD**](coord-str.md) structure that specifies the character coordinates of the first cell in the console screen buffer to which the attributes will be written.</span></span>

<span data-ttu-id="a1e81-119">*lpNumberOfAttrsWritten* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="a1e81-119">*lpNumberOfAttrsWritten* \[out\]</span></span>  
<span data-ttu-id="a1e81-120">變數的指標，此變數會接收實際寫入主控台螢幕緩衝區的屬性數目。</span><span class="sxs-lookup"><span data-stu-id="a1e81-120">A pointer to a variable that receives the number of attributes actually written to the console screen buffer.</span></span>

<a name="return-value"></a><span data-ttu-id="a1e81-121">傳回值</span><span class="sxs-lookup"><span data-stu-id="a1e81-121">Return value</span></span>
------------

<span data-ttu-id="a1e81-122">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="a1e81-122">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="a1e81-123">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="a1e81-123">If the function fails, the return value is zero.</span></span> <span data-ttu-id="a1e81-124">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="a1e81-124">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="a1e81-125">備註</span><span class="sxs-lookup"><span data-stu-id="a1e81-125">Remarks</span></span>
-------

<span data-ttu-id="a1e81-126">如果要寫入的屬性數目超過主控台螢幕緩衝區中指定之資料列的結尾，則會將屬性寫入至下一個資料列。</span><span class="sxs-lookup"><span data-stu-id="a1e81-126">If the number of attributes to be written to extends beyond the end of the specified row in the console screen buffer, attributes are written to the next row.</span></span> <span data-ttu-id="a1e81-127">如果要寫入的屬性數目超過主控台螢幕緩衝區的結尾，則會將屬性寫入至主控台畫面緩衝區的結尾。</span><span class="sxs-lookup"><span data-stu-id="a1e81-127">If the number of attributes to be written to extends beyond the end of the console screen buffer, the attributes are written up to the end of the console screen buffer.</span></span>

<span data-ttu-id="a1e81-128">寫入至的位置的字元值不會變更。</span><span class="sxs-lookup"><span data-stu-id="a1e81-128">The character values at the positions written to are not changed.</span></span>

<a name="requirements"></a><span data-ttu-id="a1e81-129">規格需求</span><span class="sxs-lookup"><span data-stu-id="a1e81-129">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="a1e81-130">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="a1e81-130">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="a1e81-131">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="a1e81-131">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a1e81-132">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="a1e81-132">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="a1e81-133">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="a1e81-133">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a1e81-134">標頭</span><span class="sxs-lookup"><span data-stu-id="a1e81-134">Header</span></span></p></td>
<td><span data-ttu-id="a1e81-135">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="a1e81-135">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="a1e81-136">程式庫</span><span class="sxs-lookup"><span data-stu-id="a1e81-136">Library</span></span></p></td>
<td><span data-ttu-id="a1e81-137">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="a1e81-137">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="a1e81-138">DLL</span><span class="sxs-lookup"><span data-stu-id="a1e81-138">DLL</span></span></p></td>
<td><span data-ttu-id="a1e81-139">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="a1e81-139">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="a1e81-140"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1e81-140"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="a1e81-141">主控台功能</span><span class="sxs-lookup"><span data-stu-id="a1e81-141">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="a1e81-142">**COORD**</span><span class="sxs-lookup"><span data-stu-id="a1e81-142">**COORD**</span></span>](coord-str.md)

[<span data-ttu-id="a1e81-143">低層級主控台輸出功能</span><span class="sxs-lookup"><span data-stu-id="a1e81-143">Low-Level Console Output Functions</span></span>](low-level-console-output-functions.md)

[<span data-ttu-id="a1e81-144">**ReadConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="a1e81-144">**ReadConsoleOutput**</span></span>](readconsoleoutput.md)

[<span data-ttu-id="a1e81-145">**ReadConsoleOutputAttribute**</span><span class="sxs-lookup"><span data-stu-id="a1e81-145">**ReadConsoleOutputAttribute**</span></span>](readconsoleoutputattribute.md)

[<span data-ttu-id="a1e81-146">**ReadConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="a1e81-146">**ReadConsoleOutputCharacter**</span></span>](readconsoleoutputcharacter.md)

[<span data-ttu-id="a1e81-147">**WriteConsoleOutput**</span><span class="sxs-lookup"><span data-stu-id="a1e81-147">**WriteConsoleOutput**</span></span>](writeconsoleoutput.md)

[<span data-ttu-id="a1e81-148">**WriteConsoleOutputCharacter**</span><span class="sxs-lookup"><span data-stu-id="a1e81-148">**WriteConsoleOutputCharacter**</span></span>](writeconsoleoutputcharacter.md)

 

 





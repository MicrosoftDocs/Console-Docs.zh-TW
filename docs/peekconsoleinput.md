---
title: PeekConsoleInput 函式
description: 從指定的主控台輸入緩衝區讀取資料，而不將它從緩衝區中移除。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi/PeekConsoleInput
- wincon/PeekConsoleInput
- PeekConsoleInput
- consoleapi/PeekConsoleInputA
- wincon/PeekConsoleInputA
- PeekConsoleInputA
- consoleapi/PeekConsoleInputW
- wincon/PeekConsoleInputW
- PeekConsoleInputW
MS-HAID:
- '\_win32\_peekconsoleinput'
- base.peekconsoleinput
- consoles.peekconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 9982dc20-43bd-4ee3-a68d-157c9134daca
topic_type:
- apiref
api_name:
- PeekConsoleInput
- PeekConsoleInputA
- PeekConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: c74df91f3b70827cd0c5410d01b2a165694909f9
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059059"
---
# <a name="peekconsoleinput-function"></a><span data-ttu-id="f11ce-104">PeekConsoleInput 函式</span><span class="sxs-lookup"><span data-stu-id="f11ce-104">PeekConsoleInput function</span></span>


<span data-ttu-id="f11ce-105">從指定的主控台輸入緩衝區讀取資料，而不將它從緩衝區中移除。</span><span class="sxs-lookup"><span data-stu-id="f11ce-105">Reads data from the specified console input buffer without removing it from the buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="f11ce-106">語法</span><span class="sxs-lookup"><span data-stu-id="f11ce-106">Syntax</span></span>
------

```C
BOOL WINAPI PeekConsoleInput(
  _In_  HANDLE        hConsoleInput,
  _Out_ PINPUT_RECORD lpBuffer,
  _In_  DWORD         nLength,
  _Out_ LPDWORD       lpNumberOfEventsRead
);
```

<a name="parameters"></a><span data-ttu-id="f11ce-107">參數</span><span class="sxs-lookup"><span data-stu-id="f11ce-107">Parameters</span></span>
----------

<span data-ttu-id="f11ce-108">*hConsoleInput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f11ce-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="f11ce-109">主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="f11ce-109">A handle to the console input buffer.</span></span> <span data-ttu-id="f11ce-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="f11ce-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="f11ce-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="f11ce-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="f11ce-112">*lpBuffer* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="f11ce-112">*lpBuffer* \[out\]</span></span>  
<span data-ttu-id="f11ce-113">接收輸入緩衝區資料之 [**輸入 \_ 記錄**](input-record-str.md) 結構陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="f11ce-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that receives the input buffer data.</span></span>

<span data-ttu-id="f11ce-114">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f11ce-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="f11ce-115">陣列元素中 *lpBuffer* 參數所指向的陣列大小。</span><span class="sxs-lookup"><span data-stu-id="f11ce-115">The size of the array pointed to by the *lpBuffer* parameter, in array elements.</span></span>

<span data-ttu-id="f11ce-116">*lpNumberOfEventsRead* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="f11ce-116">*lpNumberOfEventsRead* \[out\]</span></span>  
<span data-ttu-id="f11ce-117">變數的指標，此變數會接收讀取的輸入記錄數目。</span><span class="sxs-lookup"><span data-stu-id="f11ce-117">A pointer to a variable that receives the number of input records read.</span></span>

<a name="return-value"></a><span data-ttu-id="f11ce-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="f11ce-118">Return value</span></span>
------------

<span data-ttu-id="f11ce-119">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="f11ce-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f11ce-120">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="f11ce-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f11ce-121">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="f11ce-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="f11ce-122">備註</span><span class="sxs-lookup"><span data-stu-id="f11ce-122">Remarks</span></span>
-------

<span data-ttu-id="f11ce-123">如果要求的記錄數目超過緩衝區中可用的記錄數目，則會讀取可用的數目。</span><span class="sxs-lookup"><span data-stu-id="f11ce-123">If the number of records requested exceeds the number of records available in the buffer, the number available is read.</span></span> <span data-ttu-id="f11ce-124">如果沒有可用的資料，函數會立即傳回。</span><span class="sxs-lookup"><span data-stu-id="f11ce-124">If no data is available, the function returns immediately.</span></span>

<span data-ttu-id="f11ce-125">此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。</span><span class="sxs-lookup"><span data-stu-id="f11ce-125">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="f11ce-126">主控台的字碼頁一開始預設為系統的 OEM 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="f11ce-126">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="f11ce-127">若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 或 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函式，或使用 **chcp** 或 **mode con cp select =** 命令。</span><span class="sxs-lookup"><span data-stu-id="f11ce-127">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="f11ce-128">規格需求</span><span class="sxs-lookup"><span data-stu-id="f11ce-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f11ce-129">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="f11ce-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="f11ce-130">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="f11ce-130">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f11ce-131">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="f11ce-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="f11ce-132">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="f11ce-132">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f11ce-133">標頭</span><span class="sxs-lookup"><span data-stu-id="f11ce-133">Header</span></span></p></td>
<td><span data-ttu-id="f11ce-134">ConsoleApi .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="f11ce-134">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f11ce-135">程式庫</span><span class="sxs-lookup"><span data-stu-id="f11ce-135">Library</span></span></p></td>
<td><span data-ttu-id="f11ce-136">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="f11ce-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f11ce-137">DLL</span><span class="sxs-lookup"><span data-stu-id="f11ce-137">DLL</span></span></p></td>
<td><span data-ttu-id="f11ce-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f11ce-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f11ce-139">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="f11ce-139">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="f11ce-140"><strong>PeekConsoleInputW</strong> (Unicode) 和 <strong>PeekConsoleInputA</strong> (ANSI) </span><span class="sxs-lookup"><span data-stu-id="f11ce-140"><strong>PeekConsoleInputW</strong> (Unicode) and <strong>PeekConsoleInputA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="f11ce-141"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="f11ce-141"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="f11ce-142">主控台功能</span><span class="sxs-lookup"><span data-stu-id="f11ce-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f11ce-143">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="f11ce-143">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="f11ce-144">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="f11ce-144">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="f11ce-145">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="f11ce-145">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="f11ce-146">**WriteConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="f11ce-146">**WriteConsoleInput**</span></span>](writeconsoleinput.md)

[<span data-ttu-id="f11ce-147">**輸入 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="f11ce-147">**INPUT\_RECORD**</span></span>](input-record-str.md)

 

 





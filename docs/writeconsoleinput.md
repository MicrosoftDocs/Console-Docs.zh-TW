---
title: WriteConsoleInput 函式
description: 請參閱 WriteConsoleInput 函式的參考資訊，此函式會將資料直接寫入主控台輸入緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi2/WriteConsoleInput
- wincon/WriteConsoleInput
- WriteConsoleInput
- consoleapi2/WriteConsoleInputA
- wincon/WriteConsoleInputA
- WriteConsoleInputA
- consoleapi2/WriteConsoleInputW
- wincon/WriteConsoleInputW
- WriteConsoleInputW
MS-HAID:
- '\_win32\_writeconsoleinput'
- base.writeconsoleinput
- consoles.writeconsoleinput
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: ad06231f-5063-4aff-b14d-8df5e6e42430
topic_type:
- apiref
api_name:
- WriteConsoleInput
- WriteConsoleInputA
- WriteConsoleInputW
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 784bed6c1a7b7f7ed9ed204b8483d30371e510a3
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059551"
---
# <a name="writeconsoleinput-function"></a><span data-ttu-id="f079f-104">WriteConsoleInput 函式</span><span class="sxs-lookup"><span data-stu-id="f079f-104">WriteConsoleInput function</span></span>


<span data-ttu-id="f079f-105">將資料直接寫入主控台輸入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f079f-105">Writes data directly to the console input buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="f079f-106">語法</span><span class="sxs-lookup"><span data-stu-id="f079f-106">Syntax</span></span>
------

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

<a name="parameters"></a><span data-ttu-id="f079f-107">參數</span><span class="sxs-lookup"><span data-stu-id="f079f-107">Parameters</span></span>
----------

<span data-ttu-id="f079f-108">*hConsoleInput* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f079f-108">*hConsoleInput* \[in\]</span></span>  
<span data-ttu-id="f079f-109">主控台輸入緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="f079f-109">A handle to the console input buffer.</span></span> <span data-ttu-id="f079f-110">控制碼必須有 **一般 \_ 寫入** 存取權限。</span><span class="sxs-lookup"><span data-stu-id="f079f-110">The handle must have the **GENERIC\_WRITE** access right.</span></span> <span data-ttu-id="f079f-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="f079f-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="f079f-112">*lpBuffer* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f079f-112">*lpBuffer* \[in\]</span></span>  
<span data-ttu-id="f079f-113">[**輸入 \_ 記錄**](input-record-str.md)結構陣列的指標，其中包含要寫入至輸入緩衝區的資料。</span><span class="sxs-lookup"><span data-stu-id="f079f-113">A pointer to an array of [**INPUT\_RECORD**](input-record-str.md) structures that contain data to be written to the input buffer.</span></span>

<span data-ttu-id="f079f-114">*nLength* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f079f-114">*nLength* \[in\]</span></span>  
<span data-ttu-id="f079f-115">要寫入的輸入記錄數目。</span><span class="sxs-lookup"><span data-stu-id="f079f-115">The number of input records to be written.</span></span>

<span data-ttu-id="f079f-116">*lpNumberOfEventsWritten* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="f079f-116">*lpNumberOfEventsWritten* \[out\]</span></span>  
<span data-ttu-id="f079f-117">變數的指標，此變數會接收實際寫入之輸入記錄的數目。</span><span class="sxs-lookup"><span data-stu-id="f079f-117">A pointer to a variable that receives the number of input records actually written.</span></span>

<a name="return-value"></a><span data-ttu-id="f079f-118">傳回值</span><span class="sxs-lookup"><span data-stu-id="f079f-118">Return value</span></span>
------------

<span data-ttu-id="f079f-119">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="f079f-119">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="f079f-120">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="f079f-120">If the function fails, the return value is zero.</span></span> <span data-ttu-id="f079f-121">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="f079f-121">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="f079f-122">備註</span><span class="sxs-lookup"><span data-stu-id="f079f-122">Remarks</span></span>
-------

<span data-ttu-id="f079f-123">**WriteConsoleInput** 會將輸入記錄放入緩衝區中任何暫止事件後方的輸入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f079f-123">**WriteConsoleInput** places input records into the input buffer behind any pending events in the buffer.</span></span> <span data-ttu-id="f079f-124">視需要，輸入緩衝區會動態成長，以保存所寫入的事件數目。</span><span class="sxs-lookup"><span data-stu-id="f079f-124">The input buffer grows dynamically, if necessary, to hold as many events as are written.</span></span>

<span data-ttu-id="f079f-125">此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。</span><span class="sxs-lookup"><span data-stu-id="f079f-125">This function uses either Unicode characters or 8-bit characters from the console's current code page.</span></span> <span data-ttu-id="f079f-126">主控台的字碼頁一開始預設為系統的 OEM 字碼頁。</span><span class="sxs-lookup"><span data-stu-id="f079f-126">The console's code page defaults initially to the system's OEM code page.</span></span> <span data-ttu-id="f079f-127">若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 或 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函式，或使用 **chcp** 或 **mode con cp select =** 命令。</span><span class="sxs-lookup"><span data-stu-id="f079f-127">To change the console's code page, use the [**SetConsoleCP**](setconsolecp.md) or [**SetConsoleOutputCP**](setconsoleoutputcp.md) functions, or use the **chcp** or **mode con cp select=** commands.</span></span>

<a name="requirements"></a><span data-ttu-id="f079f-128">規格需求</span><span class="sxs-lookup"><span data-stu-id="f079f-128">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="f079f-129">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="f079f-129">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="f079f-130">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="f079f-130">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f079f-131">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="f079f-131">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="f079f-132">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="f079f-132">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f079f-133">標頭</span><span class="sxs-lookup"><span data-stu-id="f079f-133">Header</span></span></p></td>
<td><span data-ttu-id="f079f-134">ConsoleApi2 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="f079f-134">ConsoleApi2.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f079f-135">程式庫</span><span class="sxs-lookup"><span data-stu-id="f079f-135">Library</span></span></p></td>
<td><span data-ttu-id="f079f-136">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="f079f-136">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="f079f-137">DLL</span><span class="sxs-lookup"><span data-stu-id="f079f-137">DLL</span></span></p></td>
<td><span data-ttu-id="f079f-138">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f079f-138">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="f079f-139">Unicode 和 ANSI 名稱</span><span class="sxs-lookup"><span data-stu-id="f079f-139">Unicode and ANSI names</span></span></p></td>
<td><p><span data-ttu-id="f079f-140"><strong>WriteConsoleInputW</strong> (Unicode) 和 <strong>WriteConsoleInputA</strong> (ANSI) </span><span class="sxs-lookup"><span data-stu-id="f079f-140"><strong>WriteConsoleInputW</strong> (Unicode) and <strong>WriteConsoleInputA</strong> (ANSI)</span></span></p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="f079f-141"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="f079f-141"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="f079f-142">主控台功能</span><span class="sxs-lookup"><span data-stu-id="f079f-142">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f079f-143">**輸入 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="f079f-143">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="f079f-144">低層級主控台輸入函式</span><span class="sxs-lookup"><span data-stu-id="f079f-144">Low-Level Console Input Functions</span></span>](low-level-console-input-functions.md)

[<span data-ttu-id="f079f-145">**MapVirtualKey**</span><span class="sxs-lookup"><span data-stu-id="f079f-145">**MapVirtualKey**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646306)

[<span data-ttu-id="f079f-146">**PeekConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="f079f-146">**PeekConsoleInput**</span></span>](peekconsoleinput.md)

[<span data-ttu-id="f079f-147">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="f079f-147">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="f079f-148">**SetConsoleCP**</span><span class="sxs-lookup"><span data-stu-id="f079f-148">**SetConsoleCP**</span></span>](setconsolecp.md)

[<span data-ttu-id="f079f-149">**SetConsoleOutputCP**</span><span class="sxs-lookup"><span data-stu-id="f079f-149">**SetConsoleOutputCP**</span></span>](setconsoleoutputcp.md)

[<span data-ttu-id="f079f-150">**VkKeyScan**</span><span class="sxs-lookup"><span data-stu-id="f079f-150">**VkKeyScan**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms646329)

 

 





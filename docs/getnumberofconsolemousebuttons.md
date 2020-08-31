---
title: GetNumberOfConsoleMouseButtons 函式
description: 抓取目前主控台使用之滑鼠上的按鈕數目。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi3/GetNumberOfConsoleMouseButtons
- wincon/GetNumberOfConsoleMouseButtons
- GetNumberOfConsoleMouseButtons
MS-HAID:
- '\_win32\_getnumberofconsolemousebuttons'
- base.getnumberofconsolemousebuttons
- consoles.getnumberofconsolemousebuttons
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 78a6a3be-b42f-4a7a-a612-b6a2019cfec2
topic_type:
- apiref
api_name:
- GetNumberOfConsoleMouseButtons
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 67089bd301ac2632f9a99ca24cc2042789f6a3e8
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059491"
---
# <a name="getnumberofconsolemousebuttons-function"></a><span data-ttu-id="3b38a-104">GetNumberOfConsoleMouseButtons 函式</span><span class="sxs-lookup"><span data-stu-id="3b38a-104">GetNumberOfConsoleMouseButtons function</span></span>


<span data-ttu-id="3b38a-105">抓取目前主控台使用之滑鼠上的按鈕數目。</span><span class="sxs-lookup"><span data-stu-id="3b38a-105">Retrieves the number of buttons on the mouse used by the current console.</span></span>

<a name="syntax"></a><span data-ttu-id="3b38a-106">語法</span><span class="sxs-lookup"><span data-stu-id="3b38a-106">Syntax</span></span>
------

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

<a name="parameters"></a><span data-ttu-id="3b38a-107">參數</span><span class="sxs-lookup"><span data-stu-id="3b38a-107">Parameters</span></span>
----------

<span data-ttu-id="3b38a-108">*lpNumberOfMouseButtons* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="3b38a-108">*lpNumberOfMouseButtons* \[out\]</span></span>  
<span data-ttu-id="3b38a-109">變數的指標，此變數會接收滑鼠按鍵的數目。</span><span class="sxs-lookup"><span data-stu-id="3b38a-109">A pointer to a variable that receives the number of mouse buttons.</span></span>

<a name="return-value"></a><span data-ttu-id="3b38a-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="3b38a-110">Return value</span></span>
------------

<span data-ttu-id="3b38a-111">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="3b38a-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="3b38a-112">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="3b38a-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="3b38a-113">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="3b38a-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="3b38a-114">備註</span><span class="sxs-lookup"><span data-stu-id="3b38a-114">Remarks</span></span>
-------

<span data-ttu-id="3b38a-115">當主控台收到滑鼠輸入時，會將包含[**滑鼠 \_ 事件 \_ 記錄**](mouse-event-record-str.md)結構的[**輸入 \_ 記錄**](input-record-str.md)結構放在主控台的輸入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="3b38a-115">When a console receives mouse input, an [**INPUT\_RECORD**](input-record-str.md) structure containing a [**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md) structure is placed in the console's input buffer.</span></span> <span data-ttu-id="3b38a-116">**滑鼠 \_ 事件 \_ 記錄**的**dwButtonState**成員有位，表示每個滑鼠按鍵的狀態。</span><span class="sxs-lookup"><span data-stu-id="3b38a-116">The **dwButtonState** member of **MOUSE\_EVENT\_RECORD** has a bit indicating the state of each mouse button.</span></span> <span data-ttu-id="3b38a-117">如果按鈕已關閉，則位為1，如果按鈕為開啟，則為0。</span><span class="sxs-lookup"><span data-stu-id="3b38a-117">The bit is 1 if the button is down and 0 if the button is up.</span></span> <span data-ttu-id="3b38a-118">若要判斷重要位數，請使用 **GetNumberOfConsoleMouseButtons**。</span><span class="sxs-lookup"><span data-stu-id="3b38a-118">To determine the number of bits that are significant, use **GetNumberOfConsoleMouseButtons**.</span></span>

<a name="requirements"></a><span data-ttu-id="3b38a-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="3b38a-119">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="3b38a-120">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="3b38a-120">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="3b38a-121">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="3b38a-121">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3b38a-122">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="3b38a-122">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="3b38a-123">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="3b38a-123">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3b38a-124">標頭</span><span class="sxs-lookup"><span data-stu-id="3b38a-124">Header</span></span></p></td>
<td><span data-ttu-id="3b38a-125">ConsoleApi3 .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="3b38a-125">ConsoleApi3.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="3b38a-126">程式庫</span><span class="sxs-lookup"><span data-stu-id="3b38a-126">Library</span></span></p></td>
<td><span data-ttu-id="3b38a-127">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="3b38a-127">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="3b38a-128">DLL</span><span class="sxs-lookup"><span data-stu-id="3b38a-128">DLL</span></span></p></td>
<td><span data-ttu-id="3b38a-129">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="3b38a-129">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="3b38a-130"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b38a-130"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="3b38a-131">主控台功能</span><span class="sxs-lookup"><span data-stu-id="3b38a-131">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="3b38a-132">主控台輸入緩衝區</span><span class="sxs-lookup"><span data-stu-id="3b38a-132">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="3b38a-133">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="3b38a-133">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="3b38a-134">**輸入 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="3b38a-134">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="3b38a-135">**滑鼠 \_ 事件 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="3b38a-135">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

 

 





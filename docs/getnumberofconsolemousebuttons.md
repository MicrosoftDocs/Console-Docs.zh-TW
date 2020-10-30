---
title: GetNumberOfConsoleMouseButtons 函式
description: 抓取目前主控台使用之滑鼠上的按鈕數目。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
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
ms.openlocfilehash: 96a63f3d35170ed419ceb90a063044a93c0b1951
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037826"
---
# <a name="getnumberofconsolemousebuttons-function"></a><span data-ttu-id="4d168-104">GetNumberOfConsoleMouseButtons 函式</span><span class="sxs-lookup"><span data-stu-id="4d168-104">GetNumberOfConsoleMouseButtons function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="4d168-105">抓取目前主控台使用之滑鼠上的按鈕數目。</span><span class="sxs-lookup"><span data-stu-id="4d168-105">Retrieves the number of buttons on the mouse used by the current console.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d168-106">語法</span><span class="sxs-lookup"><span data-stu-id="4d168-106">Syntax</span></span>

```C
BOOL WINAPI GetNumberOfConsoleMouseButtons(
  _Out_ LPDWORD lpNumberOfMouseButtons
);
```

## <a name="parameters"></a><span data-ttu-id="4d168-107">參數</span><span class="sxs-lookup"><span data-stu-id="4d168-107">Parameters</span></span>

<span data-ttu-id="4d168-108">*lpNumberOfMouseButtons* \[擴展\]</span><span class="sxs-lookup"><span data-stu-id="4d168-108">*lpNumberOfMouseButtons* \[out\]</span></span>  
<span data-ttu-id="4d168-109">變數的指標，此變數會接收滑鼠按鍵的數目。</span><span class="sxs-lookup"><span data-stu-id="4d168-109">A pointer to a variable that receives the number of mouse buttons.</span></span>

## <a name="return-value"></a><span data-ttu-id="4d168-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="4d168-110">Return value</span></span>

<span data-ttu-id="4d168-111">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="4d168-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="4d168-112">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="4d168-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="4d168-113">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="4d168-113">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="4d168-114">備註</span><span class="sxs-lookup"><span data-stu-id="4d168-114">Remarks</span></span>

<span data-ttu-id="4d168-115">當主控台收到滑鼠輸入時，會將包含 [**滑鼠 \_ 事件 \_ 記錄**](mouse-event-record-str.md)結構的 [**輸入 \_ 記錄**](input-record-str.md)結構放在主控台的輸入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="4d168-115">When a console receives mouse input, an [**INPUT\_RECORD**](input-record-str.md) structure containing a [**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md) structure is placed in the console's input buffer.</span></span> <span data-ttu-id="4d168-116">**滑鼠 \_ 事件 \_ 記錄** 的 **dwButtonState** 成員有位，表示每個滑鼠按鍵的狀態。</span><span class="sxs-lookup"><span data-stu-id="4d168-116">The **dwButtonState** member of **MOUSE\_EVENT\_RECORD** has a bit indicating the state of each mouse button.</span></span> <span data-ttu-id="4d168-117">如果按鈕已關閉，則位為1，如果按鈕為開啟，則為0。</span><span class="sxs-lookup"><span data-stu-id="4d168-117">The bit is 1 if the button is down and 0 if the button is up.</span></span> <span data-ttu-id="4d168-118">若要判斷重要位數，請使用 **GetNumberOfConsoleMouseButtons** 。</span><span class="sxs-lookup"><span data-stu-id="4d168-118">To determine the number of bits that are significant, use **GetNumberOfConsoleMouseButtons** .</span></span>

> [!TIP]
> <span data-ttu-id="4d168-119">不建議使用此 API，也不會有對等的 **[虛擬終端](console-virtual-terminal-sequences.md)** 機。</span><span class="sxs-lookup"><span data-stu-id="4d168-119">This API is not recommended and does not have a **[virtual terminal](console-virtual-terminal-sequences.md)** equivalent.</span></span> <span data-ttu-id="4d168-120">這種決策刻意將 Windows 平臺與其他作業系統對齊。</span><span class="sxs-lookup"><span data-stu-id="4d168-120">This decision intentionally aligns the Windows platform with other operating systems.</span></span> <span data-ttu-id="4d168-121">此狀態只會與本機使用者、會話和許可權內容相關。</span><span class="sxs-lookup"><span data-stu-id="4d168-121">This state is only relevant to the local user, session, and privilege context.</span></span> <span data-ttu-id="4d168-122">使用此 API 時，透過跨平臺公用程式和傳輸（如 SSH）的應用程式遠端執行可能無法如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="4d168-122">Applications remoting via cross-platform utilities and transports like SSH may not work as expected if using this API.</span></span>

## <a name="requirements"></a><span data-ttu-id="4d168-123">規格需求</span><span class="sxs-lookup"><span data-stu-id="4d168-123">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="4d168-124">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="4d168-124">Minimum supported client</span></span> | <span data-ttu-id="4d168-125">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="4d168-125">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="4d168-126">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="4d168-126">Minimum supported server</span></span> | <span data-ttu-id="4d168-127">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="4d168-127">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="4d168-128">標頭</span><span class="sxs-lookup"><span data-stu-id="4d168-128">Header</span></span> | <span data-ttu-id="4d168-129">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="4d168-129">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="4d168-130">程式庫</span><span class="sxs-lookup"><span data-stu-id="4d168-130">Library</span></span> | <span data-ttu-id="4d168-131">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="4d168-131">Kernel32.lib</span></span> |
| <span data-ttu-id="4d168-132">DLL</span><span class="sxs-lookup"><span data-stu-id="4d168-132">DLL</span></span> | <span data-ttu-id="4d168-133">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="4d168-133">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="4d168-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="4d168-134">See also</span></span>

[<span data-ttu-id="4d168-135">主控台功能</span><span class="sxs-lookup"><span data-stu-id="4d168-135">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="4d168-136">主控台輸入緩衝區</span><span class="sxs-lookup"><span data-stu-id="4d168-136">Console Input Buffer</span></span>](console-input-buffer.md)

[<span data-ttu-id="4d168-137">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="4d168-137">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="4d168-138">**輸入 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="4d168-138">**INPUT\_RECORD**</span></span>](input-record-str.md)

[<span data-ttu-id="4d168-139">**滑鼠 \_ 事件 \_ 記錄**</span><span class="sxs-lookup"><span data-stu-id="4d168-139">**MOUSE\_EVENT\_RECORD**</span></span>](mouse-event-record-str.md)

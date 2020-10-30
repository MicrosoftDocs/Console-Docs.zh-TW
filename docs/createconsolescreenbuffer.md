---
title: CreateConsoleScreenBuffer 函式
description: CreateConsoleScreenBuffer 函式會建立 Windows 主控台的螢幕緩衝區。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi2/CreateConsoleScreenBuffer
- wincon/CreateConsoleScreenBuffer
- CreateConsoleScreenBuffer
MS-HAID:
- '\_win32\_createconsolescreenbuffer'
- base.createconsolescreenbuffer
- consoles.createconsolescreenbuffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 98bb74e4-dad2-4615-9263-48ba778a06ff
topic_type:
- apiref
api_name:
- CreateConsoleScreenBuffer
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l2-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
api_type:
- DllExport
ms.openlocfilehash: 0b8f5b33233f49167c67a47f33e5a95b8864f7bd
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93039128"
---
# <a name="createconsolescreenbuffer-function"></a><span data-ttu-id="2e0f0-104">CreateConsoleScreenBuffer 函式</span><span class="sxs-lookup"><span data-stu-id="2e0f0-104">CreateConsoleScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="2e0f0-105">建立主控台螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-105">Creates a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="2e0f0-106">語法</span><span class="sxs-lookup"><span data-stu-id="2e0f0-106">Syntax</span></span>

```C
HANDLE WINAPI CreateConsoleScreenBuffer(
  _In_             DWORD               dwDesiredAccess,
  _In_             DWORD               dwShareMode,
  _In_opt_   const SECURITY_ATTRIBUTES *lpSecurityAttributes,
  _In_             DWORD               dwFlags,
  _Reserved_       LPVOID              lpScreenBufferData
);
```

## <a name="parameters"></a><span data-ttu-id="2e0f0-107">參數</span><span class="sxs-lookup"><span data-stu-id="2e0f0-107">Parameters</span></span>

<span data-ttu-id="2e0f0-108">*dwDesiredAccess* \[在\]</span><span class="sxs-lookup"><span data-stu-id="2e0f0-108">*dwDesiredAccess* \[in\]</span></span>  
<span data-ttu-id="2e0f0-109">主控台螢幕緩衝區的存取權。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-109">The access to the console screen buffer.</span></span> <span data-ttu-id="2e0f0-110">如需存取權限的清單，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-110">For a list of access rights, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="2e0f0-111">*dwShareMode* \[在\]</span><span class="sxs-lookup"><span data-stu-id="2e0f0-111">*dwShareMode* \[in\]</span></span>  
<span data-ttu-id="2e0f0-112">這個參數可以是零，表示無法共用緩衝區，也可以是下列其中一個或多個值。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-112">This parameter can be zero, indicating that the buffer cannot be shared, or it can be one or more of the following values.</span></span>

| <span data-ttu-id="2e0f0-113">值</span><span class="sxs-lookup"><span data-stu-id="2e0f0-113">Value</span></span> | <span data-ttu-id="2e0f0-114">意義</span><span class="sxs-lookup"><span data-stu-id="2e0f0-114">Meaning</span></span> |
|-|-|
| <span data-ttu-id="2e0f0-115">**FILE_SHARE_READ** 0x00000001</span><span class="sxs-lookup"><span data-stu-id="2e0f0-115">**FILE_SHARE_READ** 0x00000001</span></span> | <span data-ttu-id="2e0f0-116">您可以在主控台螢幕緩衝區上執行其他開啟的作業，以進行讀取存取。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-116">Other open operations can be performed on the console screen buffer for read access.</span></span> |
| <span data-ttu-id="2e0f0-117">**FILE_SHARE_WRITE** 0x00000002</span><span class="sxs-lookup"><span data-stu-id="2e0f0-117">**FILE_SHARE_WRITE** 0x00000002</span></span> | <span data-ttu-id="2e0f0-118">您可以在主控台螢幕緩衝區上執行其他開啟的作業，以進行寫入存取。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-118">Other open operations can be performed on the console screen buffer for write access.</span></span> |

<span data-ttu-id="2e0f0-119">*lpSecurityAttributes* \[在中，選擇性\]</span><span class="sxs-lookup"><span data-stu-id="2e0f0-119">*lpSecurityAttributes* \[in, optional\]</span></span>  
<span data-ttu-id="2e0f0-120">[**安全性 \_ 屬性**](https://msdn.microsoft.com/library/windows/desktop/aa379560)結構的指標，可判斷是否可由子進程繼承傳回的控制碼。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-120">A pointer to a [**SECURITY\_ATTRIBUTES**](https://msdn.microsoft.com/library/windows/desktop/aa379560) structure that determines whether the returned handle can be inherited by child processes.</span></span> <span data-ttu-id="2e0f0-121">如果 *lpSecurityAttributes* 為 **Null** ，則無法繼承控制碼。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-121">If *lpSecurityAttributes* is **NULL** , the handle cannot be inherited.</span></span> <span data-ttu-id="2e0f0-122">結構的 **lpSecurityDescriptor** 成員會指定新主控台螢幕緩衝區的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-122">The **lpSecurityDescriptor** member of the structure specifies a security descriptor for the new console screen buffer.</span></span> <span data-ttu-id="2e0f0-123">如果 *lpSecurityAttributes* 為 **Null** ，則主控台螢幕緩衝區會取得預設安全描述項。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-123">If *lpSecurityAttributes* is **NULL** , the console screen buffer gets a default security descriptor.</span></span> <span data-ttu-id="2e0f0-124">主控台螢幕緩衝區之預設安全描述項中的 Acl 來自于建立者的主要或模擬權杖。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-124">The ACLs in the default security descriptor for a console screen buffer come from the primary or impersonation token of the creator.</span></span>

<span data-ttu-id="2e0f0-125">*dwFlags* \[在\]</span><span class="sxs-lookup"><span data-stu-id="2e0f0-125">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="2e0f0-126">要建立的主控台螢幕緩衝區類型。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-126">The type of console screen buffer to create.</span></span> <span data-ttu-id="2e0f0-127">唯一支援的螢幕緩衝區類型是 **主控台 \_ TEXTMODE \_ 緩衝區** 。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-127">The only supported screen buffer type is **CONSOLE\_TEXTMODE\_BUFFER** .</span></span>

<span data-ttu-id="2e0f0-128">*lpScreenBufferData*</span><span class="sxs-lookup"><span data-stu-id="2e0f0-128">*lpScreenBufferData*</span></span>  
<span data-ttu-id="2e0f0-129">保護應為 **Null** 。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-129">Reserved; should be **NULL** .</span></span>

## <a name="return-value"></a><span data-ttu-id="2e0f0-130">傳回值</span><span class="sxs-lookup"><span data-stu-id="2e0f0-130">Return value</span></span>

<span data-ttu-id="2e0f0-131">如果函式成功，則傳回值是新主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-131">If the function succeeds, the return value is a handle to the new console screen buffer.</span></span>

<span data-ttu-id="2e0f0-132">如果函式失敗，則傳回值是 **不正確 \_ 控制碼 \_ 值** 。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-132">If the function fails, the return value is **INVALID\_HANDLE\_VALUE** .</span></span> <span data-ttu-id="2e0f0-133">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-133">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

## <a name="remarks"></a><span data-ttu-id="2e0f0-134">備註</span><span class="sxs-lookup"><span data-stu-id="2e0f0-134">Remarks</span></span>

<span data-ttu-id="2e0f0-135">主控台可以有多個螢幕緩衝區，但只能有一個使用中的螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-135">A console can have multiple screen buffers but only one active screen buffer.</span></span> <span data-ttu-id="2e0f0-136">您可以存取非作用中的螢幕緩衝區以進行讀取和寫入，但是只會顯示作用中螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-136">Inactive screen buffers can be accessed for reading and writing, but only the active screen buffer is displayed.</span></span> <span data-ttu-id="2e0f0-137">若要讓新的螢幕緩衝區變成使用中的螢幕緩衝區，請使用 [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-137">To make the new screen buffer the active screen buffer, use the [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) function.</span></span>

<span data-ttu-id="2e0f0-138">新建立的螢幕緩衝區會在呼叫此函式時，從現用螢幕緩衝區複製一些屬性。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-138">The newly created screen buffer will copy some properties from the active screen buffer at the time that this function is called.</span></span> <span data-ttu-id="2e0f0-139">行為如下所示：</span><span class="sxs-lookup"><span data-stu-id="2e0f0-139">The behavior is as follows:</span></span>

- <span data-ttu-id="2e0f0-140">`Font` -從 active screen 緩衝區複製</span><span class="sxs-lookup"><span data-stu-id="2e0f0-140">`Font` - copied from active screen buffer</span></span>
- <span data-ttu-id="2e0f0-141">`Display Window Size` -從 active screen 緩衝區複製</span><span class="sxs-lookup"><span data-stu-id="2e0f0-141">`Display Window Size` - copied from active screen buffer</span></span>
- <span data-ttu-id="2e0f0-142">`Buffer Size` -符合 `Display Window Size` **未** 複製的 () </span><span class="sxs-lookup"><span data-stu-id="2e0f0-142">`Buffer Size` - matched to `Display Window Size` ( **NOT** copied)</span></span>
- <span data-ttu-id="2e0f0-143">`Default Attributes` (色彩) -從現用螢幕緩衝區複製</span><span class="sxs-lookup"><span data-stu-id="2e0f0-143">`Default Attributes` (colors) - copied from active screen buffer</span></span>
- <span data-ttu-id="2e0f0-144">`Default Popup Attributes` (色彩) -從現用螢幕緩衝區複製</span><span class="sxs-lookup"><span data-stu-id="2e0f0-144">`Default Popup Attributes` (colors) - copied from active screen buffer</span></span>

<span data-ttu-id="2e0f0-145">呼叫進程可以在任何需要控制主控台螢幕緩衝區的函式中使用傳回的控制碼，但受限於 *dwDesiredAccess* 參數所指定的存取限制。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-145">The calling process can use the returned handle in any function that requires a handle to a console screen buffer, subject to the limitations of access specified by the *dwDesiredAccess* parameter.</span></span>

<span data-ttu-id="2e0f0-146">呼叫進程可使用 [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) 函式來建立重複的螢幕緩衝區控制碼，此控制碼具有與原始控制碼不同的存取或可繼承。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-146">The calling process can use the [**DuplicateHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724251) function to create a duplicate screen buffer handle that has different access or inheritability from the original handle.</span></span> <span data-ttu-id="2e0f0-147">不過， **DuplicateHandle** 無法用來建立對不同進程 (有效的重複項，但透過繼承) 除外。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-147">However, **DuplicateHandle** cannot be used to create a duplicate that is valid for a different process (except through inheritance).</span></span>

<span data-ttu-id="2e0f0-148">若要關閉主控台畫面緩衝區控制碼，請使用 [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) 函數。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-148">To close the console screen buffer handle, use the [**CloseHandle**](https://msdn.microsoft.com/library/windows/desktop/ms724211) function.</span></span>

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a><span data-ttu-id="2e0f0-149">範例</span><span class="sxs-lookup"><span data-stu-id="2e0f0-149">Examples</span></span>

<span data-ttu-id="2e0f0-150">如需範例，請參閱 [讀取和寫入字元和屬性的區塊](reading-and-writing-blocks-of-characters-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="2e0f0-150">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="2e0f0-151">規格需求</span><span class="sxs-lookup"><span data-stu-id="2e0f0-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="2e0f0-152">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="2e0f0-152">Minimum supported client</span></span> | <span data-ttu-id="2e0f0-153">僅限 Windows 2000 Professional \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="2e0f0-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="2e0f0-154">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="2e0f0-154">Minimum supported server</span></span> | <span data-ttu-id="2e0f0-155">僅限 Windows 2000 Server \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="2e0f0-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="2e0f0-156">標頭</span><span class="sxs-lookup"><span data-stu-id="2e0f0-156">Header</span></span> | <span data-ttu-id="2e0f0-157">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="2e0f0-157">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="2e0f0-158">程式庫</span><span class="sxs-lookup"><span data-stu-id="2e0f0-158">Library</span></span> | <span data-ttu-id="2e0f0-159">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="2e0f0-159">Kernel32.lib</span></span> |
| <span data-ttu-id="2e0f0-160">DLL</span><span class="sxs-lookup"><span data-stu-id="2e0f0-160">DLL</span></span> | <span data-ttu-id="2e0f0-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="2e0f0-161">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="2e0f0-162">請參閱</span><span class="sxs-lookup"><span data-stu-id="2e0f0-162">See also</span></span>

[<span data-ttu-id="2e0f0-163">主控台功能</span><span class="sxs-lookup"><span data-stu-id="2e0f0-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="2e0f0-164">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="2e0f0-164">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="2e0f0-165">**CloseHandle**</span><span class="sxs-lookup"><span data-stu-id="2e0f0-165">**CloseHandle**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724211)

[<span data-ttu-id="2e0f0-166">**DuplicateHandle**</span><span class="sxs-lookup"><span data-stu-id="2e0f0-166">**DuplicateHandle**</span></span>](https://msdn.microsoft.com/library/windows/desktop/ms724251)

[<span data-ttu-id="2e0f0-167">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="2e0f0-167">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

[<span data-ttu-id="2e0f0-168">**安全性 \_ 屬性**</span><span class="sxs-lookup"><span data-stu-id="2e0f0-168">**SECURITY\_ATTRIBUTES**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa379560)

[<span data-ttu-id="2e0f0-169">**SetConsoleActiveScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="2e0f0-169">**SetConsoleActiveScreenBuffer**</span></span>](setconsoleactivescreenbuffer.md)

[<span data-ttu-id="2e0f0-170">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="2e0f0-170">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)

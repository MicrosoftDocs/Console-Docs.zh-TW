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
ms.openlocfilehash: 0e7e4606e561454a2037650cc8d1f3b685ff2d5d
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357958"
---
# <a name="createconsolescreenbuffer-function"></a><span data-ttu-id="f4be1-104">CreateConsoleScreenBuffer 函式</span><span class="sxs-lookup"><span data-stu-id="f4be1-104">CreateConsoleScreenBuffer function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="f4be1-105">建立主控台螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f4be1-105">Creates a console screen buffer.</span></span>

## <a name="syntax"></a><span data-ttu-id="f4be1-106">語法</span><span class="sxs-lookup"><span data-stu-id="f4be1-106">Syntax</span></span>

```C
HANDLE WINAPI CreateConsoleScreenBuffer(
  _In_             DWORD               dwDesiredAccess,
  _In_             DWORD               dwShareMode,
  _In_opt_   const SECURITY_ATTRIBUTES *lpSecurityAttributes,
  _In_             DWORD               dwFlags,
  _Reserved_       LPVOID              lpScreenBufferData
);
```

## <a name="parameters"></a><span data-ttu-id="f4be1-107">參數</span><span class="sxs-lookup"><span data-stu-id="f4be1-107">Parameters</span></span>

<span data-ttu-id="f4be1-108">*dwDesiredAccess* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f4be1-108">*dwDesiredAccess* \[in\]</span></span>  
<span data-ttu-id="f4be1-109">主控台螢幕緩衝區的存取權。</span><span class="sxs-lookup"><span data-stu-id="f4be1-109">The access to the console screen buffer.</span></span> <span data-ttu-id="f4be1-110">如需存取權限的清單，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="f4be1-110">For a list of access rights, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="f4be1-111">*dwShareMode* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f4be1-111">*dwShareMode* \[in\]</span></span>  
<span data-ttu-id="f4be1-112">這個參數可以是零，表示無法共用緩衝區，也可以是下列其中一個或多個值。</span><span class="sxs-lookup"><span data-stu-id="f4be1-112">This parameter can be zero, indicating that the buffer cannot be shared, or it can be one or more of the following values.</span></span>

| <span data-ttu-id="f4be1-113">值</span><span class="sxs-lookup"><span data-stu-id="f4be1-113">Value</span></span> | <span data-ttu-id="f4be1-114">意義</span><span class="sxs-lookup"><span data-stu-id="f4be1-114">Meaning</span></span> |
|-|-|
| <span data-ttu-id="f4be1-115">**FILE_SHARE_READ** 0x00000001</span><span class="sxs-lookup"><span data-stu-id="f4be1-115">**FILE_SHARE_READ** 0x00000001</span></span> | <span data-ttu-id="f4be1-116">您可以在主控台螢幕緩衝區上執行其他開啟的作業，以進行讀取存取。</span><span class="sxs-lookup"><span data-stu-id="f4be1-116">Other open operations can be performed on the console screen buffer for read access.</span></span> |
| <span data-ttu-id="f4be1-117">**FILE_SHARE_WRITE** 0x00000002</span><span class="sxs-lookup"><span data-stu-id="f4be1-117">**FILE_SHARE_WRITE** 0x00000002</span></span> | <span data-ttu-id="f4be1-118">您可以在主控台螢幕緩衝區上執行其他開啟的作業，以進行寫入存取。</span><span class="sxs-lookup"><span data-stu-id="f4be1-118">Other open operations can be performed on the console screen buffer for write access.</span></span> |

<span data-ttu-id="f4be1-119">*lpSecurityAttributes* \[在中，選擇性\]</span><span class="sxs-lookup"><span data-stu-id="f4be1-119">*lpSecurityAttributes* \[in, optional\]</span></span>  
<span data-ttu-id="f4be1-120">[**安全性 \_ 屬性**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85))結構的指標，可判斷是否可由子進程繼承傳回的控制碼。</span><span class="sxs-lookup"><span data-stu-id="f4be1-120">A pointer to a [**SECURITY\_ATTRIBUTES**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85)) structure that determines whether the returned handle can be inherited by child processes.</span></span> <span data-ttu-id="f4be1-121">如果 *lpSecurityAttributes* 為 **Null**，則無法繼承控制碼。</span><span class="sxs-lookup"><span data-stu-id="f4be1-121">If *lpSecurityAttributes* is **NULL**, the handle cannot be inherited.</span></span> <span data-ttu-id="f4be1-122">結構的 **lpSecurityDescriptor** 成員會指定新主控台螢幕緩衝區的安全描述項。</span><span class="sxs-lookup"><span data-stu-id="f4be1-122">The **lpSecurityDescriptor** member of the structure specifies a security descriptor for the new console screen buffer.</span></span> <span data-ttu-id="f4be1-123">如果 *lpSecurityAttributes* 為 **Null**，則主控台螢幕緩衝區會取得預設安全描述項。</span><span class="sxs-lookup"><span data-stu-id="f4be1-123">If *lpSecurityAttributes* is **NULL**, the console screen buffer gets a default security descriptor.</span></span> <span data-ttu-id="f4be1-124">主控台螢幕緩衝區之預設安全描述項中的 Acl 來自于建立者的主要或模擬權杖。</span><span class="sxs-lookup"><span data-stu-id="f4be1-124">The ACLs in the default security descriptor for a console screen buffer come from the primary or impersonation token of the creator.</span></span>

<span data-ttu-id="f4be1-125">*dwFlags* \[在\]</span><span class="sxs-lookup"><span data-stu-id="f4be1-125">*dwFlags* \[in\]</span></span>  
<span data-ttu-id="f4be1-126">要建立的主控台螢幕緩衝區類型。</span><span class="sxs-lookup"><span data-stu-id="f4be1-126">The type of console screen buffer to create.</span></span> <span data-ttu-id="f4be1-127">唯一支援的螢幕緩衝區類型是 **主控台 \_ TEXTMODE \_ 緩衝區**。</span><span class="sxs-lookup"><span data-stu-id="f4be1-127">The only supported screen buffer type is **CONSOLE\_TEXTMODE\_BUFFER**.</span></span>

<span data-ttu-id="f4be1-128">*lpScreenBufferData*</span><span class="sxs-lookup"><span data-stu-id="f4be1-128">*lpScreenBufferData*</span></span>  
<span data-ttu-id="f4be1-129">保護應為 **Null**。</span><span class="sxs-lookup"><span data-stu-id="f4be1-129">Reserved; should be **NULL**.</span></span>

## <a name="return-value"></a><span data-ttu-id="f4be1-130">傳回值</span><span class="sxs-lookup"><span data-stu-id="f4be1-130">Return value</span></span>

<span data-ttu-id="f4be1-131">如果函式成功，則傳回值是新主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="f4be1-131">If the function succeeds, the return value is a handle to the new console screen buffer.</span></span>

<span data-ttu-id="f4be1-132">如果函式失敗，則傳回值是 **INVALID\_HANDLE\_VALUE**。</span><span class="sxs-lookup"><span data-stu-id="f4be1-132">If the function fails, the return value is **INVALID\_HANDLE\_VALUE**.</span></span> <span data-ttu-id="f4be1-133">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="f4be1-133">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="f4be1-134">備註</span><span class="sxs-lookup"><span data-stu-id="f4be1-134">Remarks</span></span>

<span data-ttu-id="f4be1-135">主控台可以有多個螢幕緩衝區，但只能有一個使用中的螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f4be1-135">A console can have multiple screen buffers but only one active screen buffer.</span></span> <span data-ttu-id="f4be1-136">您可以存取非作用中的螢幕緩衝區以進行讀取和寫入，但是只會顯示作用中螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="f4be1-136">Inactive screen buffers can be accessed for reading and writing, but only the active screen buffer is displayed.</span></span> <span data-ttu-id="f4be1-137">若要讓新的螢幕緩衝區變成使用中的螢幕緩衝區，請使用 [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) 函式。</span><span class="sxs-lookup"><span data-stu-id="f4be1-137">To make the new screen buffer the active screen buffer, use the [**SetConsoleActiveScreenBuffer**](setconsoleactivescreenbuffer.md) function.</span></span>

<span data-ttu-id="f4be1-138">新建立的螢幕緩衝區會在呼叫此函式時，從現用螢幕緩衝區複製一些屬性。</span><span class="sxs-lookup"><span data-stu-id="f4be1-138">The newly created screen buffer will copy some properties from the active screen buffer at the time that this function is called.</span></span> <span data-ttu-id="f4be1-139">行為如下所示：</span><span class="sxs-lookup"><span data-stu-id="f4be1-139">The behavior is as follows:</span></span>

- <span data-ttu-id="f4be1-140">`Font` -從 active screen 緩衝區複製</span><span class="sxs-lookup"><span data-stu-id="f4be1-140">`Font` - copied from active screen buffer</span></span>
- <span data-ttu-id="f4be1-141">`Display Window Size` -從 active screen 緩衝區複製</span><span class="sxs-lookup"><span data-stu-id="f4be1-141">`Display Window Size` - copied from active screen buffer</span></span>
- <span data-ttu-id="f4be1-142">`Buffer Size` -符合 `Display Window Size` **未** 複製的 () </span><span class="sxs-lookup"><span data-stu-id="f4be1-142">`Buffer Size` - matched to `Display Window Size` (**NOT** copied)</span></span>
- <span data-ttu-id="f4be1-143">`Default Attributes` (色彩) -從現用螢幕緩衝區複製</span><span class="sxs-lookup"><span data-stu-id="f4be1-143">`Default Attributes` (colors) - copied from active screen buffer</span></span>
- <span data-ttu-id="f4be1-144">`Default Popup Attributes` (色彩) -從現用螢幕緩衝區複製</span><span class="sxs-lookup"><span data-stu-id="f4be1-144">`Default Popup Attributes` (colors) - copied from active screen buffer</span></span>

<span data-ttu-id="f4be1-145">呼叫進程可以在任何需要控制主控台螢幕緩衝區的函式中使用傳回的控制碼，但受限於 *dwDesiredAccess* 參數所指定的存取限制。</span><span class="sxs-lookup"><span data-stu-id="f4be1-145">The calling process can use the returned handle in any function that requires a handle to a console screen buffer, subject to the limitations of access specified by the *dwDesiredAccess* parameter.</span></span>

<span data-ttu-id="f4be1-146">呼叫進程可使用 [**DuplicateHandle**](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle) 函式來建立重複的螢幕緩衝區控制碼，此控制碼具有與原始控制碼不同的存取或可繼承。</span><span class="sxs-lookup"><span data-stu-id="f4be1-146">The calling process can use the [**DuplicateHandle**](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle) function to create a duplicate screen buffer handle that has different access or inheritability from the original handle.</span></span> <span data-ttu-id="f4be1-147">不過， **DuplicateHandle** 無法用來建立對不同進程 (有效的重複項，但透過繼承) 除外。</span><span class="sxs-lookup"><span data-stu-id="f4be1-147">However, **DuplicateHandle** cannot be used to create a duplicate that is valid for a different process (except through inheritance).</span></span>

<span data-ttu-id="f4be1-148">若要關閉主控台畫面緩衝區控制碼，請使用 [**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle) 函數。</span><span class="sxs-lookup"><span data-stu-id="f4be1-148">To close the console screen buffer handle, use the [**CloseHandle**](/windows/win32/api/handleapi/nf-handleapi-closehandle) function.</span></span>

[!INCLUDE [no-vt-equiv-alt-buf](./includes/no-vt-equiv-alt-buf.md)]

## <a name="examples"></a><span data-ttu-id="f4be1-149">範例</span><span class="sxs-lookup"><span data-stu-id="f4be1-149">Examples</span></span>

<span data-ttu-id="f4be1-150">如需範例，請參閱 [讀取和寫入字元和屬性的區塊](reading-and-writing-blocks-of-characters-and-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="f4be1-150">For an example, see [Reading and Writing Blocks of Characters and Attributes](reading-and-writing-blocks-of-characters-and-attributes.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="f4be1-151">規格需求</span><span class="sxs-lookup"><span data-stu-id="f4be1-151">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="f4be1-152">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="f4be1-152">Minimum supported client</span></span> | <span data-ttu-id="f4be1-153">Windows 2000 Professional \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="f4be1-153">Windows 2000 Professional \[desktop apps only\]</span></span> |
| <span data-ttu-id="f4be1-154">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="f4be1-154">Minimum supported server</span></span> | <span data-ttu-id="f4be1-155">Windows 2000 Server \[僅限傳統型應用程式\]</span><span class="sxs-lookup"><span data-stu-id="f4be1-155">Windows 2000 Server \[desktop apps only\]</span></span> |
| <span data-ttu-id="f4be1-156">標頭</span><span class="sxs-lookup"><span data-stu-id="f4be1-156">Header</span></span> | <span data-ttu-id="f4be1-157">ConsoleApi2 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="f4be1-157">ConsoleApi2.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="f4be1-158">程式庫</span><span class="sxs-lookup"><span data-stu-id="f4be1-158">Library</span></span> | <span data-ttu-id="f4be1-159">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="f4be1-159">Kernel32.lib</span></span> |
| <span data-ttu-id="f4be1-160">DLL</span><span class="sxs-lookup"><span data-stu-id="f4be1-160">DLL</span></span> | <span data-ttu-id="f4be1-161">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="f4be1-161">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="f4be1-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4be1-162">See also</span></span>

[<span data-ttu-id="f4be1-163">主控台函式</span><span class="sxs-lookup"><span data-stu-id="f4be1-163">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="f4be1-164">主控台畫面緩衝區</span><span class="sxs-lookup"><span data-stu-id="f4be1-164">Console Screen Buffers</span></span>](console-screen-buffers.md)

[<span data-ttu-id="f4be1-165">**CloseHandle**</span><span class="sxs-lookup"><span data-stu-id="f4be1-165">**CloseHandle**</span></span>](/windows/win32/api/handleapi/nf-handleapi-closehandle)

[<span data-ttu-id="f4be1-166">**DuplicateHandle**</span><span class="sxs-lookup"><span data-stu-id="f4be1-166">**DuplicateHandle**</span></span>](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle)

[<span data-ttu-id="f4be1-167">**GetConsoleScreenBufferInfo**</span><span class="sxs-lookup"><span data-stu-id="f4be1-167">**GetConsoleScreenBufferInfo**</span></span>](getconsolescreenbufferinfo.md)

<span data-ttu-id="f4be1-168">[**安全性 \_ 屬性**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="f4be1-168">[**SECURITY\_ATTRIBUTES**](/previous-versions/windows/desktop/legacy/aa379560(v=vs.85))</span></span>

[<span data-ttu-id="f4be1-169">**SetConsoleActiveScreenBuffer**</span><span class="sxs-lookup"><span data-stu-id="f4be1-169">**SetConsoleActiveScreenBuffer**</span></span>](setconsoleactivescreenbuffer.md)

[<span data-ttu-id="f4be1-170">**SetConsoleScreenBufferSize**</span><span class="sxs-lookup"><span data-stu-id="f4be1-170">**SetConsoleScreenBufferSize**</span></span>](setconsolescreenbuffersize.md)
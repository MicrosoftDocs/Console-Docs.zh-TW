---
title: SetConsoleHistoryInfo 函式
description: 為呼叫進程的 Windows 主控台設定歷程記錄設定。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/SetConsoleHistoryInfo
- wincon/SetConsoleHistoryInfo
- SetConsoleHistoryInfo
MS-HAID:
- base.setconsolehistoryinfo
- consoles.setconsolehistoryinfo
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: db180f53-aa3c-4a91-bc3e-9f3f0bb7ab01
topic_type:
- apiref
api_name:
- SetConsoleHistoryInfo
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: 3c2dcce41994929292253793fe94512ab7bc5a01
ms.sourcegitcommit: 281eb1469f77ae4fb4c67806898e14eac440522a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2021
ms.locfileid: "100357648"
---
# <a name="setconsolehistoryinfo-function"></a><span data-ttu-id="9ce7b-104">SetConsoleHistoryInfo 函式</span><span class="sxs-lookup"><span data-stu-id="9ce7b-104">SetConsoleHistoryInfo function</span></span>

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

<span data-ttu-id="9ce7b-105">設定呼叫進程主控台的歷程記錄設定。</span><span class="sxs-lookup"><span data-stu-id="9ce7b-105">Sets the history settings for the calling process's console.</span></span>

## <a name="syntax"></a><span data-ttu-id="9ce7b-106">語法</span><span class="sxs-lookup"><span data-stu-id="9ce7b-106">Syntax</span></span>

```C
BOOL WINAPI SetConsoleHistoryInfo(
  _In_ PCONSOLE_HISTORY_INFO lpConsoleHistoryInfo
);
```

## <a name="parameters"></a><span data-ttu-id="9ce7b-107">參數</span><span class="sxs-lookup"><span data-stu-id="9ce7b-107">Parameters</span></span>

<span data-ttu-id="9ce7b-108">*lpConsoleHistoryInfo* \[在\]</span><span class="sxs-lookup"><span data-stu-id="9ce7b-108">*lpConsoleHistoryInfo* \[in\]</span></span>  
<span data-ttu-id="9ce7b-109">[**主控台歷程 \_ 記錄 \_ 資訊**](console-history-info.md)結構的指標，其中包含進程主控台的歷程記錄設定。</span><span class="sxs-lookup"><span data-stu-id="9ce7b-109">A pointer to a [**CONSOLE\_HISTORY\_INFO**](console-history-info.md) structure that contains the history settings for the process's console.</span></span>

## <a name="return-value"></a><span data-ttu-id="9ce7b-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="9ce7b-110">Return value</span></span>

<span data-ttu-id="9ce7b-111">如果函式成功，則傳回非零的值。</span><span class="sxs-lookup"><span data-stu-id="9ce7b-111">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="9ce7b-112">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="9ce7b-112">If the function fails, the return value is zero.</span></span> <span data-ttu-id="9ce7b-113">若要取得擴充的錯誤資訊，請呼叫 [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)。</span><span class="sxs-lookup"><span data-stu-id="9ce7b-113">To get extended error information, call [**GetLastError**](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).</span></span>

## <a name="remarks"></a><span data-ttu-id="9ce7b-114">備註</span><span class="sxs-lookup"><span data-stu-id="9ce7b-114">Remarks</span></span>

<span data-ttu-id="9ce7b-115">如果呼叫進程不是主控台進程，此函式會失敗，並將最後一個錯誤碼設定 **為 \_ \_ 拒絕存取錯誤**。</span><span class="sxs-lookup"><span data-stu-id="9ce7b-115">If the calling process is not a console process, the function fails and sets the last error code to **ERROR\_ACCESS\_DENIED**.</span></span>

[!INCLUDE [no-vt-equiv-shell-banner](./includes/no-vt-equiv-shell-banner.md)]

## <a name="requirements"></a><span data-ttu-id="9ce7b-116">規格需求</span><span class="sxs-lookup"><span data-stu-id="9ce7b-116">Requirements</span></span>

| &nbsp; | &nbsp; |
|-|-|
| <span data-ttu-id="9ce7b-117">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="9ce7b-117">Minimum supported client</span></span> | <span data-ttu-id="9ce7b-118">\[僅限 Windows Vista 桌面應用程式\]</span><span class="sxs-lookup"><span data-stu-id="9ce7b-118">Windows Vista \[desktop apps only\]</span></span> |
| <span data-ttu-id="9ce7b-119">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="9ce7b-119">Minimum supported server</span></span> | <span data-ttu-id="9ce7b-120">僅限 Windows Server 2008 \[ desktop 應用程式\]</span><span class="sxs-lookup"><span data-stu-id="9ce7b-120">Windows Server 2008 \[desktop apps only\]</span></span> |
| <span data-ttu-id="9ce7b-121">標頭</span><span class="sxs-lookup"><span data-stu-id="9ce7b-121">Header</span></span> | <span data-ttu-id="9ce7b-122">ConsoleApi3 .h (via WinCon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="9ce7b-122">ConsoleApi3.h (via WinCon.h, include Windows.h)</span></span> |
| <span data-ttu-id="9ce7b-123">程式庫</span><span class="sxs-lookup"><span data-stu-id="9ce7b-123">Library</span></span> | <span data-ttu-id="9ce7b-124">Kernel32.lib</span><span class="sxs-lookup"><span data-stu-id="9ce7b-124">Kernel32.lib</span></span> |
| <span data-ttu-id="9ce7b-125">DLL</span><span class="sxs-lookup"><span data-stu-id="9ce7b-125">DLL</span></span> | <span data-ttu-id="9ce7b-126">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="9ce7b-126">Kernel32.dll</span></span> |

## <a name="see-also"></a><span data-ttu-id="9ce7b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ce7b-127">See also</span></span>

[<span data-ttu-id="9ce7b-128">主控台函式</span><span class="sxs-lookup"><span data-stu-id="9ce7b-128">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="9ce7b-129">**主控台歷程 \_ 記錄 \_ 資訊**</span><span class="sxs-lookup"><span data-stu-id="9ce7b-129">**CONSOLE\_HISTORY\_INFO**</span></span>](console-history-info.md)

[<span data-ttu-id="9ce7b-130">**GetConsoleHistoryInfo**</span><span class="sxs-lookup"><span data-stu-id="9ce7b-130">**GetConsoleHistoryInfo**</span></span>](getconsolehistoryinfo.md)
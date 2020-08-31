---
title: SetConsoleMode 函式
description: 設定主控台之輸入緩衝區的輸入模式或主控台螢幕緩衝區的輸出模式。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi/SetConsoleMode
- wincon/SetConsoleMode
- SetConsoleMode
MS-HAID:
- '\_win32\_setconsolemode'
- base.setconsolemode
- consoles.setconsolemode
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 77508d58-8a7a-4c47-9ec5-dc61e5c4beac
topic_type:
- apiref
api_name:
- SetConsoleMode
api_location:
- Kernel32.dll
- API-MS-Win-Core-Console-l1-1-0.dll
- KernelBase.dll
- API-MS-Win-DownLevel-Kernel32-l1-1-0.dll
- MinKernelBase.dll
api_type:
- DllExport
ms.openlocfilehash: a524a9f730d53efd331a70693aadfeddeaad4cc0
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059535"
---
# <a name="setconsolemode-function"></a><span data-ttu-id="012a2-104">SetConsoleMode 函式</span><span class="sxs-lookup"><span data-stu-id="012a2-104">SetConsoleMode function</span></span>


<span data-ttu-id="012a2-105">設定主控台之輸入緩衝區的輸入模式或主控台螢幕緩衝區的輸出模式。</span><span class="sxs-lookup"><span data-stu-id="012a2-105">Sets the input mode of a console's input buffer or the output mode of a console screen buffer.</span></span>

<a name="syntax"></a><span data-ttu-id="012a2-106">語法</span><span class="sxs-lookup"><span data-stu-id="012a2-106">Syntax</span></span>
------

```C
BOOL WINAPI SetConsoleMode(
  _In_ HANDLE hConsoleHandle,
  _In_ DWORD  dwMode
);
```

<a name="parameters"></a><span data-ttu-id="012a2-107">參數</span><span class="sxs-lookup"><span data-stu-id="012a2-107">Parameters</span></span>
----------

<span data-ttu-id="012a2-108">*hConsoleHandle* \[在\]</span><span class="sxs-lookup"><span data-stu-id="012a2-108">*hConsoleHandle* \[in\]</span></span>  
<span data-ttu-id="012a2-109">主控台輸入緩衝區或主控台螢幕緩衝區的控制碼。</span><span class="sxs-lookup"><span data-stu-id="012a2-109">A handle to the console input buffer or a console screen buffer.</span></span> <span data-ttu-id="012a2-110">控制碼必須具有 **一般 \_ 讀取** 許可權。</span><span class="sxs-lookup"><span data-stu-id="012a2-110">The handle must have the **GENERIC\_READ** access right.</span></span> <span data-ttu-id="012a2-111">如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。</span><span class="sxs-lookup"><span data-stu-id="012a2-111">For more information, see [Console Buffer Security and Access Rights](console-buffer-security-and-access-rights.md).</span></span>

<span data-ttu-id="012a2-112">*dwMode* \[在\]</span><span class="sxs-lookup"><span data-stu-id="012a2-112">*dwMode* \[in\]</span></span>  
<span data-ttu-id="012a2-113">要設定的輸入或輸出模式。</span><span class="sxs-lookup"><span data-stu-id="012a2-113">The input or output mode to be set.</span></span> <span data-ttu-id="012a2-114">如果 *hConsoleHandle* 參數是輸入控制碼，此模式可以是下列一或多個值。</span><span class="sxs-lookup"><span data-stu-id="012a2-114">If the *hConsoleHandle* parameter is an input handle, the mode can be one or more of the following values.</span></span> <span data-ttu-id="012a2-115">建立主控台時，預設會啟用 [ **啟用 \_ 視窗 \_ 輸入]** 以外的所有輸入模式。</span><span class="sxs-lookup"><span data-stu-id="012a2-115">When a console is created, all input modes except **ENABLE\_WINDOW\_INPUT** are enabled by default.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="012a2-116">值</span><span class="sxs-lookup"><span data-stu-id="012a2-116">Value</span></span></th>
<th><span data-ttu-id="012a2-117">意義</span><span class="sxs-lookup"><span data-stu-id="012a2-117">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="012a2-118"><span id="ENABLE_ECHO_INPUT"></span><span id="enable_echo_input"></span>
<strong>ENABLE_ECHO_INPUT</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="012a2-118"><span id="ENABLE_ECHO_INPUT"></span><span id="enable_echo_input"></span>
<strong>ENABLE_ECHO_INPUT</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="012a2-119"><a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a>或<a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>函式讀取的字元會在讀取時寫入至作用中螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="012a2-119">Characters read by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function are written to the active screen buffer as they are read.</span></span> <span data-ttu-id="012a2-120">只有在同時啟用 <strong>ENABLE_LINE_INPUT</strong> 模式時，才能使用這個模式。</span><span class="sxs-lookup"><span data-stu-id="012a2-120">This mode can be used only if the <strong>ENABLE_LINE_INPUT</strong> mode is also enabled.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="012a2-121"><span id="ENABLE_EXTENDED_FLAGS"></span><span id="enable_extended_flags"></span>
<strong>ENABLE_EXTENDED_FLAGS</strong> 0x0080</span><span class="sxs-lookup"><span data-stu-id="012a2-121"><span id="ENABLE_EXTENDED_FLAGS"></span><span id="enable_extended_flags"></span>
<strong>ENABLE_EXTENDED_FLAGS</strong> 0x0080</span></span></td>
<td><p><span data-ttu-id="012a2-122">啟用或停用擴充旗標所需。</span><span class="sxs-lookup"><span data-stu-id="012a2-122">Required to enable or disable extended flags.</span></span> <span data-ttu-id="012a2-123">請參閱 <strong>ENABLE_INSERT_MODE</strong> 和 <strong>ENABLE_QUICK_EDIT_MODE</strong>。</span><span class="sxs-lookup"><span data-stu-id="012a2-123">See <strong>ENABLE_INSERT_MODE</strong> and <strong>ENABLE_QUICK_EDIT_MODE</strong>.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="012a2-124"><span id="ENABLE_INSERT_MODE"></span><span id="enable_insert_mode"></span>
<strong>ENABLE_INSERT_MODE</strong> 0x0020</span><span class="sxs-lookup"><span data-stu-id="012a2-124"><span id="ENABLE_INSERT_MODE"></span><span id="enable_insert_mode"></span>
<strong>ENABLE_INSERT_MODE</strong> 0x0020</span></span></td>
<td><p><span data-ttu-id="012a2-125">啟用時，在主控台視窗中輸入的文字將會插入目前的游標位置，並且不會覆寫該位置後面的所有文字。</span><span class="sxs-lookup"><span data-stu-id="012a2-125">When enabled, text entered in a console window will be inserted at the current cursor location and all text following that location will not be overwritten.</span></span> <span data-ttu-id="012a2-126">停用時，將會覆寫下列所有文字。</span><span class="sxs-lookup"><span data-stu-id="012a2-126">When disabled, all following text will be overwritten.</span></span></p>
<p><span data-ttu-id="012a2-127">若要啟用此模式，請使用 <code>ENABLE_INSERT_MODE | ENABLE_EXTENDED_FLAGS</code> 。</span><span class="sxs-lookup"><span data-stu-id="012a2-127">To enable this mode, use <code>ENABLE_INSERT_MODE | ENABLE_EXTENDED_FLAGS</code>.</span></span> <span data-ttu-id="012a2-128">若要停用此模式，請使用不含此旗標的 <strong>ENABLE_EXTENDED_FLAGS</strong> 。</span><span class="sxs-lookup"><span data-stu-id="012a2-128">To disable this mode, use <strong>ENABLE_EXTENDED_FLAGS</strong> without this flag.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="012a2-129"><span id="ENABLE_LINE_INPUT"></span><span id="enable_line_input"></span>
<strong>ENABLE_LINE_INPUT</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="012a2-129"><span id="ENABLE_LINE_INPUT"></span><span id="enable_line_input"></span>
<strong>ENABLE_LINE_INPUT</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="012a2-130">只有在讀取換行字元時，才會傳回 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> 或 <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> 函數。</span><span class="sxs-lookup"><span data-stu-id="012a2-130">The <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function returns only when a carriage return character is read.</span></span> <span data-ttu-id="012a2-131">如果停用此模式，則函式會在有一或多個字元可用時傳回。</span><span class="sxs-lookup"><span data-stu-id="012a2-131">If this mode is disabled, the functions return when one or more characters are available.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="012a2-132"><span id="ENABLE_MOUSE_INPUT"></span><span id="enable_mouse_input"></span>
<strong>ENABLE_MOUSE_INPUT</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="012a2-132"><span id="ENABLE_MOUSE_INPUT"></span><span id="enable_mouse_input"></span>
<strong>ENABLE_MOUSE_INPUT</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="012a2-133">如果滑鼠指標位於主控台視窗的框線內，且視窗具有鍵盤焦點，則滑鼠移動和按下按鈕所產生的滑鼠事件會放置在輸入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="012a2-133">If the mouse pointer is within the borders of the console window and the window has the keyboard focus, mouse events generated by mouse movement and button presses are placed in the input buffer.</span></span> <span data-ttu-id="012a2-134">這些事件會由 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> 或 <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>捨棄，即使啟用此模式也是如此。</span><span class="sxs-lookup"><span data-stu-id="012a2-134">These events are discarded by <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, even when this mode is enabled.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="012a2-135"><span id="ENABLE_PROCESSED_INPUT"></span><span id="enable_processed_input"></span>
<strong>ENABLE_PROCESSED_INPUT</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="012a2-135"><span id="ENABLE_PROCESSED_INPUT"></span><span id="enable_processed_input"></span>
<strong>ENABLE_PROCESSED_INPUT</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="012a2-136">CTRL + C 是由系統處理，而不是放在輸入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="012a2-136">CTRL+C is processed by the system and is not placed in the input buffer.</span></span> <span data-ttu-id="012a2-137">如果 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> 或 <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>正在讀取輸入緩衝區，則系統會處理其他控制索引鍵，而不會在 <strong>ReadFile</strong> 或 <strong>ReadConsole</strong> 緩衝區中傳回。</span><span class="sxs-lookup"><span data-stu-id="012a2-137">If the input buffer is being read by <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, other control keys are processed by the system and are not returned in the <strong>ReadFile</strong> or <strong>ReadConsole</strong> buffer.</span></span> <span data-ttu-id="012a2-138">如果也啟用了 <strong>ENABLE_LINE_INPUT</strong> 模式，則倒退鍵、換行字元和換行字元會由系統處理。</span><span class="sxs-lookup"><span data-stu-id="012a2-138">If the <strong>ENABLE_LINE_INPUT</strong> mode is also enabled, backspace, carriage return, and line feed characters are handled by the system.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="012a2-139"><span id="ENABLE_QUICK_EDIT_MODE"></span><span id="enable_quick_edit_mode"></span>
<strong>ENABLE_QUICK_EDIT_MODE</strong> 0x0040</span><span class="sxs-lookup"><span data-stu-id="012a2-139"><span id="ENABLE_QUICK_EDIT_MODE"></span><span id="enable_quick_edit_mode"></span>
<strong>ENABLE_QUICK_EDIT_MODE</strong> 0x0040</span></span></td>
<td><p><span data-ttu-id="012a2-140">這個旗標可讓使用者使用滑鼠來選取和編輯文字。</span><span class="sxs-lookup"><span data-stu-id="012a2-140">This flag enables the user to use the mouse to select and edit text.</span></span></p>
<p><span data-ttu-id="012a2-141">若要啟用此模式，請使用 <code>ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS</code> 。</span><span class="sxs-lookup"><span data-stu-id="012a2-141">To enable this mode, use <code>ENABLE_QUICK_EDIT_MODE | ENABLE_EXTENDED_FLAGS</code>.</span></span> <span data-ttu-id="012a2-142">若要停用此模式，請使用不含此旗標的 <strong>ENABLE_EXTENDED_FLAGS</strong> 。</span><span class="sxs-lookup"><span data-stu-id="012a2-142">To disable this mode, use <strong>ENABLE_EXTENDED_FLAGS</strong> without this flag.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="012a2-143"><span id="ENABLE_WINDOW_INPUT"></span><span id="enable_window_input"></span>
<strong>ENABLE_WINDOW_INPUT</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="012a2-143"><span id="ENABLE_WINDOW_INPUT"></span><span id="enable_window_input"></span>
<strong>ENABLE_WINDOW_INPUT</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="012a2-144">變更控制台螢幕緩衝區大小的使用者互動會在主控台&#39;s 輸入緩衝區中報告。</span><span class="sxs-lookup"><span data-stu-id="012a2-144">User interactions that change the size of the console screen buffer are reported in the console&#39;s input buffer.</span></span> <span data-ttu-id="012a2-145">您可以使用 <a href="readconsoleinput.md" data-raw-source="[&lt;strong&gt;ReadConsoleInput&lt;/strong&gt;](readconsoleinput.md)"><strong>ReadConsoleInput</strong></a> 函式，而不是使用 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> 或 <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>的應用程式，從輸入緩衝區讀取這些事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="012a2-145">Information about these events can be read from the input buffer by applications using the <a href="readconsoleinput.md" data-raw-source="[&lt;strong&gt;ReadConsoleInput&lt;/strong&gt;](readconsoleinput.md)"><strong>ReadConsoleInput</strong></a> function, but not by those using <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="012a2-146"><span id="ENABLE_VIRTUAL_TERMINAL_INPUT"></span><span id="enable_virtual_terminal_input"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_INPUT</strong> 0x0200</span><span class="sxs-lookup"><span data-stu-id="012a2-146"><span id="ENABLE_VIRTUAL_TERMINAL_INPUT"></span><span id="enable_virtual_terminal_input"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_INPUT</strong> 0x0200</span></span></td>
<td><p><span data-ttu-id="012a2-147">設定此旗標會指示虛擬終端處理引擎將主控台視窗收到的使用者輸入轉換為主控台虛擬終端機序列，可透過 ReadFile 或 ReadConsole 函式由支援的應用程式抓取。</span><span class="sxs-lookup"><span data-stu-id="012a2-147">Setting this flag directs the Virtual Terminal processing engine to convert user input received by the console window into Console Virtual Terminal Sequences that can be retrieved by a supporting application through ReadFile or ReadConsole functions.</span></span></p>
<p><span data-ttu-id="012a2-148">此旗標的一般用法是與輸出控制碼上的 ENABLE_VIRTUAL_TERMINAL_PROCESSING 搭配使用，以連接至透過虛擬終端機序列獨佔通訊的應用程式。</span><span class="sxs-lookup"><span data-stu-id="012a2-148">The typical usage of this flag is intended in conjunction with ENABLE_VIRTUAL_TERMINAL_PROCESSING on the output handle to connect to an application that communicates exclusively via virtual terminal sequences.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
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

 

<span data-ttu-id="012a2-149">如果 *hConsoleHandle* 參數是螢幕緩衝區控制碼，此模式可以是下列其中一個或多個值。</span><span class="sxs-lookup"><span data-stu-id="012a2-149">If the *hConsoleHandle* parameter is a screen buffer handle, the mode can be one or more of the following values.</span></span> <span data-ttu-id="012a2-150">建立螢幕緩衝區時，預設會啟用這兩種輸出模式。</span><span class="sxs-lookup"><span data-stu-id="012a2-150">When a screen buffer is created, both output modes are enabled by default.</span></span>

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><span data-ttu-id="012a2-151">值</span><span class="sxs-lookup"><span data-stu-id="012a2-151">Value</span></span></th>
<th><span data-ttu-id="012a2-152">意義</span><span class="sxs-lookup"><span data-stu-id="012a2-152">Meaning</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span data-ttu-id="012a2-153"><span id="ENABLE_PROCESSED_OUTPUT"></span><span id="enable_processed_output"></span>
<strong>ENABLE_PROCESSED_OUTPUT</strong> 0x0001</span><span class="sxs-lookup"><span data-stu-id="012a2-153"><span id="ENABLE_PROCESSED_OUTPUT"></span><span id="enable_processed_output"></span>
<strong>ENABLE_PROCESSED_OUTPUT</strong> 0x0001</span></span></td>
<td><p><span data-ttu-id="012a2-154">系統會檢查 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> 或 <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> 函式或 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> 或 <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> 函式所寫入的字元是否有 ASCII 控制順序，並執行正確的動作。</span><span class="sxs-lookup"><span data-stu-id="012a2-154">Characters written by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> function or echoed by the <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a> function are examined for ASCII control sequences and the correct action is performed.</span></span> <span data-ttu-id="012a2-155">會處理倒退鍵、定位字元、鐘、換行字元和換行字元。</span><span class="sxs-lookup"><span data-stu-id="012a2-155">Backspace, tab, bell, carriage return, and line feed characters are processed.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="012a2-156"><span id="ENABLE_WRAP_AT_EOL_OUTPUT"></span><span id="enable_wrap_at_eol_output"></span>
<strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong> 0x0002</span><span class="sxs-lookup"><span data-stu-id="012a2-156"><span id="ENABLE_WRAP_AT_EOL_OUTPUT"></span><span id="enable_wrap_at_eol_output"></span>
<strong>ENABLE_WRAP_AT_EOL_OUTPUT</strong> 0x0002</span></span></td>
<td><p><span data-ttu-id="012a2-157">使用 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> 或 <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> 或使用 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> 或 <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>來進行寫入時，資料指標會在到達目前資料列的結尾時移至下一個資料列的開頭。</span><span class="sxs-lookup"><span data-stu-id="012a2-157">When writing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a> or echoing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365467" data-raw-source="[&lt;strong&gt;ReadFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365467)"><strong>ReadFile</strong></a> or <a href="readconsole.md" data-raw-source="[&lt;strong&gt;ReadConsole&lt;/strong&gt;](readconsole.md)"><strong>ReadConsole</strong></a>, the cursor moves to the beginning of the next row when it reaches the end of the current row.</span></span> <span data-ttu-id="012a2-158">這會使主控台視窗中顯示的資料列在游標前進到視窗中的最後一個資料列之後自動向上滾動。</span><span class="sxs-lookup"><span data-stu-id="012a2-158">This causes the rows displayed in the console window to scroll up automatically when the cursor advances beyond the last row in the window.</span></span> <span data-ttu-id="012a2-159">它也會使主控台畫面緩衝區的內容 (捨棄主控台畫面緩衝區的頂端列，) 當游標前進到主控台螢幕緩衝區中的最後一個資料列之後。</span><span class="sxs-lookup"><span data-stu-id="012a2-159">It also causes the contents of the console screen buffer to scroll up (discarding the top row of the console screen buffer) when the cursor advances beyond the last row in the console screen buffer.</span></span> <span data-ttu-id="012a2-160">如果停用此模式，則會以任何後續字元覆寫資料列中的最後一個字元。</span><span class="sxs-lookup"><span data-stu-id="012a2-160">If this mode is disabled, the last character in the row is overwritten with any subsequent characters.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="012a2-161"><span id="ENABLE_VIRTUAL_TERMINAL_PROCESSING"></span><span id="enable_virtual_terminal_processing"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_PROCESSING</strong> 0x0004</span><span class="sxs-lookup"><span data-stu-id="012a2-161"><span id="ENABLE_VIRTUAL_TERMINAL_PROCESSING"></span><span id="enable_virtual_terminal_processing"></span>
<strong>ENABLE_VIRTUAL_TERMINAL_PROCESSING</strong> 0x0004</span></span></td>
<td><p><span data-ttu-id="012a2-162">使用 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> 或 <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>進行寫入時，會剖析字元，以控制資料指標移動、色彩/字型模式，以及可透過現有的主控台 api 執行的類似控制字元序列。</span><span class="sxs-lookup"><span data-stu-id="012a2-162">When writing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, characters are parsed for VT100 and similar control character sequences that control cursor movement, color/font mode, and other operations that can also be performed via the existing Console APIs.</span></span> <span data-ttu-id="012a2-163">如需詳細資訊，請參閱 <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">主控台虛擬終端機序列</a>。</span><span class="sxs-lookup"><span data-stu-id="012a2-163">For more information, see <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">Console Virtual Terminal Sequences</a>.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="012a2-164"><span id="DISABLE_NEWLINE_AUTO_RETURN"></span><span id="disable_newline_auto_return"></span>
<strong>DISABLE_NEWLINE_AUTO_RETURN</strong> 0x0008</span><span class="sxs-lookup"><span data-stu-id="012a2-164"><span id="DISABLE_NEWLINE_AUTO_RETURN"></span><span id="disable_newline_auto_return"></span>
<strong>DISABLE_NEWLINE_AUTO_RETURN</strong> 0x0008</span></span></td>
<td><p><span data-ttu-id="012a2-165">使用 <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> 或 <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>進行寫入時，會將額外的狀態加入至行尾換行，以延遲游標移動和緩衝區滾動作業。</span><span class="sxs-lookup"><span data-stu-id="012a2-165">When writing with <a href="https://msdn.microsoft.com/library/windows/desktop/aa365747" data-raw-source="[&lt;strong&gt;WriteFile&lt;/strong&gt;](https://msdn.microsoft.com/library/windows/desktop/aa365747)"><strong>WriteFile</strong></a> or <a href="writeconsole.md" data-raw-source="[&lt;strong&gt;WriteConsole&lt;/strong&gt;](writeconsole.md)"><strong>WriteConsole</strong></a>, this adds an additional state to end-of-line wrapping that can delay the cursor move and buffer scroll operations.</span></span></p>
<p><span data-ttu-id="012a2-166">一般來說，當 ENABLE_WRAP_AT_EOL_OUTPUT 設定且文字到達行尾時，游標會立即移到下一行，而且緩衝區的內容會以一行滾動。</span><span class="sxs-lookup"><span data-stu-id="012a2-166">Normally when ENABLE_WRAP_AT_EOL_OUTPUT is set and text reaches the end of the line, the cursor will immediately move to the next line and the contents of the buffer will scroll up by one line.</span></span> <span data-ttu-id="012a2-167">相較于設定此旗標，捲軸操作和游標移動會延遲到下一個字元抵達為止。</span><span class="sxs-lookup"><span data-stu-id="012a2-167">In contrast with this flag set, the scroll operation and cursor move is delayed until the next character arrives.</span></span> <span data-ttu-id="012a2-168">書寫的字元將列印在行的最後一個位置，而游標會維持在此字元的上方，就像 ENABLE_WRAP_AT_EOL_OUTPUT 是 off 一樣，但是下一個可列印的字元將會列印成 ENABLE_WRAP_AT_EOL_OUTPUT 開啟。</span><span class="sxs-lookup"><span data-stu-id="012a2-168">The written character will be printed in the final position on the line and the cursor will remain above this character as if ENABLE_WRAP_AT_EOL_OUTPUT was off, but the next printable character will be printed as if ENABLE_WRAP_AT_EOL_OUTPUT is on.</span></span> <span data-ttu-id="012a2-169">不會進行覆寫。</span><span class="sxs-lookup"><span data-stu-id="012a2-169">No overwrite will occur.</span></span> <span data-ttu-id="012a2-170">明確地說，游標會迅速往下移動到下一行，視需要執行捲軸、列印字元，然後將游標前移一個位置。</span><span class="sxs-lookup"><span data-stu-id="012a2-170">Specifically, the cursor quickly advances down to the following line, a scroll is performed if necessary, the character is printed, and the cursor advances one more position.</span></span></p>
<p><span data-ttu-id="012a2-171">此旗標的一般用法是與設定 ENABLE_VIRTUAL_TERMINAL_PROCESSING 搭配使用，以更好的方式模擬終端機模擬器，也就是在右下) 角將畫面上的最後一個字元寫入 (，而不觸發立即滾動的行為是想要的行為。</span><span class="sxs-lookup"><span data-stu-id="012a2-171">The typical usage of this flag is intended in conjunction with setting ENABLE_VIRTUAL_TERMINAL_PROCESSING to better emulate a terminal emulator where writing the final character on the screen (in the bottom right corner) without triggering an immediate scroll is the desired behavior.</span></span></p></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="012a2-172"><span id="ENABLE_LVB_GRID_WORLDWIDE"></span><span id="enable_lvb_grid_worldwide"></span>
<strong>ENABLE_LVB_GRID_WORLDWIDE</strong> 0x0010</span><span class="sxs-lookup"><span data-stu-id="012a2-172"><span id="ENABLE_LVB_GRID_WORLDWIDE"></span><span id="enable_lvb_grid_worldwide"></span>
<strong>ENABLE_LVB_GRID_WORLDWIDE</strong> 0x0010</span></span></td>
<td><p><span data-ttu-id="012a2-173">撰寫字元屬性（包括 <a href="writeconsoleoutput.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutput&lt;/strong&gt;](writeconsoleoutput.md)"><strong>WriteConsoleOutput</strong></a> 和 <a href="writeconsoleoutputattribute.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutputAttribute&lt;/strong&gt;](writeconsoleoutputattribute.md)"><strong>WriteConsoleOutputAttribute</strong></a> ）的 api，可讓您使用 <a href="https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes" data-raw-source="[character attributes](https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes)">字元屬性</a> 的旗標來調整文字的前景和背景色彩。</span><span class="sxs-lookup"><span data-stu-id="012a2-173">The APIs for writing character attributes including <a href="writeconsoleoutput.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutput&lt;/strong&gt;](writeconsoleoutput.md)"><strong>WriteConsoleOutput</strong></a> and <a href="writeconsoleoutputattribute.md" data-raw-source="[&lt;strong&gt;WriteConsoleOutputAttribute&lt;/strong&gt;](writeconsoleoutputattribute.md)"><strong>WriteConsoleOutputAttribute</strong></a> allow the usage of flags from <a href="https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes" data-raw-source="[character attributes](https://msdn.microsoft.com/library/windows/desktop/ms682088.aspx#_win32_font_attributes)">character attributes</a> to adjust the color of the foreground and background of text.</span></span> <span data-ttu-id="012a2-174">此外，使用 COMMON_LVB 前置詞指定了 DBCS 旗標的範圍。</span><span class="sxs-lookup"><span data-stu-id="012a2-174">Additionally, a range of DBCS flags was specified with the COMMON_LVB prefix.</span></span> <span data-ttu-id="012a2-175">在過去，這些旗標只會在中文、日文和韓文語言的 DBCS 字碼頁中正常進行。</span><span class="sxs-lookup"><span data-stu-id="012a2-175">Historically, these flags only functioned in DBCS code pages for Chinese, Japanese, and Korean languages.</span></span></p>
<p><span data-ttu-id="012a2-176">除了開頭的位元組和尾端的位元組旗標以外，其餘的旗標描述線條繪製和反向影片 (交換前景和背景色彩) 可能有助於其他語言強調輸出的部分。</span><span class="sxs-lookup"><span data-stu-id="012a2-176">With exception of the leading byte and trailing byte flags, the remaining flags describing line drawing and reverse video (swap foreground and background colors) can be useful for other languages to emphasize portions of output.</span></span></p>
<p><span data-ttu-id="012a2-177">設定此主控台模式旗標，可讓您在每個語言的每個字碼頁中使用這些屬性。</span><span class="sxs-lookup"><span data-stu-id="012a2-177">Setting this console mode flag will allow these attributes to be used in every code page on every language.</span></span></p>
<p><span data-ttu-id="012a2-178">預設為關閉，以維持與過去利用主控台忽略這些旗標的已知應用程式之間的相容性，這些旗標會在非 CJK 電腦上略過這些旗標，以基於自己的目的或意外的方式儲存這些欄位中的位。</span><span class="sxs-lookup"><span data-stu-id="012a2-178">It is off by default to maintain compatibility with known applications that have historically taken advantage of the console ignoring these flags on non-CJK machines to store bits in these fields for their own purposes or by accident.</span></span></p>
<p><span data-ttu-id="012a2-179">請注意，使用 ENABLE_VIRTUAL_TERMINAL_PROCESSING 模式可能會導致設定 LVB 格線和反向影片旗標，但如果連結的應用程式透過 <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">主控台虛擬終端機序列</a>要求底線或反向影片，則此旗標仍會關閉。</span><span class="sxs-lookup"><span data-stu-id="012a2-179">Note that using the ENABLE_VIRTUAL_TERMINAL_PROCESSING mode can result in LVB grid and reverse video flags being set while this flag is still off if the attached application requests underlining or inverse video via <a href="console-virtual-terminal-sequences.md" data-raw-source="[Console Virtual Terminal Sequences](console-virtual-terminal-sequences.md)">Console Virtual Terminal Sequences</a>.</span></span></p></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

 

<a name="return-value"></a><span data-ttu-id="012a2-180">傳回值</span><span class="sxs-lookup"><span data-stu-id="012a2-180">Return value</span></span>
------------

<span data-ttu-id="012a2-181">如果函式成功，則傳回值為非零。</span><span class="sxs-lookup"><span data-stu-id="012a2-181">If the function succeeds, the return value is nonzero.</span></span>

<span data-ttu-id="012a2-182">如果此函式失敗，則傳回值為零。</span><span class="sxs-lookup"><span data-stu-id="012a2-182">If the function fails, the return value is zero.</span></span> <span data-ttu-id="012a2-183">若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。</span><span class="sxs-lookup"><span data-stu-id="012a2-183">To get extended error information, call [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360).</span></span>

<a name="remarks"></a><span data-ttu-id="012a2-184">備註</span><span class="sxs-lookup"><span data-stu-id="012a2-184">Remarks</span></span>
-------

<span data-ttu-id="012a2-185">主控台包含輸入緩衝區和一或多個螢幕緩衝區。</span><span class="sxs-lookup"><span data-stu-id="012a2-185">A console consists of an input buffer and one or more screen buffers.</span></span> <span data-ttu-id="012a2-186">主控台緩衝區的模式會決定主控台在輸入和輸出 (i/o) 作業時的行為。</span><span class="sxs-lookup"><span data-stu-id="012a2-186">The mode of a console buffer determines how the console behaves during input and output (I/O) operations.</span></span> <span data-ttu-id="012a2-187">有一組旗標常數用於輸入控制碼，而另一組則是與螢幕緩衝區 (輸出) 控制碼一起使用。</span><span class="sxs-lookup"><span data-stu-id="012a2-187">One set of flag constants is used with input handles, and another set is used with screen buffer (output) handles.</span></span> <span data-ttu-id="012a2-188">設定一個螢幕緩衝區的輸出模式，並不會影響其他螢幕緩衝區的輸出模式。</span><span class="sxs-lookup"><span data-stu-id="012a2-188">Setting the output modes of one screen buffer does not affect the output modes of other screen buffers.</span></span>

<span data-ttu-id="012a2-189">「 **啟用 \_ 行 \_ 輸入** 」和「 **啟用 \_ ECHO \_ 輸入** 」模式只會影響使用 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 或 [**ReadConsole**](readconsole.md) 從主控台的輸入緩衝區讀取的進程。</span><span class="sxs-lookup"><span data-stu-id="012a2-189">The **ENABLE\_LINE\_INPUT** and **ENABLE\_ECHO\_INPUT** modes only affect processes that use [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) to read from the console's input buffer.</span></span> <span data-ttu-id="012a2-190">同樣地， **啟用已 \_ 處理的 \_ 輸入** 模式主要會影響 **ReadFile** 和 **ReadConsole** 使用者，不同之處在于它也會決定在輸入緩衝區中是否報告 Ctrl + C 輸入 (由) [**ReadConsoleInput**](readconsoleinput.md) 函式讀取，或是傳遞至應用程式所定義的 [**HandlerRoutine**](handlerroutine.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="012a2-190">Similarly, the **ENABLE\_PROCESSED\_INPUT** mode primarily affects **ReadFile** and **ReadConsole** users, except that it also determines whether Ctrl+C input is reported in the input buffer (to be read by the [**ReadConsoleInput**](readconsoleinput.md) function) or is passed to a [**HandlerRoutine**](handlerroutine.md) function defined by the application.</span></span>

<span data-ttu-id="012a2-191">[ **啟用 \_ 視窗 \_ 輸入]** 和 [ **啟用 \_ 滑鼠 \_ 輸入** ] 模式會決定是否要在輸入緩衝區中報告與視窗調整大小和滑鼠動作相關的使用者互動。</span><span class="sxs-lookup"><span data-stu-id="012a2-191">The **ENABLE\_WINDOW\_INPUT** and **ENABLE\_MOUSE\_INPUT** modes determine whether user interactions involving window resizing and mouse actions are reported in the input buffer or discarded.</span></span> <span data-ttu-id="012a2-192">這些事件可由 [**ReadConsoleInput**](readconsoleinput.md)讀取，但一律會依 [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) 和 [**ReadConsole**](readconsole.md)進行篩選。</span><span class="sxs-lookup"><span data-stu-id="012a2-192">These events can be read by [**ReadConsoleInput**](readconsoleinput.md), but they are always filtered by [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) and [**ReadConsole**](readconsole.md).</span></span>

<span data-ttu-id="012a2-193">在\*\* \_ \_ \_ EOL \_ 輸出**模式下**啟用已處理的 \_ \_ 輸出\*\*和啟用 WRAP，只會影響使用[**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467)或[**ReadConsole**](readconsole.md)和[**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747)或[**WriteConsole**](writeconsole.md)的進程。</span><span class="sxs-lookup"><span data-stu-id="012a2-193">The **ENABLE\_PROCESSED\_OUTPUT** and **ENABLE\_WRAP\_AT\_EOL\_OUTPUT** modes only affect processes using [**ReadFile**](https://msdn.microsoft.com/library/windows/desktop/aa365467) or [**ReadConsole**](readconsole.md) and [**WriteFile**](https://msdn.microsoft.com/library/windows/desktop/aa365747) or [**WriteConsole**](writeconsole.md).</span></span>

<span data-ttu-id="012a2-194">若要判斷主控台輸入緩衝區或螢幕緩衝區的目前模式，請使用 [**GetConsoleMode**](getconsolemode.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="012a2-194">To determine the current mode of a console input buffer or a screen buffer, use the [**GetConsoleMode**](getconsolemode.md) function.</span></span>

<a name="examples"></a><span data-ttu-id="012a2-195">範例</span><span class="sxs-lookup"><span data-stu-id="012a2-195">Examples</span></span>
--------

<span data-ttu-id="012a2-196">如需範例，請參閱 [讀取輸入緩衝區事件](reading-input-buffer-events.md)。</span><span class="sxs-lookup"><span data-stu-id="012a2-196">For an example, see [Reading Input Buffer Events](reading-input-buffer-events.md).</span></span>

<a name="requirements"></a><span data-ttu-id="012a2-197">規格需求</span><span class="sxs-lookup"><span data-stu-id="012a2-197">Requirements</span></span>
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><span data-ttu-id="012a2-198">最低支援的用戶端</span><span class="sxs-lookup"><span data-stu-id="012a2-198">Minimum supported client</span></span></p></td>
<td><p><span data-ttu-id="012a2-199">Windows 2000 Professional [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="012a2-199">Windows 2000 Professional [desktop apps only]</span></span></p></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="012a2-200">最低支援的伺服器</span><span class="sxs-lookup"><span data-stu-id="012a2-200">Minimum supported server</span></span></p></td>
<td><p><span data-ttu-id="012a2-201">Windows 2000 伺服器 [僅限桌面應用程式]</span><span class="sxs-lookup"><span data-stu-id="012a2-201">Windows 2000 Server [desktop apps only]</span></span></p></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="012a2-202">標頭</span><span class="sxs-lookup"><span data-stu-id="012a2-202">Header</span></span></p></td>
<td><span data-ttu-id="012a2-203">ConsoleApi .h (via Wincon，包括 Windows .h) </span><span class="sxs-lookup"><span data-stu-id="012a2-203">ConsoleApi.h (via Wincon.h, include Windows.h)</span></span></td>
</tr>
<tr class="even">
<td><p><span data-ttu-id="012a2-204">程式庫</span><span class="sxs-lookup"><span data-stu-id="012a2-204">Library</span></span></p></td>
<td><span data-ttu-id="012a2-205">Kernel32.dll .lib</span><span class="sxs-lookup"><span data-stu-id="012a2-205">Kernel32.lib</span></span></td>
</tr>
<tr class="odd">
<td><p><span data-ttu-id="012a2-206">DLL</span><span class="sxs-lookup"><span data-stu-id="012a2-206">DLL</span></span></p></td>
<td><span data-ttu-id="012a2-207">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="012a2-207">Kernel32.dll</span></span></td>
</tr>
<tr class="even">
</tr>
<tr class="odd">
</tr>
<tr class="even">
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span data-ttu-id="012a2-208"><span id="see_also"></span>另請參閱</span><span class="sxs-lookup"><span data-stu-id="012a2-208"><span id="see_also"></span>See also</span></span>


[<span data-ttu-id="012a2-209">主控台功能</span><span class="sxs-lookup"><span data-stu-id="012a2-209">Console Functions</span></span>](console-functions.md)

[<span data-ttu-id="012a2-210">主控台模式</span><span class="sxs-lookup"><span data-stu-id="012a2-210">Console Modes</span></span>](console-modes.md)

[<span data-ttu-id="012a2-211">**GetConsoleMode**</span><span class="sxs-lookup"><span data-stu-id="012a2-211">**GetConsoleMode**</span></span>](getconsolemode.md)

[<span data-ttu-id="012a2-212">**HandlerRoutine**</span><span class="sxs-lookup"><span data-stu-id="012a2-212">**HandlerRoutine**</span></span>](handlerroutine.md)

[<span data-ttu-id="012a2-213">**ReadConsole**</span><span class="sxs-lookup"><span data-stu-id="012a2-213">**ReadConsole**</span></span>](readconsole.md)

[<span data-ttu-id="012a2-214">**ReadConsoleInput**</span><span class="sxs-lookup"><span data-stu-id="012a2-214">**ReadConsoleInput**</span></span>](readconsoleinput.md)

[<span data-ttu-id="012a2-215">**ReadFile**</span><span class="sxs-lookup"><span data-stu-id="012a2-215">**ReadFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365467)

[<span data-ttu-id="012a2-216">**WriteConsole**</span><span class="sxs-lookup"><span data-stu-id="012a2-216">**WriteConsole**</span></span>](writeconsole.md)

[<span data-ttu-id="012a2-217">**WriteFile**</span><span class="sxs-lookup"><span data-stu-id="012a2-217">**WriteFile**</span></span>](https://msdn.microsoft.com/library/windows/desktop/aa365747)

 

 





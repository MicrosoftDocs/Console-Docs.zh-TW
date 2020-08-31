---
title: 主控台輸入緩衝區
description: 每個主控台都有一個輸入緩衝區，其中包含輸入事件記錄的佇列。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
MS-HAID:
- '\_win32\_console\_input\_buffer'
- base.console\_input\_buffer
- consoles.console\_input\_buffer
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 6e536658-8a27-478e-82ee-d1e11f351301
ms.openlocfilehash: 0a4843279b97da0ca6db50a9ccfa3de644044b68
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059315"
---
# <a name="console-input-buffer"></a><span data-ttu-id="15255-104">主控台輸入緩衝區</span><span class="sxs-lookup"><span data-stu-id="15255-104">Console Input Buffer</span></span>


<span data-ttu-id="15255-105">每個主控台都有一個輸入緩衝區，其中包含輸入事件記錄的佇列。</span><span class="sxs-lookup"><span data-stu-id="15255-105">Each console has an input buffer that contains a queue of input event records.</span></span> <span data-ttu-id="15255-106">當主控台的視窗具有鍵盤焦點時，主控台會將每個輸入事件格式化 (例如單一按鍵、移動滑鼠，或是按下滑鼠按鍵，) 為它放在主控台輸入緩衝區中的輸入記錄。</span><span class="sxs-lookup"><span data-stu-id="15255-106">When a console's window has the keyboard focus, a console formats each input event (such as a single keystroke, a movement of the mouse, or a mouse-button click) as an input record that it places in the console's input buffer.</span></span>

<span data-ttu-id="15255-107">應用程式可以使用 [高階主控台 i/o](high-level-console-input-and-output-functions.md)函式來間接存取主控台的輸入緩衝區，或直接使用 [低層級的主控台輸入功能](low-level-console-input-functions.md)來存取。</span><span class="sxs-lookup"><span data-stu-id="15255-107">Applications can access a console's input buffer indirectly by using the [high-level console I/O functions](high-level-console-input-and-output-functions.md), or directly by using the [low-level console input functions](low-level-console-input-functions.md).</span></span> <span data-ttu-id="15255-108">高層級輸入函式會篩選和處理輸入緩衝區中的資料，只傳回輸入字元的資料流程。</span><span class="sxs-lookup"><span data-stu-id="15255-108">The high-level input functions filter and process the data in the input buffer, returning only a stream of input characters.</span></span> <span data-ttu-id="15255-109">低層級的輸入函數可讓應用程式直接從主控台的輸入緩衝區讀取輸入記錄，或將輸入記錄放入輸入緩衝區。</span><span class="sxs-lookup"><span data-stu-id="15255-109">The low-level input functions enable applications to read input records directly from a console's input buffer, or to place input records into the input buffer.</span></span> <span data-ttu-id="15255-110">若要開啟主控台輸入緩衝區的控制碼，請在[**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858)函數的呼叫中指定**CONIN $** 值。</span><span class="sxs-lookup"><span data-stu-id="15255-110">To open a handle to a console's input buffer, specify the **CONIN$** value in a call to the [**CreateFile**](https://msdn.microsoft.com/library/windows/desktop/aa363858) function.</span></span>

<span data-ttu-id="15255-111">輸入記錄是一種結構，其中包含 (鍵盤、滑鼠、視窗調整大小、焦點或功能表) 事件時所發生之事件種類的相關資訊，以及事件的特定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="15255-111">An input record is a structure containing information about the type of event that occurred (keyboard, mouse, window resizing, focus, or menu event) as well as specific details about the event.</span></span> <span data-ttu-id="15255-112">[**輸入 \_ 記錄**](input-record-str.md)結構中的 **「事件種類」成員會**指出記錄中包含哪一種類型的事件。</span><span class="sxs-lookup"><span data-stu-id="15255-112">The **EventType** member in an [**INPUT\_RECORD**](input-record-str.md) structure indicates which type of event is contained in the record.</span></span>

<span data-ttu-id="15255-113">焦點和功能表事件都放在主控台的輸入緩衝區中，供系統內部使用，且應用程式應予以忽略。</span><span class="sxs-lookup"><span data-stu-id="15255-113">Focus and menu events are placed in a console's input buffer for internal use by the system and should be ignored by applications.</span></span>

## <a name="span-idkeyboard_eventsspanspan-idkeyboard_eventsspanspan-idkeyboard_eventsspankeyboard-events"></a><span data-ttu-id="15255-114"><span id="Keyboard_Events"></span><span id="keyboard_events"></span><span id="KEYBOARD_EVENTS"></span>鍵盤事件</span><span class="sxs-lookup"><span data-stu-id="15255-114"><span id="Keyboard_Events"></span><span id="keyboard_events"></span><span id="KEYBOARD_EVENTS"></span>Keyboard Events</span></span>


<span data-ttu-id="15255-115">當按下或放開任何按鍵時，就會產生鍵盤事件;這包括控制項索引鍵。</span><span class="sxs-lookup"><span data-stu-id="15255-115">Keyboard events are generated when any key is pressed or released; this includes control keys.</span></span> <span data-ttu-id="15255-116">不過，當按下並放開時，ALT 鍵對系統具有特殊意義，而不會與另一個字元合併，且不會傳遞至應用程式。</span><span class="sxs-lookup"><span data-stu-id="15255-116">However, the ALT key has special meaning to the system when pressed and released without being combined with another character, and it is not passed through to the application.</span></span> <span data-ttu-id="15255-117">此外，如果輸入控制碼處於處理模式，則不會傳遞 CTRL + C 按鍵組合。</span><span class="sxs-lookup"><span data-stu-id="15255-117">Also, the CTRL+C key combination is not passed through if the input handle is in processed mode.</span></span>

<span data-ttu-id="15255-118">如果輸入事件是按鍵，[**輸入 \_ 記錄**](input-record-str.md)中的**事件**成員就是包含下列資訊的[**關鍵 \_ 事件 \_ 記錄**](key-event-record-str.md)結構：</span><span class="sxs-lookup"><span data-stu-id="15255-118">If the input event is a keystroke, the **Event** member in [**INPUT\_RECORD**](input-record-str.md) is a [**KEY\_EVENT\_RECORD**](key-event-record-str.md) structure containing the following information:</span></span>

- <span data-ttu-id="15255-119">指出是否已按下或放開按鍵的布林值。</span><span class="sxs-lookup"><span data-stu-id="15255-119">A Boolean value indicating whether the key was pressed or released.</span></span>
- <span data-ttu-id="15255-120">當索引鍵被關閉時，可以大於1的重複計數。</span><span class="sxs-lookup"><span data-stu-id="15255-120">A repeat count that can be greater than one when a key is held down.</span></span>
- <span data-ttu-id="15255-121">虛擬金鑰程式碼，以與裝置無關的方式識別指定的金鑰。</span><span class="sxs-lookup"><span data-stu-id="15255-121">The virtual-key code, identifying the given key in a device-independent manner.</span></span>
- <span data-ttu-id="15255-122">虛擬掃描程式碼，表示鍵盤硬體所產生的裝置相依值。</span><span class="sxs-lookup"><span data-stu-id="15255-122">The virtual-scan code, indicating the device-dependent value generated by the keyboard hardware.</span></span>
- <span data-ttu-id="15255-123">翻譯的 Unicode™或 ANSI 字元。</span><span class="sxs-lookup"><span data-stu-id="15255-123">The translated Unicode™ or ANSI character.</span></span>
- <span data-ttu-id="15255-124">旗標變數，表示控制項索引鍵的狀態 (ALT、CTRL、SHIFT、NUM LOCK、SCROLL LOCK 和 CAPS LOCK 索引鍵) 並指出是否已按下增強的按鍵。</span><span class="sxs-lookup"><span data-stu-id="15255-124">A flag variable indicating the state of the control keys (the ALT, CTRL, SHIFT, NUM LOCK, SCROLL LOCK, and CAPS LOCK keys) and indicating whether an enhanced key was pressed.</span></span> <span data-ttu-id="15255-125">適用于 IBM® 101-金鑰和102金鑰鍵盤的增強金鑰為 )  ( 數位鍵台左邊的叢集中的 INS、DEL、HOME、END、PAGE UP、PAGE DOWN 和箭號，並在數位鍵台中輸入按鍵。</span><span class="sxs-lookup"><span data-stu-id="15255-125">Enhanced keys for the IBM® 101-key and 102-key keyboards are the INS, DEL, HOME, END, PAGE UP, PAGE DOWN, and arrow keys in the clusters to the left of the numeric keypad and the divide (/) and ENTER keys in the numeric keypad.</span></span>

## <a name="span-idmouse_eventsspanspan-idmouse_eventsspanspan-idmouse_eventsspanmouse-events"></a><span data-ttu-id="15255-126"><span id="Mouse_Events"></span><span id="mouse_events"></span><span id="MOUSE_EVENTS"></span>滑鼠事件</span><span class="sxs-lookup"><span data-stu-id="15255-126"><span id="Mouse_Events"></span><span id="mouse_events"></span><span id="MOUSE_EVENTS"></span>Mouse Events</span></span>


<span data-ttu-id="15255-127">每當使用者移動滑鼠或按下或放開其中一個滑鼠按鍵時，就會產生滑鼠事件。</span><span class="sxs-lookup"><span data-stu-id="15255-127">Mouse events are generated whenever the user moves the mouse or presses or releases one of the mouse buttons.</span></span> <span data-ttu-id="15255-128">只有在符合下列條件時，滑鼠事件才會放在輸入緩衝區中：</span><span class="sxs-lookup"><span data-stu-id="15255-128">Mouse events are placed in the input buffer only if the following conditions are met:</span></span>

- <span data-ttu-id="15255-129">主控台輸入模式設定為啟用 (預設模式) 的 \*\* \_ 滑鼠 \_ 輸入\*\* 。</span><span class="sxs-lookup"><span data-stu-id="15255-129">The console input mode is set to **ENABLE\_MOUSE\_INPUT** (the default mode).</span></span>
- <span data-ttu-id="15255-130">主控台視窗具有鍵盤焦點。</span><span class="sxs-lookup"><span data-stu-id="15255-130">The console window has the keyboard focus.</span></span>
- <span data-ttu-id="15255-131">滑鼠指標位於主控台視窗的框線內。</span><span class="sxs-lookup"><span data-stu-id="15255-131">The mouse pointer is within the borders of the console's window.</span></span>

<span data-ttu-id="15255-132">如果輸入事件是滑鼠事件，[**輸入 \_ 記錄**](input-record-str.md)中的**事件**成員就是包含下列資訊的[**滑鼠 \_ 事件 \_ 記錄**](mouse-event-record-str.md)結構：</span><span class="sxs-lookup"><span data-stu-id="15255-132">If the input event is a mouse event, the **Event** member in [**INPUT\_RECORD**](input-record-str.md) is a [**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md) structure containing the following information:</span></span>

- <span data-ttu-id="15255-133">滑鼠指標在主控台螢幕緩衝區座標系統中的字元儲存格資料列和資料行的座標。</span><span class="sxs-lookup"><span data-stu-id="15255-133">The coordinates of the mouse pointer in terms of the character-cell row and column in the console screen buffer's coordinate system.</span></span>
- <span data-ttu-id="15255-134">旗標變數，指出滑鼠按鍵的狀態。</span><span class="sxs-lookup"><span data-stu-id="15255-134">A flag variable indicating the state of the mouse buttons.</span></span>
- <span data-ttu-id="15255-135">旗標變數，表示控制項索引鍵的狀態 (ALT、CTRL、SHIFT、NUM LOCK、SCROLL LOCK 和 CAPS LOCK) 並指出是否已按下增強的按鍵。</span><span class="sxs-lookup"><span data-stu-id="15255-135">A flag variable indicating the state of the control keys (ALT, CTRL, SHIFT, NUM LOCK, SCROLL LOCK, and CAPS LOCK) and indicating whether an enhanced key was pressed.</span></span> <span data-ttu-id="15255-136">適用于 IBM 101-金鑰和102鍵鍵盤的增強金鑰為數字鍵臺上左邊叢集中的 INS、DEL、HOME、END、PAGE UP、PAGE DOWN 和箭號，以及 (/) 並在數位鍵台中輸入按鍵。</span><span class="sxs-lookup"><span data-stu-id="15255-136">Enhanced keys for the IBM 101-key and 102-key keyboards are the INS, DEL, HOME, END, PAGE UP, PAGE DOWN, and arrow keys in the clusters to the left of the numeric keypad and the divide (/) and ENTER keys in the numeric keypad.</span></span>
- <span data-ttu-id="15255-137">旗標變數，指出事件是一般按鈕按下或按鈕釋放事件、滑鼠移動事件，還是第二次按一下按兩下事件。</span><span class="sxs-lookup"><span data-stu-id="15255-137">A flag variable indicating whether the event was a normal button-press or button-release event, a mouse movement event, or the second click of a double-click event.</span></span>

<span data-ttu-id="15255-138">**注意**   滑鼠位置座標是以主控台畫面緩衝區為單位，而不是主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="15255-138">**Note**  The mouse position coordinates are in terms of the console screen buffer, not the console window.</span></span> <span data-ttu-id="15255-139">螢幕緩衝區可能已針對視窗進行滾動，因此視窗的左上角不一定是主控台螢幕緩衝區的 (0、0) 座標。</span><span class="sxs-lookup"><span data-stu-id="15255-139">The screen buffer may have been scrolled with respect to the window, so the upper left corner of the window is not necessarily the (0,0) coordinate of the console screen buffer.</span></span> <span data-ttu-id="15255-140">若要判斷相對於視窗座標系統的滑鼠座標，請從滑鼠位置座標減去視窗原點座標。</span><span class="sxs-lookup"><span data-stu-id="15255-140">To determine the coordinates of the mouse relative to the coordinate system of the window, subtract the window origin coordinates from the mouse position coordinates.</span></span> <span data-ttu-id="15255-141">您可以使用 [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) 函式來判斷視窗原始座標。</span><span class="sxs-lookup"><span data-stu-id="15255-141">Use the [**GetConsoleScreenBufferInfo**](getconsolescreenbufferinfo.md) function to determine the window origin coordinates.</span></span>

 

<span data-ttu-id="15255-142">[**滑鼠 \_ 事件 \_ 記錄**](mouse-event-record-str.md)結構的**dwButtonState**成員具有對應至每個滑鼠按鍵的位。</span><span class="sxs-lookup"><span data-stu-id="15255-142">The **dwButtonState** member of the [**MOUSE\_EVENT\_RECORD**](mouse-event-record-str.md) structure has a bit corresponding to each mouse button.</span></span> <span data-ttu-id="15255-143">如果按鈕已關閉，則位為1，如果按鈕為開啟，則為0。</span><span class="sxs-lookup"><span data-stu-id="15255-143">The bit is 1 if the button is down and 0 if the button is up.</span></span> <span data-ttu-id="15255-144">**滑鼠 \_ 事件 \_ 記錄**的**dwEventFlags**成員有0個值的按鈕發行事件，以及從1到0的按鈕位變更。</span><span class="sxs-lookup"><span data-stu-id="15255-144">A button-release event is detected by a 0 value for the **dwEventFlags** member of **MOUSE\_EVENT\_RECORD** and a change in a button's bit from 1 to 0.</span></span> <span data-ttu-id="15255-145">[**GetNumberOfConsoleMouseButtons**](getnumberofconsolemousebuttons.md)函式會捕獲滑鼠上的按鈕數目。</span><span class="sxs-lookup"><span data-stu-id="15255-145">The [**GetNumberOfConsoleMouseButtons**](getnumberofconsolemousebuttons.md) function retrieves the number of buttons on the mouse.</span></span>

## <a name="span-idbuffer-resizing_eventsspanspan-idbuffer-resizing_eventsspanspan-idbuffer-resizing_eventsspanbuffer-resizing-events"></a><span data-ttu-id="15255-146"><span id="Buffer-Resizing_Events"></span><span id="buffer-resizing_events"></span><span id="BUFFER-RESIZING_EVENTS"></span>緩衝區大小調整事件</span><span class="sxs-lookup"><span data-stu-id="15255-146"><span id="Buffer-Resizing_Events"></span><span id="buffer-resizing_events"></span><span id="BUFFER-RESIZING_EVENTS"></span>Buffer-Resizing Events</span></span>


<span data-ttu-id="15255-147">主控台視窗的功能表可讓使用者變更活動畫面緩衝區的大小;這種變更會產生緩衝區調整大小的事件。</span><span class="sxs-lookup"><span data-stu-id="15255-147">A console window's menu enables the user to change the size of the active screen buffer; this change generates a buffer-resizing event.</span></span> <span data-ttu-id="15255-148">如果主控台的輸入模式設定為 **啟用 \_ 視窗 \_ 輸入** (也就是停用預設模式) ，則會將緩衝區調整大小的事件放在輸入緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="15255-148">Buffer-resizing events are placed in the input buffer if the console's input mode is set to **ENABLE\_WINDOW\_INPUT** (that is, the default mode is disabled).</span></span>

<span data-ttu-id="15255-149">如果輸入事件是緩衝區調整大小的事件，則[**輸入 \_ 記錄**](input-record-str.md)的**事件**成員是包含主控台螢幕緩衝區新大小的[**視窗 \_ 緩衝區 \_ 大小 \_ 記錄**](window-buffer-size-record-str.md)結構，以字元儲存格的資料行和資料清單示。</span><span class="sxs-lookup"><span data-stu-id="15255-149">If the input event is a buffer-resizing event, the **Event** member of [**INPUT\_RECORD**](input-record-str.md) is a [**WINDOW\_BUFFER\_SIZE\_RECORD**](window-buffer-size-record-str.md) structure containing the new size of the console screen buffer, expressed in character-cell columns and rows.</span></span>

<span data-ttu-id="15255-150">如果使用者減少了主控台螢幕緩衝區的大小，則會遺失緩衝區捨棄部分中的任何資料。</span><span class="sxs-lookup"><span data-stu-id="15255-150">If the user reduces the size of the console screen buffer, any data in the discarded portion of the buffer is lost.</span></span>

<span data-ttu-id="15255-151">由於應用程式呼叫 [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) 函式而導致主控台螢幕緩衝區大小的變更，不會產生為緩衝區調整大小的事件。</span><span class="sxs-lookup"><span data-stu-id="15255-151">Changes to the console screen buffer size as a result of application calls to the [**SetConsoleScreenBufferSize**](setconsolescreenbuffersize.md) function are not generated as buffer-resizing events.</span></span>

 

 





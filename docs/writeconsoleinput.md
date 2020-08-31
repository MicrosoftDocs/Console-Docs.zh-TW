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
# <a name="writeconsoleinput-function"></a>WriteConsoleInput 函式


將資料直接寫入主控台輸入緩衝區。

<a name="syntax"></a>語法
------

```C
BOOL WINAPI WriteConsoleInput(
  _In_        HANDLE       hConsoleInput,
  _In_  const INPUT_RECORD *lpBuffer,
  _In_        DWORD        nLength,
  _Out_       LPDWORD      lpNumberOfEventsWritten
);
```

<a name="parameters"></a>參數
----------

*hConsoleInput* \[在\]  
主控台輸入緩衝區的控制碼。 控制碼必須有 **一般 \_ 寫入** 存取權限。 如需詳細資訊，請參閱 [主控台緩衝區安全性和存取權限](console-buffer-security-and-access-rights.md)。

*lpBuffer* \[在\]  
[**輸入 \_ 記錄**](input-record-str.md)結構陣列的指標，其中包含要寫入至輸入緩衝區的資料。

*nLength* \[在\]  
要寫入的輸入記錄數目。

*lpNumberOfEventsWritten* \[擴展\]  
變數的指標，此變數會接收實際寫入之輸入記錄的數目。

<a name="return-value"></a>傳回值
------------

如果函式成功，則傳回值為非零。

如果此函式失敗，則傳回值為零。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

<a name="remarks"></a>備註
-------

**WriteConsoleInput** 會將輸入記錄放入緩衝區中任何暫止事件後方的輸入緩衝區。 視需要，輸入緩衝區會動態成長，以保存所寫入的事件數目。

此函式會從主控台的目前字碼頁使用 Unicode 字元或8位字元。 主控台的字碼頁一開始預設為系統的 OEM 字碼頁。 若要變更控制台的字碼頁，請使用 [**SetConsoleCP**](setconsolecp.md) 或 [**SetConsoleOutputCP**](setconsoleoutputcp.md) 函式，或使用 **chcp** 或 **mode con cp select =** 命令。

<a name="requirements"></a>規格需求
------------

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>最低支援的用戶端</p></td>
<td><p>Windows 2000 Professional [僅限桌面應用程式]</p></td>
</tr>
<tr class="even">
<td><p>最低支援的伺服器</p></td>
<td><p>Windows 2000 伺服器 [僅限桌面應用程式]</p></td>
</tr>
<tr class="odd">
<td><p>標頭</p></td>
<td>ConsoleApi2 .h (via Wincon，包括 Windows .h) </td>
</tr>
<tr class="even">
<td><p>程式庫</p></td>
<td>Kernel32.dll .lib</td>
</tr>
<tr class="odd">
<td><p>DLL</p></td>
<td>Kernel32.dll</td>
</tr>
<tr class="even">
<td><p>Unicode 和 ANSI 名稱</p></td>
<td><p><strong>WriteConsoleInputW</strong> (Unicode) 和 <strong>WriteConsoleInputA</strong> (ANSI) </p></td>
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

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另請參閱


[主控台功能](console-functions.md)

[**輸入 \_ 記錄**](input-record-str.md)

[低層級主控台輸入函式](low-level-console-input-functions.md)

[**MapVirtualKey**](https://msdn.microsoft.com/library/windows/desktop/ms646306)

[**PeekConsoleInput**](peekconsoleinput.md)

[**ReadConsoleInput**](readconsoleinput.md)

[**SetConsoleCP**](setconsolecp.md)

[**SetConsoleOutputCP**](setconsoleoutputcp.md)

[**VkKeyScan**](https://msdn.microsoft.com/library/windows/desktop/ms646329)

 

 





---
title: GetConsoleProcessList 函式
description: 請參閱 GetConsoleProcessList 函式的參考資訊，此函式會抓取連接到目前主控台的進程清單。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetConsoleProcessList
- wincon/GetConsoleProcessList
- GetConsoleProcessList
MS-HAID:
- '\_win32\_getconsoleprocesslist'
- base.getconsoleprocesslist
- consoles.getconsoleprocesslist
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 3d21103b-662d-4393-ae3f-773cd9e4a930
topic_type:
- apiref
api_name:
- GetConsoleProcessList
api_location:
- Kernel32.dll
api_type:
- DllExport
ms.openlocfilehash: bfc16edccb2f1be2b22c81992800d8f62d86cf4f
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93037978"
---
# <a name="getconsoleprocesslist-function"></a>GetConsoleProcessList 函式

抓取附加至目前主控台的進程清單。

## <a name="syntax"></a>語法

```C
DWORD WINAPI GetConsoleProcessList(
  _Out_ LPDWORD lpdwProcessList,
  _In_  DWORD   dwProcessCount
);
```

## <a name="parameters"></a>參數

*lpdwProcessList* \[擴展\]  
在成功時收到進程識別碼陣列的緩衝區指標。 這必須是有效的緩衝區，而且不能是 `NULL` 。 緩衝區必須有空間，才能接收至少一個傳回的處理序識別碼。

*dwProcessCount* \[在\]  
可以儲存在 *lpdwProcessList* 緩衝區中的處理序識別碼數目上限。 這必須大於0。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值小於或等於 *dwProcessCount* ，而且代表 *lpdwProcessList* 緩衝區中儲存的進程識別碼數目。

如果緩衝區太小而無法容納所有有效的處理序識別碼，則傳回值是必要的陣列元素數目。 此函數將不會在緩衝區中儲存任何識別碼。 在這種情況下，請使用傳回值配置夠大的緩衝區來儲存整個清單，然後再次呼叫函數。

如果傳回值為零，則函式失敗，因為每個主控台至少有一個相關聯的進程。 若要取得延伸錯誤資訊，請呼叫 [**GetLastError**](https://msdn.microsoft.com/library/windows/desktop/ms679360)。

如果 `NULL` 提供了進程清單，或進程計數是0，則呼叫會傳回0，而且 `GetLastError` 會傳回 `ERROR_INVALID_PARAMETER` 。 請提供至少一個元素的緩衝區，以呼叫此函數。 配置較大的緩衝區，並在傳回碼大於所提供緩衝區的長度時再呼叫一次。

## <a name="remarks"></a>備註

若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0501 或更新版本。 如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。

[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | \[僅限 WINDOWS XP desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows Server 2003 \[ desktop 應用程式\] |
| 標頭 | ConsoleApi3 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

## <a name="see-also"></a>請參閱

[**AttachConsole**](attachconsole.md)

[主控台功能](console-functions.md)

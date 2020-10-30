---
title: GetConsoleWindow 函式
description: 抓取與呼叫進程相關聯的主控台所使用的視窗控制碼。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台, 字元模式應用程式, 命令列應用程式, 終端機應用程式, 主控台 api
f1_keywords:
- consoleapi3/GetConsoleWindow
- wincon/GetConsoleWindow
- GetConsoleWindow
MS-HAID:
- '\_win32\_getconsolewindow'
- base.getconsolewindow
- consoles.getconsolewindow
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: a5ab0b37-45ac-4413-b6ff-73876556ad38
topic_type:
- apiref
api_name:
- GetConsoleWindow
api_location:
- Kernel32.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-0.dll
- kernel32legacy.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-1.dll
- API-MS-Win-Core-Kernel32-Legacy-l1-1-2.dll
- API-MS-Win-DownLevel-Kernel32-l2-1-0.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-3.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-4.dll
- API-MS-Win-Core-Kernel32-Legacy-L1-1-5.dll
api_type:
- DllExport
ms.openlocfilehash: c74fe1a29b9ba2ea721e874eb624ea2f8517094c
ms.sourcegitcommit: 463975e71920908a6bff9a6a7291ddf3736652d5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93038806"
---
# <a name="getconsolewindow-function"></a>GetConsoleWindow 函式

[!INCLUDE [not-recommended-banner](./includes/not-recommended-banner.md)]

抓取與呼叫進程相關聯的主控台所使用的視窗控制碼。

## <a name="syntax"></a>語法

```C
HWND WINAPI GetConsoleWindow(void);
```

## <a name="parameters"></a>參數

此函式沒有參數。

## <a name="return-value"></a>傳回值

傳回值是與呼叫進程相關聯的主控台所使用的視窗控制碼，如果沒有這類相關聯的主控台，則為 **Null** 。

## <a name="remarks"></a>備註

若要編譯使用此函數的應用程式，請將 **\_ WIN32 \_ WINNT** 定義為0x0500 或更新版本。 如需詳細資訊，請參閱 [使用 Windows 標頭](https://msdn.microsoft.com/library/windows/desktop/aa383745)。


[!INCLUDE [no-vt-equiv-local-context](./includes/no-vt-equiv-local-context.md)]

針對裝載在 [**pseudoconsole**](pseudoconsoles.md) 會話內的應用程式，此函式只會傳回訊息佇列用途的視窗控制碼。 相關聯的視窗不會在本機顯示，因為 _pseudoconsole_ 會將所有動作序列化至另一個終端機視窗上的顯示位置。

## <a name="requirements"></a>規格需求

| &nbsp; | &nbsp; |
|-|-|
| 最低支援的用戶端 | 僅限 Windows 2000 Professional \[ desktop 應用程式\] |
| 最低支援的伺服器 | 僅限 Windows 2000 Server \[ desktop 應用程式\] |
| 標頭 | ConsoleApi3 .h (via WinCon，包括 Windows .h)  |
| 程式庫 | Kernel32.dll .lib |
| DLL | Kernel32.dll |

</table>

## <a name="see-also"></a>請參閱

[主控台功能](console-functions.md)

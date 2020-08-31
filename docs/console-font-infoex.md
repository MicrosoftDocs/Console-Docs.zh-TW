---
title: CONSOLE_FONT_INFOEX 結構
description: 請參閱有關 CONSOLE_FONT_INFOEX 結構的參考資訊，其中包含主控台字型的延伸資訊。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- consoleapi3/CONSOLE_FONT_INFOEX
- wincon/CONSOLE_FONT_INFOEX
- CONSOLE_FONT_INFOEX
- consoleapi3/PCONSOLE_FONT_INFOEX
- wincon/PCONSOLE_FONT_INFOEX
- PCONSOLE_FONT_INFOEX
MS-HAID:
- base.console\_font\_infoex
- consoles.console\_font\_infoex
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: e9a087e1-264d-4d48-8adb-771a0e35b511
topic_type:
- apiref
api_name:
- CONSOLE_FONT_INFOEX
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 12977e288a63397c581143683047239e4d410eec
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059319"
---
# <a name="console_font_infoex-structure"></a>主控台 \_ 字型 \_ INFOEX 結構


包含主控台字型的延伸資訊。

<a name="syntax"></a>Syntax
------

```C
typedef struct _CONSOLE_FONT_INFOEX {
  ULONG cbSize;
  DWORD nFont;
  COORD dwFontSize;
  UINT  FontFamily;
  UINT  FontWeight;
  WCHAR FaceName[LF_FACESIZE];
} CONSOLE_FONT_INFOEX, *PCONSOLE_FONT_INFOEX;
```

<a name="members"></a>成員
-------

**cbSize**  
此結構的大小（以位元組為單位）。 這個成員必須在 `sizeof(CONSOLE_FONT_INFOEX)` 呼叫 [**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md) 之前設定為，否則它將會失敗。

**nFont**  
系統的主控台字型表中的字型索引。

**dwFontSize**  
[**COORD**](coord-str.md)結構，其中包含字型中每個字元的寬度和高度（以邏輯單位表示）。 **X**成員包含寬度，而**Y**成員包含高度。

**FontFamily**  
字型音調和系列。 如需此成員可能值的詳細資訊，請參閱[**TEXTMETRIC**](https://msdn.microsoft.com/library/windows/desktop/dd145132)結構之**tmPitchAndFamily**成員的描述。

**FontWeight**  
字型粗細。 權數的範圍可以從100到1000，以100的倍數為限。 例如，標準權數為400，而700為粗體。

**FaceName**  
字型 (的名稱，例如 [中] 或 [Arial]) 。

<a name="remarks"></a>備註
-------

若要取得字型的大小，請將字型索引傳遞給 [**GetConsoleFontSize**](getconsolefontsize.md) 函數。

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
<td><p>Windows Vista [僅限桌面應用程式]</p></td>
</tr>
<tr class="even">
<td><p>最低支援的伺服器</p></td>
<td><p>Windows Server 2008 [僅限桌面應用程式]</p></td>
</tr>
<tr class="odd">
<td><p>標頭</p></td>
<td>Wincon (包含) 的 Windows。h</td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另請參閱


[**GetCurrentConsoleFontEx**](getcurrentconsolefontex.md)

 

 





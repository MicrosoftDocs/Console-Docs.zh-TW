---
title: FOCUS_EVENT_RECORD 結構
description: 描述主控台輸入記錄結構中的焦點事件 \_ 。 這些事件會在內部使用，應該予以忽略。
author: miniksa
ms.author: miniksa
ms.topic: article
keywords: 主控台，字元模式應用程式，命令列應用程式，終端應用程式，主控台 api
f1_keywords:
- wincontypes/FOCUS_EVENT_RECORD
- wincon/FOCUS_EVENT_RECORD
- FOCUS_EVENT_RECORD
- wincontypes/PFOCUS_EVENT_RECORD
- wincon/PFOCUS_EVENT_RECORD
- PFOCUS_EVENT_RECORD
MS-HAID:
- '\_win32\_focus\_event\_record\_str'
- base.focus\_event\_record\_str
- consoles.focus\_event\_record\_str
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/desktop
ms.assetid: 4db0ae89-8446-4f0a-98e2-ba0b11ef7efe
topic_type:
- apiref
api_name:
- FOCUS_EVENT_RECORD
api_location:
- Wincon.h
api_type:
- HeaderDef
ms.openlocfilehash: 61f37e3645a66ca9f755f66f0baa03a2238983ad
ms.sourcegitcommit: b75f4688e080d300b80c552d0711fdd86b9974bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/24/2020
ms.locfileid: "89059206"
---
# <a name="focus_event_record-structure"></a>焦點 \_ 事件 \_ 記錄結構


描述主控台 [**輸入 \_ 記錄**](input-record-str.md) 結構中的焦點事件。 這些事件會在內部使用，應該予以忽略。

<a name="syntax"></a>Syntax
------

```C
typedef struct _FOCUS_EVENT_RECORD {
  BOOL bSetFocus;
} FOCUS_EVENT_RECORD;
```

<a name="members"></a>成員
-------

**bSetFocus**  
保留的。

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
<td>WinConTypes .h (via Wincon，包括 Windows .h) </td>
</tr>
</tbody>
</table>

## <a name="span-idsee_alsospansee-also"></a><span id="see_also"></span>另請參閱


[**輸入 \_ 記錄**](input-record-str.md)

 

 





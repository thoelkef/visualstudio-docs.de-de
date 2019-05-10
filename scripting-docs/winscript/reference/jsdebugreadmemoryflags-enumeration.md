---
title: JsDebugReadMemoryFlags-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugReadMemoryFlags
apilocation:
- jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c908fdbf17b13b84355dff208b7f3106bfc72087
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830461"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>JsDebugReadMemoryFlags-Enumeration
Flags um Verhalten anzugeben, wenn Arbeitsspeicher gelesen werden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>Member  
  
### <a name="values"></a>Werte  
  
|Name|Beschreibung|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|Gibt an, dass der Aufrufer möchte, dass der Lesevorgang erfolgreich ist, wenn nur ein Teil des Arbeitsspeichers erfolgreich gelesen wird. Wenn dies festgelegt ist, wird ein E_JsDEBUG_INVALID_MEMORY_ADDRESS-Fehler nur ausgelöst, wenn "Adresse" ungültig ist. Wenn dieses Flag klar ist, wird ein E_JsDEBUG_INVALID_MEMORY_ADDRESS-Fehler ausgelöst, wenn irgendein Teil des angeforderten Arbeitsspeichers nicht gelesen werden konnte.|  
|`None`|Gibt an, dass der Aufrufer das Standardverhalten für ReadMemory wünscht.|  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** "jscript9diag.h"  
  
## <a name="see-also"></a>Siehe auch  
 [Windows Script-Schnittstellenreferenz](../../winscript/reference/windows-script-interfaces-reference.md)
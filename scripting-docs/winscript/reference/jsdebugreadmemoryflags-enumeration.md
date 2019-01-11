---
title: JsDebugReadMemoryFlags-Enumeration | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: bef1f16ebcf678452f2fe4b0df3ade6350120f05
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094028"
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
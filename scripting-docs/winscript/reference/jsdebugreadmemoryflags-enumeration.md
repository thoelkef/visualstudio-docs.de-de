---
title: "JsDebugReadMemoryFlags-Enumeration | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JsDebugReadMemoryFlags
apilocation: jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsDebugReadMemoryFlags-Enumeration
Flags um Verhalten anzugeben, wenn Arbeitsspeicher gelesen werden.  
  
## Syntax  
  
```  
enum JsDebugReadMemoryFlags  
{  
   None = 0,  
   JsDebugAllowPartialRead= 0x1  
} JsDebugReadMemoryFlags;  
```  
  
## Member  
  
### Werte  
  
|Name|Beschreibung|  
|----------|------------------|  
|`JsDebugAllowPartialRead`|Gibt an, dass der Aufrufer möchte, dass der Lesevorgang erfolgreich ist, wenn nur ein Teil des Arbeitsspeichers erfolgreich gelesen wird.  Wenn dies festgelegt ist, wird ein E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS\-Fehler nur ausgelöst, wenn "Adresse" ungültig ist.  Wenn dieses Flag klar ist, wird ein E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS\-Fehler ausgelöst, wenn irgendein Teil des angeforderten Arbeitsspeichers nicht gelesen werden konnte.|  
|`None`|Gibt an, dass der Aufrufer das Standardverhalten für ReadMemory wünscht.|  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [Windows Script\-Schnittstellenverweis](../../winscript/reference/windows-script-interfaces-reference.md)
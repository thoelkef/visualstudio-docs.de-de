---
title: "IEnumJsStackFrames-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 49e7b425-df17-4d7f-87ff-0bc82715c911
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IEnumJsStackFrames-Schnittstelle
Implementiert durch den Debugger, um zu "jscript9diag.dll" Stapelentladung für JavaScript bereitzustellen.  
  
## Syntax  
  
```  
IEnumJsStackFrames : public IUnknown;  
```  
  
## Member  
  
### Öffentliche Methoden  
  
|Name|Beschreibung|  
|----------|------------------|  
|[IEnumJsStackFrames::Next\-Methode](../../winscript/reference/ienumjsstackframes-next-method.md)|Ruft die angegebene Anzahl an Frames ab.|  
|[IEnumJsStackFrames::Reset\-Methode](../../winscript/reference/ienumjsstackframes-reset-method.md)|Setzt den Stapelrahmen auf die Position vor dem ersten Element zurück.|  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [Windows Script\-Schnittstellenverweis](../../winscript/reference/windows-script-interfaces-reference.md)
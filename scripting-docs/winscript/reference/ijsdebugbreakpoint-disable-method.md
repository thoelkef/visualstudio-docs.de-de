---
title: "IJsDebugBreakPoint::Disable-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.Disable
apilocation: jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugBreakPoint::Disable-Methode
Deaktiviert den Haltepunkt.  
  
## Syntax  
  
```  
HRESULT Disable(void);  
```  
  
## Rückgabewert  
  
## Hinweise  
 Gibt E\_UNEXPECTED zurück, wenn der Aufruf an einem gelöschten Haltepunkt erfolgt.  Gibt "S\_FALSE" zurück bei Aufruf an einem bereits deaktivierten Haltepunkt.  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugBreakPoint\-Schnittstelle](../../winscript/reference/ijsdebugbreakpoint-interface.md)
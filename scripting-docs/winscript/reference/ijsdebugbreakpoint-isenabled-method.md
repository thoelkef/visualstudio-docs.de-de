---
title: "IJsDebugBreakPoint::IsEnabled-Methode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebugBreakPoint.IsEnabled
apilocation: jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugBreakPoint::IsEnabled-Methode
Bestimmt, ob der Haltepunkt aktiviert ist.  
  
## Syntax  
  
```  
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### Parameter  
 `pIsEnabled`  
 \[out\] Gibt "true" zurück, wenn der Haltepunkt aktiviert ist; andernfalls "false".  
  
## Rückgabewert  
  
## Hinweise  
 Gibt E\_UNEXPECTED zurück, wenn der Aufruf an einem gelöschten Haltepunkt erfolgt.  
  
## Anforderungen  
 **Header:**  jscript9diag.h  
  
## Siehe auch  
 [IJsDebugBreakPoint\-Schnittstelle](../../winscript/reference/ijsdebugbreakpoint-interface.md)
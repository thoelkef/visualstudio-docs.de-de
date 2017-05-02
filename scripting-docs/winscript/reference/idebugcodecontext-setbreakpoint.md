---
title: "IDebugCodeContext::SetBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugCodeContext.SetBreakPoint
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugCodeContext::SetBreakPoint"
ms.assetid: ecd42eae-66fa-40d3-9e47-08b826784108
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugCodeContext::SetBreakPoint
Setzt oder freie Leerzeichen ein Haltepunkt an diesem Codekontext.  
  
## Syntax  
  
```  
HRESULT SetBreakPoint(  
   BREAKPOINT_STATE  bps  
);  
```  
  
#### Parameter  
 `bps`  
 \[in\] Gibt den Haltepunktbedingung für diesen Codekontext an.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode setzt oder löscht einen Haltepunkt an diesem Codekontext.  
  
## Siehe auch  
 [IDebugCodeContext\-Schnittstelle](../../winscript/reference/idebugcodecontext-interface.md)   
 [BREAKPOINT\_STATE\-Enumeration](../../winscript/reference/breakpoint-state-enumeration.md)
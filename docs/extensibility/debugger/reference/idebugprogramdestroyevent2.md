---
title: "IDebugProgramDestroyEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramDestroyEvent2"
helpviewer_keywords: 
  - "IDebugProgramDestroyEvent2"
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgramDestroyEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird durch das Debugmodul \(DE Debuggen\) zum Manager der Sitzung \(SDM\) gesendet, wenn ein Programm bis zum Abschluss ausgeführt wurde.  
  
## Syntax  
  
```  
IDebugProgramDestroyEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE oder einer benutzerdefinierten Port lieferant implementiert diese Schnittstelle, um zu melden, dass ein Programm beendet wurde und ist nicht mehr für das Debuggen verfügbar.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden.  Das SDM [QueryInterface](/visual-cpp/atl/queryinterface) verwendet, um die `IDebugEvent2`\-Schnittstelle zuzugreifen.  
  
## Hinweise für Aufrufer  
 DE oder einer benutzerdefinierten Port lieferant erstellt und sendet das Ereignisobjekt, um die Beendigung eines Programms.  DE sendet dieses Ereignis, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wurde, als sie angefügt haben dem Programm, das gedebuggt wurde.  Der benutzerdefinierte Port lieferant sendet dieses Ereignis unter Verwendung der [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)\-Schnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle sind die Methode von `IDebugProgramDestroyEvent2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetExitCode](../../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md)|Ruft den Exitcode des Programms ab.|  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
---
title: "IDebugBreakpointUnboundEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointUnboundEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointUnboundEvent2"
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointUnboundEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird der Sitzung Debugem Manager \(SDM\) der ein gebundener Haltepunkt aus einem geladenen Programm aufgehoben wurde.  
  
## Syntax  
  
```  
IDebugBreakpointUnboundEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. \(SDM das [QueryInterface](/visual-cpp/atl/queryinterface) verwendet, um die `IDebugEvent2`\-Schnittstelle zuzugreifen\).  
  
## Hinweise für Aufrufer  
 DE erstellt und sendet das Ereignisobjekt, wenn ein gebundener Haltepunkt aufgehoben wurde.  Das Ereignis wird gesendet, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wurde, als es an das Programm, das gedebuggt wurde angefügt haben.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugBreakpointUnboundEvent2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|Ruft den Haltepunkt ab, der aufgehoben wurde.|  
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|Ruft den Grund ab, den der Haltepunkt aufgehoben wurde.|  
  
## Hinweise  
 Wenn DLLs Modul eine Debug\- oder eine Klasse entladen wird, müssen alle Haltepunkte, die dem Code in diesem Modul gebunden wurden, ungebunden vom aufrufenden Programm, das gedebuggt wird.  `IDebugBreakpointUnboundEvent2` wird für jeden ungebundenen Haltepunkt gesendet.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
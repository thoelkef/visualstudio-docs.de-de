---
title: "IDebugBreakpointBoundEvent2 | Microsoft Docs"
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
  - "IDebugBreakpointBoundEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointBoundEvent2"
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointBoundEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird der Sitzung Debugem Manager \(SDM\), den ein anstehender Haltepunkt erfolgreich zu einem geladenen Programm gebunden wurde.  
  
## Syntax  
  
```  
IDebugBreakpointBoundEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. \(SDM das [QueryInterface](/visual-cpp/atl/queryinterface) verwendet, um die `IDebugEvent2`\-Schnittstelle zuzugreifen\).  
  
## Hinweise für Aufrufer  
 DE erstellt und sendet das Ereignisobjekt, wenn ein anstehender Haltepunkt erfolgreich gebunden ist, auf das Programm, das gedebuggt wird.  Das Ereignis wird gesendet, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wurde, als es an das Programm, das gedebuggt wurde angefügt haben.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugBreakpointBoundEvent2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|Ruft den anstehenden Haltepunkt ab, der gebunden wird.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|Erstellt einen Enumerator von Haltepunkten, die für dieses Ereignis gebunden wurden.|  
  
## Hinweise  
 Sobald ein Haltepunkt gebunden ist, wird ein Ereignis zum SDM gesendet.  Wenn der Haltepunkt nicht gebunden werden kann, wird [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) gesendet. Andernfalls wird `IDebugBreakpointBoundEvent2` gesendet.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
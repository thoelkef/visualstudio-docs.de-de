---
title: "IDebugBreakpointErrorEvent2 | Microsoft Docs"
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
  - "IDebugBreakpointErrorEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointErrorEvent2"
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointErrorEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird der Sitzung Debugem Manager \(SDM\), den ein anstehender Haltepunkt nicht in einem geladenen Programm entweder aufgrund einer Warnung oder eines Fehlers nicht gebunden werden kann.  
  
## Syntax  
  
```  
IDebugBreakpointErrorEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. \(SDM das [QueryInterface](/visual-cpp/atl/queryinterface) verwendet, um die `IDebugEvent2`\-Schnittstelle zuzugreifen\).  
  
## Hinweise für Aufrufer  
 DE erstellt und sendet das Ereignisobjekt, wenn ein anstehender Haltepunkt auf das Programm nicht gebunden werden kann, das gedebuggt wird.  Das Ereignis wird gesendet, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wurde, als es an das Programm, das gedebuggt wurde angefügt haben.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugBreakpointErrorEvent2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Ruft die [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)\-Schnittstelle ab, die die Warnung oder den Fehler beschreibt.|  
  
## Hinweise  
 Sobald ein Haltepunkt gebunden ist, wird ein Ereignis zum SDM gesendet.  Wenn der Haltepunkt nicht gebunden werden kann, wird `IDebugBreakpointErrorEvent2` gesendet. Andernfalls wird [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) gesendet.  
  
 Wenn z. B. die Bedingung, die mit dem anstehenden Haltepunkt zugeordnet ist, analysieren oder nicht ausgewertet werden kann, wird eine Warnmeldung gesendet, die der ausstehenden Haltepunkt derzeit nicht gebunden werden kann.  Dies tritt möglicherweise auf, wenn der Code für den Haltepunkt noch nicht geladen wurde.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
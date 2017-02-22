---
title: "IDebugBreakpointEvent2 | Microsoft Docs"
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
  - "IDebugBreakpointEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointEvent2-Schnittstelle"
ms.assetid: 50b3a7a7-331b-42c8-922c-ff3522ebe1da
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Das Debugmodul \(DE\) sendet diese Schnittstelle zum Debuggen von Manager der Sitzung \(SDM\), wenn ein Programm bei einem Haltepunkt angehalten wird.  
  
## Syntax  
  
```  
IDebugBreakpointEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. \(SDM das [QueryInterface](/visual-cpp/atl/queryinterface) verwendet, um die `IDebugEvent2`\-Schnittstelle zuzugreifen\).  
  
## Hinweise für Aufrufer  
 DE erstellt und sendet das Ereignisobjekt, wenn mindestens ein Haltepunkt im Programm festgestellt wird.  Das Ereignis wird gesendet, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wurde, als es an das Programm, das gedebuggt wurde angefügt haben.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugBreakpointEvent2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)|Erstellt einen Enumerator für alle Haltepunkte, die am aktuellen Speicherort des Codes ausgelöst hat.|  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
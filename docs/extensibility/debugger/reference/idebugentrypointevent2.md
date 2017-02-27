---
title: "IDebugEntryPointEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEntryPointEvent2"
helpviewer_keywords: 
  - "IDebugEntryPointEvent2-Schnittstelle"
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEntryPointEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Das Debugmodul \(DE\) sendet diese Schnittstelle zum Debuggen von Manager der Sitzung \(SDM\), wenn das Programm im Begriff ist, die erste Anweisung im Benutzercode auszuführen.  
  
## Syntax  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle als Teil der Normalbetriebe.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden.  Das SDM [QueryInterface](/visual-cpp/atl/queryinterface) verwendet, um die `IDebugEvent2`\-Schnittstelle zuzugreifen.  
  
## Hinweise für Aufrufer  
 DE erstellt und sendet das Ereignisobjekt, wenn das Programm, das gedebuggt wird, geladen wurde und ist bereit, die erste Anweisung im Benutzercode auszuführen.  Das Ereignis wird gesendet, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wurde, als sie angefügt haben dem Programm, das gedebuggt wurde.  
  
## Hinweise  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) wird gesendet, wenn das Programm im Begriff ist, die allererste Anweisung auszuführen.  Beispielsweise wird `IDebugEntryPoint2` gesendet, wenn das Programm im Begriff ist, die `main`\-Funktion des Benutzers auszuführen.  
  
 Wenn DE `IDebugEntryPointEvent2`sendet, sollte die aktuelle Position des Codes an der ersten Anweisung des Benutzercodes, wie `main`sein.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)
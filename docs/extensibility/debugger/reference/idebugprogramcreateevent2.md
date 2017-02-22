---
title: "IDebugProgramCreateEvent2 | Microsoft Docs"
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
  - "IDebugProgramCreateEvent2"
helpviewer_keywords: 
  - "IDebugProgramCreateEvent2-Schnittstelle"
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramCreateEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird durch das Debugmodul \(DE Debuggen\) zum Manager der Sitzung \(SDM\) gesendet wenn ein Programm angefügt ist.  
  
## Syntax  
  
```  
IDebugProgramCreateEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE oder einer benutzerdefinierten Port lieferant implementiert diese Schnittstelle, um in der Regel zu melden, dass ein Programm erstellt wurde, wenn das Programm angefügt ist.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden.  Das SDM verwendet die `QueryInterface`\-Methode, um die `IDebugEvent2`\-Schnittstelle zuzugreifen.  
  
## Hinweise für Aufrufer  
 DE oder einer benutzerdefinierten Port lieferant erstellt und sendet das Ereignisobjekt, um die Erstellung eines Programms.  DE sendet dieses Ereignis, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wurde, als sie angefügt haben dem Programm, das gedebuggt wurde.  Der benutzerdefinierte Port lieferant sendet dieses Ereignis unter Verwendung der [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)\-Schnittstelle.  
  
## Hinweise  
 DE oder benutzerdefinierte der Port lieferant veröffentlicht eine neue [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)\-Schnittstelle, indem sie [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)aufrufen.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
---
title: "IDebugBreakEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakEvent2"
helpviewer_keywords: 
  - "IDebugBreakEvent2-Schnittstelle"
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird der Sitzung Debugem Manager \(SDM\) eine asynchrone Unterbrechung erfolgreich abgeschlossen wurde.  
  
## Syntax  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE implementiert diese Schnittstelle, um Benutzer\-Unterbrechungen in einem Programm zu unterstützen.  Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. \(SDM das [QueryInterface](/visual-cpp/atl/queryinterface) verwendet, um die `IDebugEvent2`\-Schnittstelle zuzugreifen\).  
  
## Hinweise für Aufrufer  
 Das SDM ruft [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) auf, wenn der Benutzer das Programm, das gedebuggt wird angefordert hat, angehalten werden soll.  Wenn das Programm erfolgreich angehalten wurde, sendet das Ereignis. `IDebugBreakEvent2` DE  Dieses Ereignis wird gesendet, indem die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion verwendet, die vom SDM angegeben wurde, als es an das Programm, das gedebuggt wurde angefügt haben.  
  
## Hinweise  
 Beispielsweise kann ein Benutzer den **Alle unterbrechen** Befehl im Menü **Debuggen** auswählen, von einem Programm auszubrechen, das eine Endlosschleife ausgeführt wird.  Das SDM weist das Programm mit sich aufzuhalten bei, kurz [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)aufgerufen wird.  DE `IDebugBreakEvent2` sendet dann, wenn das Programm beendet.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
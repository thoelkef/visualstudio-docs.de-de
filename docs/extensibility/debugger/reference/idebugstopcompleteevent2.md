---
title: "IDebugStopCompleteEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugStopCompleteEvent2-Schnittstelle"
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Das Debugmodul \(DE\) kann dieses Ereignis an das optionale Debuggen Manager der Sitzung \(SDM\) senden, wenn ein Programm beendet wurde.  
  
## Syntax  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Dies ist eine neue Schnittstelle für [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)].  Frühere Versionen unterstützen nicht das asynchrone Beenden.  
  
 [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) wird vom SDM in Szenarien mit mehreren PROCESS aufgerufen oder multiprogrammiert.  Wenn ein Programm ein Ereignis in das aufhörendes SDM sendet, fordert das SDM andere Programme, die ebenfalls beendet.  
  
 Es wird verwendet, um das SDM asynchron zu informieren, dass ein Programm beendet wurde.  Dies ist für eine Debug\- Modul des Interpreters manchmal nützlich, bei denen kein Code innerhalb des gedebuggten Testprogramm ausgeführt wird, sodass [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nicht synchron abgeschlossen werden.  Wenn eine Debug\- Modul diese asynchrone Benachrichtigung setzen möchte, muss er `S_ASYNC_STOP` von [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)zurückgeben.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
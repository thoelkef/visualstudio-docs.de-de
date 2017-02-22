---
title: "IDebugProgram3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProgram3-Schnittstelle"
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt ein Programm, das in einem Prozess ausgeführt wird [Ausführen](../../../extensibility/debugger/reference/idebugprogram2-execute.md) dar und erweitert, indem sie einen Thread Informationen bereitstellt.  
  
## Syntax  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) und ein benutzerdefiniertes Anschlusslieferanten diese Schnittstelle implementieren, um ein Programm in einem Prozess darstellt.  Der Debuginformationen Manager der Sitzung \(SDM\) implementiert auch diese Schnittstelle, um Informationen zu [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md)bereitzustellen.  
  
## Hinweise für Aufrufer  
 Das [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)\-Ereignis gibt diese Schnittstelle für ein neues Programm zurück.  Diese Schnittstelle wird auch als Parameter für viele Methoden für mehrere Schnittstellen verwendet.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugProgram3`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Führt das Programm aus.  Der Thread wird zurückgegeben, um den Debugger Informationen zu geben, in denen Thread der Benutzer während der Ausführung anzeigt.|  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Hinweise  
 Ein Programm kann ein Thread ausgeführten Container in einer bestimmten Laufzeit als Architektur der Prozess eine oder mehrere Programme besteht.  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Weiter](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
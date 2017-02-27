---
title: "IDebugEngine2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2"
helpviewer_keywords: 
  - "IDebugEngine2-Schnittstelle"
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugEngine2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt eine Debug\- Modul dar.\) DE  Sie wird verwendet, um verschiedene Aspekte einer Debugsitzung, durch das Erstellen von Haltepunkten zum Festlegen und Löschen von Ausnahmen zu verwalten.  
  
## Syntax  
  
```  
IDebugEngine2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird von einer benutzerdefinierten DE implementiert, um das Debuggen von Programmen zu verwalten.  Diese Schnittstelle muss implementiert werden. DE  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird vom Debugbuild Manager der Sitzung \(SDM\) aufgerufen, um die Debugsitzung, einschließlich Verwalten von Ausnahmen, die Erstellung von Haltepunkten und die synchrone die Reaktion auf Ereignisse zu verwalten, die von DE gesendet werden.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugEngine2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Erstellt einen Enumerator für alle Programme, die durch DE gedebuggt werden.|  
|[Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Fügt DE mit einem Programm an.|  
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Erstellt einen anstehenden Haltepunkt in DE.|  
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Gibt an, wie DE eine bestimmte Ausnahme behandeln soll.|  
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Entfernt die angegebene Ausnahme, sodass sie nicht mehr durch das Debugmodul behandelt.|  
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Entfernt die Ausnahmeliste, die die IDE für eine bestimmte Architektur der Common Language Runtime oder eine Sprache festgelegt wurde.|  
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Ruft die GUID DEs ab.|  
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informiert DE, dass das angegebene Programm atypisch beendet wurde und dass alle Verweise, sollte die Bereinigung DE der Programmierung und ein Programm zu zerstören Ereignis senden.|  
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Wird vom SDM, um anzugeben, dass ein synchrones Debuggen Ereignis zuvor durch Senden, Empfangen und dem DE SDM verarbeitet wurde.|  
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Legt das Gebietsschema DEs fest.|  
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Legt den Registrierungsstamm DE vom derzeit verwendeten fest.|  
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Legt eine Metrik fest.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Anforderungen, die alle Programme, die von diesem DE gedebuggt werden, die Ausführung beendet das nächste Mal versucht, einer der Threads ausgeführt werden soll.|  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
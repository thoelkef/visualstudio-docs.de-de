---
title: "IDebugProcess3 | Microsoft Docs"
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
  - "IDebugProcess3"
helpviewer_keywords: 
  - "IDebugProcess3-Schnittstelle"
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen laufenden Prozess und ihre Programme dar.  Diese Schnittstelle ist als Ersatz auf mehrere Methoden in der [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Schnittstelle.  Sie stellt Kontrolle über Alle Programme im Prozess.  
  
> [!NOTE]
>  [Weiter](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [Ausführen](../../../extensibility/debugger/reference/idebugprogram2-execute.md)und [Schritt](../../../extensibility/debugger/reference/idebugprogram2-step.md)\-Methoden sind veraltet und sollte nicht mehr verwendet werden.  Verwenden Sie die entsprechenden Methoden für die `IDebugProcess3`\-Schnittstelle.  
  
## Syntax  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird von einem benutzerdefinierten Anschlusslieferanten implementiert, um Programme als Gruppe zu verwalten.  Wenn als Gruppe von Programmen verwaltet werden, können Sie deren Ausführung steuern und eine Sprache für einen Ausdrucksauswertung fest.  Diese Schnittstelle muss vom Anschlusslieferanten implementiert werden.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird hauptsächlich vom Debugbuild Manager der Sitzung \(SDM\) aufgerufen, um mit einer Gruppe von Programmen zu interagieren, die in diesem Prozess identifiziert werden.  
  
 Rufen Sie [QueryInterface](/visual-cpp/atl/queryinterface) auf einer [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)\-Schnittstelle an, die zum Abrufen dieser Schnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden, die von [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)geerbt werden, implementiert die folgenden Methoden `IDebugProcess3` .  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Weiter](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Setzt die Ausführung von oder das Durchlaufen eines Prozesses fort.|  
|[Ausführen](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Startet die Ausführung eines Prozesses.|  
|[Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md)|Schritte nach vorn Anweisung oder Anweisung ausgeführt.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|Ruft den Grund dafür ab, dass der Prozess zu Debugzwecken gestartet wurde.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Legt die als Host fungierende Entwicklungssprache fest, damit das Debugmodul den entsprechenden Ausdrucksauswertung laden kann.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Ruft die Sprache ab, die aktuell für diesen Prozess festgelegt ist.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Deaktiviert Bearbeiten und Fortfahren \(Anlage\) für diesen Prozess fort.<br /><br /> Ein benutzerdefinierter Port lieferant diese Methode nicht implementiert \(es soll `E_NOTIMPL`immer zurückgegeben\).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Rufen Sie den Anlagen\-Zustand für diesen Prozess ab.<br /><br /> Ein benutzerdefinierter Port lieferant diese Methode nicht implementiert \(es soll `E_NOTIMPL`immer zurückgegeben\).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Ruft ein Array von Modulen für verfügbare eindeutige Bezeichner ab.|  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
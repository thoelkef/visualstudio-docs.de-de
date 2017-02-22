---
title: "Steuerelementereignisse | Microsoft Docs"
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
  - "Debugereignisse [Debugging-SDK]"
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Steuerelementereignisse
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Sie müssen über Ereignisse während der Programmausführung kontrollierten senden.  Alle Ereignisse werden mit der [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md)\-Schnittstelle übermittelt und Attribute verfügen, die Sie benötigen, die [IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md)\-Methode zu implementieren.  
  
## Zusätzliche Methoden  
 Einige Ereignisse erfordern Implementierung von zusätzlichen Methoden:  
  
-   Das Senden der [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)\-Schnittstelle, wenn das Debugmodul \(DE\) initialisiert wird, müssen Sie die [IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)\-Methode zu implementieren.  
  
-   solche Implementierung erfordert Execution Control Steuerelementereignissen wie die [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) und[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)\-Schnittstellen.  **IDebugBreakEvent2** ist nur für asynchrone Timeouts erforderlich.  
  
-   Das schrittweise Durchlaufen in Funktionen benötigt die Implementierung der [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)\-Schnittstelle und ihre Methoden.  
  
 Die Ereignisse, die von Haltepunkten abgeleitet sind, erfordern die Implementierung der [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)und [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)\-Schnittstellen und Methoden sowie [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) .  
  
 Asynchrone Ausdrucksauswertung müssen Sie die [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)\-Schnittstelle und ihre Methoden [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[und GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) zu implementieren.  
  
 Synchrone Ereignisse erfordern die Implementierung der [IDebugEngine2::ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)\-Methode.  
  
 Damit das Modul schreibt STRINGFormat Ausgabe, müssen Sie die [IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)\-Methode implementieren.  
  
## Siehe auch  
 [Steuerung der Ausführung und Status Bewertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)
---
title: Steuern von Ereignissen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7a2da9f3e91eb803d292f1ab789f8133558db049
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49913305"
---
# <a name="control-events"></a>Steuerelementereignisse
Während der kontrollierten Ausführung des Programms müssen Sie Ereignisse senden. Alle der Ereignisse gesendet werden, mithilfe der [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle und Attribute, die Sie implementieren, erfordern die [IDebugEvent2::GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) Methode.  
  
## <a name="additional-methods"></a>Zusätzliche Methoden  
 Einige Ereignisse erfordern die Implementierung der zusätzliche Methoden, wie folgt:  
  
- Senden der [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) Schnittstelle, die bei der Initialisierung der Debug-Engine (DE) erfordert, dass Sie implementieren die [IDebugEngineCreateEvent2::GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) Methode.  
  
- Steuerung der Ausführung erfordert die Implementierung des Steuerelementereignisse wie das [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) und[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) Schnittstellen. **IDebugBreakEvent2** ist nur für asynchrone Unterbrechungen erforderlich.  
  
- Einzelschritt in Funktionen erfordert die Implementierung der [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) -Schnittstelle und die zugehörigen Methoden.  
  
  Ereignisse, die von Haltepunkten erfordern die Implementierung von der [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), und [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) Schnittstellen, als auch die [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) und [EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) Methoden.  
  
  Asynchrone ausdrucksauswertung erfordert, dass Sie implementieren die [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) Schnittstelle und die zugehörige [IDebugExpressionEvaluationCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md) [und GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) Methoden.  
  
  Synchrone Ereignisse erfordern die Implementierung der [IDebugEngine2::ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) Methode.  
  
  Sie müssen für das Modul Zeichenfolge-Stil Ausgabe schreiben, implementieren die [IDebugOutputStringEvent2::GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführung und Auswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)
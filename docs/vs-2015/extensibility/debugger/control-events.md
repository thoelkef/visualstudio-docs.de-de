---
title: Steuerelement Ereignisse | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4073da9036e11f90fbf7202095e70fce797ea015
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62414632"
---
# <a name="control-events"></a>Steuerelementereignisse
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sie müssen während der kontrollierten Ausführung des Programms Ereignisse senden. Alle Ereignisse werden mithilfe der [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle gesendet und verfügen über Attribute, die es erfordern, die [IDebugEvent2:: GetAttributes](../../extensibility/debugger/reference/idebugevent2-getattributes.md) -Methode zu implementieren.  
  
## <a name="additional-methods"></a>Weitere Methoden  
 Einige Ereignisse erfordern die Implementierung zusätzlicher Methoden wie folgt:  
  
- Wenn Sie die [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) -Schnittstelle senden, wenn die Debug-Engine (de) initialisiert ist, müssen Sie die [IDebugEngineCreateEvent2:: GetEngine](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md) -Methode implementieren.  
  
- Die Ausführungs Steuerung erfordert die Implementierung solcher Steuerungs Ereignisse wie die [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) -und[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) -Schnittstellen. **IDebugBreakEvent2** ist nur für asynchrone Umbrüche erforderlich.  
  
- Die schrittweise Ausführung von Funktionen erfordert die Implementierung der [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) -Schnittstelle und ihrer Methoden.  
  
  Ereignisse, die von Breakpoints abgeleitet werden, erfordern die Implementierung der [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)-, [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)-und [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) -Schnittstellen sowie der [IDebugBreakpointBoundEvent2:: getpdingbreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) -und [enumboundbreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) -Methoden.  
  
  Bei der asynchronen Ausdrucks Auswertung müssen Sie die [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) -Schnittstelle und Ihre [IDebugExpressionEvaluationCompleteEvent2:: GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[-und GetResult-](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) Methoden implementieren.  
  
  Synchrone Ereignisse erfordern die Implementierung der [IDebugEngine2:: continuefromsynchronousvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) -Methode.  
  
  Damit die-Engine eine Zeichen folgen Ausgabe schreiben kann, müssen Sie die [IDebugOutputStringEvent2:: GetString](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) -Methode implementieren.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführungssteuerung und Zustandsauswertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)

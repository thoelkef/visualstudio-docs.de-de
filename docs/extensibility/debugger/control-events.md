---
title: Steuerelementereignisse | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2c3ad9c9b63923bdf2f107e7bc582f3c76cd62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739084"
---
# <a name="control-events"></a>Steuern von Ereignissen
Sie müssen Ereignisse während der kontrollierten Ausführung Ihres Programms senden. Alle Ereignisse werden über die [IDebugEvent2-Schnittstelle](../../extensibility/debugger/reference/idebugevent2.md) gesendet und verfügen über Attribute, die die Implementierung der [IDebugEvent2::GetAttributes-Methode](../../extensibility/debugger/reference/idebugevent2-getattributes.md) erfordern.

## <a name="additional-methods"></a>Zusätzliche Methoden
 Einige Ereignisse erfordern die Implementierung zusätzlicher Methoden wie folgt:

- Das Senden der [IDebugEngineCreateEvent2-Schnittstelle](../../extensibility/debugger/reference/idebugenginecreateevent2.md) beim Initialisieren des Debugmoduls (DE) erfordert die Implementierung der [IDebugEngineCreateEvent2::GetEngine-Methode.](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)

- Die Ausführungssteuerung erfordert die Implementierung solcher Steuerelementereignisse wie der [IDebugBreakEvent2-](../../extensibility/debugger/reference/idebugbreakevent2.md) und[IDebugStepCompleteEvent2-Schnittstellen.](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) **IDebugBreakEvent2** ist nur für asynchrone Unterbrechungen erforderlich.

- Das Betreten von Funktionen erfordert die Implementierung der [IDebugStepCompleteEvent2-Schnittstelle](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) und ihrer Methoden.

  Ereignisse, die von Breakpoints ableiten, erfordern die Implementierung der Schnittstellen [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md), [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)und [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) sowie der Methoden [IDebugBreakpointBoundEvent2::GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) und [EnumBoundBreakpoints.](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)

  Die Asynchrone Ausdrucksauswertung erfordert, dass Sie die [IDebugExpressionEvaluationCompleteEvent2-Schnittstelle](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) und ihre [IDebugExpressionEvaluationCompleteEvent2::GetExpression-](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[und GetResult-Methoden](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) implementieren.

  Synchrone Ereignisse erfordern die Implementierung der [IDebugEngine2::ContinueFromSynchronousEvent-Methode.](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)

  Damit Ihr Modul die Ausgabe im String-Stil schreiben kann, müssen Sie die [IDebugOutputStringEvent2::GetString-Methode](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md) implementieren.

## <a name="see-also"></a>Weitere Informationen
- [Ausführungskontrolle und Zustandsbewertung](../../extensibility/debugger/execution-control-and-state-evaluation.md)

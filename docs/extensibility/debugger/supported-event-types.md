---
title: Unterstützte Ereignistypen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3fc11158987ecb1d7401f1127318138c0b865f96
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53901791"
---
# <a name="supported-event-types"></a>Unterstützte Ereignistypen
Debuggen in Visual Studio unterstützt derzeit die folgenden Ereignistypen aus:  
  
- Asynchrone Ereignisse  
  
   Benachrichtigt die sitzungsbasierter Debug-Manager (SDM) und IDE, die der Zustand der Anwendung im Debugmodus befindlichen geändert wird. Diese Ereignisse werden mit der Freizeit, das SDM und die IDE verarbeitet. Keine Antwort wird an die Debug-Engine (DE) gesendet, sobald das Ereignis verarbeitet wurde. Die [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) und [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) Schnittstellen sind Beispiele für die asynchrone Ereignisse.  
  
- Synchrone Ereignisse  
  
   Benachrichtigen Sie die SDM und IDE, die der Zustand der Anwendung im Debugmodus befindlichen geändert wird. Der einzige Unterschied zwischen dieser und asynchrone Ereignisse ist, dass eine Antwort, von gesendet wird der [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) Methode.  
  
   Das Senden eines synchronen Ereignis ist nützlich, wenn Sie Ihre DE weiter zu verarbeiten, nachdem die IDE empfängt und das Ereignis verarbeitet.  
  
- Synchrone Ereignisse beenden oder das Beenden der Ereignisse  
  
   Benachrichtigen Sie das SDM und die IDE, dass die Anwendung im Debugmodus befindlichen Ausführen von Code beendet wurde. Wenn Sie eine Beenden-Ereignis senden, mithilfe der Methode [Ereignis](../../extensibility/debugger/reference/idebugeventcallback2-event.md), [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) -Parameter ist erforderlich. Beenden des Ereignisse werden durch einen Aufruf einer der folgenden Methoden fortgesetzt:  
  
  - [Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
  - [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
  - [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
    Die Schnittstellen [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) und [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sind Beispiele für Beenden-Ereignisse.  
  
  > [!NOTE]
  >  Asynchrones beenden-Ereignisse werden nicht unterstützt. Es ist ein Fehler, wenn eine asynchrone Stopping-Ereignis zu senden.  
  
## <a name="discussion"></a>Diskussion  
 Die tatsächliche Implementierung der Ereignisse hängt von den Entwurf Ihrer DE ab. Der Typ jedes Ereignisses gesendet haben, richtet sich nach der Attribute, die festgelegt werden, wenn Sie die DE entwerfen. Beispielsweise kann ein DE senden ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) als ein asynchrones Ereignis, während eine andere als eine Beenden-Ereignis senden kann.  
  
 Die folgende Tabelle gibt an, welche Programm- und Thread-Parameter für die Ereignisse sowie die Ereignistypen erforderlich sind. Jedes Ereignis kann synchron sein. Kein Ereignis muss synchron sein.  
  
> [!NOTE]
>  Die [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) Schnittstelle ist für alle Ereignisse erforderlich.  
  
|event|IDebugProgram2|IDebugThread2|Beenden von Ereignissen|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Zulässig sind, aber nicht erforderlich|Zulässig sind, aber nicht erforderlich|Nein|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Zulässig sind, aber nicht erforderlich|Zulässig sind, aber nicht erforderlich|Nein|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Zulässig sind, aber nicht erforderlich|Zulässig sind, aber nicht erforderlich|Nein|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Zulässig sind, aber nicht erforderlich|Zulässig sind, aber nicht erforderlich|Nein|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Erforderlich|Erforderlich|Nein|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Nicht zulässig|Nicht zulässig|Nein|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Nicht zulässig|Nicht zulässig|Nein|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Zulässig sind, aber nicht erforderlich|Zulässig sind, aber nicht erforderlich|Wird bei Bedarf|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Zulässig sind, aber nicht erforderlich|Zulässig sind, aber nicht erforderlich|Wird bei Bedarf|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Zulässig sind, aber nicht erforderlich|Zulässig sind, aber nicht erforderlich|Wird bei Bedarf|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Erforderlich|Zulässig sind, aber nicht erforderlich|Nein|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Zulässig sind, aber nicht erforderlich|Zulässig sind, aber nicht erforderlich|Nein|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Erforderlich|Zulässig sind, aber nicht erforderlich|Nein|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Erforderlich|Zulässig sind, aber nicht erforderlich|Nein|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Erforderlich|Zulässig sind, aber nicht erforderlich|Nein|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Erforderlich|Zulässig sind, aber nicht erforderlich|Nein|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Zulässig sind, aber nicht erforderlich|Zulässig sind, aber nicht erforderlich|Nein|  
|IDebugStopCompleteEvent2|Erforderlich|Erforderlich|Ja|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Zulässig sind, aber nicht erforderlich|Zulässig sind, aber nicht erforderlich|Nein|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Erforderlich|Erforderlich|Nein|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Erforderlich|Erforderlich|Nein|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Zulässig sind, aber nicht erforderlich|Zulässig sind, aber nicht erforderlich|Nein|  
  
## <a name="see-also"></a>Siehe auch  
 [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)
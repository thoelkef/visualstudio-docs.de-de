---
title: Unterstützte Ereignistypen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94e26897c50fd7e10a8b831655610848cb93043f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712799"
---
# <a name="supported-event-types"></a>Unterstützte Ereignistypen
Visual Studio-Debugging unterstützt derzeit die folgenden Ereignistypen:

- Asynchrone Ereignisse

   Benachrichtigen Sie den Sitzungsdebug-Manager (SDM) und die IDE, dass sich der Status der zu debuggenden Anwendung ändert. Diese Veranstaltungen werden in der Freizeit des SDM und der IDE verarbeitet. Sobald das Ereignis verarbeitet wurde, wird keine Antwort an das Debugmodul (DE) gesendet. Die Schnittstellen [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) und [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) sind Beispiele für asynchrone Ereignisse.

- Synchrone Ereignisse

   Benachrichtigen Sie SDM und IDE, dass sich der Status der zu debuggenden Anwendung ändert. Der einzige Unterschied zwischen diesen Ereignissen und asynchronen Ereignissen besteht darin, dass eine Antwort über die [ContinueFromSynchronousEvent-Methode](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) gesendet wird.

   Das Senden eines synchronen Ereignisses ist nützlich, wenn Sie ihre DE benötigen, um die Verarbeitung fortzusetzen, nachdem die IDE das Ereignis empfangen und verarbeitet hat.

- Synchrones Beenden von Ereignissen oder Beenden von Ereignissen

   Benachrichtigen Sie das SDM und die IDE, dass die zu debuggende Anwendung den Code nicht mehr ausgeführt hat. Wenn Sie ein stoppereignis über die Methode [Ereignis](../../extensibility/debugger/reference/idebugeventcallback2-event.md)senden, ist der [IDebugThread2-Parameter](../../extensibility/debugger/reference/idebugthread2.md) erforderlich. Das Beenden von Ereignissen wird durch einen Aufruf der folgenden Methoden fortgesetzt:

  - [Ausführen](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Schritt](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    Die Schnittstellen [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) und [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sind Beispiele für das Beenden von Ereignissen.

  > [!NOTE]
  > Asynchrone Stoppereignisse werden nicht unterstützt. Es ist ein Fehler, ein asynchrones Stoppereignis zu senden.

## <a name="discussion"></a>Diskussion
 Die tatsächliche Umsetzung von Ereignissen hängt vom Design Ihrer DE ab. Der Typ jedes gesendeten Ereignisses wird durch seine Attribute bestimmt, die beim Entwerfen der DE festgelegt werden. Beispielsweise kann eine DE ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) als asynchrones Ereignis senden, während es von einem anderen als Beendenereignis gesendet werden kann.

 Die folgende Tabelle gibt an, welche Programm- und Threadparameter für welche Ereignisse sowie Ereignistypen erforderlich sind. Jedes Ereignis kann synchron sein. Kein Ereignis muss synchron sein.

> [!NOTE]
> Die [IDebugEngine2-Schnittstelle](../../extensibility/debugger/reference/idebugengine2.md) ist für alle Ereignisse erforderlich.

|Ereignis|IDebugProgram2|IDebugThread2|Beenden von Ereignissen|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Erlaubt, aber nicht erforderlich|Erlaubt, aber nicht erforderlich|Nein|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Erforderlich|Erforderlich|Ja|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Erlaubt, aber nicht erforderlich|Erlaubt, aber nicht erforderlich|Nein|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Erlaubt, aber nicht erforderlich|Erlaubt, aber nicht erforderlich|Nein|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Erlaubt, aber nicht erforderlich|Erlaubt, aber nicht erforderlich|Nein|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Erforderlich|Erforderlich|Ja|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Erforderlich|Erforderlich|Nein|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Nicht zulässig|Nicht zulässig|Nein|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Nicht zulässig|Nicht zulässig|Nein|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Erforderlich|Erforderlich|Ja|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Erlaubt, aber nicht erforderlich|Erlaubt, aber nicht erforderlich|Wird bei Bedarf|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Erforderlich|Erforderlich|Ja|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Erlaubt, aber nicht erforderlich|Erlaubt, aber nicht erforderlich|Wird bei Bedarf|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Erforderlich|Erforderlich|Ja|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Erforderlich|Erforderlich|Ja|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Erlaubt, aber nicht erforderlich|Erlaubt, aber nicht erforderlich|Wird bei Bedarf|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Erforderlich|Erlaubt, aber nicht erforderlich|Nein|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Erlaubt, aber nicht erforderlich|Erlaubt, aber nicht erforderlich|Nein|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Erforderlich|Erlaubt, aber nicht erforderlich|Nein|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Erforderlich|Erlaubt, aber nicht erforderlich|Nein|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Erforderlich|Erlaubt, aber nicht erforderlich|Nein|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Erforderlich|Erlaubt, aber nicht erforderlich|Nein|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Erlaubt, aber nicht erforderlich|Erlaubt, aber nicht erforderlich|Nein|
|IDebugStopCompleteEvent2|Erforderlich|Erforderlich|Ja|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Erforderlich|Erforderlich|Ja|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Erlaubt, aber nicht erforderlich|Erlaubt, aber nicht erforderlich|Nein|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Erforderlich|Erforderlich|Nein|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Erforderlich|Erforderlich|Nein|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Erlaubt, aber nicht erforderlich|Erlaubt, aber nicht erforderlich|Nein|

## <a name="see-also"></a>Weitere Informationen
- [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)

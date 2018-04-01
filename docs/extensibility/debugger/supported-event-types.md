---
title: Ereignistypen unterstützt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 12
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: d161b078e4001ea7f02311bbcefe4c7f1eb6b7b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="supported-event-types"></a>Unterstützte Ereignistypen
Debuggen von Visual Studio unterstützt derzeit die folgenden Ereignistypen:  
  
-   Asynchrone Ereignisse  
  
     Benachrichtigen Sie die Sitzung Debug-Manager (SDM) und IDE, die der Status der gedebuggten Anwendung geändert wird. Diese Ereignisse werden auf die Gelegenheit, das SDM und die IDE verarbeitet. Keine Antwort wird zum Debugging-Modul (DE) gesendet, sobald das Ereignis verarbeitet wird. Die [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) und [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) Schnittstellen sind Beispiele für asynchrone Ereignisse.  
  
-   Synchrone Ereignisse  
  
     Benachrichtigen Sie die SDM und die IDE, die der Status der gedebuggten Anwendung geändert wird. Der einzige Unterschied zwischen dieser Ereignisse und asynchrone Ereignisse ist, dass eine Antwort, von der gesendet wird die [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md) Methode.  
  
     Senden ein synchrone Ereignis ist hilfreich, wenn Sie Ihre DE und weiter verarbeitet werden, nachdem die IDE empfängt und das Ereignis verarbeitet benötigen.  
  
-   Synchrone Ereignisse beenden oder Anhalten Ereignisse  
  
     Benachrichtigen Sie die SDM und die IDE aus, die die gedebuggten Anwendung beendet wurde, Ausführen von Code. Beim Senden einer Stopping-Ereignis mithilfe der Methode [Ereignis](../../extensibility/debugger/reference/idebugeventcallback2-event.md), [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) Parameter ist erforderlich. Beenden des Ereignisse werden durch einen Aufruf in einem der folgenden Methoden fortgesetzt:  
  
    -   [Führen Sie](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Step](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     Die Schnittstellen [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) und [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sind Beispiele für Ereignisse wird beendet.  
  
    > [!NOTE]
    >  Asynchrone beenden-Ereignisse werden nicht unterstützt. Es ist ein Fehler zum Senden eines Ereignisses asynchrone beenden.  
  
## <a name="discussion"></a>Diskussion  
 Die tatsächliche Implementierung von Ereignissen hängt von den Entwurf Ihrer de ab. Der Typ der einzelnen Ereignisse gesendet wird durch seine Attribute bestimmt, die festgelegt werden, wenn Sie die DE entwerfen. Z. B. eine DE sendet möglicherweise eine [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) als asynchrones Ereignis, während eine andere als Stopping-Ereignis gesendet werden kann.  
  
 In der folgenden Tabelle gibt an, welche Programm- und Thread-Parameter für die Ereignisse sowie die Ereignistypen erforderlich sind. Jedes Ereignis kann synchron sein. Es muss kein Ereignis synchron sein.  
  
> [!NOTE]
>  Die [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) Schnittstelle ist für alle Ereignisse erforderlich.  
  
|event|IDebugProgram2|IDebugThread2|Beenden von Ereignissen|  
|-----------|--------------------|-------------------|---------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Zulässig, jedoch nicht erforderlich.|Zulässig, jedoch nicht erforderlich.|Nein|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Zulässig, jedoch nicht erforderlich.|Zulässig, jedoch nicht erforderlich.|Nein|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Zulässig, jedoch nicht erforderlich.|Zulässig, jedoch nicht erforderlich.|Nein|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Zulässig, jedoch nicht erforderlich.|Zulässig, jedoch nicht erforderlich.|Nein|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Erforderlich|Erforderlich|Nein|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Nicht zulässig|Nicht zulässig|Nein|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Nicht zulässig|Nicht zulässig|Nein|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Zulässig, jedoch nicht erforderlich.|Zulässig, jedoch nicht erforderlich.|Wird bei Bedarf|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Zulässig, jedoch nicht erforderlich.|Zulässig, jedoch nicht erforderlich.|Wird bei Bedarf|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Zulässig, jedoch nicht erforderlich.|Zulässig, jedoch nicht erforderlich.|Wird bei Bedarf|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Erforderlich|Zulässig, jedoch nicht erforderlich.|Nein|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Zulässig, jedoch nicht erforderlich.|Zulässig, jedoch nicht erforderlich.|Nein|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Erforderlich|Zulässig, jedoch nicht erforderlich.|Nein|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Erforderlich|Zulässig, jedoch nicht erforderlich.|Nein|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Erforderlich|Zulässig, jedoch nicht erforderlich.|Nein|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Erforderlich|Zulässig, jedoch nicht erforderlich.|Nein|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Zulässig, jedoch nicht erforderlich.|Zulässig, jedoch nicht erforderlich.|Nein|  
|IDebugStopCompleteEvent2|Erforderlich|Erforderlich|Ja|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Zulässig, jedoch nicht erforderlich.|Zulässig, jedoch nicht erforderlich.|Nein|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Erforderlich|Erforderlich|Nein|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Erforderlich|Erforderlich|Nein|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Zulässig, jedoch nicht erforderlich.|Zulässig, jedoch nicht erforderlich.|Nein|  
  
## <a name="see-also"></a>Siehe auch  
 [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)
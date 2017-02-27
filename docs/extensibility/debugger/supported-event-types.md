---
title: "Die unterst&#252;tzten Ereignistypen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK] unterstützt Ereignisse"
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Die unterst&#252;tzten Ereignistypen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das Visual Studio, das gerade gedebuggt wird, unterstützt die folgenden Ereignistypen:  
  
-   Asynchrone Ereignisse  
  
     Melden Sie sich den Debug\- Manager der Sitzung \(SDM\) und IDE, das den Zustand der Anwendung, die gedebuggt wird, ändert.  Diese Ereignisse werden in der Freizeit des SDM und der IDE verarbeitet.  Keine Antwort wird dem DE Modul \(Debuggen\) gesendet sobald das Ereignis verarbeitet wird.  Die [IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) und [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)\-Schnittstellen sind Beispiele für asynchronen Ereignissen.  
  
-   Synchrone Ereignisse  
  
     Melden Sie sich das SDM und die IDE, dass der Zustand der Anwendung, die gedebuggt wird, ändert.  Der einzige Unterschied zwischen diesen Ereignissen und asynchronen Ereignissen besteht darin, dass eine Antwort mithilfe der [ContinueFromSynchronousEvent](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)\-Methode gesendet wird.  
  
     Ein synchrone Ereignis zu senden ist hilfreich, wenn Sie DE benötigen, um die Verarbeitung fortzusetzen, nachdem der IDE und verarbeitet das Ereignis empfangen.  
  
-   Synchrone aufhörende Ereignissen beenden oder Ereignisse  
  
     Melden Sie sich das SDM und die IDE, dass die Anwendung, die gedebuggt wird, beendet wurde, Code auszuführen.  Wenn Sie ein aufhörendes Ereignis mithilfe der Methode [Ereignis](../../extensibility/debugger/reference/idebugeventcallback2-event.md)senden, ist der [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)\-Parameter erforderlich.  Ereignisse werden durch einen Aufruf Beenden, bis der Fortsetzung der folgenden Methoden:  
  
    -   [Ausführen](../../extensibility/debugger/reference/idebugprogram2-execute.md)  
  
    -   [Schritt](../../extensibility/debugger/reference/idebugprogram2-step.md)  
  
    -   [Weiter](../../extensibility/debugger/reference/idebugprogram2-continue.md)  
  
     Die Schnittstellen [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) und [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sind Beispiele für Beendens von Ereignissen.  
  
    > [!NOTE]
    >  Asynchrone aufhörende Ereignisse werden nicht unterstützt.  Es ist ein Fehler, um einen asynchronen aufhörenden Ereignisses zu senden.  
  
## Erörterung  
 Die tatsächliche Implementierung von Ereignissen hängt vom Entwurf DEs ab.  Der Typ jedes gesendeten Ereignisses wird durch seine Attribute bestimmt, die festgelegt werden, wenn Sie entwerfen. DE  Zum Beispiel sendet ein DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) als asynchrones Ereignis, während andere möglicherweise als aufhörendes Ereignis senden.  
  
 Die folgende Tabelle gibt an, welche Threads und Programme erforderlichen Parameter für die Ereignistypen sowie Ereignisse.  Jedes Ereignis kann synchron sein.  Kein Ereignis muss synchron sein.  
  
> [!NOTE]
>  Die [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md)\-Schnittstelle ist für alle Ereignisse erforderlich.  
  
|Ereignis|IDebugProgram2|IDebugThread2|Beenden von Ereignissen|  
|--------------|--------------------|-------------------|-----------------------------|  
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Zulässige, aber nicht erforderlich|Zulässige, aber nicht erforderlich|Nein|  
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Zulässige, aber nicht erforderlich|Zulässige, aber nicht erforderlich|Nein|  
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Zulässige, aber nicht erforderlich|Zulässige, aber nicht erforderlich|Nein|  
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Zulässige, aber nicht erforderlich|Zulässige, aber nicht erforderlich|Nein|  
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Erforderlich|Erforderlich|Nein|  
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Nicht zulässig|Nicht zulässig|Nein|  
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Nicht zulässig|Nicht zulässig|Nein|  
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Zulässige, aber nicht erforderlich|Zulässige, aber nicht erforderlich|Kann sein|  
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Zulässige, aber nicht erforderlich|Zulässige, aber nicht erforderlich|Kann sein|  
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Zulässige, aber nicht erforderlich|Zulässige, aber nicht erforderlich|Kann sein|  
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Erforderlich|Zulässige, aber nicht erforderlich|Nein|  
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Zulässige, aber nicht erforderlich|Zulässige, aber nicht erforderlich|Nein|  
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Erforderlich|Zulässige, aber nicht erforderlich|Nein|  
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Erforderlich|Zulässige, aber nicht erforderlich|Nein|  
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Erforderlich|Zulässige, aber nicht erforderlich|Nein|  
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Erforderlich|Zulässige, aber nicht erforderlich|Nein|  
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Zulässige, aber nicht erforderlich|Zulässige, aber nicht erforderlich|Nein|  
|IDebugStopCompleteEvent2|Erforderlich|Erforderlich|Ja|  
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Erforderlich|Erforderlich|Ja|  
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Zulässige, aber nicht erforderlich|Zulässige, aber nicht erforderlich|Nein|  
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Erforderlich|Erforderlich|Nein|  
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Erforderlich|Erforderlich|Nein|  
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Zulässige, aber nicht erforderlich|Zulässige, aber nicht erforderlich|Nein|  
  
## Siehe auch  
 [Senden von Ereignissen](../../extensibility/debugger/sending-events.md)
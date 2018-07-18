---
title: Anfügen und Trennen von einem Programm | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca1eab8c6b5e1edc2354ea5f2dfd8922bb7cae16
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110067"
---
# <a name="attaching-and-detaching-to-a-program"></a>Anfügen und Trennen an ein Programm
Das Anfügen des Debuggers erfordert das Senden der richtigen Sequenz von Methoden und Ereignisse mit den entsprechenden Attributen.  
  
## <a name="sequence-of-methods-and-events"></a>Sequenz von Methoden und Ereignisse  
  
1.  Ruft die Sitzungs-Debug-Manager (SDM) die [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Methode.  
  
     Das Prozessmodell Debugmodus-Modul (DE) anhand der `IDebugProgramNodeAttach2::OnAttach` Methodenrückgabe eine der folgenden Methoden, die bestimmt, was daraufhin geschieht.  
  
     Wenn `S_FALSE` zurückgegeben wird, wird das Debugging-Modul wurde erfolgreich an das Programm angefügt wurde. Andernfalls die [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md) Methode wird aufgerufen, um den Prozess anhängen abzuschließen.  
  
     Wenn `S_OK` wird zurückgegeben, die DE ist im selben Prozess wie die SDM geladen werden soll. Die SDM führt die folgenden Aufgaben:  
  
    1.  Aufrufe [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) Modulinformationen des DE abgerufen werden.  
  
    2.  Zusammen erstellt die Deutschland.  
  
    3.  Aufrufe [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2.  Sendet die DE ein [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.  
  
3.  Sendet die DE ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.  
  
4.  Sendet die DE ein [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) , das SDM mit einer `EVENT_SYNC_STOP` Attribut.  
  
 Trennen von einem Programm ist eine einfache, zweistufiger Prozess, wie folgt:  
  
1.  Ruft die SDM [trennen](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
2.  Sendet die DE ein [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
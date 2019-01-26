---
title: Anfügen und Trennen von einem Programm | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e0e28a266653383621f1d49f37ea8ea4d3a8b8f8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957389"
---
# <a name="attaching-and-detaching-to-a-program"></a>Anfügen und Trennen von einem Programm
Das Anfügen des Debuggers gesendet werden müssen, der richtigen Sequenz von Methoden und Ereignisse mit den richtigen Attributen.  
  
## <a name="sequence-of-methods-and-events"></a>Sequenz von Methoden und Ereignisse  
  
1. Ruft die Sitzungs-Debug-Manager (SDM) die [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Methode.  
  
    Basierend auf der Debug-Engine (DE)-Prozessmodell der `IDebugProgramNodeAttach2::OnAttach` Methode gibt einen der folgenden Methoden, die bestimmt, was als Nächstes geschieht zurück.  
  
    Wenn `S_FALSE` zurückgegeben wird, wird die Debug-Engine wurde erfolgreich an das Programm angefügt wurde. Andernfalls die [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md) Methode wird aufgerufen, um den anfügungsprozess zu beenden.  
  
    Wenn `S_OK` zurückgegeben wird, ist der DE in demselben Prozess wie das SDM geladen werden. Das SDM führt die folgenden Aufgaben:  
  
   1.  Aufrufe [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) zum Abrufen der Engine Informationen des DE.  
  
   2.  Gemeinsam erstellt die DE.  
  
   3.  Aufrufe [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2. Der DE sendet eine [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.  
  
3. Der DE sendet eine [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut. 
  
4. Der DE sendet eine [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) , das SDM mit einer `EVENT_SYNC_STOP` Attribut.  
  
   Trennen von einem Programm ist eine einfache, zweistufiger Prozess, wie folgt:  
  
5. Die SDM-Aufrufe [trennen](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
6. Der DE sendet eine [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
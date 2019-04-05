---
title: Starten des Debuggers | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4ae4c7eed2ae5477be02384ebe7b7c45383eaffb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58946199"
---
# <a name="launching-the-debugger"></a>Starten des Debuggers
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Starten des Debuggers gesendet werden müssen, der richtigen Sequenz von Methoden und Ereignisse mit ihren entsprechenden Attributen.  
  
## <a name="sequences-of-methods-and-events"></a>Sequenzen von Methoden und Ereignisse  
  
1.  Sitzungsbasierter Debug-Manager (SDM) wird aufgerufen, durch Auswählen der **Debuggen** Menü auswählen und dann **starten**. Finden Sie unter [Starten eines Programms](../../extensibility/debugger/launching-a-program.md) für Weitere Informationen.  
  
2.  Die SDM-Aufrufe [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Methode.  
  
3.  Basierend auf der Debug-Engine (DE)-Prozessmodell der `IDebugProgramNodeAttach2::OnAttach` Methode gibt einen der folgenden Methoden, die bestimmt, was als Nächstes geschieht zurück.  
  
     Wenn `S_FALSE` wird zurückgegeben, die Debug-Engine (DE) ist dabei den virtuellen Computer geladen werden.  
  
     - oder -   
  
     Wenn `S_OK` zurückgegeben wird, ist der DE geladen werden von der SDM in-Process. Das SDM führt dann die folgenden Aufgaben aus:  
  
    1.  Aufrufe [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) zum Abrufen der Engine Informationen des DE.  
  
    2.  Gemeinsam erstellt die DE.  
  
    3.  Aufrufe [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  Der DE sendet eine [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.  
  
5.  Der DE sendet eine [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.  
  
6.  Der DE sendet eine [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.  
  
7.  Der DE sendet eine [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.  
  
8.  Der DE sendet eine [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)   
 [Starten eines Programms](../../extensibility/debugger/launching-a-program.md)

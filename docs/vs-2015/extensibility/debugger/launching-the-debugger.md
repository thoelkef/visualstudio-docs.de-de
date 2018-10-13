---
title: Starten des Debuggers | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2a985d2184ecc69ab4fa2da3b634ab82281fc3ef
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49201213"
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


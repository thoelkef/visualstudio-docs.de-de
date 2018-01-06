---
title: Starten des Debuggers | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7b5b596f553c0f84c9306bba010d2b97a33e1a16
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="launching-the-debugger"></a>Starten des Debuggers
Starten des Debuggers erfordert das Senden der richtigen Sequenz von Methoden und Ereignisse mit den entsprechenden Attributen.  
  
## <a name="sequences-of-methods-and-events"></a>Sequenzen von Methoden und Ereignisse  
  
1.  Die Sitzungs-Debug-Manager (SDM) wird aufgerufen, durch Auswählen der **Debuggen** Menü, und drücken Sie dann die **starten**. Finden Sie unter [Programmstart](../../extensibility/debugger/launching-a-program.md) für Weitere Informationen.  
  
2.  Ruft die SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Methode.  
  
3.  Das Prozessmodell Debugmodus-Modul (DE) anhand der `IDebugProgramNodeAttach2::OnAttach` Methodenrückgabe eine der folgenden Methoden, die bestimmt, was daraufhin geschieht.  
  
     Wenn `S_FALSE` zurückgegeben wird, wird die Debugging-Modul (DE) ist für die der virtuelle Computer geladen werden soll.  
  
     - oder -   
  
     Wenn `S_OK` wird zurückgegeben, die DE zu ladende ist von der SDM in-Process. Die SDM führt dann die folgenden Aufgaben:  
  
    1.  Aufrufe [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) Modulinformationen des DE abgerufen werden.  
  
    2.  Zusammen erstellt die Deutschland.  
  
    3.  Aufrufe [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  Sendet die DE ein [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.  
  
5.  Sendet die DE ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.  
  
6.  Sendet die DE ein [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.  
  
7.  Sendet die DE ein [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.  
  
8.  Sendet die DE ein [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debugger-Ereignisse](../../extensibility/debugger/calling-debugger-events.md)   
 [Starten eines Programms](../../extensibility/debugger/launching-a-program.md)
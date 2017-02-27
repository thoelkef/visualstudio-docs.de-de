---
title: "Starten des Debuggers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK], den Debugger zu starten"
  - "Debugger [Debugging-SDK], starten"
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Starten des Debuggers
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Starten der Debugger benötigt das Senden der richtigen Sequenz von Methoden und Ereignissen mit ihren entsprechenden Attributen.  
  
## Sequenzen von Methoden und Ereignissen  
  
1.  Der Debuginformationen Manager der Sitzung \(SDM\) wird aufgerufen, indem im Menü **Debuggen** auswählen und dann **Start**auswählt.  Weitere Informationen finden Sie unter [Starten eines Programms](../../extensibility/debugger/launching-a-program.md).  
  
2.  Das SDM ruft [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)\-Methode auf.  
  
3.  Basierend auf das Debuggen Prozessmodell des Moduls \(DE `IDebugProgramNodeAttach2::OnAttach` \) gibt die Methode eine der folgenden Methoden zurück, die bestimmt, was auf Weiter.  
  
     Wenn `S_FALSE` zurückgegeben wird, muss das Debugmodul \(DE\) im Prozess des virtuellen Computers geladen werden.  
  
     \- oder \-  
  
     Wenn `S_OK` zurückgegeben wird, wird im Prozess des DE SDM geladen werden.  Das SDM führt dann die folgenden Aufgaben aus:  
  
    1.  Aufrufe [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) Modul, in dem die Informationen DEs abzurufen.  
  
    2.  Gemeinsam erstellt. DE  
  
    3.  Aufrufen von [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4.  DE [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) sendet den SDM mit einem `EVENT_SYNC`\-Attribut.  
  
5.  DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) sendet den SDM mit einem `EVENT_SYNC`\-Attribut.  
  
6.  DE [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) sendet den SDM mit einem `EVENT_SYNC`\-Attribut.  
  
7.  DE [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) sendet den SDM mit einem `EVENT_SYNC`\-Attribut.  
  
8.  DE [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) sendet den SDM mit einem `EVENT_SYNC`\-Attribut.  
  
## Siehe auch  
 [Aufrufen von Debugger\-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)   
 [Starten eines Programms](../../extensibility/debugger/launching-a-program.md)
---
title: "Anf&#252;gen und Trennen von einem Programm | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debugmodule, Anhängen an Programme"
  - "Debugmodule, Trennen von Programmen"
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Anf&#252;gen und Trennen von einem Programm
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das Anfügen des Debuggers erfordert das Senden der richtigen Sequenz von Methoden und Ereignisse mit den entsprechenden Attributen.  
  
## Sequenz von Methoden und Ereignissen  
  
1.  Der Debuginformationen Manager der Sitzung \(SDM\) ruft die [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)\-Methode auf.  
  
     Basierend auf das Debuggen Prozessmodell des Moduls \(DE `IDebugProgramNodeAttach2::OnAttach` \) gibt die Methode eine der folgenden Methoden zurück, die bestimmt, was auf Weiter.  
  
     Wenn `S_FALSE` zurückgegeben wird, ist das Debugmodul erfolgreich auf das Programm angefügt.  Andernfalls wird die [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md)\-Methode aufgerufen, um den Prozess abzuschließen. Anfügen  
  
     Wenn `S_OK` zurückgegebene soll DE im selben Prozess wie das SDM geladen werden.  Das SDM führt die folgenden Aufgaben aus:  
  
    1.  Aufrufe [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) Modul, in dem die Informationen DEs abzurufen.  
  
    2.  Gemeinsam erstellt. DE  
  
    3.  Aufrufen von [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2.  DE [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) sendet den SDM mit einem `EVENT_SYNC`\-Attribut.  
  
3.  DE [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) sendet den SDM mit einem `EVENT_SYNC`\-Attribut.  
  
4.  DE [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) sendet den SDM mit einem `EVENT_SYNC_STOP`\-Attribut.  
  
 Das Trennen von einem Programm ist ein einfacher, die zwei Schritte wie folgt:  
  
1.  Das SDM ruft [Trennen](../../extensibility/debugger/reference/idebugprogram2-detach.md)an.  
  
2.  DE [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)sendet.  
  
## Siehe auch  
 [Aufrufen von Debugger\-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)
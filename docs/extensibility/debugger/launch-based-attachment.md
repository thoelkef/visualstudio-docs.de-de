---
title: "Launch-basierte Anlage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debugmodule, starten"
  - "Debugmodule, Anhängen an Programme"
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Launch-basierte Anlage
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Start\-basierte Anlage zu einem Programm ist automatisch.  Wenn das Programm das Hosten Prozess vom SDM gestartet wird, folgt Start\-basierte Anlage einem Pfad, der dem der manuellen Anlagen Methode ähnelt.  Weitere Informationen finden Sie unter [Zum Programmieren anfügen](../../extensibility/debugger/attaching-to-the-program.md).  
  
## Der Prozess anfügende  
 Der Hauptunterschied ist die Sequenz von Ereignissen **Anfügen** dem nächsten Aufruf wie folgt:  
  
1.  Senden Sie ein **IDebugEngineCreateEvent2** SDM auf das Ereignisobjekt.  Ausführliche Informationen finden Sie unter [Senden von Ereignissen](../../extensibility/debugger/sending-events.md).  
  
2.  Rufen Sie die `IDebugProgram2::GetProgramId`\-Methode für die **IDebugProgram2**\-Schnittstelle an, die an die Methode übergeben wird. **Anfügen**  
  
3.  Senden Sie ein **IDebugProgramCreateEvent2**\-Ereignisobjekt, um das SDM zu benachrichtigen, dass das lokale **IDebugProgram2**\-Objekt erstellt wurde, um das Programm zu präsentieren. DE  
  
4.  Senden Sie ein [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)\-Ereignisobjekt, um das SDM zu benachrichtigen, dass ein neuer Thread für den Prozess erstellt wird, der ausgelöst hat.  
  
## Siehe auch  
 [Die erforderlichen Ereignisse senden](../../extensibility/debugger/sending-the-required-events.md)   
 [Ein Programm zum Debuggen aktivieren](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
---
title: "Anf&#252;gen an ein Programm direkt | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debugmodule, Anhängen an Programme"
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Anf&#252;gen an ein Programm direkt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Benutzer, die den Testprogrammen in einem Prozess vorhanden sein sollen, der bereits in der Regel ausgeführt wird, führen diesen Prozess:  
  
1.  In der IDE **Debugprozesse** wählen Sie den Befehl aus dem Menü **Extras** aus.  
  
     Das Dialogfeld **Prozesse** wird angezeigt.  
  
2.  Wählen Sie einen Prozess aus, und klicken Sie auf die Schaltfläche **Anfügen** .  
  
     Alle, **An den Prozess anhängen** Dialogfeld angezeigt wird und führt für Module Debuggen DES \(\) auf dem Computer installiert.  
  
3.  Geben Sie die DES an, der verwendet wird, um den ausgewählten Prozess zu debuggen, und klicken Sie dann auf **OK**.  
  
 Das Debuggen von Paket startet eine Debugsitzung und übergibt die Liste mit den darauf.  Die Debugsitzung führt wiederum diese Liste zusammen mit einer Rückruffunktion, die auf den ausgewählten Prozess und fragt dann um den Prozess, um ihre Ausführung von Programmen aufzulisten.  
  
 Programmgesteuert als Reaktion auf eine Benutzeranforderung, instanziiert das Debuggen des Pakets Debuggen Manager der Sitzung \(SDM\) und übergibt die Liste ausgewählten DES darauf.  Zusammen mit der Liste führt das Debuggen des Pakets SDM eine [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)\-Schnittstelle.  Das Debuggen von Paket führt die Liste mit den in den ausgewählten Prozess, indem [IDebugProcess2::Anfügen](../../extensibility/debugger/reference/idebugprocess2-attach.md)aufruft.  Das SDM ruft dann [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) im Anschluss an die Programme aufzulisten, die in den Prozess ausgeführt werden.  
  
 Ab hier werden alle Debug\- Modul mit einem Programm angefügt, genau wie in [Nach dem Start anfügen](../../extensibility/debugger/attaching-after-a-launch.md)mit zwei Ausnahmen einzeln aufgelistet.  
  
 Für die Effizienz werden DES, die implementiert werden, um einen Adressraum mit dem SDM freizugeben, für jeden DE einen Satz von Programmen verfügt, auf Anfügen.  In diesem Fall ruft [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)[IDebugEngine2::Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md) an und übergibt es ein Array von Programmen in die Anfügen an.  
  
 Die zweite Ausnahme besteht darin, dass die Starten von Ereignissen, die durch Anfügen an ein Programm DE gesendet werden, das bereits ausgeführt wird, nicht in der Regel das Einstiegspunkt \- Ereignis enthalten.  
  
## Siehe auch  
 [Senden Startereignisse nach einem starten](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Debugging\-Aufgaben](../../extensibility/debugger/debugging-tasks.md)
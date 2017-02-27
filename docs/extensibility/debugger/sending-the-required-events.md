---
title: "Die erforderlichen Ereignisse senden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Ereignisse durch erforderliche Debuggen [SDK-Debuggen]"
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Die erforderlichen Ereignisse senden
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Verwenden Sie dieses Verfahren zum Senden von erforderlichen Ereignisse.  
  
## Prozess zum Senden von Ereignissen erforderlichen  
 Die folgenden Ereignisse sind, in dieser Reihenfolge erforderlich, wenn eine Debug\- Modul \(DE\) erstellt wurde und es in einem Programm angefügt ist:  
  
1.  Senden Sie ein [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)\-Ereignisobjekt für das Debuggen von Manager der Sitzung \(SDM\), wenn DE zum Debuggen einer oder mehreren Programmen in einem Prozess initialisiert wird.  
  
2.  Wenn das Programm gedebuggt werden soll angefügt ist, senden Sie ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) SDM auf das Ereignisobjekt.  Dieses Ereignis kann ein aufhörendes Ereignis, je nachdem, welche Motorbauart.  
  
3.  Wenn das Programm angefügt wird, wenn der Prozess gestartet wird, senden Sie ein [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) SDM auf das Ereignisobjekt, damit die IDE des neuen Threads zu benachrichtigen.  Dieses Ereignis kann ein aufhörendes Ereignis, je nachdem, welche Motorbauart.  
  
4.  Senden Sie ein [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) SDM auf das Ereignisobjekt, wenn das Programm, das gedebuggt wird, die beim Laden oder das Anfügen an das Programm ausgeführt wird.  Dieses Ereignis muss ein aufhörendes Ereignis sein.  
  
5.  Wenn die Anwendung gedebuggt werden gestartet wird, senden Sie ein [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) SDM auf das Ereignisobjekt, wenn die erste Anweisung des Codes in der Architektur der Laufzeit gerade ausgeführt wird.  Dieses Ereignis wird immer ein aufhörendes Ereignis.  Beim schrittweisen in der Debugsitzung, wird die IDE für dieses Ereignis auf.  
  
> [!NOTE]
>  Zahlreiche Sprachen verwenden globale Initialisierungen oder die externe, vorkompilierten Funktionen \(von der CRT\-Bibliothek oder \- \_Main\) am Anfang des Codes.  Wenn die Sprache des Programms, das Sie debuggen, einen dieser Typen der Elemente vor der ersten Eintrag Haupteinstiegspunkt enthält, wird dieser Code ausgeführt wird und das Einstiegspunkt für Auswahlereignisse wird gesendet, wenn der benutzerdefinierte Einstiegspunkt, wie **Main** oder `WinMain`, erreicht ist.  
  
## Siehe auch  
 [Ein Programm zum Debuggen aktivieren](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
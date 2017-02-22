---
title: "Senden von Ereignissen | Microsoft Docs"
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
  - "Debuggen [Debugging-SDK], Senden von Ereignissen"
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Senden von Ereignissen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Der Mechanismus für die Kommunikation zwischen dem Debugger und dem DE Modul \(Debuggen\) ist ein Ereignismodell auf der Grundlage von DCOM.  Ereignisse werden als COM\-Objekte gesendet, und jedes Ereignis enthält Parameter, die Folgendes angeben:  
  
-   DE, das das Ereignis aufgerufen hat.  
  
-   Eine Beschreibung der geschah.  
  
-   Der Prozess, und das Programm wird der Thread, der den Kontext angibt, in dem das Ereignis aufgetreten ist.  Der Prozess wird nicht für Ereignisse gesendet, die von DE gesendet werden.  
  
-   Der Ereignistyp, der angibt, ob das Ereignis synchron oder asynchron ist.  
  
 Alle von Ereignissen werden mithilfe der Methode [IDebugEventCallback2::Ereignis](../../extensibility/debugger/reference/idebugeventcallback2-event.md)gesendet.  
  
## In diesem Abschnitt  
 [Ereignisquellen](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Erläutert die beiden Quellen von Ereignissen: Das Debugmodul \(DE\) und der Debug\- Manager der Sitzung \(SDM\).  
  
 [Unterstützte Ereignistypen](../../extensibility/debugger/supported-event-types.md)  
 Erläutert die derzeit unterstützten Ereignistypen: synchron und asynchron.  
  
 [Ereignis\-Beschreibungen](../../extensibility/debugger/event-descriptions.md)  
 Definiert Ereignisse und die Gründe für deren Verwendung.  
  
## Verwandte Abschnitte  
 [Debuggen eines benutzerdefinierten Moduls erstellen](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Beschreibt, wie DE mit dem Interpreter oder dem Betriebssystem verwendet werden kann, um Debugdienste bereitzustellen.
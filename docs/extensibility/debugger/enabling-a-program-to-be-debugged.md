---
title: "Ein Programm zum Debuggen aktivieren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK], mit dessen Hilfe für Programme"
ms.assetid: 61d24820-0cd9-48b6-8674-6813f7493237
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# Ein Programm zum Debuggen aktivieren
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Bevor das Debugmodul \(DE\) ein Programm debuggen können, müssen Sie zuerst starten oder DE es einem vorhandenen Programm anhängen.  
  
## In diesem Abschnitt  
 [Abrufen eines Anschlusses](../../extensibility/debugger/getting-a-port.md)  
 Erläutert, wie ein Anschluss wie der erste Schritt zum Aktivieren eines Programms wird gedebuggt werden soll.  
  
 [Das Programm registrieren](../../extensibility/debugger/registering-the-program.md)  
 Erklärt den nächsten Schritt, wenn ein Programm gedebuggt werden soll: Aktivieren dieses mit dem Anschluss registrieren.  Sobald registriert, kann das Programm entweder durch die Schritte zum Debuggen oder Anfügen des Just\-In\-Time \(JIT\) \- gedebuggt werden.  
  
 [Zum Programmieren anfügen](../../extensibility/debugger/attaching-to-the-program.md)  
 Erklärt den nächsten Schritt: Programmieren den Debugger anfügen.  
  
 [Start\-basiertes anfügen](../../extensibility/debugger/launch-based-attachment.md)  
 Beschreibt Start\-basierte Anlage zu einem Programm, das nach dem Start automatisch vom SDM ist.  
  
 [Die erforderlichen Ereignisse senden](../../extensibility/debugger/sending-the-required-events.md)  
 Schritte bei der Implementierung durch die erforderlichen Ereignisse, ob eine Debug\- Modul \(DE\) erstellt wurde und es in einem Programm angefügt wird.  
  
## Verwandte Abschnitte  
 [Debuggen eines benutzerdefinierten Moduls erstellen](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Definiert eine Debug\- Modul \(DE\), und beschreibt die Dienste, die durch DE interfaces implementiert werden und wie sie den Debugger an den Übergang zwischen verschiedenen Betriebsweisen verursachen können.
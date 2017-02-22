---
title: "SDI-Serveranwendungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "SDI-Serveranwendungen"
  - "SDI-Serveranwendungen, Debuggen"
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# SDI-Serveranwendungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Debuggen einer SDI\-Serveranwendung müssen Sie für Projekte in C\/C\+\+, C\# oder Visual Basic im Dialogfeld *Project*\-Eigenschaftenseiten in der Eigenschaft **Befehlszeilenargumente** die Option `/Embedding` oder `/Automation` festlegen.  
  
 Mithilfe dieser Befehlszeilenargumente kann die Serveranwendung vom Debugger wie von einem Container aus gestartet werden.  Das Starten des Containers im Programm\-Manager oder Datei\-Manager bewirkt dann, dass der Container die im Debugger gestartete Instanz des Servers verwendet.  
  
## Suchen der Eigenschaft Befehlszeilenargumente  
 Zum Öffnen des Dialogfelds *Project*\-Eigenschaftenseiten klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf das Projekt und klicken anschließend im Kontextmenü auf Eigenschaften.  Die Eigenschaft **Befehlszeilenargumente** wird angezeigt, wenn Sie die Kategorie **Konfigurationseigenschaften** erweitern und dann auf die Seite **Debuggen** klicken.  
  
## Siehe auch  
 [Debuggen von COM und ActiveX](../debugger/com-and-activex-debugging.md)   
 [Gewusst wie: Debuggen von COM\-Servern](../debugger/how-to-debug-com-servers.md)
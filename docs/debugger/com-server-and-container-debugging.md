---
title: "Debuggen von COM-Servern und -Containern | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.com"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen eines Containers für ActiveX-Steuerelemente [Visual Studio]"
  - "ActiveX-Steuerelemente, Debuggen"
  - "COM [Visual Studio], Debuggen"
  - "COM-Server, Debuggen"
  - "Debuggen von ActiveX-Steuerelementen"
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debuggen von COM-Servern und -Containern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

COM\-Anwendungen führen eine Reihe von Tasks durch, die nicht direkt vom Programmierer gesteuert werden können.  Zu den Bereichen, in denen ein unerwartetes Verhalten auftreten kann, gehören beispielsweise die Kommunikation zwischen DLLs, die Verwendungshäufigkeit von Objekten sowie Zwischenablageoperationen.  In einem solchen Fall sollten Sie zunächst die Problemursache ermitteln.  
  
 Der Visual Studio\-Debugger unterstützt das Springen über und in Container und Server.  Dies schließt die Möglichkeit ein, Remoteprozeduraufrufe zu überspringen.  
  
## In diesem Thema  
  
1.  [Debuggen eines COM-Servers und der Container in der gleichen Projektmappe](../debugger/com-server-and-container-debugging.md#BKMK_COMServerandContainerintheSameSolution)  
  
2.  [Debuggen einer Serveranwendung ohne Containerinformationen](../debugger/com-server-and-container-debugging.md#BKMK_ServerApplicationWithoutContainerInformation)  
  
3.  [Debuggen einer Server- und Domänenisolationsanwendung (SDI)](../debugger/com-server-and-container-debugging.md#BKMK_DebuggingaServerandDomainIsolationSDIApplication)  
  
##  <a name="BKMK_COMServerandContainerintheSameSolution"></a> Debuggen eines COM\-Servers und der Container in der gleichen Projektmappe  
 COM\-Server und \-Container können mithilfe von zwei Projekten in derselben Projektmappe gedebuggt werden.  Sie legen die geeigneten Haltepunkte pro Projekt fest und beginnen dann mit dem Debuggen.  Wenn der Container einen Server aufruft und auf einen Haltepunkt trifft, wartet der Container so lange, bis der Servercode wieder verfügbar ist \(d. h., bis der Debugvorgang beendet ist\).  
  
 Das Debuggen eines COM\-Containers ist vergleichbar mit dem Debuggen eines Standardprogramms.  Hiervon ausgenommen ist jedoch das Debuggen eines Ereignisses, durch das ein Rückruf generiert wird \(z. B. das Ziehen von Daten über die Containeranwendung\).  In diesem Fall müssen Sie einen Haltepunkt in der Rückruffunktion setzen.  
  
##  <a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Debuggen einer Serveranwendung ohne Containerinformationen  
 Wenn Sie keine Debuginformationen besitzen oder diese für Ihre Containeranwendung nicht verwenden möchten, besteht das Debuggen der Serveranwendung aus drei Schritten:  
  
1.  Debuggen Sie den Server wie eine normale Anwendung.  
  
2.  Legen Sie die gewünschten Haltepunkte fest.  
  
3.  Starten Sie die Containeranwendung.  
  
##  <a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Debuggen einer Server\- und Domänenisolationsanwendung \(SDI\)  
 Beim Debuggen einer SDI\-Serveranwendung müssen Sie für Projekte in C\/C\+\+, C\# oder Visual Basic im Dialogfeld *Projekt*\-Eigenschaftenseiten in der Eigenschaft **Befehlszeilenargumente** die Option `/Embedding` oder `/Automation` festlegen.  
  
 Mithilfe dieser Befehlszeilenargumente kann die Serveranwendung vom Debugger wie von einem Container aus gestartet werden.  Das Starten des Containers im Programm\-Manager oder Datei\-Manager bewirkt dann, dass der Container die im Debugger gestartete Instanz des Servers verwendet.  
  
 Zum Öffnen des Dialogfelds *Projekt*\-Eigenschaftenseiten klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf das Projekt und klicken anschließend im Kontextmenü auf Eigenschaften.  Die Eigenschaft **Befehlszeilenargumente** wird angezeigt, wenn Sie die Kategorie **Konfigurationseigenschaften** erweitern und dann auf die Seite **Debuggen** klicken.  
  
## Siehe auch  
 [Debuggen von COM und ActiveX](../debugger/com-and-activex-debugging.md)
---
title: "Sicherheits&#252;berlegungen zu Schnellansichten | Microsoft Docs"
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
  - "Sicherheit [Visual Studio], Schnellansichten"
  - "Schnellansichten, Sicherheit"
ms.assetid: cdd86bd5-b729-409b-a7c6-374efa091eb1
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Sicherheits&#252;berlegungen zu Schnellansichten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Schreiben einer Schnellansicht kann potenzielle Sicherheitsrisiken nach sich ziehen.  Bisher sind keine bekannten Angriffe auf diese potenziellen Sicherheitslücken bekannt. Trotzdem sollten Entwickler sich der Sicherheitsrisiken bewusst sein und angemessene Vorsichtsmaßnahmen treffen, wie im Folgenden beschrieben, um sich vor zukünftigen Angriffen zu schützen.  
  
 Debuggerschnellansichten erfordern umfangreichere Privilegien, als sie von einer partiell vertrauenswürdigen Anwendung zugelassen werden.  Schnellansichten werden nicht geladen, wenn die Ausführung in Code mit partieller Vertrauenswürdigkeit unterbrochen wurde.  Wenn Sie in einer Schnellansicht debuggen möchten, müssen Sie den Code mit voller Vertrauenswürdigkeit ausführen.  
  
## Potenziell bösartige zu debuggende Komponente  
 Schnellansichten bestehen aus mindestens zwei Klassen: einer Klasse auf der Seite des Debuggers und einer Klasse auf der zu debuggenden Seite.  Schnellansichten werden häufig in eigenen Assemblys bereitgestellt, können aber auch von der zu debuggenden Komponente aus geladen werden.  In diesem Fall führt der Debugger Code aus der zu debuggenden Komponente innerhalb des Debuggers mit voller Vertrauenswürdigkeit aus.  
  
 Das Ausführen von Code der zu debuggenden Komponente mit voller Vertrauenswürdigkeit wird problematisch, wenn die zu debuggende Komponente nicht voll vertrauenswürdig ist.  Wenn eine Schnellansicht versucht, eine teilweise vertrauenswürdige Assembly der zu debuggenden Komponente zu laden, beendet Visual Studio die Schnellansicht.  
  
 Eine kleinere Sicherheitslücke ist allerdings immer noch vorhanden.  Die zu debuggende Komponente kann einer Debugger\-Komponente zugeordnet werden, die von einer anderen Quelle \(nicht von der zu debuggenden Komponente\) geladen wurde.  Die zu debuggende Komponente kann dann eine vertrauenswürdige Debugger\-Komponente mit der Ausführung von Aktionen in deren Namen beauftragen.  Wenn die vertrauenswürdige debuggerseitige Klasse z. B. einen "Diese Datei löschen"\-Mechanismus verfügbar macht, könnte die teilweise vertrauenswürdige zu debuggende Komponente diesen Mechanismus auslösen, wenn der Benutzer deren Schnellansicht aufruft.  
  
 Beachten Sie die von der Schnellansicht verfügbar gemachten Schnittstellen, wenn Sie dieses Sicherheitsproblem vermeiden möchten.  
  
## Siehe auch  
 [Schnellansichtarchitektur](../debugger/visualizer-architecture.md)   
 [Gewusst wie: Schreiben einer Schnellansicht](../debugger/how-to-write-a-visualizer.md)   
 [Schnellansichten](../debugger/create-custom-visualizers-of-data.md)   
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)
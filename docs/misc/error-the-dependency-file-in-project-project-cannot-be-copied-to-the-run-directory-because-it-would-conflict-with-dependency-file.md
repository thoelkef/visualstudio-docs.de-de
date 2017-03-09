---
title: "Fehler: Die Abh&#228;ngigkeit &quot;Datei&quot; in Projekt &quot;Projekt&quot; kann nicht in das Ausf&#252;hrungsverzeichnis kopiert werden, da sie mit Abh&#228;ngigkeit &quot;Datei&quot; in Konflikt stehen w&#252;rde | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.copy_version_conflict"
ms.assetid: cd7de1eb-7d58-4e2c-9811-a7201f7817be
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Fehler: Die Abh&#228;ngigkeit &quot;Datei&quot; in Projekt &quot;Projekt&quot; kann nicht in das Ausf&#252;hrungsverzeichnis kopiert werden, da sie mit Abh&#228;ngigkeit &quot;Datei&quot; in Konflikt stehen w&#252;rde
Es liegt ein Konflikt zwischen Verweisen vor: Mehrere unterschiedliche Abhängigkeiten mit demselben Dateinamen wurden in das Verzeichnis „bin“ für die auszuführende Anwendung kopiert. Das Ausführungsverzeichnis kann den Konflikt nicht lösen, da es sich bei den Abhängigkeiten nicht um Primärverweise handelt.  
  
 Dieser Fehler führt dazu, dass der Build fehlschlägt.  
  
 Wenn Sie auf dieses Aufgabenlistenelement doppelklicken, gelangen Sie zum Verweisknoten des Projekts, in dem der Konflikt auftritt.  
  
 **So beheben Sie diesen Fehler**  
  
-   Richten Sie eine der Assemblys als direkten Verweis auf das Projekt ein. Ein möglicher Nachteil dabei ist jedoch, dass die ausgewählte Assembly nicht unbedingt mit Assemblys arbeitet, die eine andere Version der Assembly benötigen, auf die verwiesen wird.  
  
     \- oder \-  
  
-   Stellen Sie sicher, dass beide Kopien der Assembly einen starken Namen haben und sich im globalen Assemblycache befinden. Dadurch müssen die Assemblys nicht mehr in das Verzeichnis „bin“ kopiert werden.  
  
## Siehe auch  
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)   
 [Globaler Assemblycache](../Topic/Global%20Assembly%20Cache.md)   
 [Assemblys mit starkem Namen](../Topic/Strong-Named%20Assemblies.md)   
 [Assemblyversionen](../Topic/Assembly%20Versioning.md)   
 [Gewusst wie: Erstellen und Entfernen von Projektabhängigkeiten](../ide/how-to-create-and-remove-project-dependencies.md)
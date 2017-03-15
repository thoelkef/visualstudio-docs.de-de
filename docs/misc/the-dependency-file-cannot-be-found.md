---
title: "The dependency &#39;file&#39; cannot be found | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.supdepnotfound"
ms.assetid: a0e6e658-c723-40da-8275-fa212165bd7d
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# The dependency &#39;file&#39; cannot be found
Einer der Projektverweise enthält einen Verweis \(eine Abhängigkeit\), der nicht gefunden wurde.  
  
 Wenn Sie sich bei einem von der Quellcodeverwaltung gesteuerten Projekt anmelden, werden Sie gegebenenfalls feststellen, dass einige Abhängigkeiten auf dem Computer nicht aufgelöst sind.  Dies ist darauf zurückzuführen, dass die **ReferencePath**\-Eigenschaft eine computerspezifische Eigenschaft ist und daher nicht vom Quellcode gesteuert wird.  
  
### So beheben Sie diesen Fehler  
  
1.  Suchen Sie den angegebenen Assemblyverweis auf der Festplatte, und ändern Sie die **ReferencePath**\-Eigenschaft.  
  
2.  Wenn Sie die Assemblydatei auf der Festplatte nicht finden, müssen Sie u. U. benutzerdefinierte Steuerelemente von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oder von einem Drittanbieter erneut installieren, wenn die Abhängigkeiten der Assembly nicht gefunden werden können.  Wenn Sie sich bei einem von der Quellcodeverwaltung gesteuerten Projekt anmelden, müssen Sie eventuell Steuerelemente von Drittanbietern installieren, die für dieses Projekt erforderlich sind.  
  
 Die Erstellung des Projekts wird durch diesen Umstand nicht beeinträchtigt.  Während die Anwendung ausgeführt wird, kann jedoch eine **TypeLoadException** ausgelöst werden.  Außerdem wird die betroffene Abhängigkeit nicht an den Bereitstellungsprozess gemeldet.  
  
 Im Knoten **Verweise** des Projektmappen\-Explorers werden die Verweise des Projekts angezeigt.  
  
## Siehe auch  
 [NIB: Reference Paths Dialog Box \(Visual Basic\)](http://msdn.microsoft.com/de-de/8e549b39-7256-456a-8fd7-089b23facf9c)
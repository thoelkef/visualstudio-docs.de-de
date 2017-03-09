---
title: "Der Typ &quot;&lt;Typname&gt;&quot; in Assembly &quot;&lt;Assemblyname1&gt;&quot; wurde an Assembly &quot;&lt;Assemblyname2&gt;&quot; weitergeleitet. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31424"
  - "bc31424"
helpviewer_keywords: 
  - "BC31424"
  - "Typweiterleitung"
ms.assetid: 0f53e613-c1cb-4722-acb5-afa3091e277b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Typ &quot;&lt;Typname&gt;&quot; in Assembly &quot;&lt;Assemblyname1&gt;&quot; wurde an Assembly &quot;&lt;Assemblyname2&gt;&quot; weitergeleitet.
Der Typ "\<Typname\>" in Assembly "\<Assemblyname1\>" wurde an Assembly "\<Assemblyname2\>" weitergeleitet. Entweder fehlt im Projekt ein Verweis auf "\<Assemblyname2\>", oder der Typ "\<Typname\>" fehlt in der Assembly "\<Assemblyname2\>".  
  
 Ein Ausdruck im Quellcode für eine Assembly verweist auf einen Typ, der zu einer anderen Assembly weitergeleitet wurde, aber der Typ kann in der Zielassembly nicht gefunden werden.  
  
 *Typweiterleitung* bedeutet, die Definition einer Klasse, Struktur, Schnittstelle, eines Delegaten oder einer Enumeration einer anderen als der ursprünglich definierten Assembly zuzuweisen. Sie wird häufig in Verbindung mit der *Umgestaltung von Code* verwendet, durch die Sie eine Assembly in zwei oder mehrere Assemblys aufteilen oder Code aus einer Assembly in eine andere verschieben können.  
  
 Auch wenn der Typ temporär noch in der ursprünglichen Assembly verfügbar ist, verliert er wahrscheinlich seine Definition, wenn er beim Umgestalten von Code aus der ursprünglichen Assembly entfernt wird.  
  
 **Fehler\-ID:** BC31424  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass der Typ in der Zielassembly vorhanden ist.  
  
-   Stellen Sie sicher, dass das Projekt über einen Verweis auf die Zielassembly verfügt.  
  
## Siehe auch  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>   
 [Type Forwarding \(C\+\+\/CLI\)](/visual-cpp/windows/type-forwarding-cpp-cli)   
 [Verwalten von Verweisen in einem Projekt](../ide/managing-references-in-a-project.md)   
 [NICHT IM BUILD: Gewusst wie: Hinzufügen oder Entfernen von Verweisen mithilfe des Dialogfelds "Verweis hinzufügen"](http://msdn.microsoft.com/de-de/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)
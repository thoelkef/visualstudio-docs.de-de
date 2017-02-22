---
title: "CA1713: Ereignisse sollten kein Before- oder After-Pr&#228;fix aufweisen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EventsShouldNotHaveBeforeOrAfterPrefix"
  - "CA1713"
helpviewer_keywords: 
  - "CA1713"
  - "EventsShouldNotHaveBeforeOrAfterPrefix"
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1713: Ereignisse sollten kein Before- oder After-Pr&#228;fix aufweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|  
|CheckId|CA1713|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Der Name eines Ereignisses beginnt mit "Before" oder "After".  
  
## Regelbeschreibung  
 Ereignisnamen sollten die Aktion beschreiben, die das Ereignis auslöst.  Um verwandte Ereignisse zu benennen, die in einer bestimmten Reihenfolge ausgelöst werden, verwenden Sie die Gegenwarts\- oder Vergangenheitsform, um ihre relative Position in der Aktionsfolge anzugeben.  Wenn Sie z. B. ein Paar von Ereignissen benennen, die beim Schließen einer Ressource ausgelöst werden, nennen Sie es "Closing" und "Closed" anstelle von "BeforeClose" und "AfterClose".  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild.  Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## Behandeln von Verstößen  
 Entfernen Sie das Präfix vom Ereignisnamen, und erwägen Sie eine Namensänderung und die Verwendung der Gegenwarts\- oder Vergangenheitsform eines Verbs.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.
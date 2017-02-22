---
title: "CA1721: Eigenschaftennamen sollten nicht mit Get-Methoden &#252;bereinstimmen | Microsoft Docs"
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
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
helpviewer_keywords: 
  - "CA1721"
  - "PropertyNamesShouldNotMatchGetMethods"
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1721: Eigenschaftennamen sollten nicht mit Get-Methoden &#252;bereinstimmen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertyNamesShouldNotMatchGetMethods|  
|CheckId|CA1721|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Der Name eines öffentlichen oder geschützten Members beginnt mit "Get" und stimmt in anderer Hinsicht mit dem Namen einer öffentlichen oder geschützten Eigenschaft überein.  Beispielsweise wird diese Regel durch einen Typ verletzt, der eine Methode mit dem Namen 'GetColor' und eine Eigenschaft mit dem Namen 'Color' enthält.  
  
## Regelbeschreibung  
 Get\-Methoden und \-Eigenschaften sollten Namen aufweisen, die ihre Funktionen deutlich erkennbar machen.  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild.  Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## Behandeln von Verstößen  
 Ändern Sie den Namen, sodass er nicht mit dem Namen einer Methode übereinstimmt, die mit "Get" beginnt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
> [!NOTE]
>  Diese Warnung wird möglicherweise ausgeschlossen, wenn die Get\-Methode durch die Implementierung der IExtenderProvider\-Schnittstelle ausgelöst wird.  
  
## Beispiel  
 Das folgende Beispiel enthält eine Methode und eine Eigenschaft, die gegen diese Regel verstoßen.  
  
 [!code-cs[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]  
  
## Verwandte Regeln  
 [CA1024: Nach Möglichkeit Eigenschaften verwenden](../code-quality/ca1024-use-properties-where-appropriate.md)
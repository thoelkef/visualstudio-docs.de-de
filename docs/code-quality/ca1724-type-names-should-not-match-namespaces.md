---
title: "CA1724: Typnamen sollten nicht mit Namespaces &#252;bereinstimmen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
helpviewer_keywords: 
  - "TypeNamesShouldNotMatchNamespaces"
  - "CA1724"
ms.assetid: 329af3b5-5600-4101-831d-531ab3eb7060
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1724: Typnamen sollten nicht mit Namespaces &#252;bereinstimmen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypeNamesShouldNotMatchNamespaces|  
|CheckId|CA1724|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Typname stimmt mit einem [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Namespacenamen in einem Vergleich, bei dem nicht zwischen Groß\- und Kleinschreibung unterschieden wird, überein.  
  
## Regelbeschreibung  
 Typnamen dürfen nicht mit den Namen von in der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Klassenbibliothek definierten Namespaces übereinstimmen.  Durch einen Verstoß gegen diese Regel kann die Verwendbarkeit der Bibliothek eingeschränkt werden.  
  
## Behandeln von Verstößen  
 Wählen Sie einen Typnamen aus, der nicht mit dem Namen eines Namespaces der [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Klassenbibliothek übereinstimmt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 In Zusammenhang mit Neuentwicklungen kommt es zu keinem Szenario, in dem Sie eine Warnung dieser Regel unterdrücken müssen.  Bevor Sie die Warnung unterdrücken, berücksichtigen Sie sorgfältig, wie die Benutzer der Bibliothek durch die gleichlautenden Namen verwirrt werden könnten.  Bei Versandbibliotheken müssen Sie u. U. eine Warnung dieser Regel unterdrücken.
---
title: "CA1716: Bezeichner sollten nicht mit Schl&#252;sselw&#246;rtern &#252;bereinstimmen | Microsoft Docs"
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
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
helpviewer_keywords: 
  - "IdentifiersShouldNotMatchKeywords"
  - "CA1716"
ms.assetid: 900cc8a1-1089-4069-a4ce-10b109ac4fab
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1716: Bezeichner sollten nicht mit Schl&#252;sselw&#246;rtern &#252;bereinstimmen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotMatchKeywords|  
|CheckId|CA1716|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Der Name eines Namespaces, eines Typs oder eines virtuellen Members oder eines Schnittstellenmembers stimmt mit einem reservierten Schlüsselwort in einer Programmiersprache überein.  
  
## Regelbeschreibung  
 Bezeichner für Namespaces, Typen und virtuelle sowie Schnittstellenmember sollten nicht mit Schlüsselwörtern übereinstimmen, die in Programmiersprachen definiert sind, die auf die Common Language Runtime abzielen.  Je nach der verwendeten Sprache und dem Schlüsselwort können Compilerfehler und Mehrdeutigkeiten die Verwendung der Bibliothek erschweren.  
  
 Durch diese Regel wird ein Vergleich mit Schlüsselwörtern folgender Sprachen vorgenommen:  
  
-   Visual Basic  
  
-   C\#  
  
-   C\+\+\/CLI  
  
 Ein Vergleich ohne Berücksichtigung von Groß\- und Kleinschreibung wird für [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Schlüsselwörter verwendet, und ein Vergleich unter Berücksichtigung von Groß\-\/Kleinschreibung wird für die anderen Sprachen verwendet.  
  
## Behandeln von Verstößen  
 Wählen Sie einen Namen aus, der in der Liste der Schlüsselwörter nicht angezeigt wird.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Sie können eine Warnung von dieser Regel unterdrücken, wenn Sie sicher sind, dass der Bezeichner keine Benutzer der API verwirrt und dass die Bibliothek in allen verfügbaren Sprachen in [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verwendbar ist.
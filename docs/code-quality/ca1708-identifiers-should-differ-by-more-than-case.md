---
title: "CA1708: Bezeichner sollten sich nicht nur durch die Gro&#223;-/Kleinschreibung unterscheiden | Microsoft Docs"
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
  - "IdentifiersShouldDifferByMoreThanCase"
  - "CA1708"
helpviewer_keywords: 
  - "CA1708"
  - "IdentifiersShouldDifferByMoreThanCase"
ms.assetid: dac0f01d-dd21-484d-add1-c8cd2bf6969f
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1708: Bezeichner sollten sich nicht nur durch die Gro&#223;-/Kleinschreibung unterscheiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldDifferByMoreThanCase|  
|CheckId|CA1708|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Die Namen von zwei Typen, Membern, Parametern oder vollqualifizierten Namespaces sind gleich, wenn sie in Kleinbuchstaben umgewandelt werden.  
  
## Regelbeschreibung  
 Bezeichner für Namespaces, Typen, Member und Parameter dürfen sich nicht nur durch die Groß\-\/Kleinschreibung unterscheiden, weil Sprachen, die auf die Common Language Runtime abzielen, nicht zwischen Groß\- und Kleinschreibung unterscheiden müssen.  Beispielsweise ist [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] eine weit verbreitete Sprache, in der nicht zwischen Groß\- und Kleinschreibung unterschieden wird.  
  
 Diese Regel wird nur für öffentlich sichtbare Member ausgelöst.  
  
## Behandeln von Verstößen  
 Wählen Sie einen Namen aus, der eindeutig ist, wenn ein Vergleich mit anderen Bezeichnern durchgeführt wird, bei dem die Groß\-\/Kleinschreibung ignoriert wird.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Die Bibliothek ist möglicherweise nicht in allen in [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verfügbaren Sprachen verwendbar.  
  
## Beispiel für einen Verstoß  
 Im folgenden Beispiel wird ein Verstoß gegen diese Regel veranschaulicht.  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldDifferByMoreThanCase#1](../code-quality/codesnippet/CSharp/ca1708-identifiers-should-differ-by-more-than-case_1.cs)]  
  
## Verwandte Regeln  
 [CA1709: Bei Bezeichnern sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)
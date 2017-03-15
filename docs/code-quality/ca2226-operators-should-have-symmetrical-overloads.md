---
title: "CA2226: Operatoren sollten symmetrische &#220;berladungen aufweisen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperatorsShouldHaveSymmetricalOverloads"
  - "CA2226"
helpviewer_keywords: 
  - "CA2226"
  - "OperatorsShouldHaveSymmetricalOverloads"
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA2226: Operatoren sollten symmetrische &#220;berladungen aufweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperatorsShouldHaveSymmetricalOverloads|  
|CheckId|CA2226|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ implementiert den Gleichheits\- oder Ungleichheitsoperator, ohne den entgegengesetzten Operator zu implementieren.  
  
## Regelbeschreibung  
 Es gibt keine Umstände, unter denen der Gleichheits\- oder Ungleichheitsoperator auf Instanzen eines Typs anwendbar ist und der entgegengesetzte Operator nicht definiert ist.  Typen implementieren i. d. R. den Ungleichheitsoperator, indem der negierte Wert des Gleichheitsoperators zurückgegeben wird.  
  
 Der C\#\-Compiler gibt bei Verstößen gegen diese Regel einen Fehler heraus.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie sowohl Gleichheits\- und Ungleichheitsoperator, oder entfernen Sie die vorhandene Operatorimplementierung.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Der Typ verfügt sonst über kein mit [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] konsistentes Verhalten.  
  
## Verwandte Regeln  
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Operatorüberladungen weisen benannte Alternativen auf](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
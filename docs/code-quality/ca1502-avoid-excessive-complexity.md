---
title: "CA1502: &#220;berm&#228;&#223;ige Komplexit&#228;t vermeiden | Microsoft Docs"
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
  - "AvoidExcessiveComplexity"
  - "CA1502"
helpviewer_keywords: 
  - "CA1502"
  - "AvoidExcessiveComplexity"
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 30
caps.handback.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1502: &#220;berm&#228;&#223;ige Komplexit&#228;t vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveComplexity|  
|CheckId|CA1502|  
|Kategorie \(Category\)|Microsoft.Maintainability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Methode verfügt über eine übermäßige zyklomatische Komplexität.  
  
## Regelbeschreibung  
 Die *zyklomatische Komplexität* ermöglicht Aussagen über die Anzahl linear unabhängiger Pfade in einer Methode, wobei die Anzahl der Pfade durch die Anzahl und Komplexität bedingter Verzweigungen bestimmt wird.  Eine niedrige zyklomatische Komplexität weist im Allgemeinen auf eine Methode hin, die einfach zu verstehen, zu testen und zu pflegen ist.  Die zyklomatische Komplexität wird aus einem Ablaufsteuerungsdiagramm der Methode berechnet und als  
  
 zyklomatische Komplexität \=  Anzahl der Kanten \- Anzahl der Knoten \+ 1  
  
 angegeben, wobei ein Knoten \(node\) einen Logikverzweigungspunkt und eine Kante \(edge\) eine Linie zwischen Knoten darstellt.  
  
 Von der Regel wird ein Verstoß gemeldet, wenn die zyklomatische Komplexität über dem Wert 25 liegt.  
  
 Sie können mehr zur Codemetrik unter [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md) erfahren,  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, gestalten Sie die Methode um, da sich dadurch ihre zyklomatische Komplexität verringert.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn sich die Komplexität nur schwerlich verringern lässt und die Methode einfach zu verstehen, zu testen und zu warten ist.  Insbesondere Methoden, die eine umfangreiche `switch`\-Anweisung \(bzw. `Select`\-Anweisung in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) enthalten, eignen sich potenziell für Ausschlüsse.  Das Risiko, die CodeBase in einem späten Stadium des Entwicklungszyklus zu destabilisieren oder das Laufzeitverhalten von bereits ausgeliefertem Code in unvorhergesehener Weise zu ändern, kann die Vorteile hinsichtlich der Codepflege zunichte machen, die eine Umgestaltung des Codes bietet.  
  
## Wie zyklomatische Komplexität berechnet wird  
 Die zyklomatische Komplexität wird berechnet, indem zu folgendem Wert 1 addiert wird:  
  
-   Anzahl der Verzweigungen \(z. B. `if`, `while` und `do`\)  
  
-   Anzahl von `case`\-Anweisungen in einem `switch`  
  
 In den folgenden Beispielen werden Methoden mit unterschiedlichen zyklomatischen Komplexitäten veranschaulicht.  
  
## Beispiel  
 **Zyklomatische Komplexität 1**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]  
  
## Beispiel  
 **Zyklomatische Komplexität 2**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]  
  
## Beispiel  
 **Zyklomatische Komplexität 3**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]  
  
## Beispiel  
 **Zyklomatische Komplexität 8**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-cs[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]  
  
## Verwandte Regeln  
 [CA1501: Übermäßige Vererbung vermeiden](../code-quality/ca1501-avoid-excessive-inheritance.md)  
  
## Siehe auch  
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
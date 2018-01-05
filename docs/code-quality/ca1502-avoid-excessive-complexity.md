---
title: "CA1502: Übermäßige Komplexität vermeiden | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a643d71e334d7a9228afbb9ba95df2f4cbb558c0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Übermäßige Komplexität vermeiden
|||  
|-|-|  
|TypeName|AvoidExcessiveComplexity|  
|CheckId|CA1502|  
|Kategorie|Microsoft.Maintainability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Eine Methode verfügt über eine übermäßige zyklomatische Komplexität.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 *Zyklomatische Komplexität* misst die Anzahl linear unabhängiger Pfade durch die Methode, die durch die Anzahl und Komplexität bedingter Verzweigungen bestimmt wird. Eine niedrige zyklomatische Komplexität gibt im Allgemeinen eine Methode, die ist einfach zu verstehen, zu testen und zu verwalten. Die zyklomatische Komplexität wird von einem Steuerelement verlaufdiagrammen der Methode berechnet und ist wie folgt angegeben:  
  
 Zyklomatische Komplexität = Anzahl der Kanten - die Anzahl der Knoten + 1  
  
 wobei ein Knoten einen zweigverteilungspunkt Logik und eine Kante darstellt, stellt eine Linie zwischen Knoten dar.  
  
 Die Regel gibt eine Verletzung, wenn die zyklomatische Komplexität mehr als 25 übersteigt.  
  
 Weitere Informationen finden Sie Informationen zu Codemetrik am [Messen von Komplexität und verwaltbarkeit von verwaltetem Code](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md),  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, gestalten Sie die Methode, um die zyklomatische Komplexität zu reduzieren.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn die Komplexität kann nicht einfach verringert werden und die Methode einfach ist zu verstehen, zu testen und zu verwalten. Insbesondere ist eine Methode, die eine große enthält `switch` (`Select` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])-Anweisung ist ein Kandidat für den Ausschluss. Das Risiko zur Destabilisierung die Codebasis später im Entwicklungszyklus oder Einführung in eine unerwartete Änderung im Verhalten von Common Language Runtime zuvor gelieferten Code die Verwaltbarkeit Vorteile der Umgestaltung des Codes überwiegen im Vergleich zu kann.  
  
## <a name="how-cyclomatic-complexity-is-calculated"></a>Zur Berechnung der zyklomatische Komplexität  
 Die zyklomatische Komplexität wird durch Addition von 1 wie folgt berechnet:  
  
-   Anzahl der Verzweigungen (z. B. `if`, `while`, und `do`)  
  
-   Anzahl der `case` Anweisungen in einem`switch`  
  
 Die folgenden Beispiele zeigen die Methoden, die unterschiedliche zyklomatische Komplexität aufweisen.  
  
## <a name="example"></a>Beispiel  
 **Zyklomatische Komplexität von 1**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_1.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_1.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_1.cs)]  
  
## <a name="example"></a>Beispiel  
 **Zyklomatische Komplexität von 2**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_2.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_2.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_2.cs)]  
  
## <a name="example"></a>Beispiel  
 **Zyklomatische Komplexität von 3**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_3.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_3.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_3.cs)]  
  
## <a name="example"></a>Beispiel  
 **Zyklomatische Komplexität von 8**  
  
 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CPP/ca1502-avoid-excessive-complexity_4.cpp)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/VisualBasic/ca1502-avoid-excessive-complexity_4.vb)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../code-quality/codesnippet/CSharp/ca1502-avoid-excessive-complexity_4.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1501: Übermäßige Vererbung vermeiden](../code-quality/ca1501-avoid-excessive-inheritance.md)  
  
## <a name="see-also"></a>Siehe auch  
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
---
title: 'CA1502: Übermäßige Komplexität vermeiden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0200d02b0e96e1d09ceb83678e89312bc9fc2e3f
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589235"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Übermäßige Komplexität vermeiden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA1502: Übermäßige Komplexität vermeiden](https://docs.microsoft.com/visualstudio/code-quality/ca1502-avoid-excessive-complexity).

|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|Kategorie|Microsoft.Maintainability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode hat eine übermäßige zyklomatische Komplexität.

## <a name="rule-description"></a>Regelbeschreibung
 *Zyklomatische Komplexität* misst die Anzahl der linear unabhängiger Pfade durch die Methode, die durch die Anzahl und Komplexität bedingter Branches bestimmt wird. Eine niedrige zyklomatische Komplexität gibt im Allgemeinen eine Methode, die einfach zu verstehen, zu testen und zu verwalten. Die zyklomatische Komplexität errechnet sich aus einem Diagramm Control Flow, der Methode und wird wie folgt angegeben:

 Zyklomatische Komplexität die Anzahl Rändern - die Anzahl der Knoten + 1 =

 wobei ein Knoten einem zweigverteilungspunkt Logik und einen Edge darstellt, stellt eine Linie zwischen Knoten dar.

 Einen Verstoß wird von die Regel berichtet, wenn die zyklomatische Komplexität mehr als 25 ist.

 Weitere Informationen finden Sie Informationen zu codemetriken auf [Messen von Komplexität und verwaltbarkeit von verwaltetem Code](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md),

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, gestalten Sie die Methode, um die zyklomatische Komplexität zu reduzieren.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn die Komplexität nicht ganz einfach reduziert werden kann und die Methode einfach ist zu verstehen, zu testen und zu verwalten. Insbesondere bei einer Methode, die eine große enthält `switch` (`Select` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)])-Anweisung ist ein Kandidat für den Ausschluss. Die Risiken zur Destabilisierung der Codebasis später im Entwicklungszyklus oder Einführung in eine unerwartete Änderung im Verhalten von Common Language Runtime zuvor abgelieferten Codes den Code ein refactoring der Verwaltbarkeit Vorteile möglicherweise aufgehoben werden.

## <a name="how-cyclomatic-complexity-is-calculated"></a>Berechnung der zyklomatische Komplexität
 Die zyklomatische Komplexität wird durch Hinzufügen von 1 wie folgt berechnet:

-   Anzahl der Branches (z. B. `if`, `while`, und `do`)

-   Anzahl der `case` Anweisungen in einem `switch`

 Die folgenden Beispiele zeigen die Methoden, die unterschiedliche zyklomatische Komplexität vorliegt.

## <a name="example"></a>Beispiel
 **Zyklomatische Komplexität von 1**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#1)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#1)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#1)]

## <a name="example"></a>Beispiel
 **Zyklomatische Komplexität von 2**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#2)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#2)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#2)]

## <a name="example"></a>Beispiel
 **Zyklomatische Komplexität von 3**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#3)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#3)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#3](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#3)]

## <a name="example"></a>Beispiel
 **Zyklomatische Komplexität von 8**

 [!code-cpp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cpp/FxCop.Maintainability.AvoidExcessiveComplexity.cpp#4)]
 [!code-csharp[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/cs/FxCop.Maintainability.AvoidExcessiveComplexity.cs#4)]
 [!code-vb[FxCop.Maintainability.AvoidExcessiveComplexity#4](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.AvoidExcessiveComplexity/vb/FxCop.Maintainability.AvoidExcessiveComplexity.vb#4)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1501: Übermäßige Vererbung vermeiden](../code-quality/ca1501-avoid-excessive-inheritance.md)

## <a name="see-also"></a>Siehe auch
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)




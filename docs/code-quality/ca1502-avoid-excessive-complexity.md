---
title: 'CA1502: Übermäßige Komplexität vermeiden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e968cef6491e1c24d98e5f64248b5104db8c5b65
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62797405"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Übermäßige Komplexität vermeiden.

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

Ein *Knoten* einem zweigverteilungspunkt Logik darstellt und ein *Edge* eine Linie zwischen den Knoten darstellt.

Einen Verstoß wird von die Regel berichtet, wenn die zyklomatische Komplexität mehr als 25 ist.

Weitere Informationen finden Sie Informationen zu codemetriken auf [Messen von Komplexität von verwaltetem Code](../code-quality/code-metrics-values.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, gestalten Sie die Methode, um die zyklomatische Komplexität zu reduzieren.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn die Komplexität nicht ganz einfach reduziert werden kann und die Methode einfach ist zu verstehen, zu testen und zu verwalten. Insbesondere bei einer Methode, die eine große enthält `switch` (`Select` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])-Anweisung ist ein Kandidat für den Ausschluss. Die Risiken zur Destabilisierung der Codebasis später im Entwicklungszyklus oder Einführung in eine unerwartete Änderung im Verhalten von Common Language Runtime zuvor abgelieferten Codes den Code ein refactoring der Verwaltbarkeit Vorteile möglicherweise aufgehoben werden.

## <a name="how-cyclomatic-complexity-is-calculated"></a>Berechnung der zyklomatische Komplexität

Die zyklomatische Komplexität wird durch Hinzufügen von 1 wie folgt berechnet:

- Anzahl der Branches (z. B. `if`, `while`, und `do`)

- Anzahl der `case` Anweisungen in einem `switch`

## <a name="example"></a>Beispiel

Die folgenden Beispiele zeigen die Methoden, die unterschiedliche zyklomatische Komplexität vorliegt.

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

- [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/code-metrics-values.md)
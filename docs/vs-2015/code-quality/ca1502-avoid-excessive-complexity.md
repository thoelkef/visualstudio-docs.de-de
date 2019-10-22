---
title: 'CA1502: übermäßige Komplexität vermeiden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidExcessiveComplexity
- CA1502
helpviewer_keywords:
- CA1502
- AvoidExcessiveComplexity
ms.assetid: d735454b-2f8f-47ce-907d-f7a5a5391221
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f7b830e9d3a045bb54394a91d94e036613af7d1f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607874"
---
# <a name="ca1502-avoid-excessive-complexity"></a>CA1502: Übermäßige Komplexität vermeiden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveComplexity|
|CheckId|CA1502|
|Kategorie|Microsoft. Wartbarkeit|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode weist eine übermäßige zyklomatische Komplexität auf.

## <a name="rule-description"></a>Regelbeschreibung
 Die *zyklomatische Komplexität* misst die Anzahl der Linear unabhängigen Pfade durch die Methode, die durch die Anzahl und Komplexität bedingter Verzweigungen bestimmt wird. Eine geringe zyklomatische Komplexität gibt im Allgemeinen eine Methode an, die leicht verständlich, getestet und gewartet werden kann. Die zyklomatische Komplexität wird anhand eines Ablauf Steuerungs Diagramms der-Methode berechnet und wie folgt angegeben:

 zyklomatische Komplexität = die Anzahl der Kanten: die Anzahl der Knoten + 1

 Wenn ein Knoten einen Logic Branch-Punkt darstellt und eine Kante eine Linie zwischen Knoten darstellt.

 Die Regel meldet eine Verletzung, wenn die zyklomatische Komplexität größer als 25 ist.

 Weitere Informationen zu Codemetriken finden Sie unter [Messen der Komplexität und Verwaltbarkeit von verwaltetem Code](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen Sie die-Methode umgestalten, um die zyklomatische Komplexität zu verringern.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Komplexität nicht leicht reduziert werden kann und die Methode leicht verständlich, getestet und gewartet werden kann. Insbesondere eine Methode, die eine große `switch` (`Select` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)])-Anweisung enthält, ist ein Kandidat für die Ausschluss. Das Risiko, dass die Codebasis später im Entwicklungs Durchlauf oder eine unerwartete Änderung des Lauf Zeit Verhaltens in zuvor verlauftem Code zu destabilisieren ist, kann die wart barkeits Vorteile der Umgestaltung des Codes überwiegen.

## <a name="how-cyclomatic-complexity-is-calculated"></a>So berechnen Sie die zyklomatische Komplexität
 Die zyklomatische Komplexität wird berechnet, indem der folgende Wert 1 hinzugefügt wird:

- Anzahl von Verzweigungen (z. b. `if`, `while` und `do`)

- Anzahl von `case`-Anweisungen in einer `switch`

  In den folgenden Beispielen werden Methoden veranschaulicht, die unterschiedliche zyklomatische Komplexität aufweisen.

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

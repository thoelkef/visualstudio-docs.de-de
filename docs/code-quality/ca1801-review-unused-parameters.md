---
title: 'CA1801: Nicht verwendete Parameter überprüfen.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- AvoidUnusedParameters
- CA1801
- ReviewUnusedParameters
helpviewer_keywords:
- CA1801
- ReviewUnusedParameters
ms.assetid: 5d73545c-e153-4b7c-a7b2-be6bf5aca5be
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dea30f8053844cc6ce6eb38dd5138e935e8020df
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029894"
---
# <a name="ca1801-review-unused-parameters"></a>CA1801: Nicht verwendete Parameter überprüfen.

|||
|-|-|
|TypeName|ReviewUnusedParameters|
|CheckId|CA1801|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend – Wenn das Element nicht außerhalb der Assembly, unabhängig von der Änderung angezeigt wird, die Sie vornehmen.<br /><br /> Nicht unterbrechend – Wenn Sie ändern, dass das Element, um die Parameter innerhalb des Texts zu verwenden.<br /><br /> Wichtige – Wenn Sie den Parameter entfernen und außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
 Eine Methodensignatur enthält einen Parameter, der nicht im Methodentext verwendet wird. Diese Regel untersucht nicht die folgenden Methoden:

- Methoden, die einen Delegaten auf.

- Methoden, die als Ereignishandler verwendet werden.

- Methoden deklariert werden, mit der `abstract` (`MustOverride` in Visual Basic) Modifizierer.

- Methoden deklariert werden, mit der `virtual` (`Overridable` in Visual Basic) Modifizierer.

- Methoden deklariert werden, mit der `override` (`Overrides` in Visual Basic) Modifizierer.

- Methoden deklariert werden, mit der `extern` (`Declare` -Anweisung in Visual Basic) Modifizierer.

## <a name="rule-description"></a>Regelbeschreibung
 Überprüfen Sie die Parameter in nicht virtuellen Methoden, die nicht im Methodentext verwendet werden, um sicherzustellen, dass keine Richtigkeit Umfeld des Fehlers für den Zugriff darauf vorhanden ist. Nicht verwendete Parameter fallen Kosten für Wartung und Leistung.

 Manchmal kann ein Verstoß gegen diese Regel auf einen Implementierungsfehler in der Methode hinweisen. Z. B. der Parameter sollte im Methodentext verwendet haben. Unterdrücken Sie Warnungen für diese Regel aus, wenn der Parameter aufgrund der Abwärtskompatibilität vorhanden sein muss.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den nicht verwendeten Parameter (eine fehlerhafte Änderung), oder verwenden Sie den Parameter im Methodentext (eine nicht unterbrechende Änderung).

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher eine Warnung dieser Regel für die zuvor abgelieferten Codes zu unterdrücken, für die die Lösung eine unterbrechende Änderung sein würde.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Methoden. Eine Methode verstößt gegen die Regel, und die andere Methode der Regel entspricht.

 [!code-csharp[FxCop.Usage.ReviewUnusedParameters#1](../code-quality/codesnippet/CSharp/ca1801-review-unused-parameters_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)

 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)
---
title: 'CA1815: Außer Kraft setzen equals und Gleichheitsoperator für Werttypen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d8fc26bca5ecce3b5459890e96e429ef10f3b75
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904048"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Außer Kraft setzen equals und Gleichheitsoperator für Werttypen

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein öffentlichen Werttyps überschreibt nicht die <xref:System.Object.Equals%2A?displayProperty=fullName>, oder den Gleichheitsoperator (==) nicht implementiert. Mit dieser Regel wird die Enumerationen nicht überprüft.

## <a name="rule-description"></a>Regelbeschreibung
 Für Werttypen, die der geerbten Implementierung von <xref:System.Object.Equals%2A> verwendet die Reflection-Bibliothek und der Inhalt aller Felder verglichen. Reflection ist rechenintensiv, und das Überprüfen eines jeden Felds auf Gleichheit ist eventuell unnötig. Wenn Sie erwarten, Benutzer mit Instanzen von vergleichen oder sortieren dass, oder sie als Schlüssel für Hashtabellen verwenden, sollte der Werttyp implementieren <xref:System.Object.Equals%2A>. Wenn Ihre Programmiersprache Operatorüberladung unterstützt, sollten Sie ebenso eine Implementierung der Gleichheits- und Ungleichheitsoperatoren bereitstellen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie eine Implementierung der <xref:System.Object.Equals%2A>. Wenn Sie den Gleichheitsoperator implementieren können.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn Instanzen des Werttyps nicht miteinander verglichen werden.

## <a name="example-of-a-violation"></a>Beispiel eines Verstoßes

### <a name="description"></a>Beschreibung
 Das folgende Beispiel zeigt eine Struktur (Werttyp), die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]

## <a name="example-of-how-to-fix"></a>Beispiel für die Fehlerbehebung

### <a name="description"></a>Beschreibung
 Im folgenden Beispiel wird der vorherige Verstoß durch Überschreiben korrigiert <xref:System.ValueType.Equals%2A?displayProperty=fullName> und die Gleichheitsoperatoren (==,! =).

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2224: Außerkraftsetzung equals, Equals beim Überladen](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Object.Equals%2A?displayProperty=fullName>
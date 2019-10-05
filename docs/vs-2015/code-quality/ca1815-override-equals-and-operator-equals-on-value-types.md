---
title: 'CA1815: Außer Kraft setzen zu equals und Gleichheitsoperator für Werttypen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e21585a7a56fde2fb46ea86adde92eecfd1a4565
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68201693"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Equals und Gleichheitsoperator für Werttypen überschreiben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn Instanzen des Werttyps nicht miteinander verglichen werden.

## <a name="example-of-a-violation"></a>Beispiel eines Verstoßes

### <a name="description"></a>Beschreibung
 Das folgende Beispiel zeigt eine Struktur (Werttyp), die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsViolation/cs/FxCop.Performance.OverrideEqualsViolation.cs#1)]

## <a name="example-of-how-to-fix"></a>Beispiel für die Fehlerbehebung

### <a name="description"></a>Beschreibung
 Im folgenden Beispiel wird der vorherige Verstoß durch Überschreiben korrigiert <xref:System.ValueType.Equals%2A?displayProperty=fullName> und die Gleichheitsoperatoren (==,! =).

### <a name="code"></a>Code
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.OverrideEqualsFixed/cs/FxCop.Performance.OverrideEqualsFixed.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2224: Außerkraftsetzung equals, Equals beim Überladen](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Object.Equals%2A?displayProperty=fullName>

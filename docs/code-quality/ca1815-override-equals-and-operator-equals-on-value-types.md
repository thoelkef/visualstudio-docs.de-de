---
title: 'CA1815: Equals und Gleichheitsoperator für Werttypen überschreiben.'
ms.date: 03/11/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 413119f7cdf473f3038ae212ac812d1987641bb1
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233546"
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Equals und Gleichheitsoperator für Werttypen überschreiben.

|||
|-|-|
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|
|CheckId|CA1815|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Werttyp überschreibt <xref:System.Object.Equals%2A?displayProperty=fullName> den Gleichheits Operator (= =) nicht oder implementiert ihn nicht. Diese Regel überprüft keine Enumerationen.

Standardmäßig betrachtet diese Regel nur extern sichtbare Typen, aber dies ist [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Bei Werttypen verwendet die geerbte <xref:System.Object.Equals%2A> Implementierung von die Reflektionsbibliothek und vergleicht den Inhalt aller Felder. Reflection ist rechenintensiv, und das Überprüfen eines jeden Felds auf Gleichheit ist eventuell unnötig. Wenn Sie davon ausgehen, dass Benutzer Instanzen vergleichen oder sortieren oder Sie als Hash Tabellenschlüssel verwenden, sollte der Werttyp implementieren <xref:System.Object.Equals%2A>. Wenn Ihre Programmiersprache Operatorüberladung unterstützt, sollten Sie ebenso eine Implementierung der Gleichheits- und Ungleichheitsoperatoren bereitstellen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, stellen Sie eine <xref:System.Object.Equals%2A>Implementierung von bereit. Implementieren Sie den Gleichheits Operator, wenn dies möglich ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn Instanzen des Werttyps nicht miteinander verglichen werden.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1815.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Leistung) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Der folgende Code zeigt eine Struktur (Werttyp), die gegen diese Regel verstößt:

[!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]

Im folgenden Code wird der vorherige Verstoß durch über <xref:System.ValueType.Equals%2A?displayProperty=fullName> schreiben und Implementieren der Gleichheits Operatoren (= =,! =) korrigiert:

[!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA2224: Überschreiben von Gleichheits beim Überladen von Operatoren](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
- [CA2226: Operatoren sollten symmetrische über Ladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Object.Equals%2A?displayProperty=fullName>
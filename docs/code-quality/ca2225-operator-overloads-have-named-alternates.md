---
title: 'CA2225: Operatorüberladungen weisen benannte Alternativen auf.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c027bc4581919f814b4d93eacba77248349fdf8b
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231087"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Operatorüberladungen weisen benannte Alternativen auf.

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Operator Überladung wurde erkannt, und die erwartete benannte alternative Methode wurde nicht gefunden.

Standardmäßig betrachtet diese Regel nur extern sichtbare Typen, aber dies ist [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Die Operator Überladung ermöglicht die Verwendung von Symbolen zur Darstellung von Berechnungen für einen Typ. Beispielsweise würde ein Typ, der das Pluszeichen (+) zusätzlich über lädt, in der Regel einen alternativen Member mit dem Namen "Add" aufweisen. Der benannte Alternative Member bietet Zugriff auf die gleiche Funktionalität wie der-Operator und wird für Entwickler bereitgestellt, die in Sprachen programmieren, die überladene Operatoren nicht unterstützen.

Diese Regel überprüft die in der folgenden Tabelle aufgeführten Operatoren.

|C#|Visual Basic|C++|Alternativer Name|
|---------|------------------|-----------|--------------------|
|+ (binär)|+|+ (binär)|Hinzufügen|
|+=|+=|+=|Hinzufügen|
|&|und|&|BitwiseAnd|
|&=|Und =|&=|BitwiseAnd|
|&#124;|Or|&#124;|BitwiseOr|
|&#124;=|Oder =|&#124;=|BitwiseOr|
|--|Nicht zutreffend|--|Dekrement|
|/|/|/|Teilen|
|/=|/=|/=|Teilen|
|==|=|==|gleich|
|^|Xor|^|Xor|
|^=|XOR =|^=|Xor|
|>|>|>|Vergleichen|
|>=|>=|>=|Vergleichen|
|++|Nicht zutreffend|++|Inkrement|
|<>|!=|gleich|
|<<|<<|<<|Linke UMSCHALTTASTE|
|<<=|<<=|<<=|Linke UMSCHALTTASTE|
|<|<|<|Vergleichen|
|<=|<=|\<=|Vergleichen|
|&&|Nicht zutreffend|&&|LogicalAnd|
||||Nicht zutreffend||||Logicalor|
|!|Nicht zutreffend|!|LogicalNot|
|%|Mod|%|Mod oder Restwert|
|%=|Nicht zutreffend|%=|Mod|
|* (binär)|*|*|Multiplizieren|
|*=|Nicht zutreffend|*=|Multiplizieren|
|~|Not|~|Oneskomplement|
|>>|>>|>>|Lesefolge wechseln|
=|Nicht zutreffend|>>=|Lesefolge wechseln|
|-(binär)|-(binär)|-(binär)|Subtrahieren|
|-=|Nicht zutreffend|-=|Subtrahieren|
|true|IsTrue|Nicht zutreffend|IsTrue (Eigenschaft)|
|-(unär)|Nicht zutreffend|-|Negation|
|+ (unär)|Nicht zutreffend|+|ZZ|
|False|IsFalse|False|IsTrue (Eigenschaft)|

N/A = = kann nicht in der ausgewählten Sprache überladen werden.

Die Regel überprüft auch implizite und explizite Umwandlungs Operatoren in einem`SomeType`Typ (), indem Sie `ToSomeType` auf `FromSomeType`Methoden mit dem Namen und überprüft.

Wenn C#in ein binärer Operator überladen wird, wird der entsprechende Zuweisungs Operator (sofern vorhanden) ebenfalls implizit überladen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie die alternative-Methode für den-Operator. nennen Sie Sie mithilfe des empfohlenen alternativen namens.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Unterdrücken Sie keine Warnung dieser Regel, wenn Sie eine freigegebene Bibliothek implementieren. Anwendungen können eine Warnung aus dieser Regel ignorieren.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca2225.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Verwendung) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird eine Struktur definiert, die gegen diese Regel verstößt. Fügen Sie der-Struktur eine öffentliche `Add(int x, int y)` Methode hinzu, um das Beispiel zu korrigieren.

[!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1046: Gleichheits Operator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2226: Operatoren sollten symmetrische über Ladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224: Überschreiben von Gleichheits beim Überladen von Operatoren](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: GetHashCode beim Überschreiben von ist überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
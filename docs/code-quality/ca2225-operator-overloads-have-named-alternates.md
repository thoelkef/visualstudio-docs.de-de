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
ms.openlocfilehash: e6a9b03ce2552e50ebfca8f9e6e2823dee794c20
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841777"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Operatorüberladungen weisen benannte Alternativen auf.

|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Es wurde eine operatorüberladung erkannt, und die erwartete benannte Alternativmethode wurde nicht gefunden.

Diese Regel nur sucht standardmäßig an extern sichtbare Typen, aber dies ist [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Überladen von Operatoren ermöglicht die Verwendung der Symbole, die Berechnungen für einen Typ darstellt. Ein Typ, der das Pluszeichen (+) für die Addition überlädt müsste z. B. in der Regel einen alternativen Member, die mit dem Namen "Hinzufügen". Der benannte Alternativmember ermöglicht den Zugriff auf die gleiche Funktionalität wie der Operator, und es wird bereitgestellt, um Entwickler beim Programmieren in Sprachen, die überladene Operatoren nicht unterstützen.

Diese Regel überprüft die Operatoren in der folgenden Tabelle aufgelistet sind.

|C#|Visual Basic|C++|Alternativer name|
|---------|------------------|-----------|--------------------|
|+ (binär)|+|+ (binär)|Hinzufügen|
|+=|+=|+=|Hinzufügen|
|&|und|&|BitwiseAnd|
|&=|' Und ' =|&=|BitwiseAnd|
|&#124;|Or|&#124;|BitwiseOr|
|&#124;=|"Oder" =|&#124;=|BitwiseOr|
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
|<<|<<|<<|LeftShift|
|<<=|<<=|<<=|LeftShift|
|<|<|<|Vergleichen|
|<=|<=|\<=|Vergleichen|
|&&|Nicht zutreffend|&&|LogicalAnd|
|&#124;&#124;|Nicht zutreffend|&#124;&#124;|LogicalOr|
|!|Nicht zutreffend|!|LogicalNot|
|%|Mod|%|MOD oder Rest|
|%=|Nicht zutreffend|%=|Mod|
|* (binär)|*|*|Multiplizieren|
|*=|Nicht zutreffend|*=|Multiplizieren|
|~|Not|~|OnesComplement|
|>>|>>|>>|RightShift|
=|Nicht zutreffend|>>=|RightShift|
|-(binär)|-(binär)|-(binär)|Subtrahieren|
|-=|Nicht zutreffend|-=|Subtrahieren|
|true|IsTrue|Nicht zutreffend|"IsTrue" (Eigenschaft)|
|-(Unär)|Nicht zutreffend|-|Negate-|
|+ (Unär)|Nicht zutreffend|+|Plus|
|False|IsFalse|False|"IsTrue" (Eigenschaft)|

N/v == kann nicht überladen werden, in der ausgewählten Sprache.

Die Regel überprüft auch implizite und explizite Umwandlungsoperatoren in einem Typ (`SomeType`) durch Prüfen auf Methoden, die mit dem Namen `ToSomeType` und `FromSomeType`.

In C# geschrieben Wenn ein binärer Operator überladen ist, wird der zugehörige Zuweisungsoperator, ggf. auch implizit überladen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie die alternative Methode für den Operator aus. Nennen Sie ihn mit den empfohlenen alternativen Namen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie eine Warnung dieser Regel nicht, wenn Sie eine freigegebene Bibliothek implementieren. Anwendungen können eine Warnung dieser Regel ignorieren.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```ini
dotnet_code_quality.ca2225.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Nutzung) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="example"></a>Beispiel

Das folgende Beispiel definiert eine Struktur, die gegen diese Regel verstößt. Um das Beispiel zu korrigieren, fügen Sie eine öffentliche `Add(int x, int y)` Methode, um die Struktur.

[!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)
- [CA2226: Operatoren sollten symmetrische Überladungen aufweisen.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)
- [CA2224: Außerkraftsetzung equals, Equals beim Überladen](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)
- [CA2218: Überschreiben von GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)
- [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
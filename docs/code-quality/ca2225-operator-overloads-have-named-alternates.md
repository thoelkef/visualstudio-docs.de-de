---
title: 'CA2225: Operatorüberladungen weisen benannte Alternativen auf'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 991358ec361e414c9f5d335feb43eadde628a763
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Operatorüberladungen weisen benannte Alternativen auf
|||
|-|-|
|TypeName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Es wurde eine Operatorüberladung erkannt, und die erwartete benannte Alternativmethode wurde nicht gefunden.

## <a name="rule-description"></a>Regelbeschreibung
 Operatoren überladen ermöglicht die Verwendung von Symbolen, um Berechnungen für einen Typ darzustellen. Beispielsweise müsste ein Typ, der das Pluszeichen (+) für die Addition überlädt in der Regel einen alternativen Member mit dem Namen 'Hinzufügen'. Der benannte Alternativmember ermöglicht den Zugriff auf die gleiche Funktionalität wie der Operator, und wird für Entwickler, die in Sprachen programmieren, in denen überladene Operatoren nicht unterstützen bereitgestellt.

 Diese Regel untersucht die Operatoren in der folgenden Tabelle aufgelistet sind.

|C#|Visual Basic|C++|Alternative Namen|
|---------|------------------|-----------|--------------------|
|+ (binär)|+|+ (binär)|Hinzufügen|
|+=|+=|+=|Hinzufügen|
|&|And|&|BitwiseAnd|
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
|<<|<<|<<|Linke UMSCHALTTASTE|
|<<=|<<=|<<=|Linke UMSCHALTTASTE|
|<|<|<|Vergleichen|
|<=|<=|\<=|Vergleichen|
|&&|Nicht zutreffend|&&|LogicalAnd|
||||Nicht zutreffend||||LogicalOr|
|!|Nicht zutreffend|!|LogicalNot|
|%|Mod|%|MOD oder Rest|
|%=|Nicht zutreffend|%=|Mod|
|* (binär)|*|*|Multiplizieren|
|*=|Nicht zutreffend|*=|Multiplizieren|
|~|Not|~|OnesComplement|
|>>|>>|>>|Rechte UMSCHALTTASTE|
=|Nicht zutreffend|>>=|Rechte UMSCHALTTASTE|
|-(binär)|-(binär)|-(binär)|Subtrahieren|
|-=|Nicht zutreffend|-=|Subtrahieren|
|true|IsTrue|Nicht zutreffend|IsTrue (Eigenschaft)|
|-(Unär)|Nicht zutreffend|-|Negate-|
|+ (Unär)|Nicht zutreffend|+|Plus|
|False|IsFalse|False|IsTrue (Eigenschaft)|

 N/v == kann nicht in der ausgewählten Sprache nicht überladen werden.

 Diese Regel überprüft auch implizite und explizite Umwandlungsoperatoren in einem Typ (`SomeType`) mit der Überprüfung Methoden, die mit dem Namen `ToSomeType` und `FromSomeType`.

 In c# ist bei ein binärer Operator überladen wird, ist der entsprechenden Zuweisungsoperator ggf. auch implizit überladene.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie die alternative Methode für den Operator aus. Nennen sie die empfohlenen alternativen Namen verwenden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, wenn Sie eine freigegebene Bibliothek implementieren. Anwendungen können eine Warnung dieser Regel ignorieren.

## <a name="example"></a>Beispiel
 Das folgende Beispiel definiert eine Struktur, die mit dieser Regel verletzt. Um das Beispiel zu beheben, fügen Sie einen öffentlichen `Add(int x, int y)` Methode, um die Struktur.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
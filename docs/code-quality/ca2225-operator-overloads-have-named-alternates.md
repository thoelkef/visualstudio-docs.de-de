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
ms.openlocfilehash: a12060752317a2b4c23ec2eba7e96e945be00db0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914579"
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
 Überladen von Operatoren ermöglicht die Verwendung der Symbole, die Berechnungen für einen Typ darstellt. Ein Typ, der das Pluszeichen (+) für die Addition überlädt müsste z. B. in der Regel einen alternativen Member, die mit dem Namen "Hinzufügen". Der benannte Alternativmember ermöglicht den Zugriff auf die gleiche Funktionalität wie der Operator, und es wird bereitgestellt, um Entwickler beim Programmieren in Sprachen, die überladene Operatoren nicht unterstützen.

 Diese Regel überprüft die Operatoren in der folgenden Tabelle aufgelistet sind.

|C#|Visual Basic|C++|Alternativer name|
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

## <a name="example"></a>Beispiel
 Das folgende Beispiel definiert eine Struktur, die gegen diese Regel verstößt. Um das Beispiel zu korrigieren, fügen Sie eine öffentliche `Add(int x, int y)` Methode, um die Struktur.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../code-quality/codesnippet/CSharp/ca2225-operator-overloads-have-named-alternates_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)
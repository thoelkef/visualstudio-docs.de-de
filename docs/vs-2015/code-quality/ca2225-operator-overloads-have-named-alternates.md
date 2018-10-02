---
title: 'CA2225: Operatorüberladungen müssen benannte alternativen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 8b8ebf513b54667e48309fd495b7cd511b98c7c3
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589660"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Operatorüberladungen weisen benannte Alternativen auf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA2225: operatorüberladungen müssen mit dem alternativen Namen](https://docs.microsoft.com/visualstudio/code-quality/ca2225-operator-overloads-have-named-alternates).

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel nicht, wenn Sie eine freigegebene Bibliothek implementieren. Anwendungen können eine Warnung dieser Regel ignorieren.

## <a name="example"></a>Beispiel
 Das folgende Beispiel definiert eine Struktur, die gegen diese Regel verstößt. Um das Beispiel zu korrigieren, fügen Sie eine öffentliche `Add(int x, int y)` Methode, um die Struktur.

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)




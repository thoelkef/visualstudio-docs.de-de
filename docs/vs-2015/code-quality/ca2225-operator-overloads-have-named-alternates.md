---
title: 'CA2225: Operator Überladungen weisen benannte Alternativen auf | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
helpviewer_keywords:
- OperatorOverloadsHaveNamedAlternates
- CA2225
ms.assetid: af8f7ab1-63ad-4861-afb9-b7a7a2be15e1
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2dc43e92b92b6f963900057a76dfe88e38a3638f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545222"
---
# <a name="ca2225-operator-overloads-have-named-alternates"></a>CA2225: Operatorüberladungen weisen benannte Alternativen auf.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|OperatorOverloadsHaveNamedAlternates|
|CheckId|CA2225|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Es wurde eine Operatorüberladung erkannt, und die erwartete benannte Alternativmethode wurde nicht gefunden.

## <a name="rule-description"></a>Beschreibung der Regel
 Die Operator Überladung ermöglicht die Verwendung von Symbolen zur Darstellung von Berechnungen für einen Typ. Beispielsweise würde ein Typ, der das Pluszeichen (+) zusätzlich über lädt, in der Regel einen alternativen Member mit dem Namen "Add" aufweisen. Der benannte Alternative Member bietet Zugriff auf die gleiche Funktionalität wie der-Operator und wird für Entwickler bereitgestellt, die in Sprachen programmieren, die überladene Operatoren nicht unterstützen.

 Diese Regel überprüft die in der folgenden Tabelle aufgeführten Operatoren.

|C#|Visual Basic|C++|Alternativer Name|
|---------|------------------|-----------|--------------------|
|+ (binär)|+|+ (binär)|Add|
|+=|+=|+=|Add|
|&|Und|&|BitwiseAnd|
|&=|Und =|&=|BitwiseAnd|
|&#124;|oder|&#124;|BitwiseOr|
|&#124;=|Oder =|&#124;=|BitwiseOr|
|--|–|--|Dekrement|
|/|/|/|Dividieren|
|/=|/=|/=|Dividieren|
|==|=|==|Equals|
|^|Xor|^|Xor|
|^=|XOR =|^=|Xor|
|>|>|>|Vergleich|
|>=|>=|>=|Vergleich|
|++|–|++|Increment|
|<>|!=|Equals|
|<<|<<|<<|Linke UMSCHALTTASTE|
|<<=|<<=|<<=|Linke UMSCHALTTASTE|
|<|<|<|Vergleich|
|<=|<=|\<=|Vergleich|
|&&|–|&&|LogicalAnd|
|&#124;&#124;|–|&#124;&#124;|Logicalor|
|!|–|!|LogicalNot|
|%|Mod|%|Mod oder Restwert|
|%=|–|%=|Mod|
|* (binär)|*|*|Multiplizieren|
|*=|–|*=|Multiplizieren|
|~|Not|~|Oneskomplement|
|>>|>>|>>|Lesefolge wechseln|
=|–|>>=|Lesefolge wechseln|
|-(binär)|-(binär)|-(binär)|Subtrahieren|
|-=|–|-=|Subtrahieren|
|wahr|IsTrue|–|IsTrue (Eigenschaft)|
| - (unär)   |–|-|Negate|
|+ (unär)|–|+|Plus|
|false|IsFalse|False|IsTrue (Eigenschaft)|

 N/A = = kann nicht in der ausgewählten Sprache überladen werden.

 Die Regel überprüft auch implizite und explizite Umwandlungs Operatoren in einem Typ ( `SomeType` ), indem Sie auf Methoden mit dem Namen `ToSomeType` und überprüft `FromSomeType` .

 Wenn in c# ein binärer Operator überladen ist, wird der entsprechende Zuweisungs Operator (sofern vorhanden) ebenfalls implizit überladen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie die alternative-Methode für den-Operator. nennen Sie Sie mithilfe des empfohlenen alternativen namens.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel, wenn Sie eine freigegebene Bibliothek implementieren. Anwendungen können eine Warnung aus dieser Regel ignorieren.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird eine Struktur definiert, die gegen diese Regel verstößt. Fügen Sie der-Struktur eine öffentliche Methode hinzu, um das Beispiel zu korrigieren `Add(int x, int y)` .

 [!code-csharp[FxCop.Usage.OperatorOverloadsHaveNamedAlternates#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorOverloadsHaveNamedAlternates/cs/FxCop.Usage.OperatorOverloadsHaveNamedAlternates.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen.](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben.](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: GetHashCode beim Überschreiben von Equals überschreiben.](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

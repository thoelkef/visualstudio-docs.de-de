---
title: 'CA2224: Außerkraftsetzung equals, Equals beim Überladen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b4c16ed5858f18456af59c4cc26f2e0d56e6006a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955797"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein öffentlicher Typ implementiert den Gleichheitsoperator, aber überschreibt nicht die <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung
 Der Gleichheitsoperator syntaktisch bequem Zugriff auf die Funktionen werden die <xref:System.Object.Equals%2A> Methode. Wenn Sie den Gleichheitsoperator implementieren, die Logik muss identisch mit dem der <xref:System.Object.Equals%2A>.

 Der C#-Compiler gibt eine Warnung aus, wenn Ihr Code gegen diese Regel verstößt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, sollten Sie entweder entfernen Sie die Implementierung des Gleichheitsoperators oder außer Kraft setzen <xref:System.Object.Equals%2A> und haben die beiden Methoden die gleichen Werte zurückgibt. Wenn der Gleichheitsoperator nicht inkonsistentes Verhalten einleitet, können Sie den Verstoß beheben, indem eine Implementierung von <xref:System.Object.Equals%2A> aufruft, die <xref:System.Object.Equals%2A> -Methode in der Basisklasse.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicherer, eine Warnung dieser Regel zu unterdrücken, sofern es sich bei der Equality-Operator gibt zurück, den gleichen Wert wie der geerbten Implementierung von <xref:System.Object.Equals%2A>. Im Abschnitt Beispiel umfasst einen Typ, der sicher unterdrücken Sie eine Warnung dieser Regel kann.

## <a name="examples-of-inconsistent-equality-definitions"></a>Beispiele für Gleichheitsdefinitionen von inkonsistenten

### <a name="description"></a>Beschreibung
 Das folgende Beispiel zeigt einen Typ mit inkonsistente Definitionen auf Wertgleichheit. `BadPoint` Ändert die Bedeutung der Gleichheit, indem eine benutzerdefinierte Implementierung des Gleichheitsoperators jedoch überschreibt nicht die <xref:System.Object.Equals%2A> , damit es identisch verhält.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>Beispiel
 Der folgende Code überprüft das Verhalten der `BadPoint`.

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **a = ([0] 1,1) und b = ([1] 2,2) gleich sind? No**
**a == b ? Keine**
**a1 und einer gleich? Ja**
**a1 == ein? Ja**
**b und Bcopy gleich sind? No**
**b == bcopy ? "Ja"**
## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Typ, der technisch verstößt gegen diese Regel, aber nicht in einem inkonsistenten Weise verhält.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>Beispiel
 Der folgende Code überprüft das Verhalten der `GoodPoint`.

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **a = (1,1) und b = (2,2) gleich sind? No**
**a == b ? Keine**
**a1 und einer gleich? Ja**
**a1 == ein? Ja**
**b und Bcopy gleich sind? Ja**
**b == Bcopy? "Ja"**
## <a name="class-example"></a>Beispiel:

### <a name="description"></a>Beschreibung
 Das folgende Beispiel zeigt eine Klasse (Referenztyp), die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird der Verstoß durch Überschreiben korrigiert <xref:System.Object.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>Struktur-Beispiel

### <a name="description"></a>Beschreibung
 Das folgende Beispiel zeigt eine Struktur (Werttyp), die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird der Verstoß durch Überschreiben korrigiert <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Operatorüberladungen weisen benannte alternativen auf](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: Überschreiben von GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

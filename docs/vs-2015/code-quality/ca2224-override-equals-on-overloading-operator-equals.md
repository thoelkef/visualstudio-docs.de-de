---
title: 'CA2224: beim Überladen von Operatoren ist Gleichheits- Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 39272790b6ef366c64d45e0aea238606d0b62bf4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538635"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein öffentlicher Typ implementiert den Gleichheits Operator, überschreibt jedoch nicht <xref:System.Object.Equals%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Beschreibung der Regel
 Der Gleichheits Operator soll eine syntaktisch bequeme Methode für den Zugriff auf die Funktionen der <xref:System.Object.Equals%2A> Methode sein. Wenn Sie den Gleichheits Operator implementieren, muss die zugehörige Logik mit der von identisch sein <xref:System.Object.Equals%2A> .

 Der c#-Compiler gibt eine Warnung aus, wenn Ihr Code gegen diese Regel verstößt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, sollten Sie entweder die Implementierung des Gleichheits Operators entfernen oder überschreiben und festlegen, dass <xref:System.Object.Equals%2A> die beiden Methoden dieselben Werte zurückgeben. Wenn der Gleichheits Operator kein inkonsistentes Verhalten einführt, können Sie die Verletzung beheben, indem Sie eine Implementierung von bereitstellen <xref:System.Object.Equals%2A> , die die- <xref:System.Object.Equals%2A> Methode in der Basisklasse aufruft.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Gleichheits Operator denselben Wert zurückgibt wie die geerbte Implementierung von <xref:System.Object.Equals%2A> . Der Beispiel Abschnitt enthält einen Typ, der eine Warnung aus dieser Regel sicher unterdrücken könnte.

## <a name="examples-of-inconsistent-equality-definitions"></a>Beispiele für inkonsistente Gleichheits Definitionen

### <a name="description"></a>BESCHREIBUNG
 Das folgende Beispiel zeigt einen Typ mit inkonsistenten Definitionen der Gleichheit. `BadPoint` ändert die Bedeutung von Gleichheit durch Bereitstellen einer benutzerdefinierten Implementierung des Gleichheits Operators, jedoch nicht, <xref:System.Object.Equals%2A> sodass Sie identisch verhält.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OperatorEqualsRequiresEquals/cs/FxCop.Usage.OperatorEqualsRequiresEquals.cs#1)]

## <a name="example"></a>Beispiel
 Der folgende Code testet das Verhalten von `BadPoint` .

 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestOperatorEqualsRequiresEquals/cs/FxCop.Usage.TestOperatorEqualsRequiresEquals.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **a = ([0] 1, 1) und b = ([1] 2, 2) sind gleich? Nein** 
 **= = b? ** 
 **A1 und a sind gleich? Ja** 
 **a1 = = a? Ja** 
 **b und bcopy sind gleich? Nein** 
 **b = = bcopy? Ja**
## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird ein Typ gezeigt, der technisch gegen diese Regel verstößt, sich aber nicht auf inkonsistente Weise verhält.

 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ValueTypeEquals/cs/FxCop.Usage.ValueTypeEquals.cs#1)]

## <a name="example"></a>Beispiel
 Der folgende Code testet das Verhalten von `GoodPoint` .

 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestValueTypeEquals/cs/FxCop.Usage.TestValueTypeEquals.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **a = (1, 1) und b = (2, 2) sind gleich? Nein** 
 **= = b? ** 
 **A1 und a sind gleich? Ja** 
 **a1 = = a? Ja** 
 **b und bcopy sind gleich? Ja** 
 **b = = bcopy? Ja**
## <a name="class-example"></a>Klassenbeispiel

### <a name="description"></a>BESCHREIBUNG
 Das folgende Beispiel zeigt eine Klasse (Verweistyp), die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassViolation/cs/FxCop.Usage.OverrideEqualsClassViolation.cs#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Verletzung durch Überschreiben behoben <xref:System.Object.Equals%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsClassFixed/cs/FxCop.Usage.OverrideEqualsClassFixed.cs#1)]

## <a name="structure-example"></a>Struktur Beispiel

### <a name="description"></a>BESCHREIBUNG
 Das folgende Beispiel zeigt eine Struktur (Werttyp), die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructViolation/cs/FxCop.Usage.OverrideEqualsStructViolation.cs#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die Verletzung durch Überschreiben behoben <xref:System.ValueType.Equals%2A?displayProperty=fullName> .

 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.OverrideEqualsStructFixed/cs/FxCop.Usage.OverrideEqualsStructFixed.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen.](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Operatorüberladungen weisen benannte Alternativen auf.](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2218: GetHashCode beim Überschreiben von Equals überschreiben.](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

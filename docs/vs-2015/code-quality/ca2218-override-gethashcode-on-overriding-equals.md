---
title: 'CA2218: GetHashCode beim Überschreiben von ist überschreiben | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8083edf04aa799c8031fbcd1b53a2e17104dd4a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538800"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218: GetHashCode beim Überschreiben von Equals überschreiben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein öffentlicher Typ überschreibt, <xref:System.Object.Equals%2A?displayProperty=fullName> aber nicht außer Kraft <xref:System.Object.GetHashCode%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Beschreibung der Regel
 <xref:System.Object.GetHashCode%2A> gibt basierend auf der aktuellen Instanz einen-Wert zurück, der sich für Hash Algorithmen und Datenstrukturen eignet, z. b. eine Hash Tabelle. Zwei Objekte, die denselben Typ und gleich sind, müssen denselben Hashcode zurückgeben, um sicherzustellen, dass Instanzen der folgenden Typen ordnungsgemäß funktionieren:

- <xref:System.Collections.Hashtable?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

- Typen, die implementieren <xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie eine Implementierung von bereit <xref:System.Object.GetHashCode%2A> . Bei einem Paar von Objekten desselben Typs müssen Sie sicherstellen, dass die Implementierung denselben Wert zurückgibt, wenn die Implementierung von <xref:System.Object.Equals%2A> `true` für das Paar zurückgibt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="class-example"></a>Klassenbeispiel

### <a name="description"></a>BESCHREIBUNG
 Das folgende Beispiel zeigt eine Klasse (Verweistyp), die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeErrorClass/cs/FxCop.Usage.GetHashCodeErrorClass.cs#1)]

### <a name="comments"></a>Kommentare
 Im folgenden Beispiel wird die Verletzung durch Überschreiben behoben <xref:System.Object.GetHashCode> .

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedClass/cs/FxCop.Usage.GetHashCodeFixedClass.cs#1)]

## <a name="structure-example"></a>Struktur Beispiel

### <a name="description"></a>BESCHREIBUNG
 Das folgende Beispiel zeigt eine Struktur (Werttyp), die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeErrorStruct/cs/FxCop.Usage.GetHashCodeErrorStruct.cs#1)]

### <a name="comments"></a>Kommentare
 Im folgenden Beispiel wird die Verletzung durch Überschreiben behoben <xref:System.Object.GetHashCode> .

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.GetHashCodeFixedStruct/cs/FxCop.Usage.GetHashCodeFixedStruct.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen.](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Operatorüberladungen weisen benannte Alternativen auf.](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben.](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals.](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>Weitere Informationen

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [Gleichheits Operatoren](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
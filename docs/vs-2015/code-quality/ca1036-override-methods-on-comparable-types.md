---
title: 'CA1036: Methoden für vergleichbare Typen überschreiben | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 52247c9175b22d3d96aa91557ee133f37c55e789
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546600"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Methoden bei vergleichbaren Typen überschreiben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ implementiert die <xref:System.IComparable?displayProperty=fullName> -Schnittstelle und <xref:System.Object.Equals%2A?displayProperty=fullName> überschreibt oder nicht den sprachspezifischen Operator auf Gleichheit, Ungleichheit, kleiner als oder größer als. Die Regel meldet keine Verletzung, wenn der Typ nur eine Implementierung der-Schnittstelle erbt.

## <a name="rule-description"></a>Beschreibung der Regel
 Typen, die eine benutzerdefinierte Sortierreihenfolge definieren, implementieren die <xref:System.IComparable> Schnittstelle Die- <xref:System.IComparable.CompareTo%2A> Methode gibt einen ganzzahligen Wert zurück, der die richtige Sortierreihenfolge für zwei Instanzen des-Typs angibt. Diese Regel identifiziert Typen, die eine Sortierreihenfolge festlegen. Dies impliziert, dass die gewöhnliche Bedeutung von Gleichheit, Ungleichheit, kleiner als und größer als nicht zutreffen. Wenn Sie eine Implementierung von bereitstellen <xref:System.IComparable> , müssen Sie in der Regel auch überschreiben, <xref:System.Object.Equals%2A> sodass Werte zurückgegeben werden, die mit übereinstimmen <xref:System.IComparable.CompareTo%2A> . Wenn Sie <xref:System.Object.Equals%2A> überschreiben und in einer Sprache programmieren, die Operator Überladungen unterstützt, sollten Sie auch Operatoren bereitstellen, die mit konsistent sind <xref:System.Object.Equals%2A> .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, überschreiben Sie <xref:System.Object.Equals%2A> . Wenn die Programmiersprache Operator Überladung unterstützt, stellen Sie die folgenden Operatoren bereit:

- op_Equality

- op_Inequality

- op_LessThan

- op_GreaterThan

  In c# lauten die Token, die zur Darstellung dieser Operatoren verwendet werden, wie folgt: = =,! =, \<, and > .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Verletzung durch fehlende Operatoren verursacht wird und Ihre Programmiersprache das Überladen von Operatoren nicht unterstützt, wie es bei Visual Basic .net der Fall ist. Es ist auch sicher, eine Warnung für aus dieser Regel zu unterdrücken, wenn Sie für Gleichheits Operatoren außer op_Equality ausgelöst wird, wenn Sie feststellen, dass die Implementierung der Operatoren im Anwendungskontext nicht sinnvoll ist. Sie sollten jedoch immer über op_Equality und den = =-Operator verfügen, wenn Sie Object. ist mit überschreiben.

## <a name="example"></a>Beispiel
 Das folgende Beispiel enthält einen Typ, der ordnungsgemäß implementiert <xref:System.IComparable> . Code Kommentare identifizieren die Methoden, die verschiedene Regeln erfüllen, die mit <xref:System.Object.Equals%2A> und der- <xref:System.IComparable> Schnittstelle verknüpft sind.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung testet das Verhalten der <xref:System.IComparable> zuvor gezeigten-Implementierung.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>Weitere Informationen
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [Gleichheits Operatoren](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)

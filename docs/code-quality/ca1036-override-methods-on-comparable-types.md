---
title: 'CA1036: Methoden bei vergleichbaren Typen überschreiben.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12b00c202373310b04021a46e74af2af7e10d535
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868871"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Methoden bei vergleichbaren Typen überschreiben.

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ implementiert die <xref:System.IComparable?displayProperty=fullName> -Schnittstelle und überschreibt nicht die <xref:System.Object.Equals%2A?displayProperty=fullName> oder ist nicht überladen, den sprachspezifischen Operator für gleich, ungleich, kleiner-als "," oder größer-als. Die Regel meldet einen Verstoß gegen nicht, wenn der Typ nur eine Implementierung der Schnittstelle erbt.

Diese Regel nur sucht standardmäßig an öffentliche und geschützte Typen. Dies ist jedoch [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Implementieren von Typen, die eine benutzerdefinierte Sortierreihenfolge definieren die <xref:System.IComparable> Schnittstelle. Die <xref:System.IComparable.CompareTo%2A> Methode gibt einen ganzzahligen-Wert, der die richtigen Sortierreihenfolge für zwei Instanzen des Typs angibt. Diese Regel identifiziert die Typen, die eine Sortierreihenfolge festgelegt. Festlegen der Sortierreihenfolge bedeutet, dass die gewöhnliche Bedeutung der Gleichheit, Ungleichheit, kleiner-als und größer-als nicht gelten. Wenn Sie eine Implementierung bereitstellen <xref:System.IComparable>, müssen Sie in der Regel außer Kraft setzen <xref:System.Object.Equals%2A> , damit sie Werte zurückgibt, die konsistent mit sind <xref:System.IComparable.CompareTo%2A>. Wenn Sie außer Kraft setzen <xref:System.Object.Equals%2A> und Codierung werden in einer Sprache, die von überladenen Operatoren unterstützt, sollten Sie auch Operatoren, die konsistent mit sind bereitstellen <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, außer Kraft setzen <xref:System.Object.Equals%2A>. Wenn Ihre Programmiersprache operatorüberladung unterstützt, geben Sie die folgenden Operatoren:

- op_Equality
- op_Inequality
- op_LessThan
- op_GreaterThan

Sind in C# wie folgt die Token, die verwendet werden, um diese Operatoren darstellen:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher, unterdrücken Sie eine Warnung aus, dass CA1036, wenn die Verletzung verursacht wird, durch fehlende Operatoren und Ihre bevorzugte Programmiersprache operatorüberladung, wie mit Visual Basic nicht unterstützt. Wenn Sie feststellen, dass die Implementierung der Operatoren nicht in den app-Kontext sinnvoll ist, ist es auch sicher, unterdrücken Sie eine Warnung dieser Regel ein, wenn dieser auf Gleichheitsoperatoren als Op_Equality ausgelöst wird. Allerdings sollten Sie immer Op_Equality überschreiben und dem == Operator, wenn Sie außer Kraft setzen <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```
dotnet_code_quality.ca1036.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="examples"></a>Beispiele

Der folgende Code enthält einen Typ, der korrekt implementiert <xref:System.IComparable>. Codekommentare zu identifizieren, die Methoden, die verschiedene Regeln, die im Zusammenhang erfüllen mit <xref:System.Object.Equals%2A> und <xref:System.IComparable> Schnittstelle.

[!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

Der folgende Code überprüft das Verhalten der <xref:System.IComparable> -Implementierung, die zuvor gezeigt wurde.

[!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Gleichheitsoperatoren](/dotnet/standard/design-guidelines/equality-operators)
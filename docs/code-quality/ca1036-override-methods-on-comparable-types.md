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
ms.openlocfilehash: 2a4e04e1afdbecdc9c333ea43a52bff3123d448a
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547616"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Methoden bei vergleichbaren Typen überschreiben.

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ implementiert die <xref:System.IComparable?displayProperty=fullName> -Schnittstelle und über <xref:System.Object.Equals%2A?displayProperty=fullName> schreibt oder nicht den sprachspezifischen Operator auf Gleichheit, Ungleichheit, kleiner als oder größer als. Die Regel meldet keine Verletzung, wenn der Typ nur eine Implementierung der-Schnittstelle erbt.

Standardmäßig untersucht diese Regel nur öffentliche und geschützte Typen, dies ist jedoch [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Typen, die eine benutzerdefinierte Sortierreihenfolge definieren, implementieren die <xref:System.IComparable> Schnittstelle Die <xref:System.IComparable.CompareTo%2A> -Methode gibt einen ganzzahligen Wert zurück, der die richtige Sortierreihenfolge für zwei Instanzen des-Typs angibt. Diese Regel identifiziert Typen, die eine Sortierreihenfolge festlegen. Das Festlegen einer Sortierreihenfolge impliziert, dass die gewöhnliche Bedeutung von Gleichheit, Ungleichheit, kleiner als und größer als nicht zutrifft. Wenn Sie eine Implementierung von <xref:System.IComparable>bereitstellen, müssen Sie in der Regel auch überschreiben <xref:System.Object.Equals%2A> , sodass Werte zurückgegeben <xref:System.IComparable.CompareTo%2A>werden, die mit übereinstimmen. Wenn Sie über <xref:System.Object.Equals%2A> schreiben und in einer Sprache programmieren, die Operator Überladungen unterstützt, sollten Sie auch Operatoren bereit <xref:System.Object.Equals%2A>stellen, die mit konsistent sind.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, <xref:System.Object.Equals%2A>überschreiben Sie. Wenn die Programmiersprache Operator Überladung unterstützt, stellen Sie die folgenden Operatoren bereit:

- op_Equality
- op_Inequality
- op_LessThan
- op_GreaterThan

In C#werden die Token, die zur Darstellung dieser Operatoren verwendet werden, wie folgt verwendet:

```csharp
==
!=
<
>
```

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus der Regel zu unterdrücken CA1036 wenn die Verletzung durch fehlende Operatoren verursacht wird und Ihre Programmiersprache das Überladen von Operatoren nicht unterstützt, wie es bei Visual Basic der Fall ist. Wenn Sie feststellen, dass die Implementierung der Operatoren im App-Kontext keinen Sinn macht, ist es auch sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn Sie für Gleichheits Operatoren außer op_Equality ausgelöst wird. Sie sollten jedoch immer op_Equality und den = =-Operator überschreiben, wenn <xref:System.Object.Equals%2A?displayProperty=nameWithType>Sie überschreiben.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1036.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="examples"></a>Beispiele

Der folgende Code enthält einen Typ, der Ordnungs <xref:System.IComparable>gemäß implementiert. Code Kommentare identifizieren die Methoden, die verschiedene Regeln erfüllen, die mit <xref:System.Object.Equals%2A> und der <xref:System.IComparable> -Schnittstelle verknüpft sind.

[!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]

Der folgende Anwendungscode testet das Verhalten <xref:System.IComparable> der zuvor gezeigten-Implementierung.

[!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.IComparable?displayProperty=fullName>
- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Gleichheitsoperatoren](/dotnet/standard/design-guidelines/equality-operators)
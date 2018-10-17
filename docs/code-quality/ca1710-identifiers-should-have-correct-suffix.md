---
title: 'CA1710: Bezeichner sollten ein richtiges Suffix aufweisen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 263870511715757c8771b0b596e443d82be91525
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549883"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Bezeichner sollten ein richtiges Suffix aufweisen

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Bezeichner muss nicht das richtige Suffix.

## <a name="rule-description"></a>Regelbeschreibung

Gemäß der Konvention, die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen implementieren, bzw. von diesen Typen abgeleitete Typen, müssen Sie ein Suffix, das die Basisklasse oder Schnittstelle zugeordnet ist.

Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

Die folgende Tabelle enthält die Basistypen und Schnittstellen, die Suffixe zugeordnet sind.

|Basistyp/Schnittstelle|Suffix|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Attribut|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Ausnahme|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Auflistung|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dictionary|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Auflistung|
|<xref:System.Collections.Queue?displayProperty=fullName>|Auflistung oder einer Warteschlange|
|<xref:System.Collections.Stack?displayProperty=fullName>|Auflistung oder Stack|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Auflistung|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dictionary|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Auflistung oder DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Stream|
|<xref:System.Security.IPermission?displayProperty=fullName>|Berechtigung|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Bedingung|
|Ein Ereignishandlerdelegat.|EventHandler|

Typen implementiert <xref:System.Collections.ICollection> und sind ein generalisiertes Datenstruktur, wie z. B. ein Wörterbuch, Stapel oder Warteschlange, Namen, die aussagekräftige Informationen über die beabsichtigte Verwendung des Typs ermöglichen dürfen.

Typen implementiert <xref:System.Collections.ICollection> und eine Sammlung von bestimmten Elementen haben Namen, mit dem Wort "Collection" enden. Z. B. eine Auflistung von <xref:System.Collections.Queue> Objekte würde den Namen "QueueCollection" aufweisen. Das Suffix "Collection" gibt an, dass die Mitglieder der Sammlung mit aufgelistet werden, können die `foreach` (`For Each` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) Anweisung.

Typen implementiert <xref:System.Collections.IDictionary> haben Namen, mit dem Wort "Dictionary" enden, selbst wenn der Typ auch implementiert <xref:System.Collections.IEnumerable> oder <xref:System.Collections.ICollection>. Durch die Benennungskonventionen für die Suffix "Collection" und "Dictionary" können Benutzer zwischen den folgenden zwei Enumerationsmustern zu unterscheiden.

Typen mit dem Suffix "Collection" Enumerationsmuster auf.

```
foreach(SomeType x in SomeCollection) { }
```

Typen mit dem Suffix "Dictionary" Enumerationsmuster auf.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

Ein <xref:System.Data.DataSet> Objekt besteht aus einer Auflistung von <xref:System.Data.DataTable> Objekten, die Auflistungen von bestehen <xref:System.Data.DataColumn?displayProperty=fullName> und <xref:System.Data.DataRow?displayProperty=fullName> u. a. die Objekte. Diese Auflistungen implementieren <xref:System.Collections.ICollection> mithilfe der <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> Klasse.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Benennen Sie den Typ, damit es mit dem richtigen angehängt ist.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher, unterdrücken Sie eine Warnung aus, um das Suffix "Collection" verwenden, wenn der Typ eine verallgemeinerte Datenstruktur ist, die erweitert werden kann, oder die wird eine beliebige Gruppe von verschiedenen Elementen enthalten. In diesem Fall kann ein Namen, der aussagekräftige Informationen über die Implementierung, Leistung oder andere Merkmale der Datenstruktur bereitstellt (z. B. BinaryTree) sinnvoll. In Fällen, in denen der Typ stellt eine Auflistung eines bestimmten Typs (z. B. StringCollection) dar, nicht unterdrücken Sie eine Warnung dieser Regel, weil das Suffix gibt an, dass der Typ mit aufgelistet werden, kann ein `foreach` Anweisung.

Unterdrücken Sie keine Warnung dieser Regel, bei anderen Suffixen. Das Suffix ermöglicht die beabsichtigte Verwendung aus dem Typnamen zu sehen sein.

## <a name="related-rules"></a>Verwandte Regeln

[CA1711: Bezeichner sollten kein falsches Suffix aufweisen](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Siehe auch

- [Attribute](/dotnet/standard/design-guidelines/attributes)
- [Behandeln und Auslösen von Ereignissen](/dotnet/standard/events/index)
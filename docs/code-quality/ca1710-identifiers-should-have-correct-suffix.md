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
ms.openlocfilehash: f5e36fef8745e4068a8dd4ad9281a69aa653ed73
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31917151"
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
 Gemäß der Konvention werden die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen bzw. von diesen Typen abgeleitete Typen implementieren, ein Suffix aufweisen, das mit dem Basistyp oder der Schnittstelle verknüpft ist.

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
|<xref:System.Collections.Queue?displayProperty=fullName>|Auflistung oder eine Warteschlange|
|<xref:System.Collections.Stack?displayProperty=fullName>|Auflistung oder den Stapel|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Auflistung|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dictionary|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Auflistung oder eine Datentabelle|
|<xref:System.IO.Stream?displayProperty=fullName>|Stream|
|<xref:System.Security.IPermission?displayProperty=fullName>|Berechtigung|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Bedingung|
|Ein Ereignishandlerdelegat.|EventHandler|

 Typen implementiert, <xref:System.Collections.ICollection> und sind ein generalisiertes Datenstruktur, z. B. ein Wörterbuch, Stapel oder Warteschlange zulässig sind Namen, die aussagekräftige Informationen über die beabsichtigte Verwendung des Typs bereitstellen.

 Typen implementiert, <xref:System.Collections.ICollection> und eine Auflistung von bestimmten Elementen verfügen über Namen, die mit dem Wort "Sammlung" enden. Angenommen, eine Auflistung von <xref:System.Collections.Queue> Objekte müssten den Namen "QueueCollection". Das Suffix "Collection" gibt an, dass die Elemente der Auflistung aufgelistet werden können, mithilfe der `foreach` (`For Each` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) Anweisung.

 Typen implementiert, <xref:System.Collections.IDictionary> haben Namen, die mit dem Wort "Wörterbuch" enden, auch wenn der Typ auch implementiert <xref:System.Collections.IEnumerable> oder <xref:System.Collections.ICollection>. Durch die Benennungskonventionen für die Suffix "Collection" und "Wörterbuch" können Benutzer die folgenden zwei Enumeration Muster unterscheiden.

 Typen mit dem Suffix "Collection" Enumerationsmuster auf.

```
foreach(SomeType x in SomeCollection) { }
```

 Typen mit dem Suffix "Wörterbuch" Enumerationsmuster auf.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 Ein <xref:System.Data.DataSet> Objekt besteht aus einer Auflistung von <xref:System.Data.DataTable> Objekte, die Auflistungen von umfassen <xref:System.Data.DataColumn?displayProperty=fullName> und <xref:System.Data.DataRow?displayProperty=fullName> u. a. die Objekte. Diese Auflistungen implementieren <xref:System.Collections.ICollection> mithilfe der <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> Klasse.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Benennen Sie den Typ, sodass er mit dem richtigen Formatangabe ist.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig zum Unterdrücken einer Warnung, um das Suffix "Collection" verwenden, wenn der Typ eine verallgemeinerte Datenstruktur ist, die erweitert werden kann, oder, die in einer beliebigen Gruppe von verschiedenen Elementen gespeichert werden. In diesem Fall könnte ein Namen, der aussagekräftige Informationen über die Implementierung, Leistung oder andere Merkmale der Datenstruktur bereitstellt (z. B. BinaryTree) sinnvoll. In Fällen, in denen der Typ stellt eine Auflistung eines bestimmten Typs (z. B. StringCollection) dar, unterdrücken Sie keine Warnung dieser Regel, weil das Suffix gibt an, dass der Typ mit aufgelistet werden, kann eine `foreach` Anweisung.

 Unterdrücken Sie für andere Suffixe keine Warnung dieser Regel. Das Suffix ermöglicht die beabsichtigte Verwendung aus dem Typnamen offensichtlich sein.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1711: Bezeichner sollten kein falsches Suffix aufweisen](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Siehe auch
 [Attribute](/dotnet/standard/design-guidelines/attributes) [behandeln und Auslösen von Ereignissen](/dotnet/standard/events/index)
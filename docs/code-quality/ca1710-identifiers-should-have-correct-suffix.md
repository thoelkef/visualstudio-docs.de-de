---
title: 'CA1710: Bezeichner sollten ein richtiges Suffix aufweisen.'
ms.date: 03/11/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50c67c614c4ece8f1925f4133f749a1c5747fe31
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234169"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Bezeichner sollten ein richtiges Suffix aufweisen.

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Bezeichner weist nicht das richtige Suffix auf.

Standardmäßig prüft diese Regel nur extern sichtbare Bezeichner, aber dies ist [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Gemäß der Konvention verfügen die Namen von Typen, die bestimmte Basis Typen erweitern oder bestimmte Schnittstellen oder Typen implementieren, die von diesen Typen abgeleitet sind, über ein Suffix, das dem Basistyp oder der Schnittstelle zugeordnet ist.

Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

In der folgenden Tabelle werden die Basis Typen und Schnittstellen aufgelistet, die über zugeordnete Suffixe verfügen.

|Basistyp/Schnittstelle|Suffix|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Attribut|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Ausnahme|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Auflistung|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dictionary|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Auflistung|
|<xref:System.Collections.Queue?displayProperty=fullName>|Sammlung oder Warteschlange|
|<xref:System.Collections.Stack?displayProperty=fullName>|Sammlung oder Stapel|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Auflistung|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dictionary|
|<xref:System.Data.DataSet?displayProperty=fullName>|Dataset|
|<xref:System.Data.DataTable?displayProperty=fullName>|Sammlung oder Datentabelle|
|<xref:System.IO.Stream?displayProperty=fullName>|Stream|
|<xref:System.Security.IPermission?displayProperty=fullName>|Berechtigung|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Bedingung|
|Ein Ereignishandlerdelegat.|EventHandler|

Typen, die <xref:System.Collections.ICollection> und implementieren, sind eine generalisierte Art von Datenstruktur, z. b. Wörterbuch, Stapel oder Warteschlange, sind zulässige Namen, die aussagekräftige Informationen über die beabsichtigte Verwendung des Typs bereitstellen.

Typen, die <xref:System.Collections.ICollection> und implementieren, sind eine Auflistung bestimmter Elemente, die mit dem Wort "Collection" enden. Beispielsweise würde eine Auflistung von <xref:System.Collections.Queue> -Objekten den Namen ' QueueCollection ' aufweisen. Das Suffix "Collection" bedeutet, dass die Member der Auflistung mithilfe der `foreach` Anweisung (`For Each` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) aufgelistet werden können.

Typen, die <xref:System.Collections.IDictionary> implementieren, haben Namen, die mit dem Wort "Dictionary" enden, auch wenn <xref:System.Collections.IEnumerable> der <xref:System.Collections.ICollection>Typ auch oder implementiert. Mit den Namenskonventionen "Collection" und "Dictionary" können Benutzer zwischen den folgenden beiden Enumerationsmustern unterscheiden.

Typen mit dem Suffix "Collection" folgen diesem Enumerationsmuster.

```
foreach(SomeType x in SomeCollection) { }
```

Typen mit dem "Dictionary"-Suffix folgen diesem Enumerationsmuster.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

Ein <xref:System.Data.DataSet> -Objekt besteht aus einer Auflistung <xref:System.Data.DataTable> von-Objekten, die unter anderem <xref:System.Data.DataColumn?displayProperty=fullName> aus <xref:System.Data.DataRow?displayProperty=fullName> Auflistungen von-Objekten und-Objekten bestehen. Diese Auflistungen implementieren <xref:System.Collections.ICollection> über <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> die Basisklasse.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Benennen Sie den Typ so um, dass er mit dem richtigen Begriff versehen wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung zu unterdrücken, um das Suffix "Collection" zu verwenden, wenn der Typ eine verallgemeinerte Datenstruktur ist, die erweitert werden kann oder einen beliebigen Satz unterschiedlicher Elemente enthalten wird. In diesem Fall kann es sinnvoll sein, einen Namen zu erstellen, der sinnvolle Informationen über die Implementierung, die Leistung oder andere Merkmale der Datenstruktur liefert (z. b. BinaryTree). In Fällen, in denen der Typ eine Auflistung eines bestimmten Typs (z. b. StringCollection) darstellt, unterdrücken Sie keine Warnung dieser Regel, da das Suffix angibt, dass der Typ mithilfe einer `foreach` -Anweisung aufgelistet werden kann.

Unterdrücken Sie bei anderen Suffixen keine Warnung aus dieser Regel. Das Suffix ermöglicht, dass die beabsichtigte Verwendung aus dem Typnamen ersichtlich ist.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1710.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Naming) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Verwandte Regeln

[CA1711: Bezeichner sollten kein falsches Suffix aufweisen](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Siehe auch

- [Attribute](/dotnet/standard/design-guidelines/attributes)
- [Behandeln und Auswerfen von Ereignissen](/dotnet/standard/events/index)
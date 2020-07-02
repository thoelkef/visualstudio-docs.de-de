---
title: 'CA1710: Bezeichner sollten ein korrektes Suffix aufweisen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ee7ce7c4e9edad9d941b4a70b2a199a37130e43
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543987"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Bezeichner sollten ein richtiges Suffix aufweisen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Bezeichner weist nicht das richtige Suffix auf.

## <a name="rule-description"></a>Beschreibung der Regel
 Gemäß der Konvention verfügen die Namen von Typen, die bestimmte Basis Typen erweitern oder bestimmte Schnittstellen oder Typen implementieren, die von diesen Typen abgeleitet sind, über ein Suffix, das dem Basistyp oder der Schnittstelle zugeordnet ist.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

 In der folgenden Tabelle werden die Basis Typen und Schnittstellen aufgelistet, die über zugeordnete Suffixe verfügen.

|Basistyp/Schnittstelle|Suffix|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Attribut|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Ausnahme|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Sammlung|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Wörterbuch|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Sammlung|
|<xref:System.Collections.Queue?displayProperty=fullName>|Sammlung oder Warteschlange|
|<xref:System.Collections.Stack?displayProperty=fullName>|Sammlung oder Stapel|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Sammlung|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Wörterbuch|
|<xref:System.Data.DataSet?displayProperty=fullName>|Dataset|
|<xref:System.Data.DataTable?displayProperty=fullName>|Sammlung oder Datentabelle|
|<xref:System.IO.Stream?displayProperty=fullName>|STREAM|
|<xref:System.Security.IPermission?displayProperty=fullName>|Berechtigung|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Bedingung|
|Ein Ereignishandlerdelegat.|EventHandler|

 Typen, die <xref:System.Collections.ICollection> und implementieren, sind eine generalisierte Art von Datenstruktur, z. b. Wörterbuch, Stapel oder Warteschlange, sind zulässige Namen, die aussagekräftige Informationen über die beabsichtigte Verwendung des Typs bereitstellen.

 Typen, die <xref:System.Collections.ICollection> und implementieren, sind eine Auflistung bestimmter Elemente, die mit dem Wort "Collection" enden. Beispielsweise würde eine Auflistung von- <xref:System.Collections.Queue> Objekten den Namen ' QueueCollection ' aufweisen. Das Suffix "Collection" bedeutet, dass die Member der Auflistung mithilfe der `foreach` `For Each` Anweisung (in) aufgelistet werden können [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .

 Typen, die implementieren, <xref:System.Collections.IDictionary> haben Namen, die mit dem Wort "Dictionary" enden, auch wenn der Typ auch <xref:System.Collections.IEnumerable> oder implementiert <xref:System.Collections.ICollection> . Mit den Namenskonventionen "Collection" und "Dictionary" können Benutzer zwischen den folgenden beiden Enumerationsmustern unterscheiden.

 Typen mit dem Suffix "Collection" folgen diesem Enumerationsmuster.

```
foreach(SomeType x in SomeCollection) { }
```

 Typen mit dem "Dictionary"-Suffix folgen diesem Enumerationsmuster.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 Ein <xref:System.Data.DataSet> -Objekt besteht aus einer Auflistung von <xref:System.Data.DataTable> -Objekten, die unter anderem aus Auflistungen von <xref:System.Data.DataColumn?displayProperty=fullName> -Objekten und- <xref:System.Data.DataRow?displayProperty=fullName> Objekten bestehen. Diese Auflistungen implementieren <xref:System.Collections.ICollection> über die Basis <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> Klasse.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Benennen Sie den Typ so um, dass er mit dem richtigen Begriff versehen wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung zu unterdrücken, um das Suffix "Collection" zu verwenden, wenn der Typ eine verallgemeinerte Datenstruktur ist, die erweitert werden kann oder einen beliebigen Satz unterschiedlicher Elemente enthalten wird. In diesem Fall kann es sinnvoll sein, einen Namen zu erstellen, der sinnvolle Informationen über die Implementierung, die Leistung oder andere Merkmale der Datenstruktur liefert (z. b. BinaryTree). In Fällen, in denen der Typ eine Auflistung eines bestimmten Typs (z. b. StringCollection) darstellt, unterdrücken Sie keine Warnung dieser Regel, da das Suffix angibt, dass der Typ mithilfe einer-Anweisung aufgelistet werden kann `foreach` .

 Unterdrücken Sie bei anderen Suffixen keine Warnung aus dieser Regel. Das Suffix ermöglicht, dass die beabsichtigte Verwendung aus dem Typnamen ersichtlich ist.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1711: Bezeichner sollten kein falsches Suffix aufweisen.](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Weitere Informationen
 [Attribute](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: Ereignisse und](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115) Delegaten

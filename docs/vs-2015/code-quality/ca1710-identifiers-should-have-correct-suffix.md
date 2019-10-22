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
ms.openlocfilehash: 7dc0ed72ddab39bda5f3de9b978f4d55dc2358ba
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669166"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Bezeichner sollten ein richtiges Suffix aufweisen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Bezeichner weist nicht das richtige Suffix auf.

## <a name="rule-description"></a>Regelbeschreibung
 Gemäß der Konvention verfügen die Namen von Typen, die bestimmte Basis Typen erweitern oder bestimmte Schnittstellen oder Typen implementieren, die von diesen Typen abgeleitet sind, über ein Suffix, das dem Basistyp oder der Schnittstelle zugeordnet ist.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

 In der folgenden Tabelle werden die Basis Typen und Schnittstellen aufgelistet, die über zugeordnete Suffixe verfügen.

|Basistyp/Schnittstelle|Suffix|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Attribut|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|-Ausnahme|
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

 Typen, die <xref:System.Collections.ICollection> und einen generalisierten Typ von Datenstruktur (z. b. Wörterbuch, Stapel oder Warteschlange) implementieren, sind zulässige Namen, die aussagekräftige Informationen über die beabsichtigte Verwendung des Typs bereitstellen.

 Typen, die <xref:System.Collections.ICollection> implementieren und eine Auflistung spezifischer Elemente sind, haben Namen, die mit dem Wort "Collection" enden. Beispielsweise würde eine Auflistung von <xref:System.Collections.Queue> Objekten den Namen ' QueueCollection ' aufweisen. Das Suffix "Collection" gibt an, dass die Member der Auflistung mithilfe der `foreach`-Anweisung (`For Each` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) aufgelistet werden können.

 Typen, die <xref:System.Collections.IDictionary> implementieren, haben Namen, die mit dem Wort "Dictionary" enden, auch wenn der Typ ebenfalls <xref:System.Collections.IEnumerable> oder <xref:System.Collections.ICollection> implementiert. Mit den Namenskonventionen "Collection" und "Dictionary" können Benutzer zwischen den folgenden beiden Enumerationsmustern unterscheiden.

 Typen mit dem Suffix "Collection" folgen diesem Enumerationsmuster.

```
foreach(SomeType x in SomeCollection) { }
```

 Typen mit dem "Dictionary"-Suffix folgen diesem Enumerationsmuster.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 Ein <xref:System.Data.DataSet>-Objekt besteht aus einer Auflistung von <xref:System.Data.DataTable> Objekten, die unter anderem aus Auflistungen von <xref:System.Data.DataColumn?displayProperty=fullName> und <xref:System.Data.DataRow?displayProperty=fullName> Objekten bestehen. Diese Auflistungen implementieren <xref:System.Collections.ICollection> über die Basis <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> Klasse.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Benennen Sie den Typ so um, dass er mit dem richtigen Begriff versehen wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung zu unterdrücken, um das Suffix "Collection" zu verwenden, wenn der Typ eine verallgemeinerte Datenstruktur ist, die erweitert werden kann oder einen beliebigen Satz unterschiedlicher Elemente enthalten wird. In diesem Fall kann es sinnvoll sein, einen Namen zu erstellen, der sinnvolle Informationen über die Implementierung, die Leistung oder andere Merkmale der Datenstruktur liefert (z. b. BinaryTree). In Fällen, in denen der Typ eine Auflistung eines bestimmten Typs (z. b. StringCollection) darstellt, unterdrücken Sie keine Warnung aus dieser Regel, da das Suffix angibt, dass der Typ mit einer `foreach` Anweisung aufgelistet werden kann.

 Unterdrücken Sie bei anderen Suffixen keine Warnung aus dieser Regel. Das Suffix ermöglicht, dass die beabsichtigte Verwendung aus dem Typnamen ersichtlich ist.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1711: Bezeichner sollten kein falsches Suffix aufweisen](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Siehe auch
 [Attribute](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: Ereignisse und](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115) Delegaten

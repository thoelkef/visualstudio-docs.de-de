---
title: 'CA1711: Bezeichner sollten kein falsches Suffix aufweisen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9773dc808d6fbbc7161053dcd4d7a1d7d4e6f13
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55970230"
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711: Bezeichner sollten kein falsches Suffix aufweisen.

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|CheckId|CA1711|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Ein Bezeichner weist ein falsches Suffix auf.

## <a name="rule-description"></a>Regelbeschreibung

Nur die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen bzw. Typen implementieren, die von diesen Typen abgeleitet werden, sollten stets mit bestimmten reservierten Suffixen enden. Für andere Typnamen sollten diese reservierten Suffixe nicht verwendet werden.

In der folgenden Tabelle werden die reservierten Suffixe sowie die Basistypen und die Schnittstellen aufgeführt, denen die Suffixe zugeordnet sind.

|Suffix|Basistyp/Schnittstelle|
|------------|--------------------------|
|Attribut|<xref:System.Attribute?displayProperty=fullName>|
|Auflistung|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|
|Dictionary|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|
|EventHandler|Ein Ereignishandlerdelegat.|
|Ausnahme|<xref:System.Exception?displayProperty=fullName>|
|Berechtigung|<xref:System.Security.IPermission?displayProperty=fullName>|
|Warteschlange|<xref:System.Collections.Queue?displayProperty=fullName>|
|Stapel|<xref:System.Collections.Stack?displayProperty=fullName>|
|Stream|<xref:System.IO.Stream?displayProperty=fullName>|

Darüber hinaus sollten die folgenden Suffixe **nicht** verwendet werden:

- `Delegate`

- `Enum`

- `Impl` (verwenden Sie `Core` stattdessen)

- `Ex` oder ein ähnliches Suffix zur Unterscheidung von einer früheren Version desselben Typs

Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Entfernen Sie das Suffix aus dem Typnamen.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel, es sei denn, das Suffix hat eine eindeutige Bedeutung in der Anwendungsdomäne.

## <a name="related-rules"></a>Verwandte Regeln

- [CA1710: Bezeichner sollten ein richtiges Suffix aufweisen](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>Siehe auch

- [Attribute](/dotnet/standard/design-guidelines/attributes)
- [Behandeln und Auslösen von Ereignissen](/dotnet/standard/events/index)
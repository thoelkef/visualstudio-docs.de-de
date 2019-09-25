---
title: 'CA1306: Gebietsschema für Datentypen festlegen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aaf16ccd187681be7406fdadbde620a167a40c96
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235025"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Gebietsschema für Datentypen festlegen.

|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Eine Methode oder ein Konstruktor hat mindestens eine <xref:System.Data.DataTable?displayProperty=fullName> - <xref:System.Data.DataSet?displayProperty=fullName> Instanz oder eine-Instanz erstellt und nicht explizit die<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> locale <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>-Eigenschaft (oder) festgelegt.

## <a name="rule-description"></a>Regelbeschreibung
Das Gebiets Schema bestimmt kulturspezifische Präsentationselemente für Daten, z. b. für numerische Werte, Währungssymbole und die Sortierreihenfolge verwendete Formatierung. Wenn Sie ein oder <xref:System.Data.DataTable> <xref:System.Data.DataSet>ein erstellen, sollten Sie das Gebiets Schema explizit festlegen. Standardmäßig ist das Gebiets Schema für diese Typen die aktuelle Kultur. Für Daten, die in einer Datenbank oder Datei gespeichert sind und Global gemeinsam genutzt werden, sollte das Gebiets Schema normalerweise auf die invariante<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>Kultur () festgelegt werden. Wenn Daten über Kulturen hinweg freigegeben werden, kann die Verwendung des Standard Gebiets Schemas <xref:System.Data.DataTable> bewirken <xref:System.Data.DataSet> , dass der Inhalt von oder falsch dargestellt oder interpretiert wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, legen Sie explizit das Gebiets <xref:System.Data.DataTable> Schema <xref:System.Data.DataSet>für das oder fest.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe verwendet wird, die Daten nicht freigegeben werden oder wenn die Standardeinstellung das gewünschte Verhalten in allen unterstützten Szenarios ergibt.

## <a name="example"></a>Beispiel
Im folgenden Beispiel werden zwei <xref:System.Data.DataTable> -Instanzen erstellt.

[!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.Data.DataTable?displayProperty=fullName>
- <xref:System.Data.DataSet?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
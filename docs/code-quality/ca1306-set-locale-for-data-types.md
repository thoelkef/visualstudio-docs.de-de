---
title: 'CA1306: Gebietsschema für Datentypen festlegen.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: aa74ce81e7923115cf4fa07aba26be171e187690
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946554"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Gebietsschema für Datentypen festlegen.

|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode oder einen Konstruktor erstellt eine oder mehrere <xref:System.Data.DataTable?displayProperty=fullName> oder <xref:System.Data.DataSet?displayProperty=fullName> Instanzen und die Gebietsschemaeigenschaft wurde nicht explizit festgelegt (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> oder <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).

## <a name="rule-description"></a>Regelbeschreibung
 Das Gebietsschema bestimmt kulturspezifische Darstellungselemente für Daten, z. B. für Zahlenwerte, Währungssymbole und Sortierreihenfolge verwendete Formatierung. Bei der Erstellung einer <xref:System.Data.DataTable> oder <xref:System.Data.DataSet>, sollten Sie das Gebietsschema explizit festlegen. Standardmäßig ist das Gebietsschema für diese Art der aktuellen Kultur. Für Daten, die in einer Datenbank oder Datei gespeichert und global freigegeben ist, sollte das Gebietsschema normalerweise auf die invariante Kultur festgelegt werden (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Wenn Daten über Kulturen hinweg freigegeben werden, verwenden das Standardgebietsschema kann dazu führen, dass der Inhalt des der <xref:System.Data.DataTable> oder <xref:System.Data.DataSet> angezeigt oder nicht ordnungsgemäß interpretiert werden soll.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, legen Sie explizit das Gebietsschema für die <xref:System.Data.DataTable> oder <xref:System.Data.DataSet>.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher ist, eine Warnung dieser Regel zu unterdrücken, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe ist, die Daten nicht freigegeben werden, oder die Standardeinstellung das gewünschte Verhalten in allen unterstützten Szenarien ergibt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel erstellt zwei <xref:System.Data.DataTable> Instanzen.

 [!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>Siehe auch

- <xref:System.Data.DataTable?displayProperty=fullName>
- <xref:System.Data.DataSet?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
- <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
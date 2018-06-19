---
title: 'CA1306: Gebietsschema für Datentypen festlegen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b9a7188f3679e04164411472fd2d53948466a30d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900402"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: Gebietsschema für Datentypen festlegen
|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode oder ein Konstruktor erstellt eine oder mehrere <xref:System.Data.DataTable?displayProperty=fullName> oder <xref:System.Data.DataSet?displayProperty=fullName> Instanzen und die Gebietsschemaeigenschaft nicht explizit festgelegt (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> oder <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).

## <a name="rule-description"></a>Regelbeschreibung
 Das Gebietsschema bestimmt kulturspezifische Darstellungselemente für Daten, z. B. für Zahlenwerte, Währungssymbole und Sortierreihenfolge verwendete Formatierung. Beim Erstellen einer <xref:System.Data.DataTable> oder <xref:System.Data.DataSet>, sollten Sie das Gebietsschema explizit festlegen. Standardmäßig ist das Gebietsschema für diese Art der aktuellen Kultur. Für Daten, die in einer Datenbank oder Datei gespeichert und Global gemeinsam genutzt wird, sollte das Gebietsschema in der Regel auf die invariante Kultur festgelegt werden (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). Wenn Daten über Kulturen hinweg gemeinsam verwendet werden, verwenden das Standardgebietsschema kann dazu führen, dass der Inhalt des der <xref:System.Data.DataTable> oder <xref:System.Data.DataSet> dargestellt oder falsch interpretiert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, legen Sie explizit das Gebietsschema für die <xref:System.Data.DataTable> oder <xref:System.Data.DataSet>.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn die Bibliothek oder Anwendung für eine begrenzte lokale Zielgruppe ist, die Daten nicht freigegeben werden oder die Standardeinstellung das gewünschte Verhalten in allen unterstützten Szenarien ergibt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel erstellt zwei <xref:System.Data.DataTable> Instanzen.

 [!code-csharp[FxCop.Globalization.DataTable#1](../code-quality/codesnippet/CSharp/ca1306-set-locale-for-data-types_1.cs)]

## <a name="see-also"></a>Siehe auch
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName> <xref:System.Globalization.CultureInfo?displayProperty=fullName> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
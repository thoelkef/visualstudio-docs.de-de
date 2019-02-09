---
title: Regelsatz für Globalisierungsregeln für verwalteten Code
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 28199eb9fa09e2096939ffa8e678eb9812a61b1f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55940476"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Regelsatz für Globalisierungsregeln für verwalteten Code
Sie können den Microsoft-Globalisierungsregeln Regelsatz, der sich auf Probleme, die Daten in Ihrer Anwendung angezeigt werden, in verschiedenen Sprachen, Gebietsschemas und Kulturen ordnungsgemäß verhindern könnten. Sie sollten berücksichtigen, diese Regel festgelegt, wenn Ihre Anwendung globalisiert, lokalisiert wird, oder beides.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|MessageBoxOptions angeben.|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Doppelte Zugriffstasten vermeiden.|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Keine Hartkodierung für gebietsschemaspezifische Zeichenfolgen verwenden.|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Literale nicht als lokalisierte Parameter übergeben.|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|CultureInfo angeben.|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|IFormatProvider angeben.|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Gebietsschema für Datentypen festlegen.|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|StringComparison angeben.|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Zeichenfolgen in Großbuchstaben normalisieren.|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Ordinal-StringComparison verwenden.|
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Marshalling für P/Invoke-Zeichenfolgenargumente festlegen.|
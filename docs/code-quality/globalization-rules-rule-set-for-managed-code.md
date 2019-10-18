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
ms.openlocfilehash: 905f3323f4ede33ba8a7e1547bed7a81c43be96d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449032"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Regelsatz für Globalisierungsregeln für verwalteten Code

Verwenden Sie den Regelsatz Microsoft-Globalisierungsregeln, um sich auf Probleme zu konzentrieren, die möglicherweise verhindern, dass Daten in Ihrer Anwendung in verschiedenen Sprachen, Gebiets Schemata und Kulturen ordnungsgemäß angezeigt werden. Sie sollten diesen Regelsatz einschließen, wenn Ihre Anwendung lokalisiert, globalisiert oder beides ist.

|Regel|Beschreibung|
|----------|-----------------|
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|MessageBoxOptions angeben.|
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Doppelte Zugriffstasten vermeiden.|
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Gebiets Schema spezifische Zeichen folgen nicht hart codieren|
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Literale nicht als lokalisierte Parameter übergeben.|
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|CultureInfo angeben.|
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|IFormatProvider angeben.|
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Gebietsschema für Datentypen festlegen.|
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|StringComparison angeben.|
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Zeichenfolgen in Großbuchstaben normalisieren.|
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Ordinal-StringComparison verwenden.|
|[CA2101](../code-quality/ca2101.md)|Marshalling für P/Invoke-Zeichenfolgenargumente festlegen.|

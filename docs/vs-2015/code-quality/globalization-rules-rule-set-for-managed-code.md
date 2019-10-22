---
title: Regelsatz für Globalisierungsregeln für verwalteten Code | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1630769b5150d9cef7b00e575ac9c555f5bc5be1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667603"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>Regelsatz für Globalisierungsregeln für verwalteten Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können den Regelsatz für Microsoft-Globalisierungsregeln verwenden, um sich auf Probleme zu konzentrieren, die möglicherweise verhindern, dass Daten in Ihrer Anwendung in verschiedenen Sprachen, Gebiets Schemas und Kulturen ordnungsgemäß angezeigt werden. Sie sollten diesen Regelsatz einschließen, wenn Ihre Anwendung lokalisiert, globalisiert oder beides ist.

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

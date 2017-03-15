---
title: "Regelsatz f&#252;r Globalisierungsregeln f&#252;r verwalteten Code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# Regelsatz f&#252;r Globalisierungsregeln f&#252;r verwalteten Code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit dem Regelsatz für Microsoft\-Globalisierungsregeln können Sie sich auf Probleme zu konzentrieren, die dazu führen können, dass Daten in der Anwendung in allen Sprachen, Gebietsschemas und Kulturen richtig angezeigt werden.  Sie sollten diesen Regelsatz aufnehmen, wenn die Anwendung lokalisiert oder globalisiert wird oder beides.  
  
|Regel|**Beschreibung**|  
|-----------|----------------------|  
|[CA1300](../code-quality/ca1300-specify-messageboxoptions.md)|MessageBoxOptions angeben|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Doppelte Zugriffstasten vermeiden|  
|[CA1302](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|Keine Hartkodierung für gebietsschemaspezifische Zeichenfolgen verwenden|  
|[CA1303](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|Literale nicht als lokalisierte Parameter übergeben|  
|[CA1304](../code-quality/ca1304-specify-cultureinfo.md)|CultureInfo angeben|  
|[CA1305](../code-quality/ca1305-specify-iformatprovider.md)|IFormatProvider angeben|  
|[CA1306](../code-quality/ca1306-set-locale-for-data-types.md)|Gebietsschema für Datentypen festlegen|  
|[CA1307](../code-quality/ca1307-specify-stringcomparison.md)|StringComparison angeben|  
|[CA1308](../code-quality/ca1308-normalize-strings-to-uppercase.md)|Zeichenfolgen in Großbuchstaben normalisieren|  
|[CA1309](../code-quality/ca1309-use-ordinal-stringcomparison.md)|Ordinal\-StringComparison verwenden|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Marshalling für P\/Invoke\-Zeichenfolgenargumente festlegen|
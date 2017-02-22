---
title: "CA1308: Zeichenfolgen in Gro&#223;buchstaben normalisieren | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1308"
  - "NormalizeStringsToUppercase"
helpviewer_keywords: 
  - "NormalizeStringsToUppercase"
  - "CA1308"
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1308: Zeichenfolgen in Gro&#223;buchstaben normalisieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NormalizeStringsToUppercase|  
|CheckId|CA1308|  
|Kategorie \(Category\)|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Die Zeichenfolge wird durch einen Vorgang in Kleinbuchstaben normalisiert.  
  
## Regelbeschreibung  
 Zeichenfolgen sollten in Großschreibung normalisiert werden.  Bei einer kleinen Gruppe von Zeichen kann bei der Konvertierung in Kleinbuchstaben kein Roundtrip ausgeführt werden.  Ein Roundtrip bedeutet, dass die Zeichen von einem Gebietsschema in ein anderes Gebietsschema konvertiert werden, das Zeichendaten anders darstellt, und anschließend die ursprünglichen Zeichen aus den konvertierten Zeichen exakt wieder abgerufen werden.  
  
## Behandeln von Verstößen  
 Ändern Sie Operationen, durch die Zeichenfolgen in Kleinschreibung konvertiert werden, damit die Zeichenfolgen stattdessen in Großschreibung konvertiert werden.  Ändern Sie beispielsweise `String.ToLower(CultureInfo.InvariantCulture)` zu `String.ToUpper(CultureInfo.InvariantCulture)`.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Warnmeldungen können gefahrlos unterdrückt werden, wenn Sie keine Sicherheitsentscheidung auf der Grundlage des Ergebnisses treffen, dieses also beispielsweise in der Benutzeroberfläche anzeigen lassen.  
  
## Siehe auch  
 [Globalisierungswarnungen](../code-quality/globalization-warnings.md)
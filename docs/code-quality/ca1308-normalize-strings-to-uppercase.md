---
title: 'CA1308: Zeichenfolgen in Großbuchstaben normalisieren | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 979b6d0bbd14d6432ea376622ce61f6329f708fa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Zeichenfolgen in Großbuchstaben normalisieren
|||  
|-|-|  
|TypeName|NormalizeStringsToUppercase|  
|CheckId|CA1308|  
|Kategorie|Microsoft.Globalization|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein Vorgang wird eine Zeichenfolge in Kleinbuchstaben normalisiert.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Zeichenfolgen sollten in Großschreibung normalisiert werden. Eine kleine Gruppe von Zeichen, wenn sie in Kleinbuchstaben konvertiert wurden, kann keinen Roundtrip vorgenommen werden. Um einen Roundtrip abrufen Möglichkeit zum Konvertieren der Zeichen aus einem Gebietsschema auf einem anderen Gebietsschema, die Zeichendaten anders darstellt, und dann zu genau die ursprünglichen Zeichen aus der konvertierten Zeichen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Ändern Sie die Vorgänge, die Zeichenfolgen in Kleinbuchstaben konvertiert, sodass die Zeichenfolgen konvertiert werden stattdessen in Großbuchstaben. Ändern Sie beispielsweise `String.ToLower(CultureInfo.InvariantCulture)` zu `String.ToUpper(CultureInfo.InvariantCulture)`.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig auf eine Warnung zu unterdrücken, wenn Sie nicht sicherheitsentscheidung abhängig vom Ergebnis (z. B. vornehmen, wenn Sie in der Benutzeroberfläche angezeigt werden).  
  
## <a name="see-also"></a>Siehe auch  
 [Globalisierungswarnungen](../code-quality/globalization-warnings.md)
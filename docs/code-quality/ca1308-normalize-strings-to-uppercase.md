---
title: 'CA1308: Zeichenfolgen in Großbuchstaben normalisieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
ms.openlocfilehash: a5cda66d2a43ee3fde8e3e7b2d22a64a09655da3
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31897142"
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
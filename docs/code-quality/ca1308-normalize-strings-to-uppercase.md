---
title: 'CA1308: Zeichenfolgen in Großbuchstaben normalisieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: cf3acc0911f82a95bde3ce51a8869227c817e49a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53894966"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Zeichenfolgen in Großbuchstaben normalisieren

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Vorgang normalisiert eine Zeichenfolge in Kleinbuchstaben.

## <a name="rule-description"></a>Regelbeschreibung
 Zeichenfolgen sollten in Großschreibung normalisiert werden. Eine kleine Gruppe von Zeichen, wenn sie in Kleinbuchstaben konvertiert wurden, kann keinen Roundtrip vorgenommen werden. Ein Roundtrip abrufen Mittel zum Konvertieren von Zeichen aus einem Gebietsschema an einem anderen Gebietsschema, die Zeichendaten anders darstellt und dann auf genau die ursprünglichen Zeichen aus der konvertierten Zeichen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ändern Sie die Vorgänge, die Zeichenfolgen in Kleinbuchstaben zu konvertieren, sodass die Zeichenfolgen konvertiert werden stattdessen in Großbuchstaben. Ändern Sie beispielsweise `String.ToLower(CultureInfo.InvariantCulture)` zu `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher ist, eine Warnmeldung zu unterdrücken, wenn Sie nicht vornehmen, sind sicherheitsrelevante Entscheidungen basierend auf dem Ergebnis (z. B., wenn Sie es in der Benutzeroberfläche anzeigen).

## <a name="see-also"></a>Siehe auch
 [Globalisierungswarnungen](../code-quality/globalization-warnings.md)
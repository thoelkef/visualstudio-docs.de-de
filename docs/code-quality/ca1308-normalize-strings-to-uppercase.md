---
title: 'CA1308: Zeichenfolgen in Großbuchstaben normalisieren.'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c33f4b0b55728d659c34e0ffc8723f555a6d074d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234919"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Zeichenfolgen in Großbuchstaben normalisieren.

|||
|-|-|
|TypeName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Ein Vorgang normalisiert eine Zeichenfolge in Kleinbuchstaben.

## <a name="rule-description"></a>Regelbeschreibung
Zeichenfolgen sollten in Großschreibung normalisiert werden. Bei einer kleinen Gruppe von Zeichen, die in Kleinbuchstaben konvertiert werden, kann kein Roundtrip durchlaufen werden. Ein Roundtrip bedeutet, dass die Zeichen von einem Gebiets Schema in ein anderes Gebiets Schema konvertiert werden sollen, das Zeichendaten unterschiedlich darstellt, und dann die ursprünglichen Zeichen aus den konvertierten Zeichen genau abzurufen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Änderungs Vorgänge, bei denen Zeichen folgen in Kleinbuchstaben konvertiert werden, sodass die Zeichen folgen stattdessen in Großbuchstaben konvertiert werden. Ändern Sie beispielsweise `String.ToLower(CultureInfo.InvariantCulture)` zu `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Es ist sicher, eine Warnmeldung zu unterdrücken, wenn Sie keine Sicherheits Entscheidung basierend auf dem Ergebnis treffen (z. b. bei der Anzeige in der Benutzeroberfläche).

## <a name="see-also"></a>Siehe auch
[Globalisierungswarnungen](../code-quality/globalization-warnings.md)
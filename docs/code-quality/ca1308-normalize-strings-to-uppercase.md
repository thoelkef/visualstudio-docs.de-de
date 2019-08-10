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
ms.openlocfilehash: 06fe8d4fbd4def14bfb8a24f4f211a121c809930
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922241"
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
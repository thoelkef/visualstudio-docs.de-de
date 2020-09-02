---
title: 'CA1308: Zeichen folgen in Großbuchstaben normalisieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c068fcda7d03ae91435c040d2110d632668d832a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85538735"
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Zeichenfolgen in Großbuchstaben normalisieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|NormalizeStringsToUppercase|
|CheckId|CA1308|
|Category|Microsoft. Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein Vorgang normalisiert eine Zeichenfolge in Kleinbuchstaben.

## <a name="rule-description"></a>Beschreibung der Regel
 Zeichenfolgen sollten in Großschreibung normalisiert werden. Bei einer kleinen Gruppe von Zeichen, die in Kleinbuchstaben konvertiert werden, kann kein Roundtrip durchlaufen werden. Ein Roundtrip bedeutet, dass die Zeichen von einem Gebiets Schema in ein anderes Gebiets Schema konvertiert werden sollen, das Zeichendaten unterschiedlich darstellt, und dann die ursprünglichen Zeichen aus den konvertierten Zeichen genau abzurufen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Änderungs Vorgänge, bei denen Zeichen folgen in Kleinbuchstaben konvertiert werden, sodass die Zeichen folgen stattdessen in Großbuchstaben konvertiert werden. Ändern Sie beispielsweise `String.ToLower(CultureInfo.InvariantCulture)` in `String.ToUpper(CultureInfo.InvariantCulture)`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnmeldung zu unterdrücken, wenn Sie keine Sicherheits Entscheidung basierend auf dem Ergebnis treffen (z. b. bei der Anzeige in der Benutzeroberfläche).

## <a name="see-also"></a>Weitere Informationen
 [Globalisierungs Warnungen](../code-quality/globalization-warnings.md)

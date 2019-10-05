---
title: 'CA1820: Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b197cacc764f1f5472d3eb074ac89199db508408
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233427"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen.

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Zeichenfolge wird mithilfe <xref:System.Object.Equals%2A?displayProperty=nameWithType>von mit der leeren Zeichenfolge verglichen.

## <a name="rule-description"></a>Regelbeschreibung

Das Vergleichen von Zeichen <xref:System.String.Length%2A?displayProperty=nameWithType> folgen mit der <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> -Eigenschaft oder der- <xref:System.Object.Equals%2A>Methode ist schneller als die Verwendung von Dies liegt daran <xref:System.Object.Equals%2A> , dass wesentlich mehr MSIL-Anweisungen <xref:System.String.IsNullOrEmpty%2A> ausführt, als entweder oder die Anzahl der Anweisungen <xref:System.String.Length%2A> , die ausgeführt werden, um den Eigenschafts Wert abzurufen und mit NULL zu vergleichen.

Bei Null-Zeichen <xref:System.Object.Equals%2A> folgen `<string>.Length == 0` und Verhalten sich unterschiedlich. Wenn Sie versuchen, den Wert der- <xref:System.String.Length%2A> Eigenschaft für eine NULL-Zeichenfolge zu erhalten, löst der Common Language Runtime einen <xref:System.NullReferenceException?displayProperty=fullName>aus. Wenn Sie einen Vergleich zwischen einer NULL-Zeichenfolge und der leeren Zeichenfolge durchführen, löst der Common Language Runtime keine Ausnahme `false`aus und gibt zurück. Das Testen auf NULL wirkt sich nicht maßgeblich auf die relative Leistung dieser beiden Ansätze aus. Verwenden Sie die <xref:System.String.IsNullOrEmpty%2A> -Methode, wenn Sie auf .NET Framework 2,0 oder höher abzielen. Verwenden Sie andernfalls den <xref:System.String.Length%2A> = = 0-Vergleich, wann immer dies möglich ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Vergleich so <xref:System.String.IsNullOrEmpty%2A> , dass die-Methode verwendet wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Leistung kein Problem ist.

## <a name="example"></a>Beispiel

Im folgenden Beispiel werden die verschiedenen Techniken veranschaulicht, die für die Suche nach einer leeren Zeichenfolge verwendet werden.

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]
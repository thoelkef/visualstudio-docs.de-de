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
ms.openlocfilehash: ae65ad9c1ad740b3ea39dd97d7430804292df057
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55948445"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen.

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategorie|Microsoft.Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Zeichenfolge ist eine leere Zeichenfolge verglichen, mit <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="rule-description"></a>Regelbeschreibung

Vergleichen von Zeichenfolgen mithilfe der <xref:System.String.Length%2A?displayProperty=nameWithType> Eigenschaft oder das <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> Methode ist schneller als die Verwendung von <xref:System.Object.Equals%2A>. Grund hierfür ist, <xref:System.Object.Equals%2A> führt die erheblich mehr MSIL-Anweisungen als <xref:System.String.IsNullOrEmpty%2A> oder die Anzahl von Anweisungen ausgeführt, um die <xref:System.String.Length%2A> Eigenschaft Wert ein, und vergleichen Sie ihn auf 0 (null).

Bei null-Zeichenfolgen <xref:System.Object.Equals%2A> und <xref:System.String.Length%2A> == 0 anders verhalten. Wenn Sie versuchen, den Wert der Abrufen der <xref:System.String.Length%2A> Eigenschaft eine null-Zeichenfolge, die common Language Runtime löst eine <xref:System.NullReferenceException?displayProperty=fullName>. Wenn Sie einen Vergleich zwischen einem null-Zeichenfolge und die leere Zeichenfolge ausführen, wird die common Language Runtime löst keine Ausnahme und gibt `false`. Testen auf Null erheblich wirkt die relative Leistung der beiden Ansätze sich nicht. Wenn .NET Framework 2.0 oder höher abzielen, verwenden Sie die <xref:System.String.IsNullOrEmpty%2A> Methode. Verwenden Sie andernfalls die <xref:System.String.Length%2A> == 0 Vergleich, wann immer möglich.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Vergleich so um die <xref:System.String.Length%2A> -Eigenschaft und der Test für die null-Zeichenfolge. Wenn .NET Framework 2.0 oder höher abzielen, verwenden Sie die <xref:System.String.IsNullOrEmpty%2A> Methode.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn die Leistung kein Problem darstellt.

## <a name="example"></a>Beispiel

Das folgende Beispiel veranschaulicht die verschiedenen Methoden, die verwendet werden, um eine leere Zeichenfolge zu suchen.

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]
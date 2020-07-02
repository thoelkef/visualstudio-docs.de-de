---
title: 'CA1820: mithilfe der Zeichen folgen Länge auf leere Zeichen folgen testen Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 296eb6407e3ce63b0eb28ff86c215c12ec724ce9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545313"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategorie|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Zeichenfolge wird mithilfe von mit der leeren Zeichenfolge verglichen <xref:System.Object.Equals%2A?displayProperty=fullName> .

## <a name="rule-description"></a>Beschreibung der Regel
 Das Vergleichen von Zeichen folgen mit der- <xref:System.String.Length%2A?displayProperty=fullName> Eigenschaft oder der- <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> Methode ist bedeutend schneller als die Verwendung von <xref:System.Object.Equals%2A> Dies liegt daran, dass <xref:System.Object.Equals%2A> wesentlich mehr MSIL-Anweisungen ausführt, als entweder <xref:System.String.IsNullOrEmpty%2A> oder die Anzahl der Anweisungen, die ausgeführt werden, um den <xref:System.String.Length%2A> Eigenschafts Wert abzurufen und mit NULL zu vergleichen.

 Beachten Sie, dass sich <xref:System.Object.Equals%2A> und <xref:System.String.Length%2A> = = 0 bei Null-Zeichen folgen anders Verhalten. Wenn Sie versuchen, den Wert der- <xref:System.String.Length%2A> Eigenschaft für eine NULL-Zeichenfolge zu erhalten, löst der Common Language Runtime einen aus <xref:System.NullReferenceException?displayProperty=fullName> . Wenn Sie einen Vergleich zwischen einer NULL-Zeichenfolge und der leeren Zeichenfolge durchführen, löst der Common Language Runtime keine Ausnahme aus. der Vergleich gibt zurück `false` . Das Testen auf NULL wirkt sich nicht maßgeblich auf die relative Leistung dieser beiden Ansätze aus. Verwenden Sie [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] die-Methode, wenn Sie auf abzielen <xref:System.String.IsNullOrEmpty%2A> . Verwenden Sie andernfalls den <xref:System.String.Length%2A> = =-Vergleich, wann immer dies möglich ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Vergleich so, dass die Eigenschaft verwendet wird, <xref:System.String.Length%2A> und testen Sie die NULL-Zeichenfolge. Verwenden Sie [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] die-Methode, wenn Sie auf abzielen <xref:System.String.IsNullOrEmpty%2A> .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Leistung kein Problem ist.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die verschiedenen Techniken veranschaulicht, die für die Suche nach einer leeren Zeichenfolge verwendet werden.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]

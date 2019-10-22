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
ms.openlocfilehash: 6711dac907de2777cf892b20269fec7e99d3bd6f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657502"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Kategorie|Microsoft. Performance|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Zeichenfolge wird mithilfe von <xref:System.Object.Equals%2A?displayProperty=fullName> mit der leeren Zeichenfolge verglichen.

## <a name="rule-description"></a>Regelbeschreibung
 Das Vergleichen von Zeichen folgen mit der <xref:System.String.Length%2A?displayProperty=fullName>-Eigenschaft oder der <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName>-Methode ist wesentlich schneller als die Verwendung von <xref:System.Object.Equals%2A>. Dies liegt daran, dass <xref:System.Object.Equals%2A> wesentlich mehr MSIL-Anweisungen ausführt, als entweder <xref:System.String.IsNullOrEmpty%2A> oder die Anzahl der Anweisungen, die ausgeführt werden, um den <xref:System.String.Length%2A>-Eigenschafts Wert abzurufen und ihn mit NULL zu vergleichen

 Beachten Sie, dass sich <xref:System.Object.Equals%2A> und <xref:System.String.Length%2A> = = 0 bei Null-Zeichen folgen unterschiedlich verhalten. Wenn Sie versuchen, den Wert der <xref:System.String.Length%2A>-Eigenschaft für eine NULL-Zeichenfolge zu erhalten, löst die Common Language Runtime eine <xref:System.NullReferenceException?displayProperty=fullName> aus. Wenn Sie einen Vergleich zwischen einer NULL-Zeichenfolge und der leeren Zeichenfolge durchführen, löst der Common Language Runtime keine Ausnahme aus. beim Vergleich wird `false` zurückgegeben. Das Testen auf NULL wirkt sich nicht maßgeblich auf die relative Leistung dieser beiden Ansätze aus. Wenn Sie [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] verwenden, verwenden Sie die <xref:System.String.IsNullOrEmpty%2A>-Methode. Verwenden Sie andernfalls den <xref:System.String.Length%2A> = =-Vergleich, wann immer dies möglich ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Vergleich so, dass die <xref:System.String.Length%2A>-Eigenschaft verwendet wird, und testen Sie die NULL-Zeichenfolge. Wenn Sie [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] Ziel verwenden, verwenden Sie die <xref:System.String.IsNullOrEmpty%2A>-Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Leistung kein Problem ist.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die verschiedenen Techniken veranschaulicht, die für die Suche nach einer leeren Zeichenfolge verwendet werden.

 [!code-csharp[FxCop.Performance.StringTest#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.StringTest/cs/FxCop.Performance.StringTest.cs#1)]

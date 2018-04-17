---
title: ': Ca1820 Verwendung von leeren Zeichenfolgen, die mithilfe der Zeichenfolgenlänge | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b70f2579a7c5afb0baa24cf1c6ad9b33ec5a47d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Mithilfe der Zeichenfolgenlänge auf leere Zeichenfolgen prüfen
|||  
|-|-|  
|TypeName|TestForEmptyStringsUsingStringLength|  
|CheckId|CA1820|  
|Kategorie|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Eine Zeichenfolge ist auf die leere Zeichenfolge mithilfe verglichen <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Vergleichen von Zeichenfolgen mit den <xref:System.String.Length%2A?displayProperty=fullName> Eigenschaft oder die <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName> Methode ist bedeutend schneller als die Verwendung von <xref:System.Object.Equals%2A>. Grund hierfür ist, <xref:System.Object.Equals%2A> führt deutlich mehr MSIL-Anweisungen als <xref:System.String.IsNullOrEmpty%2A> oder die Anzahl der Anweisungen ausgeführt, um die <xref:System.String.Length%2A> Eigenschaft-Wert, und vergleichen es mit 0 (null).  
  
 Sie sollten sich bewusst sein, die <xref:System.Object.Equals%2A> und <xref:System.String.Length%2A> == 0 bei null-Zeichenfolgen anders verhalten. Wenn Sie versuchen, das Abrufen des Werts der <xref:System.String.Length%2A> Eigenschaft auf eine null-Zeichenfolge, die common Language Runtime löst eine <xref:System.NullReferenceException?displayProperty=fullName>. Wenn Sie einen Vergleich zwischen null-Zeichenfolgen und die leere Zeichenfolge ausführen, löst die common Language Runtime eine Ausnahme; der Vergleich gibt `false`. Testen auf Null erheblich wirkt die relative Leistung einer dieser beiden Ansätze sich nicht. Beim Abzielen auf [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], verwenden Sie die <xref:System.String.IsNullOrEmpty%2A> Methode. Verwenden Sie andernfalls die <xref:System.String.Length%2A> == Vergleich, wann immer möglich.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Vergleich mit der <xref:System.String.Length%2A> -Eigenschaft und der Test für die null-Zeichenfolge. Bei der Ausrichtung auf [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)], verwenden Sie die <xref:System.String.IsNullOrEmpty%2A> Methode.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn Leistung kein Problem darstellt.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht die verschiedenen Verfahren, die verwendet werden, um eine leere Zeichenfolge zu suchen.  
  
 [!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]
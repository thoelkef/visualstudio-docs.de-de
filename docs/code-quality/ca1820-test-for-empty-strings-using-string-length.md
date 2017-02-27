---
title: "CA1820: Mithilfe der Zeichenfolgenl&#228;nge auf leere Zeichenfolgen pr&#252;fen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
helpviewer_keywords: 
  - "TestForEmptyStringsUsingStringLength"
  - "CA1820"
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1820: Mithilfe der Zeichenfolgenl&#228;nge auf leere Zeichenfolgen pr&#252;fen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TestForEmptyStringsUsingStringLength|  
|CheckId|CA1820|  
|Kategorie \(Category\)|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Zeichenfolge wird unter Verwendung von <xref:System.Object.Equals%2A?displayProperty=fullName> mit der leeren Zeichenfolge verglichen.  
  
## Regelbeschreibung  
 Der Vergleich von Zeichenfolgen mit der <xref:System.String.Length%2A?displayProperty=fullName>\-Eigenschaft oder der <xref:System.String.IsNullOrEmpty%2A?displayProperty=fullName>\-Methode ist bedeutend schneller als ein Vergleich mit <xref:System.Object.Equals%2A>.  Der Grund dafür liegt darin, dass <xref:System.String.IsNullOrEmpty%2A> bedeutend mehr MSIL\-Anweisungen ausführt als <xref:System.String.Length%2A> oder die Anweisungen, die ausgeführt werden, um den Wert der <xref:System.Object.Equals%2A>\-Eigenschaft abzurufen und mit 0 \(null\) zu vergleichen.  
  
 Sie sollten beachten, dass sich <xref:System.Object.Equals%2A> und <xref:System.String.Length%2A> \=\= 0 bei NULL\-Zeichenfolgen anders verhalten.  Wenn versucht wird, den Wert der <xref:System.String.Length%2A>\-Eigenschaft für eine NULL\-Zeichenfolge abzurufen, löst die Common Language Runtime einen <xref:System.NullReferenceException?displayProperty=fullName>\-Fehler aus.  Wenn eine NULL\-Zeichenfolge mit einer leeren Zeichenfolge verglichen wird, löst die Common Language Runtime keine Ausnahme aus. Der Vergleich ergibt `false`.  Die Überprüfung auf NULL wirkt sich kaum auf die relative Leistung dieser zwei Ansätze aus.  Wenn auf [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] abgezielt wird, verwenden Sie die <xref:System.String.IsNullOrEmpty%2A>\-Methode.  Andernfalls verwenden Sie den <xref:System.String.Length%2A> \=\= Vergleich, wenn irgend möglich.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Vergleich ab, sodass die <xref:System.String.Length%2A>\-Eigenschaft verwendet wird und überprüft wird, ob eine NULL\-Zeichenfolge vorliegt.  Wenn auf [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] abgezielt wird, verwenden Sie die <xref:System.String.IsNullOrEmpty%2A>\-Methode.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn die Leistung nicht von Belang ist.  
  
## Beispiel  
 Im folgenden Beispiel werden die verschiedenen Techniken veranschaulicht, die zur Suche nach einer leeren Zeichenfolge eingesetzt werden können.  
  
 [!code-cs[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]
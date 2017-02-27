---
title: "CA1008: Enumerationen m&#252;ssen einen Wert von 0 (null) aufweisen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
helpviewer_keywords: 
  - "CA1008"
  - "EnumsShouldHaveZeroValue"
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 21
---
# CA1008: Enumerationen m&#252;ssen einen Wert von 0 (null) aufweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumsShouldHaveZeroValue|  
|CheckId|CA1008|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend – Wenn Sie aufgefordert werden, einer Enumeration ohne Flag\-Attribut einen **None**\-Wert hinzuzufügen. Unterbrechend – Wenn Sie aufgefordert werden, einen Enumerationswert umzubenennen oder zu entfernen.|  
  
## Ursache  
 Eine Enumeration, auf die <xref:System.FlagsAttribute?displayProperty=fullName> nicht angewendet wird, definiert keinen Member mit einem Wert von 0 \(null\), bzw. eine Enumeration, auf die <xref:System.FlagsAttribute> angewendet wird, definiert einen Member mit einem Wert von 0 \(null\), ihr Name lautet jedoch nicht "None", oder die Enumeration definiert mehrere Member mit dem Wert 0 \(null\).  
  
## Regelbeschreibung  
 Der Standardwert einer nicht initialisierten Enumeration ist ebenso wie der anderer Werttypen 0 \(null\).  Eine Enumeration ohne das Flags\-Attribut sollte einen Member mit dem Wert 0 \(null\) definieren, damit der Standardwert ein gültiger Wert der Enumeration ist.  Geben Sie dem Member gegebenenfalls den Namen "None".  Weisen Sie andernfalls dem am häufigsten verwendeten Member den Wert 0 \(null\) zu.  Wenn der Wert des ersten Enumerationsmembers in der Deklaration nicht festgelegt wird, ist 0 \(null\) der Standardwert.  
  
 Wenn eine Enumeration, auf die <xref:System.FlagsAttribute> angewendet wird, einen Member mit dem Wert 0 \(null\) definiert, sollte dieser den Namen "None" haben, um anzugeben, dass in der Enumeration keine Werte festgelegt wurden.  Die Verwendung eines Members mit dem Wert 0 \(null\) für andere Zwecke widerspricht der Verwendung von <xref:System.FlagsAttribute> dahingehend, dass die bitweisen Operatoren AND und OR für den Member nutzlos sind.  Dies impliziert, dass nur einem Member der Wert 0 \(null\) zugewiesen werden sollte.  Wenn eine Enumeration mit dem Flags\-Attribut mehrere Member mit dem Wert 0 \(null\) enthält, gibt `Enum.ToString()` für die Member, die nicht den Wert 0 \(null\) aufweisen, falsche Ergebnisse zurück.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, definieren Sie bei Enumerationen ohne Flags\-Attribut einen Member mit dem Wert 0 \(null\). Dies ist eine nicht unterbrechende Änderung.  Geben Sie bei Enumerationen, die einen Member mit dem Wert 0 \(null\) definieren, diesem Member den Namen "None", und löschen Sie alle übrigen Member, die einen Wert von 0 \(null\) aufweisen. Dies ist eine unterbrechende Änderung.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel nur bei Enumerationen mit dem Flags\-Attribut, die zuvor versendet wurden.  
  
## Beispiel  
 Das folgende Beispiel zeigt zwei Enumerationen, die der Regel entsprechen, und eine Enumeration, `BadTraceOptions`, die gegen die Regel verstößt.  
  
 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CPP/ca1008-enums-should-have-zero-value_1.cpp)]
 [!code-cs[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/CSharp/ca1008-enums-should-have-zero-value_1.cs)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../code-quality/codesnippet/VisualBasic/ca1008-enums-should-have-zero-value_1.vb)]  
  
## Verwandte Regeln  
 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: Enumerationswerte nicht mit "Reserviert" benennen](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: Keine Typnamen als Präfixe für Enumerationswerte verwenden](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
 [CA1028: Der Enumerationsspeicher sollte Int32 sein.](../code-quality/ca1028-enum-storage-should-be-int32.md)  
  
 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
## Siehe auch  
 <xref:System.Enum?displayProperty=fullName>
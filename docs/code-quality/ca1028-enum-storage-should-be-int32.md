---
title: "CA1028: Der Enumerationsspeicher sollte Int32 sein. | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
helpviewer_keywords: 
  - "CA1028"
  - "EnumStorageShouldBeInt32"
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA1028: Der Enumerationsspeicher sollte Int32 sein.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumStorageShouldBeInt32|  
|CheckId|CA1028|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Der zugrunde liegende Typ einer öffentlichen Enumeration ist nicht <xref:System.Int32?displayProperty=fullName>.  
  
## Regelbeschreibung  
 Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert.  Standardmäßig wird zum Speichern des konstanten Werts der <xref:System.Int32?displayProperty=fullName>\-Datentyp verwendet.  Sie können diesen zugrunde liegenden Typ zwar ändern, für die meisten Szenarien ist dies jedoch nicht notwendig oder empfehlenswert.  Es gibt keinen deutlichen Leistungszuwachs, wenn Sie einen Datentyp verwenden, der kleiner ist als <xref:System.Int32>.  Wenn Sie den Standarddatentyp nicht verwenden können, sollten Sie einen der CLS \(Common Language System\)\-kompatiblen ganzzahligen Typen wie <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32> oder <xref:System.Int64> verwenden, um sicherzustellen, dass alle Werte der Enumeration in CLS\-kompatiblen Programmiersprachen dargestellt werden können.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie <xref:System.Int32>, es sei denn, es gibt Größen\- oder Kompatibilitätsprobleme.  Verwenden Sie <xref:System.Int64> in Fällen, in denen <xref:System.Int32> zum Speichern der Werte nicht ausreicht.  Wenn zwecks Abwärtskompatibilität ein kleinerer Datentyp benötigt wird, verwenden Sie <xref:System.Byte> oder <xref:System.Int16>.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel nur dann, wenn dies aufgrund von Abwärtskompatibilitätsproblemen erforderlich ist.  In Anwendungen verursachen Verstöße gegen diese Regel normalerweise keine Probleme.  In Bibliotheken, in denen die Sprachinteroperabilität erforderlich ist, wirkt sich ein Verstoß gegen diese Regel aus Sicht des Benutzers u. U. negativ aus.  
  
## Beispiel für einen Verstoß  
  
### **Beschreibung**  
 Im folgenden Beispiel werden zwei Enumerationen dargestellt, in denen der empfohlene zugrunde liegende Datentyp nicht verwendet wird.  
  
### Code  
 [!code-vb[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_1.vb)]
 [!code-cs[FxCop.Design.EnumIntegralType#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_1.cs)]  
  
## Beispiel für die Behandlung  
  
### **Beschreibung**  
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem der zugrunde liegende Datentyp in <xref:System.Int32> geändert wird.  
  
### Code  
 [!code-cs[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/CSharp/ca1028-enum-storage-should-be-int32_2.cs)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../code-quality/codesnippet/VisualBasic/ca1028-enum-storage-should-be-int32_2.vb)]  
  
## Verwandte Regeln  
 [CA1008: Enumerationen müssen einen Wert von 0 \(null\) aufweisen](../code-quality/ca1008-enums-should-have-zero-value.md)  
  
 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
 [CA1700: Enumerationswerte nicht mit "Reserviert" benennen](../code-quality/ca1700-do-not-name-enum-values-reserved.md)  
  
 [CA1712: Keine Typnamen als Präfixe für Enumerationswerte verwenden](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)  
  
## Siehe auch  
 <xref:System.Byte?displayProperty=fullName>   
 <xref:System.Int16?displayProperty=fullName>   
 <xref:System.Int32?displayProperty=fullName>   
 <xref:System.Int64?displayProperty=fullName>
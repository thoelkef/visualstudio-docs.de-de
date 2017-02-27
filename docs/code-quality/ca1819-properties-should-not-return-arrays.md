---
title: "CA1819: Eigenschaften sollten keine Arrays zur&#252;ckgeben | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
helpviewer_keywords: 
  - "PropertiesShouldNotReturnArrays"
  - "CA1819"
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 22
---
# CA1819: Eigenschaften sollten keine Arrays zur&#252;ckgeben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertiesShouldNotReturnArrays|  
|CheckId|CA1819|  
|Kategorie \(Category\)|Microsoft.Performance|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine öffentliche oder geschützte Eigenschaft in einem öffentlichen Typ gibt ein Array zurück.  
  
## Regelbeschreibung  
 Von Eigenschaften zurückgegebene Arrays sind nicht schreibgeschützt, auch wenn die Eigenschaft schreibgeschützt ist.  Damit das Array gegen Manipulationen geschützt bleibt, muss die Eigenschaft eine Kopie des Arrays zurückgeben.  Normalerweise verstehen die Benutzer nicht, welche negativen Auswirkungen der Aufruf einer solchen Eigenschaft auf die Leistung hat.  Insbesondere könnten sie die Eigenschaft als indizierte Eigenschaft verwenden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, wandeln Sie die Eigenschaft entweder in eine Methode um oder ändern die Eigenschaft, so dass sie eine Auflistung zurückgibt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Attribute können Eigenschaften enthalten, die Arrays zurückgeben, aber können keine Eigenschaften enthalten, die Auflistungen zurückgeben.  Sie können eine Warnung unterdrücken, die für eine Eigenschaft eines Attributs ausgelöst wird, das von der [System.Attribute](assetId:///System.Attribute?qualifyHint=False&autoUpgrade=True)\-Klasse abgeleitet wird.  Unterdrücken Sie andernfalls keine Warnung dieser Regel.  
  
## Beispiel für einen Verstoß  
  
### **Beschreibung**  
 Im folgenden Beispiel wird eine Eigenschaft veranschaulicht, die gegen diese Regel verstößt.  
  
### Code  
 [!code-cs[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]  
  
### Kommentare  
 Um einen Verstoß gegen diese Regel zu beheben, wandeln Sie die Eigenschaft entweder in eine Methode um oder ändern die Eigenschaft, so dass sie anstelle eines Arrays eine Auflistung zurückgibt.  
  
## Ändern der Eigenschaft in ein Methodenbeispiel  
  
### **Beschreibung**  
 Im folgenden Beispiel wird der Verstoß korrigiert, indem die Eigenschaft in eine Methode geändert wird.  
  
### Code  
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-cs[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]  
  
## Zurückgeben eines Auflistungsbeispiels  
  
### **Beschreibung**  
 Im folgenden Beispiel wird der Verstoß korrigiert, indem die Eigenschaft geändert wird, sodass folgender Wert zurückgegeben wird:  
  
 <xref:System.Collection.ObjectModel.ReadOnlyCollection?displayProperty=fullName>.  
  
### Code  
 [!code-cs[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]  
  
## Zulassen der Änderung von Eigenschaften durch Benutzer  
  
### **Beschreibung**  
 Sie möchten es dem Consumer der Klasse ermöglichen, eine Eigenschaft zu ändern.  Im folgenden Beispiel wird eine Eigenschaft mit Lese\-\/Schreibzugriff veranschaulicht, die gegen diese Regel verstößt.  
  
### Code  
 [!code-cs[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]  
  
### Kommentare  
 Im folgenden Beispiel wird der Verstoß korrigiert, indem die Eigenschaft so geändert wird, dass sie <xref:System.Collection.ObjectModel.Collection?displayProperty=fullName> zurückgibt.  
  
### Code  
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-cs[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]  
  
## Verwandte Regeln  
 [CA1024: Nach Möglichkeit Eigenschaften verwenden](../code-quality/ca1024-use-properties-where-appropriate.md)
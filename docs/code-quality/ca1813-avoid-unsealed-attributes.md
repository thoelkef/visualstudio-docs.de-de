---
title: "CA1813: Nicht versiegelte Attribute vermeiden | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1813"
  - "AvoidUnsealedAttributes"
helpviewer_keywords: 
  - "AvoidUnsealedAttributes"
  - "CA1813"
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1813: Nicht versiegelte Attribute vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidUnsealedAttributes|  
|CheckId|CA1813|  
|Kategorie \(Category\)|Microsoft.Performance|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentlicher Typ, der von <xref:System.Attribute?displayProperty=fullName> erbt, ist nicht abstrakt und nicht versiegelt \( in Visual Basic `NotInheritable`\).  
  
## Regelbeschreibung  
 Die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]\-Klassenbibliothek stellt Methoden zum Abrufen benutzerdefinierter Attribute bereit.  Standardmäßig durchsucht diese Methode die Vererbungshierarchie des Attributs. Beispielsweise sucht <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> nach dem angegebenen Attributtyp oder nach einem Attributtyp, der den angegebenen Attributtyp erweitert.  Durch die Verwendung eines versiegelten Attributs wird das Durchsuchen der Vererbungshierarchie unterbunden und die Leistung u. U. verbessert.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, deklarieren Sie den Attributtyp als sealed oder abstract.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Warnungen dieser Regel können gefahrlos unterdrückt werden.  Sie sollten dies aber nur tun, wenn Sie eine Attributhierarchie definieren und das Attribut weder als sealed noch als abstract deklarieren können.  
  
## Beispiel  
 Im folgenden Beispiel wird ein benutzerdefiniertes Attribut veranschaulicht, das der Regel entspricht.  
  
 [!code-cs[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
 [!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]  
  
## Verwandte Regeln  
 [CA1019: Accessors für Attributargumente definieren](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1018: Attribute mit AttributeUsageAttribute markieren](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)  
  
## Siehe auch  
 [Attribute](../Topic/Attributes1.md)
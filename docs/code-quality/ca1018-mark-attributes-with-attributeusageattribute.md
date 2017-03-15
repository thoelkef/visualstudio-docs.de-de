---
title: "CA1018: Attribute mit AttributeUsageAttribute markieren | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
helpviewer_keywords: 
  - "CA1018"
  - "MarkAttributesWithAttributeUsage"
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1018: Attribute mit AttributeUsageAttribute markieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAttributesWithAttributeUsage|  
|CheckId|CA1018|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Das <xref:System.AttributeUsageAttribute?displayProperty=fullName>\-Attribut ist im benutzerdefinierten Attribut nicht vorhanden.  
  
## Regelbeschreibung  
 Wenn Sie ein benutzerdefiniertes Attribut definieren, markieren Sie es mithilfe von <xref:System.AttributeUsageAttribute>, um anzugeben, an welcher Stelle im Quellcode das benutzerdefinierte Attribut angewendet werden kann.  Die Bedeutung und die beabsichtigte Verwendung eines Attributs bestimmen die gültigen Positionen des Attributs im Code.  Sie könnten z. B. ein Attribut definieren, das die Person identifiziert, die für das Beibehalten und Verbessern jedes Typs in einer Bibliothek zuständig ist, und diese Verantwortung wird immer auf Typebene zugewiesen.  In diesem Fall sollten Compiler das Attribut bei Klassen, Enumerationen und Schnittstellen aktivieren, nicht aber bei Methoden, Ereignissen oder Eigenschaften.  Ob das Attribut in Assemblys aktiviert werden sollte, würde dann von Organisationsrichtlinien und Prozeduren bestimmt.  
  
 Die <xref:System.AttributeTargets?displayProperty=fullName>\-Enumeration definiert die Ziele, die Sie für ein benutzerdefiniertes Attribut angeben können.  Wenn Sie <xref:System.AttributeUsageAttribute> weglassen, ist das benutzerdefinierte Attribut für alle Ziele gültig, wie vom `All`\-Wert der <xref:System.AttributeTargets>\-Enumeration definiert.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, geben Sie Ziele für das Attribut mithilfe von <xref:System.AttributeUsageAttribute> an.  \(Siehe nachstehendes Beispiel.\)  
  
## Wann sollten Warnungen unterdrückt werden?  
 Sie sollten einen Verstoß gegen diese Regel beheben, anstatt die Meldung auszuschließen.  Auch wenn das Attribut <xref:System.AttributeUsageAttribute> erbt, sollte es vorhanden sein, da dadurch die Codewartung vereinfacht wird.  
  
## Beispiel  
 Im folgenden Beispiel werden zwei Attribute definiert.  `BadCodeMaintainerAttribute` lässt die <xref:System.AttributeUsageAttribute>\-Anweisung fälschlicherweise weg, und `GoodCodeMaintainerAttribute` implementiert korrekterweise das Attribut, das in diesem Abschnitt früher beschrieben wurde.  Beachten Sie, dass die `DeveloperName`\-Eigenschaft von der Entwurfsregel [CA1019: Accessors für Attributargumente definieren](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) benötigt wird und der Vollständigkeit halber eingefügt wird.  
  
 [!code-cs[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]  
  
## Verwandte Regeln  
 [CA1019: Accessors für Attributargumente definieren](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)  
  
 [CA1813: Nicht versiegelte Attribute vermeiden](../code-quality/ca1813-avoid-unsealed-attributes.md)  
  
## Siehe auch  
 [Attribute](../Topic/Attributes1.md)
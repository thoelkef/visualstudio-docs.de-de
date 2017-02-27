---
title: "CA1041: ObsoleteAttribute-Meldung bereitstellen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1041"
  - "ProvideObsoleteAttributeMessage"
helpviewer_keywords: 
  - "ProvideObsoleteAttributeMessage"
  - "CA1041"
ms.assetid: be5bee69-d2d2-44e1-be2e-3ea451969003
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1041: ObsoleteAttribute-Meldung bereitstellen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ProvideObsoleteAttributeMessage|  
|CheckId|CA1041|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ oder Member ist durch ein <xref:System.ObsoleteAttribute?displayProperty=fullName>\-Attribut markiert, dessen <xref:System.ObsoleteAttribute.Message%2A?displayProperty=fullName>\-Eigenschaft nicht festgelegt wurde.  
  
## Regelbeschreibung  
 <xref:System.ObsoleteAttribute> wird verwendet, um veraltete Bibliothekstypen und Member zu markieren.  Bibliotheksconsumer sollten die Verwendung von Typen oder Membern vermeiden, die als veraltet markiert sind.  Das liegt daran, dass es eventuell nicht unterstützt und in späteren Versionen der Bibliothek möglicherweise nicht mehr enthalten sein wird.  Wenn ein Typ oder ein Member, der mit <xref:System.ObsoleteAttribute> markiert wurde, kompiliert wird, wird die <xref:System.ObsoleteAttribute.Message%2A>\-Eigenschaft des Attributs angezeigt.  Auf diese Weise erhält der Benutzer Informationen zum veralteten Typ oder Member.  Diese Informationen enthalten im Allgemeinen Angaben darüber, wie lange der veraltete Typ oder Member von den Bibliotheksentwicklern noch unterstützt wird und durch welches Element er ersetzt werden soll.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie den `message`\-Parameter dem <xref:System.ObsoleteAttribute>\-Konstruktor hinzu.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel, da die <xref:System.ObsoleteAttribute.Message%2A>\-Eigenschaft wichtige Informationen über den veralteten Typ oder Member bereitstellt.  
  
## Beispiel  
 Im folgenden Beispiel wird ein veralteter Member veranschaulicht, der über einen ordnungsgemäß deklarierten <xref:System.ObsoleteAttribute> verfügt.  
  
 [!code-cpp[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CPP/ca1041-provide-obsoleteattribute-message_1.cpp)]
 [!code-cs[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/CSharp/ca1041-provide-obsoleteattribute-message_1.cs)]
 [!code-vb[FxCop.Design.ObsoleteAttributeOnMember#1](../code-quality/codesnippet/VisualBasic/ca1041-provide-obsoleteattribute-message_1.vb)]  
  
## Siehe auch  
 <xref:System.ObsoleteAttribute?displayProperty=fullName>
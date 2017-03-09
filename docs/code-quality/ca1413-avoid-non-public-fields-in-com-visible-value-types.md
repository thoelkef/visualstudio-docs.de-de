---
title: "CA1413: Nicht &#246;ffentliche Felder in f&#252;r COM sichtbaren Werttypen vermeiden | Microsoft Docs"
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
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
helpviewer_keywords: 
  - "CA1413"
  - "AvoidNonpublicFieldsInComVisibleValueTypes"
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1413: Nicht &#246;ffentliche Felder in f&#252;r COM sichtbaren Werttypen vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidNonpublicFieldsInComVisibleValueTypes|  
|CheckId|CA1413|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Werttyp, der ausdrücklich als für Component Object Model \(COM\) sichtbar markiert ist, deklariert ein nicht öffentliches Instanzfeld.  
  
## Regelbeschreibung  
 Nicht öffentliche Instanzenfelder von COM\-sichtbaren Werttypen sind für COM\-Clients sichtbar.  Überprüfen Sie den Inhalt des Felds auf Informationen, die nicht verfügbar gemacht werden sollen oder unbeabsichtigte Auswirkungen auf Design oder Sicherheit haben.  
  
 Standardmäßig sind alle öffentlichen Werttypen für COM sichtbar.  Um falsche Positive zu reduzieren, erfordert diese Regel jedoch die COM\-Sichtbarkeit des Typs, der explizit angegeben werden soll.  Die enthaltende Assembly muss mit einem <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> markiert werden, das auf `false` festgelegt ist. Der Typ muss mit einem <xref:System.Runtime.InteropServices.ComVisibleAttribute> markiert werden, das auf `true` festgelegt ist.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben und dafür zu sorgen, dass das Feld ausgeblendet bleibt, ändern Sie den Werttyp für einen Verweistyp oder entfernen das <xref:System.Runtime.InteropServices.ComVisibleAttribute>\-Attribut von dem Typ.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Warnungen dieser Regel können gefahrlos unterdrückt werden, wenn das öffentliche Verfügbarmachen des Feldes zulässig ist.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen die Regel verstößt.  
  
 [!code-cs[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
 [!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]  
  
## Verwandte Regeln  
 [CA1407: Statische Member in für COM sichtbaren Typen vermeiden](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)  
  
 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Siehe auch  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)
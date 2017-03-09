---
title: "CA1405: F&#252;r COM sichtbare Basistypen sollten f&#252;r COM sichtbar sein | Microsoft Docs"
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
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
helpviewer_keywords: 
  - "CA1405"
  - "ComVisibleTypeBaseTypesShouldBeComVisible"
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1405: F&#252;r COM sichtbare Basistypen sollten f&#252;r COM sichtbar sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComVisibleTypeBaseTypesShouldBeComVisible|  
|CheckId|CA1405|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|DependsOnFix|  
  
## Ursache  
 Ein sichtbarer Component Object Model \(COM\)\-Typ leitet sich von einem Typ ab, der nicht für COM sichtbar ist.  
  
## Regelbeschreibung  
 Wenn ein für COM sichtbarer Typ Member in einer neuen Version hinzufügt, muss er sich an strenge Richtlinien halten, damit COM\-Clients, die an die aktuelle Version gebunden sind, die Verbindung nicht abbrechen.  Bei einem Typ, der für COM nicht sichtbar ist, wird davon ausgegangen, dass er diese COM\-Versionsregeln nicht einhalten muss, wenn er neue Member hinzufügt.  Wenn jedoch ein für COM sichtbarer Typ von dem für COM nicht sichtbaren Typ abgeleitet wird und eine Klassenschnittstelle von <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> oder <xref:System.Runtime.InteropServices.ClassInterfaceType> \(Standard\) verfügbar macht, werden alle öffentlichen Member des Basistyps für COM verfügbar gemacht, sofern sie nicht als für COM nicht sichtbar markiert sind. Dies wäre allerdings redundant.  Wenn der Basistyp in einer späteren Version neue Member hinzufügt, unterbrechen möglicherweise sämtliche COM\-Clients, die an die Klassenschnittstelle des abgeleiteten Typs gebunden sind, die Verbindung.  Für COM sichtbare Typen sollten nur von für COM sichtbaren Typen abgeleitet werden, um die Wahrscheinlichkeit einer Verbindungsunterbrechung zu reduzieren.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, machen Sie die Basistypen für COM sichtbar oder den abgeleiteten Typ für COM unsichtbar.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen die Regel verstößt.  
  
 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-cs[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]  
  
## Siehe auch  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>   
 [Introducing the Class Interface](http://msdn.microsoft.com/de-de/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)
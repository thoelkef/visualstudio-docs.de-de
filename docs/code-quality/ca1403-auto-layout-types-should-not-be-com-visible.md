---
title: "CA1403: Typen mit automatischem Layout sollten nicht f&#252;r COM sichtbar sein | Microsoft Docs"
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
  - "AutoLayoutTypesShouldNotBeComVisible"
  - "CA1403"
helpviewer_keywords: 
  - "CA1403"
  - "AutoLayoutTypesShouldNotBeComVisible"
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1403: Typen mit automatischem Layout sollten nicht f&#252;r COM sichtbar sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AutoLayoutTypesShouldNotBeComVisible|  
|CheckId|CA1403|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein sichtbarer Component Object Model \(COM\)\-Werttyp wird mit dem auf <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName> festgelegten <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName>\-Attribut markiert.  
  
## Regelbeschreibung  
 <xref:System.Runtime.InteropServices.LayoutKind>\-Layouttypen werden von der Common Language Runtime verwaltet.  Das Layout dieser Typen kann zwischen den verschiedenen .NET Framework\-Versionen voneinander abweichen, wodurch die Verbindung zu COM\-Clients unterbrochen wird, die ein bestimmtes Layout erwarten.  Wenn das <xref:System.Runtime.InteropServices.StructLayoutAttribute>\-Attribut nicht angegeben ist, legen der C\#\-, der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\- und der C\+\+\-Compiler das <xref:System.Runtime.InteropServices.LayoutKind>\-Layout für Werttypen fest.  
  
 Sofern nicht anders markiert, sind alle öffentlichen, nicht generischen Typen für COM sichtbar; alle nicht öffentlichen, generischen Typen sind für COM nicht sichtbar.  Um jedoch die Anzahl falscher positiver Ergebnisse zu verringern, muss entsprechend der Regel die COM\-Sichtbarkeit des Typs explizit angegeben werden, die enthaltende Assembly muss mit dem auf `false` festgelegten <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>\-Attribut markiert sein, und der Typ muss mit dem auf `true` festgelegten <xref:System.Runtime.InteropServices.ComVisibleAttribute>\-Attribut markiert sein.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Wert des <xref:System.Runtime.InteropServices.StructLayoutAttribute>\-Attributs in <xref:System.Runtime.InteropServices.LayoutKind> oder <xref:System.Runtime.InteropServices.LayoutKind>, oder machen Sie den Typ für COM unsichtbar.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Das folgende Beispiel zeigt einen Typ, der gegen die Regel verstößt, und einen Typ, der der Regel entspricht.  
  
 [!code-cs[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]  
  
## Verwandte Regeln  
 [CA1408: AutoDual ClassInterfaceType nicht verwenden](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## Siehe auch  
 [Introducing the Class Interface](http://msdn.microsoft.com/de-de/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)
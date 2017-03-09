---
title: "CA1017: Assemblys mit ComVisibleAttribute markieren | Microsoft Docs"
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
  - "CA1017"
  - "MarkAssembliesWithComVisible"
helpviewer_keywords: 
  - "MarkAssembliesWithComVisible"
  - "CA1017"
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1017: Assemblys mit ComVisibleAttribute markieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkAssembliesWithComVisible|  
|CheckId|CA1017|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Auf eine Assembly wird das <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName>\-Attribut nicht angewendet.  
  
## Regelbeschreibung  
 Das <xref:System.Runtime.InteropServices.ComVisibleAttribute>\-Attribut bestimmt, wie COM\-Clients auf verwalteten Code zugreifen.  Gute Entwurfsprinzipien verlangen, dass die COM\-Sichtbarkeit durch Assemblys explizit angegeben wird.  Die COM\-Sichtbarkeit kann für eine gesamte Assembly festgelegt und anschließend für einzelne Typen und Typmember überschrieben werden.  Wenn das Attribut fehlt, ist der Inhalt der Assembly für COM\-Clients sichtbar.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der Assembly das Attribut hinzu.  Wenn die Assembly für COM\-Clients nicht sichtbar sein soll, wenden Sie das Attribut an, und legen Sie seinen Wert auf `false` fest.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Wenn die Assembly sichtbar sein soll, wenden Sie das Attribut an, und legen Sie seinen Wert auf `true` fest.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Assembly mit dem <xref:System.Runtime.InteropServices.ComVisibleAttribute>\-Attribut, das verhindert, dass die Assembly für COM\-Clients sichtbar ist.  
  
 [!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
 [!code-cs[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]  
  
## Siehe auch  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)   
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)
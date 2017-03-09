---
title: "CA2215: Dispose-Methoden m&#252;ssen die Dispose-Funktion der Basisklasse aufrufen | Microsoft Docs"
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
  - "CA2215"
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "Dispose methods should call base class dispose"
helpviewer_keywords: 
  - "DisposeMethodsShouldCallBaseClassDispose"
  - "CA2215"
ms.assetid: c772e7a6-a87e-425c-a70e-912664ae9042
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2215: Dispose-Methoden m&#252;ssen die Dispose-Funktion der Basisklasse aufrufen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeMethodsShouldCallBaseClassDispose|  
|CheckId|CA2215|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ, der <xref:System.IDisposable?displayProperty=fullName> implementiert, erbt von einem Typ, der auch <xref:System.IDisposable> implementiert.  Die <xref:System.IDisposable.Dispose%2A>\-Methode des erbenden Typs ruft die <xref:System.IDisposable.Dispose%2A>\-Methode des übergeordneten Typs nicht auf.  
  
## Regelbeschreibung  
 Wenn ein Typ von einem verwerfbaren Typ erbt, muss in seiner <xref:System.IDisposable.Dispose%2A>\-Methode die <xref:System.IDisposable.Dispose%2A>\-Methode des Basistyps aufgerufen werden.  Die Basistypmethode "Dispose" zu nennen stellt sicher, dass alle vom Basistyp erstellten Ressourcen freigegeben werden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie `base`.<xref:System.IDisposable.Dispose%2A> in der <xref:System.IDisposable.Dispose%2A>\-Methode auf.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Aufruf von `base`.<xref:System.IDisposable.Dispose%2A> auf einer tieferen Aufrufebene erfolgt, die von der Regel nicht mehr überprüft wird.  
  
## Beispiel  
 Im folgenden Beispiel wird der Typ `TypeA`, der <xref:System.IDisposable> implementiert, veranschaulicht.  
  
 [!code-cs[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2215-dispose-methods-should-call-base-class-dispose_1.cs)]  
  
## Beispiel  
 Im folgenden Beispiel wird der Typ `TypeB` veranschaulicht, der vom Typ `TypeA` erbt und ordnungsgemäß dessen <xref:System.IDisposable.Dispose%2A>\-Methode aufruft.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2215-dispose-methods-should-call-base-class-dispose_2.vb)]  
  
## Siehe auch  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Dispose\-Muster](../Topic/Dispose%20Pattern.md)
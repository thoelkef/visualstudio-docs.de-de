---
title: "CA2220: Finalizer sollten Basisklassen-Finalizer aufrufen | Microsoft Docs"
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
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
helpviewer_keywords: 
  - "CA2220"
  - "FinalizersShouldCallBaseClassFinalizer"
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2220: Finalizer sollten Basisklassen-Finalizer aufrufen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FinalizersShouldCallBaseClassFinalizer|  
|CheckId|CA2220|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ, der <xref:System.Object.Finalize%2A?displayProperty=fullName> überschreibt, ruft die <xref:System.Object.Finalize%2A>\-Methode in seiner Basisklasse nicht auf.  
  
## Regelbeschreibung  
 Der Abschluss muss durch die Vererbungshierarchie weitergegeben werden.  Um dies sicherzustellen, müssen die Typen die <xref:System.Object.Finalize%2A>\-Methode ihrer Basisklasse innerhalb ihrer eigenen <xref:System.Object.Finalize%2A>\-Methode aufrufen.  Der C\#\-Compiler fügt den Aufruf automatisch dem Basisklassenfinalizer hinzu.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie die <xref:System.Object.Finalize%2A>\-Methode des Basistyps in der <xref:System.Object.Finalize%2A>\-Methode auf.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Einige Compiler, die auf die Common Language Runtime abzielen, fügen in die Microsoft Intermediate Language \(MSIL\) einen Aufruf des Finalizers des Basistyps ein.  Wenn eine Warnung dieser Regel gemeldet wird, fügt der Compiler den Aufruf nicht ein, sodass Sie ihn in Ihren Code einfügen müssen.  
  
## Beispiel  
 Das folgende Visual Basic\-Beispiel zeigt den Typ `TypeB`, durch den die <xref:System.Object.Finalize%2A>\-Methode in seiner Basisklasse ordnungsgemäß aufgerufen wird.  
  
 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../code-quality/codesnippet/VisualBasic/ca2220-finalizers-should-call-base-class-finalizer_1.vb)]  
  
## Siehe auch  
 [Dispose\-Muster](../Topic/Dispose%20Pattern.md)
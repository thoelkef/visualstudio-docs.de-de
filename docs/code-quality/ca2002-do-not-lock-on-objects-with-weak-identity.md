---
title: "CA2002: Auf Objekten mit schwacher Identit&#228;t nicht sperren | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotLockOnObjectsWithWeakIdentity"
  - "CA2002"
helpviewer_keywords: 
  - "CA2002"
  - "DoNotLockOnObjectsWithWeakIdentity"
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2002: Auf Objekten mit schwacher Identit&#228;t nicht sperren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotLockOnObjectsWithWeakIdentity|  
|CheckId|CA2002|  
|Kategorie \(Category\)|Microsoft.Reliability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Thread versucht, eine Sperre für ein Objekt zu erhalten, das eine schwache Identität aufweist.  
  
## Regelbeschreibung  
 Ein Objekt hat eine schwache Identität, wenn ein Zugriff darauf über Grenzen von Anwendungsdomänen hinweg möglich ist.  Ein Thread, der eine Sperre für ein Objekt zu erhalten versucht, das über eine schwache Identität verfügt, kann durch einen zweiten Thread in einer anderen Anwendungsdomäne blockiert werden, der eine Sperre für das gleiche Objekt besitzt.  Die folgenden Typen haben eine schwache Identität und werden durch die Regel gekennzeichnet:  
  
-   <xref:System.MarshalByRefObject>  
  
-   <xref:System.ExecutionEngineException>  
  
-   <xref:System.OutOfMemoryException>  
  
-   <xref:System.StackOverflowException>  
  
-   <xref:System.String>  
  
-   <xref:System.Reflection.MemberInfo>  
  
-   <xref:System.Reflection.ParameterInfo>  
  
-   <xref:System.Threading.Thread>  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie ein Objekt eines Typs, der nicht in der Liste im Abschnitt Beschreibung enthalten ist.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Verwandte Regeln  
 [CA2213: Verwerfbare Felder verwerfen](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
## Beispiel  
 Im folgenden Beispiel werden einige Objektsperren veranschaulicht, die gegen die Regel verstoßen.  
  
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
 [!code-cs[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]  
  
## Siehe auch  
 <xref:System.Threading.Monitor>   
 <xref:System.AppDomain>   
 [lock\-Anweisung](/dotnet/csharp/language-reference/keywords/lock-statement)   
 [SyncLock Statement](/dotnet/visual-basic/language-reference/statements/synclock-statement)
---
title: "CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren | Microsoft Docs"
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
  - "DisposableTypesShouldDeclareFinalizer"
  - "CA2216"
helpviewer_keywords: 
  - "CA2216"
  - "DisposableTypesShouldDeclareFinalizer"
ms.assetid: 0cabcc5e-b526-452b-8c2a-0cbe3b93c0ef
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2216: Verwerfbare Typen sollten einen Finalizer deklarieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposableTypesShouldDeclareFinalizer|  
|CheckId|CA2216|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ, der <xref:System.IDisposable?displayProperty=fullName> implementiert und Felder besitzt, bei denen die Verwendung nicht verwalteter Ressourcen empfohlen wird, implementiert keinen Finalizer wie von <xref:System.Object.Finalize%2A?displayProperty=fullName> beschrieben.  
  
## Regelbeschreibung  
 Ein Verstoß gegen diese Regel wird gemeldet, wenn der verwerfbare Typ Felder folgender Typen enthält:  
  
-   <xref:System.IntPtr?displayProperty=fullName>  
  
-   <xref:System.UIntPtr?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie einen Finalizer, der die <xref:System.IDisposable.Dispose%2A>\-Methode aufruft.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Typ nicht <xref:System.IDisposable> implementiert, um nicht verwaltete Ressourcen freizugeben.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen diese Regel verstößt.  
  
 [!code-cs[FxCop.Usage.DisposeNoFinalize#1](../code-quality/codesnippet/CSharp/ca2216-disposable-types-should-declare-finalizer_1.cs)]  
  
## Verwandte Regeln  
 [CA2115: GC.KeepAlive beim Verwenden systemeigener Ressourcen aufrufen](../code-quality/ca2115-call-gc-keepalive-when-using-native-resources.md)  
  
 [CA1816: GC.SuppressFinalize korrekt aufrufen](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)  
  
 [CA1049: Typen, die systemeigene Ressourcen besitzen, müssen gelöscht werden können](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)  
  
## Siehe auch  
 <xref:System.IDisposable?displayProperty=fullName>   
 <xref:System.IntPtr?displayProperty=fullName>   
 <xref:System.Runtime.InteropServices.HandleRef?displayProperty=fullName>   
 <xref:System.UIntPtr?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [Dispose\-Muster](../Topic/Dispose%20Pattern.md)
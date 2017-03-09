---
title: "CA2213: Verwerfbare Felder verwerfen | Microsoft Docs"
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
  - "DisposableFieldsShouldBeDisposed"
  - "CA2213"
helpviewer_keywords: 
  - "CA2213"
  - "DisposableFieldsShouldBeDisposed"
ms.assetid: e99442c9-70e2-47f3-b61a-d8ac003bc6e5
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2213: Verwerfbare Felder verwerfen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposableFieldsShouldBeDisposed|  
|CheckId|CA2213|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ, der <xref:System.IDisposable?displayProperty=fullName> implementiert, deklariert Felder, die Typen aufweisen, die ebenfalls <xref:System.IDisposable> implementieren.  Die <xref:System.IDisposable.Dispose%2A>\-Methode des Felds wird nicht von der <xref:System.IDisposable.Dispose%2A>\-Methode des deklarierenden Typs aufgerufen.  
  
## Regelbeschreibung  
 Ein Typ muss all seine nicht verwalteten Ressourcen freigeben \(verwerfen\). Dies wird durch die Implementierung von <xref:System.IDisposable> erreicht.  Mit dieser Regel wird überprüft, ob ein verwerfbarer Typ `T` ein Feld `F` deklariert, das eine Instanz eines verwerfbaren Typs `FT` ist.  Für jedes Feld `F` versucht die Regel, einen Aufruf von `FT.Dispose` zu finden.  Die Regel durchsucht die von `T.Dispose` aufgerufenen Methoden und die Ebene darunter \(also die Methoden, die von `FT.Dispose` aufgerufen wurden\).  
  
## Behandeln von Verstößen  
 Wenn Sie für die Zuordnung und Freigabe der im Feld gespeicherten nicht verwalteten Ressourcen zuständig sind, beheben Sie einen Verstoß gegen diese Regel, indem Sie <xref:System.IDisposable.Dispose%2A> für Felder aufrufen, die typbedingt <xref:System.IDisposable> implementieren.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn Sie nicht für die Freigabe der Ressourcen verantwortlich sind, die im Feld gespeichert sind, oder wenn der Aufruf von <xref:System.IDisposable.Dispose%2A> in einer Ebene unterhalb der Regelüberprüfung erfolgt.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ gezeigt \(`TypeA`\), der <xref:System.IDisposable> \(`FT` im vorherigen Beispiel\) implementiert.  
  
 [!code-cs[FxCop.Usage.IDisposablePattern#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_1.cs)]  
  
## Beispiel  
 Im folgenden Beispiel verstößt ein Typ \(`TypeB`\) gegen diese Regel, da ein Feld `aFieldOfADisposableType` \(`F` in der vorherigen Diskussion\) als verwerfbarer Typ \(`TypeA`\) deklariert und <xref:System.IDisposable.Dispose%2A> im Feld nicht aufgerufen wird.  `TypeB` entspricht `T` in der vorherigen Diskussion.  
  
 [!code-cs[FxCop.Usage.IDisposableFields#1](../code-quality/codesnippet/CSharp/ca2213-disposable-fields-should-be-disposed_2.cs)]  
  
## Siehe auch  
 <xref:System.IDisposable?displayProperty=fullName>   
 [Dispose\-Muster](../Topic/Dispose%20Pattern.md)
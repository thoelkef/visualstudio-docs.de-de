---
title: "Compilerfehler CS0462 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0462"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0462"
ms.assetid: 0732b12d-0f7a-47d5-bc54-8b6147d7249f
caps.latest.revision: 16
caps.handback.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0462
Die geerbten Member "Member1" und "Member2" haben die gleiche Signatur im Typ "Typ" und können daher nicht überschrieben werden  
  
 Dieser Fehler entsteht bei der Einführung generischer Methoden. In der Regel können in einer Klasse mit derselben Signatur nicht zwei Versionen einer Methode vorhanden sein. Bei Generika können Sie jedoch eine generische Methode angeben, die möglicherweise eine andere Methode dupliziert, wenn sie mit einem bestimmten Typ instanziiert wird.  
  
## Beispiel  
 Beim Instanziieren von `C<int>` werden zwei Versionen der `F`\-Methode mit derselben Signatur erstellt, sodass beim Überschreiben in der `D`\-Klasse keine Entscheidung getroffen werden kann, welche Version überschrieben werden soll.  
  
 Im folgenden Beispiel wird CS0462 generiert.  
  
```  
// CS0462.cs // compile with: /target:library class C<T> { public virtual void F(T t) {} public virtual void F(int t) {} } class D : C<int> { public override void F(int t) {}   // CS0462 }  
```
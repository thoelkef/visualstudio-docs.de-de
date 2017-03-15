---
title: "Compilerwarnung (Stufe 3) CS0414 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0414"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0414"
ms.assetid: 6a0a80be-799b-4d9c-a7e0-6b91e9ce7be0
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 3) CS0414
Dem privaten Feld "Feld" wurde ein Wert zugewiesen, der aber nie verwendet wird.  
  
 Diese Warnung kann in verschiedenen Szenarien auftreten, in denen der Compiler feststellen kann, dass nie auf eine Variable verwiesen wird:  
  
-   Einem privaten Feld wurde ein konstanter Wert zugewiesen, das Feld wird nachfolgend aber nie gelesen. Die unnötige Zuweisung kann die Leistung beeinträchtigen. Sie sollten das Feld u. U. entfernen.  
  
-   Einem privaten oder internen statischen Feld wird nur im Initialisierer ein konstanter Wert zugewiesen. Sie sollten das Feld u. U. in "const" ändern.  
  
-   Einem privaten oder internen Feld werden konstante Werte zugewiesen, und es wird nur in Blöcken verwendet, die durch \#ifdef\-Direktiven ausgeschlossen werden. Sie sollten das Feld u. U. innerhalb des \#ifdef\-Blocks platzieren.  
  
-   Einem privaten oder internen Feld werden an mehreren Stellen konstante Werte zugewiesen, ohne dass ansonsten darauf zugegriffen wird. Wenn Sie das Feld nicht benötigen, sollten Sie es u. U. entfernen. Verwenden Sie es andernfalls in einer geeigneten Weise.  
  
 Verwenden Sie in anderen Situationen oder, wenn die vorgeschlagene Problemumgehung nicht akzeptabel ist, \#pragma 0414.  
  
 Das folgende Beispiel zeigt einen Fall, in dem CS0414 generiert wird:  
  
```  
// CS0414 // compile with: /W3 class C { private int i = 1;  // CS0414 public static void Main() { } }  
```  
  
 **Hinweis** Wenn die Variable `i` als `protected or public` deklariert wird, wird kein Fehler generiert, da der Compiler nicht wissen kann, ob sie von einer abgeleiteten Klasse verwendet wird oder ob die Klasse durch anderen Clientcode instanziiert wird und im Code auf die Variable verwiesen wird.  
  
## Siehe auch  
 [C\# Compiler Errors](/dotnet/csharp/language-reference/compiler-messages/index)   
 [C\# Compiler Options](/dotnet/csharp/language-reference/compiler-options/index)
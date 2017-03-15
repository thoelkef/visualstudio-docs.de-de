---
title: "Compilerfehler CS0666 | Microsoft Docs"
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
  - "CS0666"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0666"
ms.assetid: 44ad4574-b4a2-487b-8d05-0116762231ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0666
'Member': In der Struktur wurde ein neuer geschützter Member deklariert.  
  
 Eine [Struktur](/dotnet/csharp/language-reference/keywords/struct) kann nicht [abstrakt](/dotnet/csharp/language-reference/keywords/abstract) sein und ist immer implizit [versiegelt](/dotnet/csharp/language-reference/keywords/sealed). Da Strukturen keine Vererbung unterstützen, ist das Konzept eines [geschützten](/dotnet/csharp/language-reference/keywords/protected) Member in einer Struktur nicht sinnvoll. Weitere Informationen finden Sie unter [Vererbung](/dotnet/csharp/programming-guide/classes-and-structs/inheritance).  
  
## Beispiel  
 Im folgenden Beispiel wird CS0666 generiert:  
  
```  
// CS0666.cs class M { static void Main() { } } struct S { protected int x;   // CS0666 }  
```
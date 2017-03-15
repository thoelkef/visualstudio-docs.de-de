---
title: "Compilerfehler CS0215 | Microsoft Docs"
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
  - "CS0215"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0215"
ms.assetid: 2060440d-be22-4c10-8b26-43b08b615447
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0215
Der Rückgabetyp des True\- oder False\-Operators muss boolesch sein.  
  
 Benutzerdefinierte [true](/dotnet/csharp/language-reference/keywords/true)\- und [false](/dotnet/csharp/language-reference/keywords/false)\-Operatoren müssen den Rückgabetyp [bool](/dotnet/csharp/language-reference/keywords/bool) aufweisen. Weitere Informationen finden Sie unter [Überladbare Operatoren](/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators).  
  
 Im folgenden Beispiel wird CS0215 generiert:  
  
```  
// CS0215.cs class MyClass { public static int operator true (MyClass MyInt)   // CS0215 // try the following line instead // public static bool operator true (MyClass MyInt) { return true; } public static int operator false (MyClass MyInt)   // CS0215 // try the following line instead // public static bool operator false (MyClass MyInt) { return true; } public static void Main() { } }  
```
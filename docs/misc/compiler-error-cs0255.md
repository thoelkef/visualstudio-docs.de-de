---
title: "Compilerfehler CS0255 | Microsoft Docs"
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
  - "CS0255"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0255"
ms.assetid: b45f5d5a-1923-4fe1-a858-e5ef5590a108
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0255
"stackalloc" darf nicht in einem catch\- oder finally\-Block verwendet werden.  
  
 Das [stackalloc](/dotnet/csharp/language-reference/keywords/stackalloc)\-Schlüsselwort darf nicht in einem [catch](/dotnet/csharp/language-reference/keywords/try-catch)\- oder [finally](/dotnet/csharp/language-reference/keywords/try-catch-finally)\-Block verwendet werden. Weitere Informationen finden Sie unter [Ausnahmen und Ausnahmebehandlung](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling).  
  
 Im folgenden Beispiel wird CS0255 generiert:  
  
```  
// CS0255.cs // compile with: /unsafe using System; public class TestTryFinally { public static unsafe void Test() { int i = 123; string s = "Some string"; object o = s; try { // Conversion is not valid; o contains a string not an int i = (int) o; } finally { Console.Write("i = {0}", i); int* fib = stackalloc int[100];   // CS0255 } } public static void Main() { } }  
```
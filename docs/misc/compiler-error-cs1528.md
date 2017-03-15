---
title: "Compilerfehler CS1528 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1528"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1528"
ms.assetid: 38aabc5c-b32f-4bea-a585-c4212f42751d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1528
";" oder "\=" erwartet. \(Konstruktorargumente können nicht in einer Deklaration angegeben werden.\)  
  
 Ein Verweis auf eine Klasse wurde formuliert, als ob ein Objekt der Klasse erstellt wird. Es wurde beispielsweise versucht, eine Variable an den Konstruktor zu übergeben. Verwenden Sie den [New](/dotnet/csharp/language-reference/keywords/new)\-Operator, um ein Objekt einer Klasse zu erstellen.  
  
 Im folgenden Beispiel wird CS1528 generiert:  
  
```  
// CS1528.cs using System; public class B { public B(int i) { _i = i; } public void PrintB() { Console.WriteLine(_i); } private int _i; } public class mine { public static void Main() { B b(3);   // CS1528, reference is not an object // try one of the following // B b; // or // B bb = new B(3); // bb.PrintB(); } }  
```
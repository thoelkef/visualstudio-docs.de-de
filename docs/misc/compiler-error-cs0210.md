---
title: "Compilerfehler CS0210 | Microsoft Docs"
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
  - "CS0210"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0210"
ms.assetid: 9f2ec1b8-6ca4-4147-b004-e3b43e7e8754
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0210
Sie müssen in einer fixed\- oder using\-Anweisungsdeklaration einen Initialisierer bereitstellen.  
  
 Müssen Sie die Variable in einer [fixed\-Anweisung](/dotnet/csharp/language-reference/keywords/fixed-statement) deklarieren und initialisieren. Weitere Informationen finden Sie unter [Unsicherer Code und Zeiger](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 Im folgenden Beispiel wird CS0210 generiert:  
  
```  
// CS0210a.cs // compile with: /unsafe class Point { public int x, y; } public class MyClass { unsafe public static void Main() { Point pt = new Point(); fixed (int i)    // CS0210 { } // try the following lines instead /* fixed (int* p = &pt.x) { } fixed (int* q = &pt.y) { } */ } }  
```  
  
 Im folgenden Beispiel wird auch CS0210 generiert, da die [using\-Anweisung](/dotnet/csharp/language-reference/keywords/using-statement) keinen Initialisierer aufweist.  
  
```  
// CS0210b.cs using System.IO; class Test { static void Main() { using (StreamWriter w) // CS0210 // Try this line instead: // using (StreamWriter w = new StreamWriter("TestFile.txt")) { w.WriteLine("Hello there"); } } }  
```
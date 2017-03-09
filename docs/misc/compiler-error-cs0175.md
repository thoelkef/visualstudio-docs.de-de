---
title: "Compilerfehler CS0175 | Microsoft Docs"
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
  - "CS0175"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0175"
ms.assetid: cedd769d-8258-4235-a321-362981b9f84b
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0175
Die Verwendung des base\-Schlüsselworts ist in diesem Kontext nicht gültig.  
  
 Zum Angeben eines bestimmten Members der Basisklasse muss das [Basis](/dotnet/csharp/language-reference/keywords/base)\-Schlüsselwort muss verwendet werden. Weitere Informationen finden Sie unter [Konstruktoren](/dotnet/csharp/programming-guide/classes-and-structs/constructors).  
  
 Im folgenden Beispiel wird CS0175 generiert:  
  
```  
// CS0175.cs using System; class BaseClass { public int TestInt = 0; } class MyClass : BaseClass { public static void Main() { MyClass aClass = new MyClass(); aClass.BaseTest(); } public void BaseTest() { Console.WriteLine(base); // CS0175 // Try the following line instead: // Console.WriteLine(base.TestInt); base = 9;   // CS0175 // Try the following line instead: // base.TestInt = 9; } }  
```
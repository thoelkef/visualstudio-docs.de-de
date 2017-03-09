---
title: "Compilerfehler CS0220 | Microsoft Docs"
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
  - "CS0220"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0220"
ms.assetid: f520bf34-bff8-4796-882b-1a9b1d5b977c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0220
Vorgangsüberlauf zur Kompilierzeit im aktivierten Modus.  
  
 Ein Vorgang wurde von [checked](/dotnet/csharp/language-reference/keywords/checked) erkannt, wobei es sich um die Standardeinstellung handelt, und es ist ein Datenverlust aufgetreten. Korrigieren Sie die Eingaben für die Zuweisung, oder verwenden Sie [unchecked](/dotnet/csharp/language-reference/keywords/unchecked), um diesen Fehler zu beheben. Weitere Informationen finden Sie unter [Checked und Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked).  
  
 Im folgenden Beispiel wird CS0220 generiert:  
  
```  
// CS0220.cs using System; class TestClass { const int x = 1000000; const int y = 1000000; public int MethodCh() { int z = (x * y);   // CS0220 return z; } public int MethodUnCh() { unchecked { int z = (x * y); return z; } } public static void Main() { TestClass myObject = new TestClass(); Console.WriteLine("Checked  : {0}", myObject.MethodCh()); Console.WriteLine("Unchecked: {0}", myObject.MethodUnCh()); } }  
```
---
title: "Compilerfehler CS0199 | Microsoft Docs"
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
  - "CS0199"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0199"
ms.assetid: 9eede3f2-b55a-4b85-a05d-6bf177e1c602
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0199
An Felder des statischen schreibgeschützten Felds "name" kann kein Verweis und keine Ausgabe übergeben werden \(Ausnahme: in einem statischen Konstruktor\).  
  
 Eine [readonly](/dotnet/csharp/language-reference/keywords/readonly)\-Variable muss dieselbe [static](/dotnet/csharp/language-reference/keywords/static)\-Verwendung wie der Konstruktor aufweisen, in dem sie als [ref](/dotnet/csharp/language-reference/keywords/ref)\- oder [out](/dotnet/csharp/language-reference/keywords/out)\-Parameter übergeben werden soll. Weitere Informationen finden Sie unter [Übergeben von Parametern](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## Beispiel  
 Im folgenden Beispiel wird CS0199 generiert:  
  
```  
// CS0199.cs class MyClass { public static readonly int TestInt = 6; static void TestMethod(ref int testInt) { testInt = 0; } MyClass() { TestMethod(ref TestInt);   // CS0199, TestInt is static } public static void Main() { } }  
```
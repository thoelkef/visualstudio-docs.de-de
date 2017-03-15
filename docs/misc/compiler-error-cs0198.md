---
title: "Compilerfehler CS0198 | Microsoft Docs"
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
  - "CS0198"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0198"
ms.assetid: 222c20f6-3f7f-4750-9f99-b5e6ae6c1271
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0198
Feldern des statischen schreibgeschützten Felds 'Name' kann nichts zugewiesen werden \(Ausnahme: in einem statischen Konstruktor oder einem Variableninitialisierer\).  
  
 Eine [readonly](/dotnet/csharp/language-reference/keywords/readonly)\-Variable muss dieselbe [static](/dotnet/csharp/language-reference/keywords/static)\-Verwendung wie der Konstruktor aufweisen, in dem Sie sie initialisieren möchten. Weitere Informationen finden Sie unter [Statische Konstruktoren](/dotnet/csharp/programming-guide/classes-and-structs/static-constructors).  
  
 Im folgenden Beispiel wird CS0198 generiert:  
  
```  
// CS0198.cs class MyClass { public static readonly int TestInt = 6; MyClass() { TestInt = 11;   // CS0198, constructor is not static and readonly field is } public static void Main() { } }  
```
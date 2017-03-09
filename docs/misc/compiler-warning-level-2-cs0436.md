---
title: "Compilerwarnung (Stufe 2) CS0436 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0436"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0436"
ms.assetid: c4135d9d-3511-4bbc-9540-48c2091f869c
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS0436
Der Typ 'Typ' in 'Assembly' verursacht einen Konflikt mit dem importierten Typ 'Typ2' in 'Assembly'. Es wird der in 'Assembly' definierte Typ verwendet.  
  
 Diese Warnung wird ausgegeben, wenn ein Typ in einer Quelldatei \(Datei\_2\) mit einem importierten Typ in Datei\_1 in Konflikt steht. Der Compiler verwendet den Typ in der Quelldatei.  
  
## Beispiel  
  
```  
// CS0436_a.cs // compile with: /target:library public class A { public void Test() { System.Console.WriteLine("CS0436_a"); } }  
```  
  
## Beispiel  
 Im folgenden Beispiel wird CS0436 generiert:  
  
```  
// CS0436_b.cs // compile with: /reference:CS0436_a.dll // CS0436 expected public class A { public void Test() { System.Console.WriteLine("CS0436_b"); } } public class Test { public static void Main() { A x = new A(); x.Test(); } }  
```
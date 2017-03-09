---
title: "Compilerwarnung (Stufe 2) CS0437 | Microsoft Docs"
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
  - "CS0437"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0437"
ms.assetid: cba5c9b6-a0bc-4f19-b1f0-c1f66436ee91
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS0437
Der Typ "Typ" in "Assembly2" verursacht einen Konflikt mit dem importierten Namespace "Namespace" in "Assembly1". Es wird der in "Assembly" definierte Typ verwendet.  
  
 Diese Warnung wird ausgegeben, wenn ein Typ in einer Quelldatei \(Datei\_2\) mit einem importierten Namespace in Datei\_1 in Konflikt steht. Der Compiler verwendet den Typ in der Quelldatei.  
  
## Beispiel  
  
```  
// CS0437_a.cs // compile with: /target:library namespace Util { public class A { public void Test() { System.Console.WriteLine("CS0437_a.cs"); } } }  
```  
  
## Beispiel  
 Im folgenden Beispiel wird CS0437 generiert.  
  
```  
// CS0437_b.cs // compile with: /reference:CS0437_a.dll /W:2 // CS0437 expected class Util { public class A { public void Test() { System.Console.WriteLine("CS0437_b.cs"); } } } public class Test { public static void Main() { Util.A x = new Util.A(); x.Test(); } }  
```
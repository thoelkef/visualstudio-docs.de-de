---
title: "Compilerwarnung (Stufe 2) CS0435 | Microsoft Docs"
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
  - "CS0435"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0435"
ms.assetid: e70cd8c1-d399-4af8-8b1e-69a1de389aad
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS0435
Der Namespace 'Namespace' in 'Assembly' verursacht einen Konflikt mit dem importierten Typ 'Typ' in 'Assembly'. Der in 'Assembly' definierte Namespace wird verwendet.  
  
 Diese Warnung wird ausgegeben, wenn ein Namespace in einer Quelldatei \(Datei\_2\) mit einem importierten Typ in Datei\_1 in Konflikt steht. Der Compiler verwendet den Typ in der Quelldatei.  
  
 Im folgenden Beispiel wird CS0435 generiert:  
  
 Kompilieren Sie zunächst diese Datei:  
  
```  
// CS0435_1.cs // compile with: /t:library public class Util { public class A { } }  
```  
  
 Kompilieren Sie dann diese Datei:  
  
```  
// CS0435_2.cs // compile with: /r:CS0435_1.dll using System; namespace Util { public class A { } } public class Test { public static void Main() { Console.WriteLine(typeof(Util.A)); // CS0435 } }  
```
---
title: "Compilerfehler CS1949 | Microsoft Docs"
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
  - "CS1949"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1949"
ms.assetid: 959f553e-ac3d-43a1-b0a0-11e270f2ad64
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1949
Das kontextbezogene Schlüsselwort 'var' darf nicht in der Deklaration einer Bereichsvariablen verwendet werden.  
  
 Eine Bereichsvariable wird implizit vom Compiler typisiert. Es ist nicht erforderlich, [var](/dotnet/csharp/language-reference/keywords/var) für eine Bereichsvariable zu verwenden.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie das Schlüsselwort `var`  vor der Bereichsvariablen.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1949 generiert:  
  
```  
// cs1949.cs using System; using System.Linq; class Test { static void Main() { var x = from var i in Enumerable.Range(1, 100) // CS1949 select i; } }  
```  
  
## Siehe auch  
 [LINQ\-Abfrageausdrücke](/dotnet/csharp/programming-guide/linq-query-expressions/index)   
 [Introduction to LINQ Queries \(C\#\)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
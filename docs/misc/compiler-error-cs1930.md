---
title: "Compilerfehler CS1930 | Microsoft Docs"
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
  - "CS1930"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1930"
ms.assetid: d28d2334-825c-4ffc-b9e9-f5d61f44d672
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1930
Die Bereichsvariable "Name" wurde bereits deklariert.  
  
 Die Bereichsvariable in einem Abfrageausdruck liegt innerhalb des Bereichs, bis der Abfrageausdruck endet. Sie muss daher einen eindeutigen Bezeichner aufweisen.  
  
### So beheben Sie diesen Fehler  
  
1.  Geben Sie jeder Bereichsvariablen, die in einem Abfrageausdruck eingeführt wird, einen eindeutigen Namen.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1930 generiert, da der Bezeichner `num` für die Bereichsvariable in der `from`\-Klausel und für die durch die `let`\-Klausel eingeführten Bereichsvariable verwendet wird.  
  
```  
// cs1930.cs using System.Linq; class Program { static void Main() { int[] nums = { 0, 1, 2, 3, 4, 5 }; var query = from num in nums let num = 3 // CS1930 select num; } }  
```  
  
## Siehe auch  
 [LINQ\-Abfrageausdrücke](/dotnet/csharp/programming-guide/linq-query-expressions/index)
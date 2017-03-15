---
title: "Compilerfehler CS0023 | Microsoft Docs"
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
  - "CS0023"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0023"
ms.assetid: 7a30073c-99de-41fa-ac6d-4a0dfbb76de9
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0023
Der Operator "Operator" kann nicht auf einen Operanden vom Typ "Typ" angewendet werden.  
  
 Es wurde versucht, einen Operator auf eine Variable anzuwenden, deren Typ nicht für die Zusammenarbeit mit dem Operator bestimmt ist. Weitere Informationen finden Sie unter [Typen](/dotnet/csharp/programming-guide/types/index) und [C\#\-Operatoren](/dotnet/csharp/language-reference/operators/index).  
  
 Im folgenden Beispiel wird CS0023 generiert:  
  
```  
// CS0023.cs namespace x { public class a { public static void Main() { string s = "hello"; s = -s;   // CS0023, minus operator not allowed on strings } } }  
```
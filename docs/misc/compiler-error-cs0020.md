---
title: "Compilerfehler CS0020 | Microsoft Docs"
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
  - "CS0020"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0020"
ms.assetid: 7a54db39-6530-4e34-aa17-a90f85223d08
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0020
Division durch Konstante 0 \(null\).  
  
 Ein Ausdruck verwendet den Literalwert \(keine Variable\) 0 \(null\) im Nenner eines Divisionsvorgangs. Division durch 0 \(null\) ist nicht definiert und daher ungültig.  
  
 Im folgenden Beispiel wird CS0020 generiert:  
  
```  
// CS0020.cs namespace x { public class b { public static void Main() { 1 / 0;   // CS0020 } } }  
```  
  
## Siehe auch  
 [Operatoren](/dotnet/csharp/programming-guide/statements-expressions-operators/operators)
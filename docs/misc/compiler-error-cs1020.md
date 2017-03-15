---
title: "Compilerfehler CS1020 | Microsoft Docs"
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
  - "CS1020"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1020"
ms.assetid: e8860769-a847-4248-a37b-77a59863467c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1020
Überladbarer binärer Operator erwartet.  
  
 Es wurde versucht, eine [Operatorüberladung](/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators) zu definieren, aber der Operator war kein binärer Operator, der zwei Parameter übernimmt.  
  
 Im folgenden Beispiel wird CS1020 generiert:  
  
```  
// CS1020.cs public class iii { public static int operator ++(iii aa, int bb)   // CS1020, change ++ to + { return 0; } public static void Main() { } }  
```
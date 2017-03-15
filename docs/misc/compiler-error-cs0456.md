---
title: "Compilerfehler CS0456 | Microsoft Docs"
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
  - "CS0456"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0456"
ms.assetid: d714ec06-a7f4-405e-bf32-423696848319
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0456
Typparameter „Type Parameter Name 1“ weist die Einschränkung „struct“ auf, daher kann „Type Parameter Name 1“ nicht als Einschränkung für „Type Parameter Name 2“ verwendet werden.  
  
 Werttypeinschränkungen sind implizit versiegelt, sodass diese Einschränkungen nicht als Einschränkungen für einen zweiten Typparameter verwendet werden können. Grund hierfür ist, dass Werttypen nicht außer Kraft gesetzt werden können. Um diesen Fehler zu beheben, legen Sie Werttypeinschränkung direkt für den zweiten Typparameter, anstatt indirekt mit dem ersten Typparameter fest.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0456 generiert:  
  
```  
// CS0456.cs // compile with: /target:library public class GenericsErrors { public class G5<T> where T : struct { public class N<U> where U : T {}   // CS0456 public class N2<U> where U : struct {}   // OK } }  
```
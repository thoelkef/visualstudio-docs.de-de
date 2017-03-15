---
title: "Compilerfehler CS0216 | Microsoft Docs"
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
  - "CS0216"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0216"
ms.assetid: afb3dd29-3eff-4b62-8267-eb726c2bcee4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0216
Für den Operator 'operator' muss außerdem ein passender Operator 'fehlender\_operator' definiert werden  
  
 Für einen benutzerdefinierten [wahr](/dotnet/csharp/language-reference/keywords/true)\-Operator ist ein entsprechender benutzerdefinierter Operator [falsch](/dotnet/csharp/language-reference/keywords/false) erforderlich, und umgekehrt. Weitere Informationen finden Sie unter [Operatoren](/dotnet/csharp/programming-guide/statements-expressions-operators/operators).  
  
 Im folgenden Beispiel wird CS0216 generiert:  
  
```  
// CS0216.cs class MyClass { public static bool operator true (MyClass MyInt)   // CS0216 { return true; } // to resolve, uncomment the following operator definition /* public static bool operator false (MyClass MyInt) { return true; } */ public static void Main() { } }  
```
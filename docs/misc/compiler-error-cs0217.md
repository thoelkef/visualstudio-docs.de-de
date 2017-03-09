---
title: "Compilerfehler CS0217 | Microsoft Docs"
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
  - "CS0217"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0217"
ms.assetid: ede61095-6e11-4f4a-8e7d-85e7a3f4fc3d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0217
Um als Kurzschlussoperator anwendbar zu sein, muss der Rückgabetyp eines benutzerdefinierten logischen Operators \('Operator'\) mit dem Typ seiner zwei Parameter übereinstimmen.  
  
 Wenn Sie einen Operator für einen benutzerdefinierten Typ definieren und anschließend versuchen, den Operator als Kurzschlussoperator zu verwenden, muss der benutzerdefinierte Operator über Parameter und Rückgabewerte desselben Typs verfügen. Weitere Informationen zu Kurzschlussoperatoren finden Sie unter [&&\-Operator](/dotnet/csharp/language-reference/operators/conditional-and-operator) und [&#124;&#124;\-Operator](../Topic/%7C%7C%20Operator%20\(C%23%20Reference\).md).  
  
 Im folgenden Beispiel wird CS0217 generiert:  
  
```  
// CS0217.cs using System; public class MyClass { public static bool operator true (MyClass f) { return false; } public static bool operator false (MyClass f) { return false; } public static implicit operator int(MyClass x) { return 0; } public static int operator & (MyClass f1, MyClass f2)   // CS0217 // try the following line instead // public static MyClass operator & (MyClass f1, MyClass f2) { return new MyClass(); } public static void Main() { MyClass f = new MyClass(); int i = f && f; } }  
```  
  
## Siehe auch  
 [Überladbare Operatoren](/dotnet/csharp/programming-guide/statements-expressions-operators/overloadable-operators)
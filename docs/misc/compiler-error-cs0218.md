---
title: "Compilerfehler CS0218 | Microsoft Docs"
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
  - "CS0218"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0218"
ms.assetid: f675e06a-c55c-44a1-b5db-0df178fd8f79
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0218
Der Typ \('Typ'\) muss Deklarationen des True\- und des False\-Operators enthalten.  
  
 Wenn Sie einen Operator für einen benutzerdefinierten Typ definieren und anschließend versuchen, den Operator als Kurzschlussoperator zu verwenden, müssen für den benutzerdefinierten Operator der True\- und der False\-Operator definiert sein. Weitere Informationen zu Kurzschlussoperatoren finden Sie unter [&&\-Operator](/dotnet/csharp/language-reference/operators/conditional-and-operator) und [&#124;&#124;\-Operator](../Topic/%7C%7C%20Operator%20\(C%23%20Reference\).md).  
  
 Im folgenden Beispiel wird CS0218 generiert:  
  
```  
// CS0218.cs using System; public class MyClass { // uncomment these operator declarations to resolve this CS0218 /* public static bool operator true (MyClass f) { return false; } public static bool operator false (MyClass f) { return false; } */ public static implicit operator int(MyClass x) { return 0; } public static MyClass operator & (MyClass f1, MyClass f2) { return new MyClass(); } public static void Main() { MyClass f = new MyClass(); int i = f && f;   // CS0218, requires operators true and false } }  
```  
  
## Siehe auch  
 [Konvertierungsoperatoren](/dotnet/csharp/programming-guide/statements-expressions-operators/conversion-operators)
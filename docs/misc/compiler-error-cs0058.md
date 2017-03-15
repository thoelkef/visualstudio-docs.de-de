---
title: "Compilerfehler CS0058 | Microsoft Docs"
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
  - "CS0058"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0058"
ms.assetid: 9535da60-03b9-41ab-93e1-e57b6440fca9
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0058
Inkonsistenter Zugriff: Der Rückgabetyp 'typ' ist weniger zugreifbar als der Delegat 'delegat'.  
  
 Ein public\-Konstrukt muss ein öffentlich zugreifbares Objekt zurückgeben. Weitere Informationen finden Sie unter [Zugriffsmodifizierer](/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers).  
  
 Im folgenden Beispiel wird CS0058 generiert, weil auf 'MyClass' keine Zugriffsmodifizierer angewendet werden und ihr daher der standardmäßige private Zugriff zugewiesen wird:  
  
```  
// CS0058.cs class MyClass // try the following line instead // public class MyClass { } public delegate MyClass MyClassDel();   // CS0058 public class A { public static void Main() { } }  
```  
  
## Siehe auch  
 [Private](/dotnet/csharp/language-reference/keywords/private)
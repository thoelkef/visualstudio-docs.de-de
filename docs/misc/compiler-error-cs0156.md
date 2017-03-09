---
title: "Compilerfehler CS0156 | Microsoft Docs"
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
  - "CS0156"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0156"
ms.assetid: 32026b1b-bcd7-4464-b63f-3b38c00452a6
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0156
In einer finally\-Klausel, die in der nächsten einschließenden catch\-Klausel geschachtelt ist, ist keine throw\-Anweisung ohne Argumente zulässig.  
  
 Eine [throw](/dotnet/csharp/language-reference/keywords/throw)\-Anweisung ohne Parameter kann nur in einer **catch**\-Klausel vorkommen, die keine Parameter annimmt.  
  
 Weitere Informationen finden Sie unter [Ausnahmebehandlungsanweisungen](/dotnet/csharp/language-reference/keywords/exception-handling-statements) und [Ausnahmen und Ausnahmebehandlung](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling).  
  
 Im folgenden Beispiel wird CS0156 generiert:  
  
```  
// CS0156.cs using System; namespace MyNamespace { public class MyClass2 : Exception { } public class MyClass { public static void Main() { try { throw;   // CS0156 } catch(MyClass2) { throw;   // this throw is valid } } } }  
```
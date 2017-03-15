---
title: "Compilerfehler CS0155 | Microsoft Docs"
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
  - "CS0155"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0155"
ms.assetid: 6c92984a-2b10-453e-9cb7-e6a1d1b98aa6
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0155
Der aufgefangene oder ausgelöste Typ muss von System.Exception abgeleitet werden.  
  
 Es wurde versucht, einen Datentyp, der nicht von **System.Exception** abgeleitet wurde, an einen [catch](/dotnet/csharp/language-reference/keywords/try-catch)\-Block zu übergeben. An einen **catch**\-Block können nur Datentypen übergeben werden, die von **System.Exception** abgeleitet wurden. Weitere Informationen finden Sie unter [Ausnahmebehandlungsanweisungen](/dotnet/csharp/language-reference/keywords/exception-handling-statements) und [Ausnahmen und Ausnahmebehandlung](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling).  
  
 Im folgenden Beispiel wird CS0155 generiert:  
  
```  
// CS0155.cs using System; namespace MyNamespace { public class MyClass2 // try the following line instead // public class MyClass2 : Exception { } public class MyClass { public static void Main() { try { } catch (MyClass2)   // CS0155, resolves if you derive MyClass2 from Exception { } } } }  
```
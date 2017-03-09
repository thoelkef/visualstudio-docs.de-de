---
title: "Compilerwarnung (Stufe 4) CS0028 | Microsoft Docs"
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
  - "CS0028"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0028"
ms.assetid: 47df919f-01fa-45ae-a4b7-912445e679e2
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 4) CS0028
Die "Funktionsdeklaration" weist als Einstiegspunkt die falsche Signatur auf.  
  
 Die Methodendeklaration für `Main` war ungültig: Die Deklaration erfolgte mit einer ungültigen Signatur.`Main` muss als statisch deklariert werden und entweder [int](/dotnet/csharp/language-reference/keywords/int) oder [void](/dotnet/csharp/language-reference/keywords/void) zurückgeben. Weitere Informationen finden Sie unter [Main\(\) und Befehlszeilenargumente](/dotnet/csharp/programming-guide/main-and-command-args/main-and-command-line-arguments).  
  
 Im folgenden Beispiel wird CS0028 generiert:  
  
```  
// CS0028.cs // compile with: /W:4 /warnaserror public class a { public static double Main(int i)   // CS0028 // Try the following line instead: // public static void Main() { } }  
```
---
title: "Compilerfehler CS1922 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1922"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1922"
ms.assetid: a4098a25-6581-4966-b61d-318cd12f76d3
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1922
Auflistungsinitialisierer erfordert, dass sein type\-Typ „System.Collections.IEnumerable“ implementiert.  
  
 Um einen Auflistungsinitialisierer mit einem Typ zu verwenden, muss der Typ `IEnumerable` implementieren. Dieser Fehler kann auftreten, wenn Sie versehentlich Auflistungsinitialisierersyntax anstelle eines Objektinitialisierers verwenden.  
  
### So beheben Sie diesen Fehler  
  
-   Wenn der Typ keine Auflistung darstellt, verwenden Sie Objektinitialisierersyntax anstelle von Auflistungsinitialisierersyntax.  
  
-   Wenn der Typ eine Auflistung darstellt, ändern Sie ihn so, dass er `IEnumerable` implementiert, bevor Sie Auflistungsinitialisierer zum Initialisieren von Objekten dieses Typs verwenden können.  
  
-   Wenn der Typ eine Auflistung darstellt und Sie keinen Zugriff auf den Quellcode haben, initialisieren Sie nur seine Elemente, indem Sie deren Klassenkonstruktoren oder andere Initialisierungsmethoden verwenden.  
  
## Beispiel  
 Im folgenden Code generiert den Fehler CS1922:  
  
```  
// cs1922.cs public class Test { public static void Main() { // Collection initializer. var tc = new TestClass  {1,"hello"} ; // CS1922 // Object initalizer. var tc2 = new TestClass { memberA = 1, memberB = "hello" }; // OK } } public class TestClass { public int memberA { get; set; } public string memberB { get; set; } }  
  
```  
  
## Siehe auch  
 [Objekt\- und Auflistungsinitialisierer](/dotnet/csharp/programming-guide/classes-and-structs/object-and-collection-initializers)
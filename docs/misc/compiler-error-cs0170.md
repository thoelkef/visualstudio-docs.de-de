---
title: "Compilerfehler CS0170 | Microsoft Docs"
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
  - "CS0170"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0170"
ms.assetid: ba881e38-2abf-4a5f-b9e6-28d26a5bd235
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0170
Verwendung des möglicherweise nicht zugewiesenen Felds 'Feld'.  
  
 Ein Feld in einer Struktur wurde ohne vorherige Initialisierung verwendet. Ermitteln Sie zunächst, welches Feld nicht initialisiert wurde, und initialisieren Sie es anschließend, bevor Sie versuchen, darauf zuzugreifen, um dieses Problem zu beheben. Weitere Informationen zum Initialisieren von Strukturen finden Sie unter [Strukturen](/dotnet/csharp/programming-guide/classes-and-structs/structs) und [Verwenden von Strukturen](/dotnet/csharp/programming-guide/classes-and-structs/using-structs).  
  
 Im folgenden Beispiel wird CS0170 generiert:  
  
```  
// CS0170.cs public struct error { public int i; } public class MyClass { public static void Main() { error e; // uncomment the next line to resolve this error // e.i = 0; System.Console.WriteLine( e.i );   // CS0170 because //e.i was never assigned } }  
```
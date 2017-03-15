---
title: "Compilerfehler CS0131 | Microsoft Docs"
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
  - "CS0131"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0131"
ms.assetid: 822852cc-a426-4b7d-b2ff-0026a0c0a0e7
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0131
Die linke Seite einer Zuweisung muss eine Variable, eine Eigenschaft oder ein Indexer sein.  
  
 In einer Zuweisungsanweisung wurde der Wert der rechten Seite der linken Seite zugewiesen. Die linke Seite einer Zuweisung muss eine Variable, eine Eigenschaft oder ein Indexer sein.  
  
 Um diesen Fehler zu beheben, stellen Sie sicher, dass alle Operatoren auf der rechten Seite stehen und dass die linke Seite eine Variable, eine Eigenschaft oder ein Indexer ist. Weitere Informationen finden Sie unter [Anweisungen, Ausdrücke und Operatoren](/dotnet/csharp/programming-guide/statements-expressions-operators/index).  
  
## Beispiel  
 Im folgenden Beispiel wird CS0131 generiert:  
  
```  
// CS0131.cs public class MyClass { public int i = 0; public void MyMethod() { i++ = 1;   // CS0131 // try the following line instead // i = 1; } public static void Main() { } }  
```  
  
## Beispiel  
 Dieser Fehler kann auch auftreten, wenn Sie versuchen, arithmetische Operationen auf der linken Seite eines Zuweisungsoperators auszuführen, wie im folgenden Beispiel dargestellt.  
  
```  
// CS0131b.cs public class C { public static int Main() { int a = 1, b = 2, c = 3; if (a + b = c) // CS0131 // try this instead // if (a + b == c) return 0; return 1; } }  
```
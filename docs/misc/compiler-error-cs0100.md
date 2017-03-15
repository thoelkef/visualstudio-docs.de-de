---
title: "Compilerfehler CS0100 | Microsoft Docs"
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
  - "CS0100"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0100"
ms.assetid: b49e4846-2a82-48ed-9ca8-953eb5c1baaa
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0100
Der Parameter 'Parametername' ist ein Duplikat.  
  
 Eine Methodendeklaration hat denselben Parameternamen mehrmals verwendet. Parameternamen müssen in einer Methodendeklaration eindeutig sein. Weitere Informationen finden Sie unter [Methoden](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 Im folgenden Beispiel wird CS0100 generiert:  
  
```  
// CS0100.cs namespace x { public class a { public static void f(int i, char i)   // CS0100 // try the following line instead // public static void f(int i, char j) { } public static void Main() { } } }  
```
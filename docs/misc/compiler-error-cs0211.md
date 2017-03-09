---
title: "Compilerfehler CS0211 | Microsoft Docs"
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
  - "CS0211"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0211"
ms.assetid: 720be9a9-b0c1-4391-94e5-4c4027e83036
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0211
Die Adresse des angegebenen Ausdrucks kann nicht übernommen werden.  
  
 Sie können die Adresse von Feldern, lokalen Variablen und die Dereferenzierung von Zeigern übernehmen, aber Sie nicht können z. B. nicht die Adresse der Summe zweier lokaler Variablen verwenden. Weitere Informationen finden Sie unter [Unsicherer Code und Zeiger](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
 Im folgenden Beispiel wird CS0211 generiert:  
  
```  
// CS0211.cs // compile with: /unsafe public class MyClass { unsafe public void M() { int a = 0, b = 0; int *i = &(a + b);   // CS0211, the addition of two local variables // try the following line instead // int *i = &a; } public static void Main() { } }  
```
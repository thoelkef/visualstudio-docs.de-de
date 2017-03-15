---
title: "Compilerfehler CS0213 | Microsoft Docs"
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
  - "CS0213"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0213"
ms.assetid: 3c1d55e3-2b84-4c28-8206-ef65869a898c
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0213
Sie können die fixed\-Anweisung nicht verwenden, um die Adresse eines bereits festen Ausdrucks abzurufen.  
  
 Eine lokale Variable in einer [unsafe](/dotnet/csharp/language-reference/keywords/unsafe)\-Methode oder einem Parameter ist bereits "fixed" \(auf dem Stapel\), sodass Sie die Adresse keiner dieser beiden Variablen in einem [fixed](/dotnet/csharp/language-reference/keywords/fixed-statement)\-Ausdruck verwenden können. Weitere Informationen finden Sie unter [Unsicherer Code und Zeiger](/dotnet/csharp/programming-guide/unsafe-code-pointers/index).  
  
## Beispiel  
 Im folgenden Beispiel wird CS0213 generiert.  
  
```  
// CS0213.cs // compile with: /unsafe public class MyClass { unsafe public static void Main() { int i = 45; fixed (int *j = &i) { }  // CS0213 // try the following line instead // int* j = &i; int[] a = new int[] {1,2,3}; fixed (int *b = a) { fixed (int *c = b) { }  // CS0213 // try the following line instead // int *c = b; } } }  
```
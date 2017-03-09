---
title: "Compilerfehler CS1655 | Microsoft Docs"
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
  - "CS1655"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1655"
ms.assetid: 041e9daa-c026-494f-b086-0db9a23c969b
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1655
Felder von "Variable" können nicht als ref\- oder out\-Argument übergeben werden, da es sich um einen "schreibgeschützten Variablentyp" handelt.  
  
 Dieser Fehler tritt auf, wenn Sie versuchen, einen Member einer [foreach](/dotnet/csharp/language-reference/keywords/foreach-in)\-Variablen, [using](/dotnet/csharp/language-reference/keywords/using-statement)\-Variablen oder [fixed](/dotnet/csharp/language-reference/keywords/fixed-statement)\-Variablen als ref\- oder out\-Argument an eine Funktion zu übergeben. Da diese Variablen in diesen Kontexten als schreibgeschützt betrachtet werden, ist dies nicht zulässig.  
  
 Im folgenden Beispiel wird CS1655 generiert:  
  
```  
// CS1655.cs struct S { public int i; } class CMain { static void f(ref int iref) { } public static void Main() { S[] sa = new S[10]; foreach(S s in sa) { CMain.f(ref s.i);  // CS1655 } } }  
```
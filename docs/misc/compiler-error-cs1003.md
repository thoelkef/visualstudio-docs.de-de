---
title: "Compilerfehler CS1003 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1003"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1003"
ms.assetid: 59f4d053-13c0-4f79-830e-263acdbe94fa
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1003
Syntaxfehler. 'char' wurde erwartet.  
  
 Der Compiler gibt diesen Fehler für jede einer Reihe von Fehlerbedingungen aus. Überprüfen Sie den Code, um den Syntaxfehler zu finden.  
  
 Im folgenden Beispiel wird CS1003 generiert:  
  
```  
// CS1003.cs public class b { public static void Main() { int[] a; a[);   // CS1003 } }  
```
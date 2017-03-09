---
title: "Compilerfehler CS1530 | Microsoft Docs"
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
  - "CS1530"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1530"
ms.assetid: 3844b5ef-e0ec-42df-9267-72689020f128
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1530
Das Schlüsselwort 'new' ist für Elemente, die in einem Namespace definiert sind, nicht zulässig.  
  
 Das Schlüsselwort [new](/dotnet/csharp/language-reference/keywords/new) muss für Konstrukte in einem [Namespace](/dotnet/csharp/language-reference/keywords/namespace) nicht angegeben werden.  
  
 Im folgenden Beispiel wird CS1530 generiert:  
  
```  
// CS1530.cs namespace a { new class i   // CS1530 { } // try the following instead class ii { public static void Main() { } } }  
```
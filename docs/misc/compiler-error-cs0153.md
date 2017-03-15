---
title: "Compilerfehler CS0153 | Microsoft Docs"
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
  - "CS0153"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0153"
ms.assetid: 3a0791e9-0ab9-4eaa-a230-d39aabaa9d5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0153
Eine "goto case"\-Anweisung ist nur innerhalb einer switch\-Anweisung gültig.  
  
 Es wurde versucht, die [switch](/dotnet/csharp/language-reference/keywords/switch)\-Syntax außerhalb einer **switch**\-Anweisung zu verwenden. Weitere Informationen finden Sie unter [switch](/dotnet/csharp/language-reference/keywords/switch).  
  
 Im folgenden Beispiel wird CS0153 generiert:  
  
```  
// CS0153.cs public class a { public static void Main() { goto case 5;   // CS0153 } }  
```
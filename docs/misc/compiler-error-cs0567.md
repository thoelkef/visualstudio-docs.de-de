---
title: "Compilerfehler CS0567 | Microsoft Docs"
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
  - "CS0567"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0567"
ms.assetid: 90aefbf9-d216-4eb4-96d4-44926fa23b1e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0567
Schnittstellen können keine Operatoren enthalten.  
  
 Operatoren sind in [Schnittstellendefinitionen](/dotnet/csharp/language-reference/keywords/interface) nicht zulässig.  
  
 Im folgenden Beispiel wird CS0567 generiert:  
  
```  
// CS0567.cs interface IA { int operator +(int aa, int bb);   // CS0567 } class Sample { public static void Main() { } }  
```
---
title: "Compilerfehler CS0564 | Microsoft Docs"
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
  - "CS0564"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0564"
ms.assetid: 4c152e10-eb22-4437-a85f-1599c76470e0
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0564
Der erste Operand eines überladenen Schiebeoperators muss den enthaltenden Typ aufweisen, und der zweite Operand muss eine ganze Zahl sein.  
  
 Sie haben versucht, einen Shift\-Operator \(\<\< oder \>\>\) mit falsch geschriebenen Operanden zu überladen. Der erste Operand muss der Typ sein, und der zweite Operand muss vom Typ `int` sein.  
  
 Im folgenden Beispiel wird CS0564 generiert:  
  
```  
// CS0564.cs using System; class C { public static int operator << (C c1, C c2) // CS0564 // To correct, change second operand to int, like so: // public static int operator << (C c1, int c2) { return 0; } static void Main() { } }  
```
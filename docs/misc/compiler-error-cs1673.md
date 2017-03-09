---
title: "Compilerfehler CS1673 | Microsoft Docs"
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
  - "CS1673"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1673"
ms.assetid: 5c7dd58b-dcbc-45c9-be36-7d15fafaa067
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1673
Anonyme Methoden, Lambdaausdrücke und Abfrageausdrücke innerhalb von Strukturen können nicht auf Instanzmember von 'this' zugreifen. Erwägen Sie, 'this' in eine lokale Variable außerhalb der anonymen Methode, des Lambdaausdrucks oder des Abfrageausdrucks zu kopieren und die lokale Variable stellvertretend zu verwenden.  
  
 Im folgenden Beispiel wird CS1673 generiert:  
  
```  
// CS1673.cs delegate int MyDelegate(); public struct S { int member; public int F(int i) { member = i; // Try assigning to a local variable // S s = this; MyDelegate d = delegate() { i = this.member;  // CS1673 // And use the local variable instead of "this" // i =  s.member; return i; }; return d(); } } class CMain { public static void Main() { } }  
```
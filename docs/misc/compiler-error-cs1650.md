---
title: "Compilerfehler CS1650 | Microsoft Docs"
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
  - "CS1650"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1650"
ms.assetid: 251a3a67-6e56-4795-874a-d54610c70595
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1650
Feldern des statischen schreibgeschützten Felds 'Bezeichner' kann nichts zugewiesen werden \(Ausnahme: in einem statischen Konstruktor oder einem Variableninitialisierer\).  
  
 Dieser Fehler tritt auf, wenn versucht wird, ein Member eines schreibgeschützten und statischen Felds zu ändern, wo Änderungen nicht zulässig sind. Um diesen Fehler zu beheben, beschränken Sie Zuweisungen an schreibgeschützte Felder auf den Konstruktor oder Variableninitialisierer, oder entfernen Sie das `readonly`\-Schlüsselwort aus der Deklaration des Felds.  
  
```  
// CS1650.cs public struct Inner { public int i; } class Outer { public static readonly Inner inner = new Inner(); } class D { static void Main() { Outer.inner.i = 1;  // CS1650 } }  
```
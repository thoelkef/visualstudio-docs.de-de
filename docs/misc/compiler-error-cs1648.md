---
title: "Compilerfehler CS1648 | Microsoft Docs"
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
  - "CS1648"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1648"
ms.assetid: 5cf1bc84-cd18-4df2-942f-1cc17eabacd6
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1648
Member des schreibgeschützten Felds 'identifier' können nicht bearbeitet werden \(Ausnahme: in einem Konstruktor oder einem Variableninitialisierer\).  
  
 Dieser Fehler tritt auf, wenn versucht wird, ein Member eines schreibgeschützten Felds zu ändern, wo Änderungen nicht zulässig sind. Um diesen Fehler zu beheben, beschränken Sie Zuweisungen an schreibgeschützte Felder auf den Konstruktor oder Variableninitialisierer, oder entfernen Sie das Schlüsselwort „readonly“ aus der Deklaration des Felds.  
  
 Im folgenden Beispiel wird CS1648 generiert:  
  
```  
// CS1648.cs public struct Inner { public int i; } class Outer { public readonly Inner inner = new Inner(); } class D { static void Main() { Outer outer = new Outer(); outer.inner.i = 1;  // CS1648 } }  
```
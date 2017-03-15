---
title: "Compilerfehler CS0837 | Microsoft Docs"
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
  - "CS0837"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0837"
ms.assetid: cbde45dc-222c-4bfe-8814-856476319d37
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0837
Der erste Operand des "is"\- oder "as"\-Operators darf kein Lambda\-Ausdruck und keine anonyme Methode sein.  
  
 Lambda\-Ausdrücke und anonyme Methoden dürfen nicht auf der linken Seite von [is](/dotnet/csharp/language-reference/keywords/is) oder [as](/dotnet/csharp/language-reference/keywords/as) verwendet werden.  
  
### So beheben Sie diesen Fehler  
  
-   Wenn der Fehler bei einem `is`\-Operator auftritt, müssen Sie bedenken, dass `is` einen Wert und einen Typ annimmt und Ihnen mitteilt, ob der Wert mittels Verweis\-, Boxing\- oder Unboxing\-Konvertierung in diesen Typ umgewandelt werden kann. Da Lambda\-Ausdrücke keine Werte sind und keine Verweis\-, Boxing\- oder Unboxing\-Konvertierungen aufweisen, können Lambda\-Ausdrücke nicht mit `is` verwendet werden.  
  
-   Wenn im Code `as` falsch verwendet wird, ist die beste Lösung wahrscheinlich die Änderung in eine Umwandlung.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0837 generiert:  
  
```  
// cs0837.cs namespace TestNamespace { public delegate void Del(); class Test { static int Main() { bool b1 = (() => { }) is Del;   // CS0837 bool b2 = delegate() { } is Del;// CS0837 Del d1 = () => { } as Del;      // CS0837 Del d2 = delegate() { } as Del; // CS0837 return 1; } } }  
```
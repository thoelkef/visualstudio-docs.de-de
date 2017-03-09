---
title: "Compilerfehler CS1932 | Microsoft Docs"
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
  - "CS1932"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1932"
ms.assetid: fc927899-2d35-4d47-9ae9-8fc99295bb66
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1932
'Ausdruck' kann keiner Bereichsvariablen zugewiesen werden.  
  
 Der Compiler muss in der Lage sein, den Typ einer Bereichsvariablen unabhängig davon abzuleiten, ob sie in einer `from`\- oder `let`\-Klausel eingeführt wurde. Er darf nicht null sein, da NULL kein Typ ist, und er kann nicht zu einem Ausdruck mit unsicherem Typ zugewiesen werden.  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die ungültige Zuordnung.  
  
-   Wandeln Sie den Ausdruck explizit in einen zulässigen Typ um.  
  
## Beispiel  
 Der folgende Code führt zu Fehler CS1932, da der Typ der Bereichsvariablen nicht abgeleitet werden kann. Wandeln Sie den Wert in den gewünschten Typ um, um den Fehler zu beheben, wie im folgenden Beispiel gezeigt.  
  
```  
// CS1932.cs using System.Linq; class Test { static void Main() { var x = from i in Enumerable.Range(1, 100) let k = null // CS1932 // Try the following line instead. let k = (string) null select i; } }  
```  
  
## Siehe auch  
 [LINQ\-Abfrageausdrücke](/dotnet/csharp/programming-guide/linq-query-expressions/index)
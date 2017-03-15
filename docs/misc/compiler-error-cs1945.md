---
title: "Compilerfehler CS1945 | Microsoft Docs"
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
  - "CS1945"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1945"
ms.assetid: 787f61b0-4767-451c-8c78-8e456b5057eb
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1945
Eine Ausdrucksbaumstruktur darf keinen anonymen Methodenausdruck enthalten  
  
 Ausdrucksbaumstrukturen können nur Ausdrücke enthalten. Anonyme Methoden können nur Anweisungen darstellen.  
  
### So beheben Sie diesen Fehler  
  
1.  Versuchen Sie nicht, eine Ausdrucksbaumstruktur mit einer Anweisung zu erstellen.  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS1945 ausgelöst:  
  
```  
// cs1945.cs using System; using System.Linq.Expressions; public delegate void D(); class Test { static void Main() { Expression<Func<int, Func<int, bool>>> tree = (x => delegate(int i) { return true; }); // CS1945 } }  
```  
  
## Siehe auch  
 [Ausdrucksbaumstrukturen](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)   
 [Anweisungen, Ausdrücke und Operatoren](/dotnet/csharp/programming-guide/statements-expressions-operators/index)
---
title: "Compilerfehler CS1951 | Microsoft Docs"
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
  - "CS1951"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1951"
ms.assetid: 799ba212-a000-44d9-b7da-a8c00eae63fa
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1951
Der Lambda\-Ausdruck einer Ausdrucksbaumstruktur darf weder einen out\-Parameter noch einen ref\-Parameter enthalten  
  
 Eine Ausdrucksbaumstruktur stellt Ausdrücke nur als Datenstrukturen dar. Es gibt keine Möglichkeit, bestimmte Speicheradressen darzustellen. Dies ist jedoch erforderlich, wenn Sie einen Parameter durch Verweis übergeben.  
  
### So beheben Sie diesen Fehler  
  
1.  Die einzige Möglichkeit, diesen Fehler zu beheben, besteht darin, den `ref`\-Modifizierer in der Delegatdefinition zu entfernen und den Parameter durch Wert zu übergeben.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS1951 generiert:  
  
```  
// cs1951.cs using System.Linq; public delegate int TestDelegate(ref int i); class Test { static void Main() { System.Linq.Expressions.Expression<TestDelegate> tree1 = (ref int x) => x; // CS1951 } }  
```  
  
## Siehe auch  
 [Ausdrucksbaumstrukturen](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)
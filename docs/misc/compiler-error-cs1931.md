---
title: "Compilerfehler CS1931 | Microsoft Docs"
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
  - "CS1931"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1931"
ms.assetid: c0071c3d-ae11-4073-87df-508150daef68
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1931
Die Bereichsvariable 'Variable' verursacht einen Konflikt mit einer früheren Deklaration von 'Variable'.  
  
 Die Deklaration einer Bereichsvariablen muss genau wie jede andere Deklaration über einen Bezeichner verfügen, der innerhalb des Deklarationsabschnitts der Variablen eindeutig ist.  
  
### So beheben Sie diesen Fehler  
  
1.  Weisen Sie der Bereichsvariablen einen eindeutigen Namen zu.  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS1931 ausgelöst, da der Bezeichner `x` sowohl als lokale Variable in `Main` als auch als Bereichsvariable im Abfrageausdruck verwendet wird:  
  
```  
// cs1931.cs class Test { static void Main() { int x = 1; var y = from x in Enumerable.Range(1, 100) // CS1931 select x; } }  
```  
  
## Siehe auch  
 [LINQ\-Abfrageausdrücke](/dotnet/csharp/programming-guide/linq-query-expressions/index)
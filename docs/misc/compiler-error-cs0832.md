---
title: "Compilerfehler CS0832 | Microsoft Docs"
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
  - "CS0832"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0832"
ms.assetid: b5527209-a9bd-4f8c-a432-2e89bb1905d1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0832
Eine Ausdrucksbaumstruktur darf keinen Zuweisungsoperator enthalten.  
  
 Eine Ausdrucksbaumstruktur behält den variablen Zustand nicht bei oder hat kein Konzept für einen Speicherort.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie den Zuweisungsoperator aus dem Lambda\- oder Abfrageausdruck.  
  
## Beispiel  
 `x` ist im Beispielcode wie in allen Lambdaausdrücken nur ein Eingabeparameter, der als Wert übergeben wird. Der Wert kann in einer Ausdrucksbaumstruktur nicht geändert werden. Er kann in einem Delegatlambdaausdruck geändert werden.  
  
```  
// cs0843.cs using System; using System.Linq; using System.Linq.Expressions; public class C { public static int Main() { Expression<Func<int, int>> e = x => x += 5; // CS0843 return 1; } }  
```
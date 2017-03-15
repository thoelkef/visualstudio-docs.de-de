---
title: "Compilerfehler CS1649 | Microsoft Docs"
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
  - "CS1649"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1649"
ms.assetid: 6355c7f2-157c-441d-8925-500062988636
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1649
An Member des schreibgeschützten Felds "Bezeichner" kann kein Verweis \(ref\) und keine Ausgabe \(out\) übergeben werden \(Ausnahme: in einem Konstruktor\).  
  
 Dieser Fehler tritt auf, wenn Sie eine Variable an eine Funktion, die ein Member eines `readonly`\-Felds ist, als `ref`\- oder `out`\-Argument übergeben. Da `ref`\- und `out`\-Parameter von der Funktion geändert werden können, ist dies nicht zulässig. Um diesen Fehler zu beheben, entfernen Sie das `readonly`\-Schlüsselwort für das Feld, oder übergeben Sie die Member des `readonly`\-Felds nicht an die Funktion. Sie könnten beispielsweise versuchen, eine temporäre Variable zu erstellen, die geändert werden kann, und die temporäre Variable als `ref`\-Argument zu übergeben, wie im folgenden Beispiel gezeigt.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1649 generiert:  
  
```  
// CS1649.cs public struct Inner { public int i; } class Outer { public readonly Inner inner = new Inner(); } class D { static void f(ref int iref) { } static void Main() { Outer outer = new Outer(); f(ref outer.inner.i);  // CS1649 // Try this code instead: // int tmp = outer.inner.i; // f(ref tmp); } }  
```
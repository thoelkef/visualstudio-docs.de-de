---
title: "Compilerfehler CS1651 | Microsoft Docs"
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
  - "CS1651"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1651"
ms.assetid: ce1043e3-b453-4b4c-b949-f344834e3845
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1651
An Felder des statischen schreibgeschützten Felds "ID" kann kein Verweis und keine Ausgabe übergeben werden \(Ausnahme: in einem statischen Konstruktor\).  
  
 Dieser Fehler tritt auf, wenn Sie eine Variable an eine Funktion übergeben, die ein Member eines statischen schreibgeschützten Felds als Ref\-Argument ist. Da Ref\-Parameter von der Funktion geändert werden können, ist dies nicht zulässig. Um diesen Fehler zu beheben, entfernen Sie das **readonly**\-Schlüsselwort für das Feld, oder übergeben Sie die Members des schreibgeschützten Feld nicht an die Funktion. Sie könnten beispielsweise versuchen, eine temporäre Variable zu erstellen, die geändert werden kann, und die temporäre Variable als Ref\-Argument zu übergeben, wie im folgenden Beispiel gezeigt.  
  
 Im folgenden Beispiel wird CS1651 generiert:  
  
```  
// CS1651.cs public struct Inner { public int i; } class Outer { public static readonly Inner inner = new Inner(); } class D { static void f(ref int iref) { } static void Main() { f(ref Outer.inner.i);  // CS1651 // Try this instead: // int tmp = Outer.inner.i; // f(ref tmp); } }  
```
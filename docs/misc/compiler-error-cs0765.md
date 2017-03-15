---
title: "Compilerfehler CS0765 | Microsoft Docs"
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
  - "CS0765"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0765"
ms.assetid: adfb1f95-f7b1-4e43-83c2-42e8531eb980
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0765
In Ausdrucksbaumstrukturen dürfen weder partielle Methoden mit nur einer definierenden Deklaration noch entfernte bedingte Methoden verwendet werden.  
  
 Obwohl es sich bei einem Aufruf einer entfernten partiellen Methode um einen Ausdruck handelt, stellt er keinen in einem Ausdrucksbaum akzeptablen Ausdruck dar.  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie eine implementierende Deklaration für die partielle Methode hinzu, oder entfernen Sie den Code, der den Ausschluss der bedingten Methode bei der Kompilation verhindert.  
  
## Beispiel  
 Mit dem folgenden Code wird CS0765 an zwei Positionen generiert:  
  
```  
// cs0765.cs using System; using System.Collections; using System.Collections.Generic; using System.Diagnostics; using System.Linq; using System.Linq.Expressions; public delegate void dele(); public class ConClass { [Conditional("CONDITION")] public static void TestMethod() { } } public partial class PartClass : IEnumerable { List<object> list = new List<object>(); partial void Add(int x); public IEnumerator GetEnumerator() { for (int i = 0; i < list.Count; i++) yield return list[i]; } static void Main() { Expression<Func<PartClass>> testExpr1 = () => new PartClass { 1, 2 }; // CS0765 Expression<dele> testExpr2 = () => ConClass.TestMethod(); // CS0765 } }  
```  
  
## Siehe auch  
 [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [Ausdrucksbaumstrukturen](../Topic/Expression%20Trees%20\(C%23%20and%20Visual%20Basic\).md)
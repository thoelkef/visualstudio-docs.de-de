---
title: "Compilerfehler CS0836 | Microsoft Docs"
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
  - "CS0836"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0836"
ms.assetid: 74a12271-1612-45aa-a398-7964e0269892
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0836
In einem konstanten Ausdruck kann kein anonymer Typ verwendet werden  
  
 Die einzigen in einem konstanten Ausdruck zulässigen Elemente sind benannte Konstanten, Literale und mathematische Ausdrücke, die konstante Ausdrücke verbinden.  
  
### So beheben Sie diesen Fehler  
  
1.  Verwandeln Sie den anonymen Typ in einen benannten Typ.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Möglichkeit zum Generieren von CS0836 dargestellt:  
  
```  
// cs0836.cs using System; [AttributeUsage(AttributeTargets.Class, AllowMultiple = true, Inherited = false)] public class A : Attribute { public A(object obj) { } } [A(new { })] // CS0836 public class B { } public class Test { public static int Main() { return 0; } }  
```
---
title: "Compilerfehler CS0431 | Microsoft Docs"
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
  - "CS0431"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0431"
ms.assetid: 05da7ea7-f33d-48d4-948e-d64be56f91ba
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0431
Der Alias "Bezeichner" kann nicht mit "::" verwendet werden, da der Alias auf einen Typ verweist. Verwenden Sie stattdessen ".".  
  
 Sie haben "::" mit einem Alias verwendet, der auf einen Typ verweist. Verwenden Sie den "."\-Operator, um diesen Fehler zu beheben.  
  
 Im folgenden Beispiel wird CS0431 generiert:  
  
```  
// CS0431.cs using A = Outer; public class Outer { public class Inner { public static void Meth() {} } } public class MyClass { public static void Main() { A::Inner.Meth();   // CS0431 A.Inner.Meth();   // OK } }  
```
---
title: "Compilerfehler CS0111 | Microsoft Docs"
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
  - "CS0111"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0111"
ms.assetid: 87afb689-f27b-451d-84eb-d6bdf17aea41
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0111
Der Typ "Klasse" definiert bereits einen Member namens "Member" mit den gleichen Parametertypen.  
  
 CS0111 tritt auf, wenn eine Klasse zwei Memberdeklarationen enthält, die denselben Namen und dieselben Parametertypen haben. Weitere Informationen finden Sie unter [Methoden](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
## Beispiel  
 Im folgenden Beispiel wird CS0111 generiert:  
  
```  
// CS0111.cs class A { void Test() { } public static void Test(){}   // CS0111 public static void Main() {} }  
```
---
title: "Compilerfehler CS0081 | Microsoft Docs"
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
  - "CS0081"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0081"
ms.assetid: a5649abc-89ea-4f64-8c3c-eb36df926561
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0081
Eine Typparameterdeklaration muss ein Bezeichner sein, kein Typ.  
  
 Wenn Sie eine generische Methode oder einen generischen Typ deklarieren, geben Sie den Typparameter als Bezeichner an, z. B. „T“ oder „inputType“. Wenn die Methode von Clientcode aufgerufen wird, liefert sie den Typ, der jedes Vorkommen des Bezeichners im Text der Methode oder Klasse ersetzt. Weitere Informationen finden Sie unter [Generische Typparameter](/dotnet/csharp/programming-guide/generics/generic-type-parameters).  
  
```  
// CS0081.cs class MyClass { public void F<int>() {}   // CS0081 public void F<T>(T input) {}   // OK public static void Main() { MyClass a = new MyClass(); a.F<int>(2); a.F<double>(.05); } }  
```  
  
## Siehe auch  
 [Generika](/dotnet/csharp/programming-guide/generics/index)
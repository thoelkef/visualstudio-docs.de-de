---
title: "Compilerfehler CS0264 | Microsoft Docs"
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
  - "CS0264"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0264"
ms.assetid: a8a87185-5915-4b0d-a8cd-2f129ea51b8f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0264
Partielle Deklarationen von „type“ müssen die gleichen Typparameternamen in der gleichen Reihenfolge aufweisen.  
  
 Dieser Fehler tritt auf, wenn Sie einen generischen Typ in partiellen Deklarationen definieren und die Namen und die Reihenfolge der Typparameter nicht in allen partiellen Deklarationen konsistent sind. Zum Beheben dieses Fehlers überprüfen Sie die Typparameter für jede partielle Deklaration, und stellen Sie sicher, dass die gleichen Namen und dieselbe Reihenfolge für die Parameter verwendet werden. Weitere Informationen finden Sie unter [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods) und [Generische Typparameter](/dotnet/csharp/programming-guide/generics/generic-type-parameters).  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS0264 generiert:  
  
```  
// CS0264.cs partial class MyClass<T>  // CS0264 { } partial class MyClass <MyType> { }  
```
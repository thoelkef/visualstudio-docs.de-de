---
title: "Compilerfehler CS0761 | Microsoft Docs"
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
  - "CS0761"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0761"
ms.assetid: b16ac1df-0ddc-44d2-89f1-8d9c32af87ad
caps.latest.revision: 5
caps.handback.revision: 5
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0761
Die Deklarationen der partiellen 'Methode\<T\>'\-Methode enthalten inkonsistente Typparametereinschränkungen.  
  
 Weist eine partielle Methode eine Implementierung auf, muss die generische Typeinschränkung mit der Einschränkung identisch sein, die für die Methodensignatur definiert wurde.  
  
### So beheben Sie diesen Fehler  
  
1.  Sorgen Sie dafür, dass die generischen Typeinschränkungen für jede Komponente der partiellen Methode identisch sind.  
  
## Beispiel  
 Mit dem folgenden Code wird CS0761 generiert:  
  
```  
// cs0761.cs using System; public partial class C { partial void Part<T>() where T : class; partial void Part<T>() where T : struct // CS0761 { } public static int Main() { return 1; } }  
  
```  
  
## Siehe auch  
 [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [Einschränkungen für Typparameter](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)
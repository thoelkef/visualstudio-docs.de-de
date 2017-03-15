---
title: "Compilerfehler CS0191 | Microsoft Docs"
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
  - "CS0191"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0191"
ms.assetid: 512479e4-656e-4dcb-8d71-801541d72dcd
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0191
Einer Eigenschaft oder einem Indexer "Name" kann nichts zugewiesen werden \-\- sie sind schreibgeschützt.  
  
 Für ein [readonly](/dotnet/csharp/language-reference/keywords/readonly)\-Feld kann eine Zuweisung nur in einem Konstruktor oder bei der Deklaration erfolgen. Weitere Informationen finden Sie unter [Konstruktoren](/dotnet/csharp/programming-guide/classes-and-structs/constructors).  
  
 CS0191 wird auch ausgegeben, wenn das `readonly`\-Feld [static](/dotnet/csharp/language-reference/keywords/static) ist und der Konstruktor nicht als `static` markiert ist.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0191 generiert:  
  
```  
// CS0191.cs class MyClass { public readonly int TestInt = 6;  // OK to assign to readonly field in declaration MyClass() { TestInt = 11; // OK to assign to readonly field in constructor } public void TestReadOnly() { TestInt = 19;                  // CS0191 } public static void Main() { } }  
```
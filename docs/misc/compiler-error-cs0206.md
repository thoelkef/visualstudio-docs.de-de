---
title: "Compilerfehler CS0206 | Microsoft Docs"
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
  - "CS0206"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0206"
ms.assetid: d2f9838a-d8ae-4342-b8bd-fa5745619a26
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0206
Eine Eigenschaft oder ein Indexer kann nicht als out\- oder ref\-Parameter übergeben werden.  
  
 Es ist keine [Eigenschaft](/dotnet/csharp/programming-guide/classes-and-structs/properties) verfügbar, die als [ref](/dotnet/csharp/language-reference/keywords/ref)\- oder [out](/dotnet/csharp/language-reference/keywords/out)\-Parameter übergeben werden könnte. Weitere Informationen finden Sie unter [Übergeben von Parametern](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).  
  
## Beispiel  
 Im folgenden Beispiel wird CS0206 generiert:  
  
```  
// CS0206.cs public class MyClass { public static int P { get { return 0; } set { } } public static void MyMeth(ref int i) // public static void MyMeth(int i) { } public static void Main() { MyMeth(ref P);   // CS0206 // try the following line instead // MyMeth(P);   // CS0206 } }  
```
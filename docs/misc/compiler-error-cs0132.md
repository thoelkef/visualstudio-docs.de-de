---
title: "Compilerfehler CS0132 | Microsoft Docs"
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
  - "CS0132"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0132"
ms.assetid: e8ad1281-2912-4b6a-b2af-a319a23ddd16
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0132
'Konstruktor': Ein statischer Konstruktor muss parameterlos sein.  
  
 Ein [statischer](/dotnet/csharp/language-reference/keywords/static) Konstruktor kann nicht mit einem oder mehreren Parametern deklariert werden. Weitere Informationen finden Sie unter [Konstruktoren](/dotnet/csharp/programming-guide/classes-and-structs/constructors).  
  
 Im folgenden Beispiel wird CS0132 generiert:  
  
```  
// CS0132.cs namespace MyNamespace { public class MyClass { public MyClass(int i) { } } public class MyClass2 : MyClass { static MyClass2(int i)   // CS0132 { } } }  
```
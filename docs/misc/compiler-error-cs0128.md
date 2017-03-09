---
title: "Compilerfehler CS0128 | Microsoft Docs"
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
  - "CS0128"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0128"
ms.assetid: 35db9025-2bed-437f-a78a-f2862766bde2
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0128
Eine lokale Variable mit dem Namen "Variable" ist bereits in diesem Bereich definiert  
  
 Der Compiler hat Deklarationen zweier lokaler Variablen mit demselben Namen gefunden. Weitere Informationen finden Sie unter [Methoden](/dotnet/csharp/programming-guide/classes-and-structs/methods).  
  
 Im folgenden Beispiel wird CS0128 generiert:  
  
```  
// CS0128.cs namespace MyNamespace { public class MyClass { public static void Main() { char i; int i;   // CS0128 } } }  
```
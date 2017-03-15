---
title: "Compilerfehler CS0101 | Microsoft Docs"
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
  - "CS0101"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0101"
ms.assetid: edb5246b-c16b-4845-bb2d-0ef769d014c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0101
Der Namespace 'Namespace' enthält bereits eine Definition für 'Typ'.  
  
 Ein [Namespace](/dotnet/csharp/language-reference/keywords/namespace) weist doppelte Bezeichner auf. Benennen Sie einen der doppelten Bezeichner um oder löschen Sie ihn. Weitere Informationen finden Sie unter [Namespaces](/dotnet/csharp/programming-guide/namespaces/index)  
  
 Im folgenden Beispiel wird CS0101 generiert:  
  
```  
// CS0101.cs namespace MyNamespace { public class MyClass { static public void Main() { } } public class MyClass   // CS0101 { } }  
```
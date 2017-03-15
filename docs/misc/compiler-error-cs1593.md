---
title: "Compilerfehler CS1593 | Microsoft Docs"
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
  - "CS1593"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1593"
ms.assetid: 7476e799-8a8d-457d-b4e7-2d5e073799d8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1593
Der Delegat "del" akzeptiert "number"\-Argumente nicht  
  
 Die Anzahl der an einen [Delegat](/dotnet/csharp/language-reference/keywords/delegate)aufruf übergebenen Argumente stimmt nicht mit der Anzahl der Parameter in der Delegatdeklaration überein.  
  
 Im folgenden Beispiel wird CS1593 generiert:  
  
```  
// CS1593.cs using System; delegate string func(int i);   // declare delegate class a { public static void Main() { func dt = new func(z); x(dt); } public static string z(int j) { Console.WriteLine(j); return j.ToString(); } public static void x(func hello) { hello(8, 9);   // CS1593 // try the following line instead // hello(8); } }  
```
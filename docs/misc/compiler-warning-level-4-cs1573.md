---
title: "Compilerwarnung (Stufe 4) CS1573 | Microsoft Docs"
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
  - "CS1573"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1573"
ms.assetid: 1b68cb1a-9bfd-4343-b9b6-8ce195af5e23
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 4) CS1573
Der Parameter 'parameter' besitzt kein übereinstimmendes param\-Tag im XML\-Kommentar für 'parameter' \(andere Parameter jedoch schon\)  
  
 Bei Verwendung der [\/doc](/dotnet/csharp/language-reference/compiler-options/doc-compiler-option)\-Compileroption wurde ein Kommentar für einige Parameter, aber nicht für alle Parameter in einer Methode angegeben. Möglicherweise haben Sie vergessen, für diese Parameter einen Kommentar einzugeben.  
  
 Im folgenden Beispiel wird CS1573 generiert:  
  
```  
// CS1573.cs // compile with: /W:4 public class MyClass { /// <param name='Int1'>Used to indicate status.</param> // enter a comment for Char1? public static void MyMethod(int Int1, char Char1) { } public static void Main () { } }  
```
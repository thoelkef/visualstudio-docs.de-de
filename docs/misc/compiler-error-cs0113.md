---
title: "Compilerfehler CS0113 | Microsoft Docs"
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
  - "CS0113"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0113"
ms.assetid: 43c5c0b7-67c0-45c1-8363-21c844c094f3
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0113
Ein Member "Funktion", der als "override" markiert ist, kann nicht als "new" oder "virtual" markiert werden.  
  
 Die zum Markieren einer Methode verwendeten Schlüsselwörter [new](/dotnet/csharp/language-reference/keywords/new) und [override](/dotnet/csharp/language-reference/keywords/override) schließen sich gegenseitig aus.  
  
 Im folgenden Beispiel wird CS0113 generiert:  
  
```  
// CS0113.cs namespace MyNamespace { abstract public class MyClass { public abstract void Foo(); } public class MyClass2 : MyClass { override new public void Foo()   // CS0113, remove new keyword { } public static int Main() { return 0; } } }  
```
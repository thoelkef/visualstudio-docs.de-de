---
title: "Compilerfehler CS0438 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0438"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0438"
ms.assetid: 92c91ecb-8d6a-4850-84eb-c095c3c957f1
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0438
Der Typ 'typ' in 'modul\_1' verursacht einen Konflikt mit dem Namespace 'namespace' in 'modul\_2'.  
  
 Dieser Fehler tritt auf, wenn ein Typ in einer Quelldatei im Konflikt mit einem Namespace in einer anderen Quelldatei steht. Dies tritt meistens dann auf, wenn einer oder beide aus einem hinzugefügten Modul stammen. Um das Problem zu beheben, benennen Sie den Typ oder den Namespace um, der den Konflikt verursacht hat.  
  
 Im folgenden Beispiel wird CS0438 generiert:  
  
 Kompilieren Sie zuerst diese Datei:  
  
```  
// CS0438_1.cs // compile with: /target:module public class Util { public class A { } }  
```  
  
 Kompilieren Sie dann diese Datei:  
  
```  
// CS0438_2.cs // compile with: /target:module namespace Util { public class A { } }  
```  
  
 Und kompilieren Sie dann diese Datei:  
  
```  
// CS0438_3.cs // compile with: /addmodule:CS0438_1.netmodule /addmodule:CS0438_2.netmodule using System; public class Test { public static void Main() { Console.WriteLine(typeof(Util.A));   // CS0438 } }  
  
```
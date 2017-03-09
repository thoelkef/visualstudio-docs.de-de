---
title: "Compilerfehler CS1511 | Microsoft Docs"
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
  - "CS1511"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1511"
ms.assetid: c04b5268-5bc3-41db-af6b-463ab1d802b4
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1511
Das base\-Schlüsselwort ist in einer statischen Methode nicht verfügbar.  
  
 Das [basis](/dotnet/csharp/language-reference/keywords/base)\-Schlüsselwort wurde in einer [statischen](/dotnet/csharp/language-reference/keywords/static) Methode verwendet.`base` kann nur in einem Instanzkonstruktor, in einer Instanzmethode oder in einem Instanzaccessor aufgerufen werden.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1511 generiert:  
  
```  
// CS1511.cs // compile with: /target:library public class A { public int j = 0; } class C : A { public void Method() { base.j = 3;   // base allowed here } public static int StaticMethod() { base.j = 3;   // CS1511 return 1; } }  
```